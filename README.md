# swift_core_graphics_tutorial

### Core Graphics

Core Graphics is Apple’s vector drawing framework. It’s a big, powerful application programming interface (API) with many tools to master and cool features like

### Core Image

[https://www.techotopia.com/index.php/An_iOS_8_Swift_Graphics_Tutorial_using_Core_Graphics_and_Core_Image](https://www.techotopia.com/index.php/An_iOS_8_Swift_Graphics_Tutorial_using_Core_Graphics_and_Core_Image)

### Core Image Intro

[https://www.objc.io/issues/21-camera-and-photos/core-image-intro/](https://www.objc.io/issues/21-camera-and-photos/core-image-intro/)

```swift
//
//  DrawViews.swift
//  SwiftCoreGraphics
//
//  Created by shin seunghyun on 2020/06/30.
//  Copyright © 2020 shin seunghyun. All rights reserved.
//

/**
 About Core Graphics
 https://www.techotopia.com/index.php/An_iOS_8_Swift_Graphics_Tutorial_using_Core_Graphics_and_Core_Image
 **/

/**
 About Core Image
 https://www.objc.io/issues/21-camera-and-photos/core-image-intro/
 **/

import UIKit
//import CoreImage

class Draw2D: UIView {
    
    override func draw(_ rect: CGRect) {
        super.draw(rect)
        //Drawing Code
        
        drawImageWithFilter()
        
    }
    
    private func drawLineBlue() {
            /** Drawing a line **/
            
            /* Initialize CGContext */
            let context: CGContext? = UIGraphicsGetCurrentContext()
            context?.setLineWidth(2.0)
            
            /* Apply Color to Stroke */
            context?.setStrokeColor(UIColor.blue.cgColor)
            
            /* Start Point */
            context?.move(to: CGPoint(x: 30, y: 30))
            
            /* Add Line */
            context?.addLine(to: CGPoint(x: 300, y: 400))
            
            /* Draw */
            context?.strokePath()
    }
    
    private func drawLineWithCustomBlue() {
            /** Drawing a line **/
            
            /* Initialize CGContext */
            let context: CGContext? = UIGraphicsGetCurrentContext()
            context?.setLineWidth(2.0)
            
            /* Create Color */
            let colorSpace: CGColorSpace = CGColorSpaceCreateDeviceRGB()
            let components: [CGFloat] = [0.0, 0.0, 1.0, 1.0]
            let color: CGColor? = CGColor(colorSpace: colorSpace, components: components)
            
            
            /* Apply Color to Stroke */
            context?.setStrokeColor(color!)
            
            /* Start Point */
            context?.move(to: CGPoint(x: 30, y: 30))
            
            /* Add Line */
            context?.addLine(to: CGPoint(x: 300, y: 400))
            
            /* Draw */
            context?.strokePath()
    }
    
    private func drawDiagonal() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(2.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        context?.move(to: CGPoint(x: 100, y: 100))
        context?.addLine(to: CGPoint(x: 150, y: 150))
        context?.addLine(to: CGPoint(x: 100, y: 200))
        context?.addLine(to: CGPoint(x: 50, y: 150))
        context?.addLine(to: CGPoint(x: 100, y: 100))
        context?.strokePath()
    }
    
    private func drawSquare() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(2.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        /* Rectangle */
        let rectangle: CGRect = CGRect(x: 60, y: 170, width: 200, height: 80)
        /* Add Rect */
        context?.addRect(rectangle)
        context?.strokePath()
    }
    
    private func drawCircle() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(2.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        /* Rectangle */
        let rectangle: CGRect = CGRect(x: 60, y: 170, width: 200, height: 80)
        /* Add Ellipse */
        context?.addEllipse(in: rectangle)
        context?.strokePath()
    }
    
    private func drawPathWithFillColor() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.move(to: CGPoint(x: 100, y: 100))
        context?.addLine(to: CGPoint(x: 150, y: 150))
        context?.addLine(to: CGPoint(x: 100, y: 200))
        context?.addLine(to: CGPoint(x: 50, y: 150))
        context?.addLine(to: CGPoint(x: 100, y: 100))
        /* setFillColor */
        context?.setFillColor(UIColor.red.cgColor)
        /* fillPath */
        context?.fillPath()
    }
    
    
    private func drawPathWithFillColorAndBorder() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(4.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        let rectangle: CGRect = CGRect(x: 60, y: 170, width: 200, height: 80)
        context?.addRect(rectangle)
        context?.strokePath() //stroke path when using fillColor draws border
        context?.setFillColor(UIColor.red.cgColor)
        context?.fill(rectangle)
    }
 
    private func drawArc() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(4.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        context?.move(to: CGPoint(x: 100, y: 100))
        //add Arc
        context?.addArc(
            tangent1End: CGPoint(x: 100, y: 200),
            tangent2End: CGPoint(x: 300, y: 200),
            radius: 100)
        context?.strokePath()
    }
    
    private func drawCubicBezierCurve() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(4.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        context?.move(to: CGPoint(x: 10, y: 10))
        context?.addCurve(to: CGPoint(x: 0, y: 50),
                          control1: CGPoint(x: 300, y: 250),
                          control2: CGPoint(x: 300, y: 40))
        context?.strokePath()
    }
    
    private func drawQuadraticBezierCurve() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(4.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        context?.move(to: CGPoint(x: 10, y: 200))
        context?.addQuadCurve(
            to: CGPoint(x: 300, y: 200),
            control: CGPoint(x: 150, y: 10))
        context?.strokePath()
    }
    
    private func drawDashedLine() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        context?.setLineWidth(20.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        let dashArray: [CGFloat] = [2, 6, 4, 2]
        context?.setLineDash(phase: 3, lengths: dashArray)
        context?.move(to: CGPoint(x: 10, y: 200))
        context?.addQuadCurve(to: CGPoint(x: 300, y: 200),
                              control: CGPoint(x: 150, y: 10))
        context?.strokePath()
    }
    
    private func drawShadows() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        let shadowOffset: CGSize = CGSize(width: -10, height: 15)
        context?.saveGState()
        context?.setShadow(offset: shadowOffset, blur: 5)
        context?.setLineWidth(4.0)
        context?.setStrokeColor(UIColor.blue.cgColor)
        let rectangle: CGRect = CGRect(x: 60, y: 170, width: 200, height: 80)
        context?.addEllipse(in: rectangle)
        context?.strokePath()
        context?.restoreGState()
    }
    
    private func drawGradient() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        let colorSpace: CGColorSpace = CGColorSpaceCreateDeviceRGB()
        let colors = [
            UIColor.red.cgColor,
            UIColor.gray.cgColor,
            UIColor.blue.cgColor,
            UIColor.yellow.cgColor
        ]
        let locations: [CGFloat] = [0.0, 0.25, 0.5, 0.75]
        let gradient: CGGradient? = CGGradient(colorsSpace: colorSpace, colors: colors as CFArray, locations: locations)
        var startPoint: CGPoint = CGPoint()
        var endPoint: CGPoint = CGPoint()
        startPoint.x = 0.0
        startPoint.y = 0.0
        endPoint.x = 600
        endPoint.y = 600
        context?.drawLinearGradient(gradient!, start: startPoint, end: endPoint, options: .drawsBeforeStartLocation)
    }
    
    private func drawRadialGradient() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        let colorSpace: CGColorSpace = CGColorSpaceCreateDeviceRGB()
        let colors = [
            UIColor.red.cgColor,
            UIColor.green.cgColor,
            UIColor.cyan.cgColor
        ]
        let locations: [CGFloat] = [0.0, 0.5, 1.0]
        let graident: CGGradient? = CGGradient(colorsSpace: colorSpace, colors: colors as CFArray, locations: locations)
        var startPoint: CGPoint = CGPoint()
        var endPoint: CGPoint = CGPoint()
        startPoint.x = 100
        startPoint.y = 100
        endPoint.x = 200
        endPoint.y = 200
        let startRadius: CGFloat = 10
        let endRadius: CGFloat = 75
        context?.drawRadialGradient(graident!, startCenter: startPoint, startRadius: startRadius, endCenter: endPoint, endRadius: endRadius, options: [])
    }
    
    private func drawRadialGrandientWithOption() {
        let context: CGContext? = UIGraphicsGetCurrentContext()
        let colorSpace: CGColorSpace = CGColorSpaceCreateDeviceRGB()
        let colors = [
            UIColor.red.cgColor,
            UIColor.green.cgColor,
            UIColor.cyan.cgColor
        ]
        let locations: [CGFloat] = [0.0, 0.5, 1.0]
        let graident: CGGradient? = CGGradient(colorsSpace: colorSpace, colors: colors as CFArray, locations: locations)
        var startPoint: CGPoint = CGPoint()
        var endPoint: CGPoint = CGPoint()
        startPoint.x = 100
        startPoint.y = 100
        endPoint.x = 200
        endPoint.y = 200
        let startRadius: CGFloat = 10
        let endRadius: CGFloat = 75
        context?.drawRadialGradient(graident!, startCenter: startPoint, startRadius: startRadius, endCenter: endPoint, endRadius: endRadius, options: .drawsBeforeStartLocation)
    }
    
    private func drawImageIntoGraphicContext() {
        let image: UIImage = UIImage(named: "paris.jpg")!
        let imagePoint: CGPoint = CGPoint(x: 0, y: 0)
        image.draw(at: imagePoint)
    }
    
    /*
     Core Image was introduced with iOS 5 and provides a mechanism for filtering and manipulating still images and videos. Included with Core Image is a wide range of different filters together with the ability to build custom filters to meet specific requirements. Examples of filters that may be applied include cropping, color effects, blurring, warping, transformations and gradients. A full listing of filters is available in Apple’s Core Image Filter Reference document which is located in the iOS Developer portal.
     */
    /***
    Available Filters
     - cropping
     - color effects
     - blurring
     - warping
     - transformations
     - gradients
     ***/
    /*
     A CIImage object is typically initialized with a reference to the image to be manipulated. A CIFilter object is then created and configured with the type of filtering to be performed, together with any input parameters required by that filter. The CIFilter object is then instructed to perform the operation and the modified image is subsequently returned in the form of a CIImage object. The application’s CIContext reference may then be used to render the image for display to the user.
     */
    private func drawImageWithFilter() {
        let myImage: UIImage = UIImage(named: "paris.jpg")!
        let ciImage = CIImage(image: myImage)
        let sepiaFilter: CIFilter? = CIFilter(name: "CISepiaTone")
        sepiaFilter!.setDefaults()
        sepiaFilter!.setValue(ciImage, forKey: "inputImage")
        sepiaFilter!.setValue(NSNumber(value: 0.8 as Float),
                     forKey: "inputIntensity")
        let image: CIImage? = sepiaFilter!.outputImage
        let context: CIContext = CIContext(options: nil)
        
        /* import CGImage */
        let cgImage: CGImage? = context.createCGImage(image!,
                     from: image!.extent)
        
        let resultImage: UIImage = UIImage(cgImage: cgImage!)
        let imageRect: CGRect = UIScreen.main.bounds
        resultImage.draw(in: imageRect)
    }
    
}
```
