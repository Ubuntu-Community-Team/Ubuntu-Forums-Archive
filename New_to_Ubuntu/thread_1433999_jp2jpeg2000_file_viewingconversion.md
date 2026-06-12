---
title: "jp2/jpeg2000 file viewing/conversion"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by Dave.B on 2010-03-19
hi
i received an archive with *.jp2 files in it.

I have tried gimp and gThumb to view them and neither worked.

if their an easy way to convert them to a jpg format 

thank you for the help

---

### Post by roton on 2010-03-19
I don't know about converting but last time I looked gimp needed a plugin to view .jp2 files.
Try [http://registry.gimp.org/node/9899](http://registry.gimp.org/node/9899)

---

### Post by Dave.B on 2010-03-19
i was hoping to convert them all at once to jpg

it is a pain to try and do them 1 at a time

---

### Post by tom.swartz07 on 2010-03-19
> **Dave.B said:**
> hi
i received an archive with *.jp2 files in it.

I have tried gimp and gThumb to view them and neither worked.

if their an easy way to convert them to a jpg format 

thank you for the help

You could use this old tool: [https://launchpad.net/ubuntu/intrepid/+package/openjpeg-tools](https://launchpad.net/ubuntu/intrepid/+package/openjpeg-tools)
to convert those files.

Heres the page that highlights what you should do: [http://manpages.ubuntu.com/manpages/intrepid/man1/j2k_to_image.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/j2k_to_image.1.html)

In short, you need to run

```
sudo apt-get install openjpeg-tools
```

then run 
```
j2k_to_image -i **source file** -o **destination file**
```

---

### Post by kaibob on 2010-03-19
Imagemagick both reads and writes the JP2 file format:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

To change all JP2 files to JPG format while retaining the original files:

```
mogrify -format jpg *.jp2
```

---

### Post by CPKS on 2010-03-31
The program /usr/bin/eog will display .jp2 files (although it's a bit slow). It doesn't seem to be configured by default to act as a .jp2 displayer, though. Here's how to get it working: open a view of the directory where the .jp2 file(s) reside. Right click on one of them and select "properties" from the menu. Click on the "open with" tab, then the "Add" button at the bottom. At the bottom of the list pane there's a control for "Custom command". Click this and an input field will appear. You can either browse to /usr/bin/eog (safest if you're not sure whether you have eog installed) or just type the command into the box. Once you have OKayed your way back out of there, .jp2 files will preview with eog.

---

### Post by CPKS on 2010-03-31
I should have known: /usr/bin/eog is actually the default Picture Viewer. So setting it to open .jp2 files is a lot easier than in my previous post. No need to use "Custom command", just select the picture viewer from the list.

---

### Post by phaustus on 2010-11-28
Hi, I'm running 10.04 with 12 GB RAM, and I can't open a .JP2 to save my life.  At least not the JP2s on the MRO-HiRISE website -- really large ones, images of the Martian surface, like this:

[http://hirise-pds.lpl.arizona.edu/download/PDS/EXTRAS/RDR/PSP/ORB_010400_010499/PSP_010486_1775/PSP_010486_1775_RED.QLOOK.JP2](http://hirise-pds.lpl.arizona.edu/download/PDS/EXTRAS/RDR/PSP/ORB_010400_010499/PSP_010486_1775/PSP_010486_1775_RED.QLOOK.JP2)

I tried :


sudo apt-get install openjpeg-tools
j2k_to_image -i **source file** -o **destination file**

as suggested, and got a Segmentation fault.  I also tried :

mogrify -format jpg filename.jp2
and got a segmentation fault.  

I also tried eye-of-gnome, and got a Segmentation fault.  Ubuntu has been a dream except in this one @#$%@ case: I can't open or convert JP2s.  

Even MATLAB chokes on it.

It's also possible there's something weird about the HiRISE JP2s, but I have no trouble opening them under Winblows.  If there's someone out there who can download this file and open or convert it under Ubuntu, please let me know.

Thanks,

Phaustus

---

### Post by phaustus on 2010-11-28
To answer my own question...

I tried installing the Java-based "IAS viewer 3.1" for navigating JP2 files and it totally bombed.  (Although it was supposed to have Linux support, it barfed a message about searching for DLLs; probably thought it was under Winblows.)

But I eventually found a link to a Java JP2 viewer that's open-source and available from the European Space Agency:

[http://www.jhelioviewer.org/index.html](http://www.jhelioviewer.org/index.html)

And it works!  

So, if you need to *view* some huge JP2 files that don't respond to anything else, try the JHelioViewer.

I am still interested to know if anyone succeeds in converting the JP2 I linked in my last message, as that would be ideal.

Cheers,

Phaustus

---

