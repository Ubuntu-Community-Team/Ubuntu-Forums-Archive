---
title: "Creating PDF file from JPG images"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by CivicSpoon on 2009-09-15
I'm trying to find a program that can create a .pdf file from .jpg images, but I haven't had any luck from searching.  I have 641 jpgs that I'd like to create a .pdf "manual" from them.  If possible, I'd also like to add bookmarks to the pdf, for easy navigation.  The bookmark part isn't really a necessity, because I've come across many programs that claim to do this with existing pdf files; but if anyone has any suggestions I'd certainly take them.  

I've been reading that OpenOffice can do the basics of what I want, but I haven't been able to figure it out.  I'm not sure what part of OpenOffice to use; Presentation, Word Processor, Spreadsheet, etc.  But from what I've seen, it seems like I'd have to click "Insert > Picture > From File" 641 times anyways.  To be honest, I couldn't even figure out how to add more than 1 image into the file, using the Word Processor.

If anyone has any ideas, I would GREATLY appreciate it.  I'm using Ubuntu 9.04 Jaunty by the way.  I'm also not good with the terminal, so a program with a graphical interface would be preferred over a command line based solution.

---

### Post by earthpigg on 2009-09-15
GIMP can export jpg to pdf, iirc.

take a look at applications -> add/remove -> search for 'pdf' and take a look at the offerings.

---

### Post by ovid9 on 2009-09-15
Scribus is a free desktop publishing program you could use as well.  I haven't fiddled with it much, but it looks like it could easily do what you want it too.

In OO Word Processor, there is a button right next to print file directly that allows you to export as a PDF.

Also, GIMP is a handy way to do it.  GIMP can be overwhelming for a new user (it still is for me to a large extent) but its amazingly powerful.

---

### Post by kaibob on 2009-09-15
Are you going to annotate the JPG images in some way, or do you simply want to merge and convert them to PDF format. If the latter, I would be inclined to use the Imagemagick convert utility. I know you said you wanted a GUI but a command-line tool may be best for this job.

If you have Imagemagick installed, just put all the JPG images in one directory, open a terminal window, change to the target directory, and enter the following:

```
convert -compress Zip *.jpg output.pdf
```

BTW, with the large number of JPG files, you may receive a memory error message. Also, it will take some time for convert to do its job. 

If a GUI that suits your needs isn't provided by another forum member, give convert a try. It won't take much time.

---

### Post by k33bz on 2009-09-15
You could also install a nautilus script. With the script installed all you would need to do is right click on the jpg file (or any other file you wish) and select pdf.

I dont remember where I got mine, but you might try googling "nautilus scripts". There is alot of different scripts out there, including merging pdf files. One particular site will give you a whole package of scripts as well as a tutorial on how to install them.

[http://g-scripts.sourceforge.net/index.php]("http://g-scripts.sourceforge.net/index.php")

Then there is this site, it is in a different language, but one of the scripts it offers is to merge a whole directory of images into a pdf form.

[http://pixatintes.freeprohost.com/?page_id=319]("http://pixatintes.freeprohost.com/?page_id=319")

---

### Post by jerrrys on 2009-09-15
you can link a jpg to pdf with Zotero

[http://www.zotero.org/](http://www.zotero.org/)

---

### Post by expatCM on 2009-09-16
A dead easy solution is to use gscan2pdf which is found in the repositories.

Import the jpg files and save as a pdf.  As easy as that.  The order of the jpg's can be changed if you wish before conversion to the pdf.

---

### Post by CivicSpoon on 2009-09-20
Thank you everyone, for your help.  I couldn't figure out how to do it in Scribus or GIMP; in the same way I couldn't figure out how to do it in OpenOffice.  

The Imagemagick command thing worked up until it hit a jpg that was corrupted.  I tried a couple different things to fix it; editing the image, copying & renaming one of the other images and pasting the picture from the corrupt image onto the new one.  No matter what I did, I couldn't get it to get past that 1 image.  I have no doubt it would have worked, had the image not been corrupted.

I was about to try the nautilus scripts, but I figured I'd give the gscan2pdf program a try first (easiest first), and it worked!  Thanks again for the help everyone, I truly appreciate it.

---

### Post by eumetaxas on 2010-09-24
> **kaibob said:**
> 
```
convert -compress Zip *.jpg output.pdf
```


Thank you!

---

### Post by kaibob on 2010-09-24
> **eumetaxas said:**
> Thank you!

Your welcome!

As an aside, I am not sure why I used zip compression in my earlier post, because JPEG compression typically yields smaller file sizes with little or no difference in quality. With newer versions of convert, I believe JPEG compression is enabled by default for JPG files.

```
convert -compress JPEG *.jpg output.pdf
```

---

### Post by mhiggins1785 on 2010-11-27
installed imagemagick, tried suggested command and received this error message: 

missing an image filename 'output.pdf' @ convert.c/ConvertImageCommand/2775

---

### Post by jobjol on 2012-08-12
Try

```
do for every jpg {
convert -scale ".$HEIGHT."x".$WIDTH." -border ".$MARGIN."x".$MARGIN." -bordercolor white $inputfile $outputfile
}

find . -maxdepth 1 -iname 'page*.jpg' -exec sam2p '{}' '{}'.pdf \;"
sam2p_pdf_scale ".$PAGE_WIDTH." ".$PAGE_HEIGHT." page".$key.".jpg.pdf
pdfjoin page*.pdf --outfile out.pdf
```

Check the output and functionality of the code above at [http://convertjpgpdf.net]("http://convertjpgpdf.net")

---

