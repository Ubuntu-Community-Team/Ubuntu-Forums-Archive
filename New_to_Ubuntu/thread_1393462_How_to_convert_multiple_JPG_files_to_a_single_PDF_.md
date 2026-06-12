---
title: "How to convert multiple JPG files to a single PDF file in one command line?"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-29
Hello
 
How to convert multiple JPG files to a single PDF file in one command line?
How to make such challenge, 1 single command line (or already made script)?
Hello

---

### Post by inobe on 2010-01-29
```
convert file.pdf file.jpg

```

i don't know how to print multiples from terminal.

there is an app that will do it [http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/)

---

### Post by frenchn00b on 2010-01-29
OK, 

I start the script
```

#!/bin/sh

ProcedureScanning {

echo "Scanning " | festival --tts
cd
DEVIT=`scanimage -L`
echo "$DEVIT  selected "
DEVI=$(echo "$DEVIT" | grep snap  | cut -d" " -f2 | sed s/\`//g  |   sed s/\'//g)
echo "$DEVI  selected "
rm /tmp/autoscanning78.ppm
echo "Scanning ... "
echo "scanimage --mode color  -d  $DEVI > /tmp/autoscanning78.ppm"
scanimage -d $DEVI --mode color > test.ppm
cp test.ppm /tmp/autoscanning78.ppm
mkdir -p "$HOME/scanned"
convert -rotate 180 /tmp/autoscanning78.ppm "$HOME/scanned/$( date +%Y%m%d%H%M%S)scanned.jpg"

}

echo "Enter Return to scan or something else to merge the jpg to a single PDF:" 
inputuserreturnyn=""
while [  "`read inputuserreturnyn`" = ""  ]  ; do 
     echo "Enter Return to scan or something else to merge the jpg to a single PDF:" 
     ProcedureScanning
done 

cd
cd scanned

for each in *.jpg ; do 

filename="$each"
basename=${filename%.*}
extension=${filename##*.}

### Can someone continue this script and make it better and into the github or the sourceforge...
## needs imagemagik installed and pdftk
convert basename.jpg basename.pdf
done 

for each in *.pdf ; do 
   pdftk ... ## I forgot how it works
done

 


```


**### Can someone continue this script and make it better and into the github or the sourceforge...**

---

