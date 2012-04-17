[![Build Status](https://secure.travis-ci.org/deepakjois/blaze-svg.png)](http://travis-ci.org/deepakjois/blaze-svg)

blaze-svg uses [blaze-markup] to provide a SVG combinator library. blaze-markup
is a fast combinator library which was derived from [blaze-html].
 
[blaze-markup]: http://github.com/jaspervdj/blaze-markup
[blaze-html]: http://jaspervdj.be/blaze/

## Usage

Read the [blaze-html tutorial][tutorial] to get a better understanding of how to 
construct markup documents using these combinators.

[tutorial]: http://jaspervdj.be/blaze/tutorial.html

Here is a small example program that demonstrates its usage.
 
```
{-# LANGUAGE OverloadedStrings #-}
module Example where
import Text.Blaze.Svg11 ((!))
import qualified Text.Blaze.Svg11 as S
import qualified Text.Blaze.Svg11.Attributes as A
import Text.Blaze.Svg.Renderer.String (renderSvg)

main :: IO ()
main = do
  let a = renderSvg svgDoc
  putStrLn a

svgDoc :: S.Svg
svgDoc = S.docTypeSvg ! A.version "1.1" ! A.width "150" ! A.height "100" ! A.viewbox "0 0 3 2" $ do
    S.rect ! A.width "1" ! A.height "2" ! A.fill "#008d46"
    S.rect ! A.width "1" ! A.height "2" ! A.fill "#ffffff"
    S.rect ! A.width "1" ! A.height "2" ! A.fill "#d2232c"
```

This produces the output below (formatted for readability)

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
    "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="150" height="100" viewBox="0 0 3 2">
  <rect width="1" height="2" fill="#008d46" />
  <rect width="1" height=" 2" fill="#ffffff" />
  <rect width="1" height="2" fill="#d2232c" />
</svg>
```
