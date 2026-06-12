---
title: "Can I convert all folder contents from .jpg to .pdf?"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by kansasnoob on 2009-04-03
I actually have the job done so there is no urgency.

An old friend sent me a butt-load of text files (regarding taxes) in a .zip. No problem there but after extracting all files they were produced in .jpg rather than the proper format - .pdf!

So after unzipping all files I had to go thru and change every folder from .jpg to .pdf so I could use Abiword to print things in the proper format.

What I couldn't figure out was how to convert *ALL* contents of the folder to .pdf. I'm sure there must be a better way. I just ticked rename on each folder/file and changed the .jpg to .pdf and I got it all done, but it seemed a bit tedious (even though it only took about 10 minutes).

---

### Post by LeWench on 2009-04-03
I think there is a print option that will allow you to print to PDF. You can select all, print, select the directory to store and you should be set.

---

### Post by coffeecat on 2009-04-03
> **kansasnoob said:**
> I just ticked rename on each folder/file and changed the .jpg to .pdf and I got it all done, but it seemed a bit tedious (even though it only took about 10 minutes).

You've haven't converted the files to PDFs, you've just renamed them. Unix OSs (such as Linux and MacOS) don't rely on filename extensions to determine the file type. They look at some metadata somewhere near the beginning of the file. What you have there are a load of JPEGs with .pdf filename extensions. If you double-click on them, Linux or MacOS will use the default software for JPEGs to open them. Because they will open, you'll think you've been successful. Sorry - you're looking at a JPEG.

But if you double-click on them in Windows, goodness only knows what will happen. :? If you need to send those JPEGs masquerading as PDFs to someone with a Windows computer you might want to do some checking first. Like trying to open them in Windows and see if it tries to use photo software or adobe reader.

**Edit:** actually Ubuntu will open a jpeg renamed to .pdf in Evince and Evince will display it quite happily - because Evince will open jpegs as well. But Acroread (Adobe reader) won't. A jpeg renamed to .pdf gives me 'not supported filetype' error.

---

### Post by kanikilu on 2009-04-03
Also, you can do this from the command line with ImageMagick's **convert** utility. It's as simple as ```
convert file.jpg file.pdf
``` And it will give you a "real" PDF, not just a renamed JPG ;)

As for doing a whole directory, I'm sure it can be done with a pretty simple shell script, but I'm not really good with that, so hopefully someone else can answer that...

---

### Post by ibuclaw on 2009-04-03
To test what type of file one is:
```
file **Filename**.jpg
```
An example output: **Filename.jpg: JPEG image data, JFIF standard 1.01**

**Scenario 1)**
If the files turn out to be jpegs and you want to convert it to a **pdf**. Install imagemagick.
```
sudo apt-get install imagemagick
```
Then run **convert**
```
convert **Filename**.jpg **Filename**.pdf
```
Or to make it more automated, type in:
```
function jpg2pdf { while [ -n "$1" ]; do convert "$1" "$1".pdf; rename 's/\.jpg(\.pdf)$/$1/' "$1".pdf; shift; done; }
```

Then type in:
```
jpg2pdf *.jpg
```
And all .jpg files in the directory you are in will be converted to pdfs in a matter of seconds.


**Scenario 2)**
If the files were PDFs, but had a **jpg** extension for whatever reason.
```
rename 's/\.jpg$/\.pdf/' *.jpg
```

Regards
Iain

---

### Post by stchman on 2009-04-03
> **kansasnoob said:**
> I actually have the job done so there is no urgency.

An old friend sent me a butt-load of text files (regarding taxes) in a .zip. No problem there but after extracting all files they were produced in .jpg rather than the proper format - .pdf!

So after unzipping all files I had to go thru and change every folder from .jpg to .pdf so I could use Abiword to print things in the proper format.

What I couldn't figure out was how to convert *ALL* contents of the folder to .pdf. I'm sure there must be a better way. I just ticked rename on each folder/file and changed the .jpg to .pdf and I got it all done, but it seemed a bit tedious (even though it only took about 10 minutes).

Changing the extension will not solve your problem.  A .jpg is a picture and .pdf is portable document format.  AFAIK Evince has no ability to display jpeg files.  You should use the image viewer to view and print jpeg files.

---

### Post by coffeecat on 2009-04-03
> **stchman said:**
> AFAIK Evince has no ability to display jpeg files.

It took me by surprise too, but.. Oh, yes it does!

At least the version in Jaunty does.

**Edit:** just found out that it opens .png, .svg and .bmp files as well. A bit of an unsung hero is our Evince.

---

### Post by leandromartinez98 on 2009-04-03
Rename back your files to jpg, as others suggest. And this is another
way to do the conversion of all of them using convert:

$ for file in `ls *.jpg`; do convert $file $file.pdf; done

Actually your files will be pdfs named  "file.jpg.pdf". Then you can rename them, because they will be true pdf files. 
Of course there are ways to avoid this final name problem 
inteligently, I just don't have it in my mind. 

Actually the Tinivole post is the complete tutorial,
I just like this command line because it is very simple to see how
to use it for other purposes.

Ps. I take back this. I've read the Tinivole suggestion more carefully and it is really the best way to do it. I didn't
know that functions could be defined that way.

---

### Post by theozzlives on 2009-04-03
you could use a good OCR program.

---

### Post by kansasnoob on 2009-04-06
Just got around to trying this today and imagemagick does the trick!

Bonus: It also handles conversion of old photo formats that I'd been using xnview for!

---

### Post by dox_drum on 2009-05-04
Wow! Thank you very much!

---

