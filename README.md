# image_to_string
画像から文字列を抽出する

# installation
- Tesseract OCR
```
brew install tesseract
```

- 学習データ
download from https://github.com/tesseract-ocr/tesseract/wiki/Data-Files
to /usr/local/share/tessdata

- PyOCR
```
sudo pip3 install pyocr
```

# example source code
from https://qiita.com/nabechi6011/items/3a367ca94dbd208efcc7
```
from PIL import Image
import sys

import pyocr
import pyocr.builders

tools = pyocr.get_available_tools()
if len(tools) == 0:
    print("No OCR tool found")
    sys.exit(1)

tool = tools[0]
print("Will use tool '%s'" % (tool.get_name()))

txt = tool.image_to_string(
    Image.open("[ファイル名]"),
    lang="jpn",
    builder=pyocr.builders.TextBuilder(tesseract_layout=6)
)
print( txt )
```

## referrence
- Tesseract+PyOCRで簡易OCRを試してみる
https://qiita.com/nabechi6011/items/3a367ca94dbd208efcc7
- tesseract datafile
https://github.com/tesseract-ocr/tesseract/wiki/Data-Files
- pyocr
https://gitlab.gnome.org/World/OpenPaperwork/pyocr