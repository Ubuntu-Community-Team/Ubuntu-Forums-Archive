---
title: "saving multiple .cr2 files as .jpg files"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by naomibrown on 2010-03-04
Hi,

I'm wanting to save multiple .cr2 files as .jpg files. Is it possible to do that using the command line?

At the moment I'm using:

convert IMG_7119.CR2 1.jpg but there must be a way to do this for a whole folder at once!

Thanks,

---

### Post by earthpigg on 2010-03-04
you just want to rename them from cr2 to .jpg?

navigate to the directory where you have them all.

```
rename .cr2 .jpg *.cr2
```

that will keep existing filenames, but change the extension... blabla555.cr2 will become blabla555.jpg.

and if you want to undo that:

```
rename .jpg .cr2 *.jpg
```


EDIT: ah, just googled .cr2. it may not be as simple as i make it out to be above, but it may be worth trying first, in case it is. the directions to undo the experiment are there if it fails. i did find this link: [http://marc.merlins.org/linux/technotes/cr2_dcraw_jhead.html](http://marc.merlins.org/linux/technotes/cr2_dcraw_jhead.html)

edit2: [http://marc.merlins.org/linux/technotes/cr2_dcraw_jhead.html](http://marc.merlins.org/linux/technotes/cr2_dcraw_jhead.html)

---

### Post by kaibob on 2010-03-04
The following commmand will do what you want. It retains the original files and creates new JPG images with the same base name but with the jpg extension. As a precaution, use some test files initially to insure that it works as you want. 

```
mogrify -format jpg *.CR2
```

I assume that the conversion from CR2 to JPG has worked for you before.

---

### Post by naomibrown on 2010-03-14
It has worked before, but I just forgot how it works.

I tried what you said kaibob but it doesn't seem to work :( 

None of the files are changing to be jpegs and it seems to be "stuck" on a blank line in the terminal. 

I must be doing something really stupid wrong.

---

### Post by naomibrown on 2010-03-17
I still can't get this to work :(

---

### Post by naomibrown on 2010-03-17
When I try the link: [http://marc.merlins.org/linux/technotes/cr2_dcraw_jhead.html]("http://marc.merlins.org/linux/technotes/cr2_dcraw_jhead.html")


I get: 

```
naomi@sam:~/Desktop$ for i in *.cr2; do dcraw -c -q 0 -B 2 4 -w -H 5 -b 8 $i | cjpeg -quality 80 > $i.jpg; done
Unknown option "-B".
Empty input file
naomi@sam:~/Desktop$ 
```

I've also found this script on my travels, but I don't know how to use it, or if it is what I want to do!

```
#!/bin/bash
DCRAW="dcraw -w -c "


while [ $# -ge 1 ]
do

targetdir="$1"

for rawfile in "$targetdir"/*.[cC][rR][wW]

do
    	
    OJPEG=$(echo "$rawfile"| perl -pe 's/\.crw$//i' | tr 'A-Z' 'a-z')'.jpeg'
    echo "${DCRAW} "$rawfile" | cjpeg > ${OJPEG}"
    ${DCRAW} -q 3 "$rawfile" | cjpeg -quality 100 > "${OJPEG}" || echo " *PROBLEM*"
    # transfer EXIF data from the original raw file
    exiftool -overwrite_original -TagsFromFile "$rawfile" "${OJPEG}" >/dev/null
    # preserve timestamps as much as possible
    # touch -r "$rawfile" "${OJPEG}"
    dcraw -z "${OJPEG}"

    # UNCOMMENT to delete raw files:
    # rm -f "$rawfile"

done
    shift
    
done
```

Thanks! :)

---

### Post by naomibrown on 2010-03-24
I still haven't had any luck :(

---

### Post by naomibrown on 2010-04-04
I still haven't got any alternatives to work.

I've tried my old method today (convert IMG_7119.CR2 1.jpg) and it didn't work :( 

This is the error that I got.

```

convert: Delegate failed `"ufraw-batch" --silent --wb=camera --black-point=auto --exposure=auto --create-id=also --out-type=ppm --out-depth=16 "--output=%u.pnm" "%i"' @ delegate.c/InvokeDelegate/1015.
convert: unable to open image `/tmp/magick-XXUT661S.pnm': No such file or directory @ blob.c/OpenBlob/2439.
convert: missing an image filename `7409.jpg' @ convert.c/ConvertImageCommand/2775.

```

---

### Post by airblade on 2010-09-13
I got this working, using Ubuntu 10.04 LTS x64.

```
for i in *.CR2; do dcraw -c $i | ppmtojpeg > jpeg/`basename $i CR2`jpg; echo $i done; done
```

---

### Post by Nemo_bis on 2012-06-13
In case someone wants to use imagemagick as in the original request.

> **naomibrown said:**
> I still haven't got any alternatives to work.

I've tried my old method today (convert IMG_7119.CR2 1.jpg) and it didn't work :( 

This is the error that I got.
You're missing some dependency, probably ufraw or ufraw-batch (I had the latter but not the former, for instance): install it. You can check the list of delegates you need to install by typing convert -list configure.
See [http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=17848](http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=17848)

---

### Post by lisati on 2012-06-13
Back to sleep, old thread!

---

