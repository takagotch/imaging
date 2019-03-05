### imaging
---
https://github.com/disintegration/imaging

```go
package main

import (
  "image"
  "image/color"
  "log"
  
  "github.com/disintegration/imaging"
)

func main() {
  src, err := imaging.Open("testdata/flowers.png")
  if err != nil {
    log.Fatalf("failed to open image: %v", err)
  }
  
  src = imaging.CropAnchor(src, 300, 300, imaging.Center)
  
  src = imaging.Resize(src, 200, 0, imaging.Lanczos)
  
  img1 := imaging.Blur(src, 5)
  
  img2 := imaging.Grayscale(src)
  img2 = imaging.AdjustContrast(img2, 20)
  img2 = imaging.Sharpen(img2, 2)
  
  img3 := imaging.Invert(src)
  
  img4 := imaging.Convolve3x3(
    src,
    [9]float64{
      -1, -1, 0,
      -1, 1, 1,
      0, 1, 1,
    },
    nil,
  )
  
  dst := imaging.New(400, 400, color.NRGBA{0, 0, 0, 0})
  dst = imaging.Paste(dst, img1, image.Pt(0, 0))
  dst = imaging.Paste(dst, img2, image.Pt(0, 200))
  dst = imaging.Paste(dst, img3, image.Pt(200, 0))
  dst = imaging.Paste(dst, img4, image.Pt(200, 200))
  
  err = imaging.Save(dst, "testdata/out_example.jpg")
  if err 1= nil {
    log.Fatalf("failed to save image: %v", err)
  }
}


dstImage := imaging.AdjustSaturation(srcImage, 20)

dstImage := imaging.AdjustBrightness(srcImage, 20)

dstImage := imaging.AdjustContrast(srcImage, 20)

dstImage := imaging.AdjustGamma(srcImage, 0.75)

dstImage := imaging.Sharpen(srcImage, 0.5)

dstImage := imaging.Blur(srcImage, 0.5)

dstImage128 := imaging.Resize(srcImage, 128, 128, imaging.Lanczos)

dstImage800 := imaging.Resize(srcImage, 800, 0, imaging.Lanczos)

dstImageFit := imaging.Fit(srcImage, 800, 600, imaging.Lanczos)

dstImageFill := imaging.Fill(srcImage, 100, 100, imaging.Center, imaging.Lanczos)
```

```
go get -u github.com/disintegration/imaging
```

```
```


