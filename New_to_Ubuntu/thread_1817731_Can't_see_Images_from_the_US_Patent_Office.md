---
title: "Can't see Images from the US Patent Office"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by mrpeb on 2011-08-03
When trying to look at Images at the US Patent Office 
I get an error "additional plug-ins are required"
But when I tell the system to find it,"mo suitable plug-ins exist"

I don't even know where to begin...

here is a website to go to 

[http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.htm&r=1&f=G&l=50&s1=4177779.PN.&OS=PN/4177779&RS=PN/4177779](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.htm&r=1&f=G&l=50&s1=4177779.PN.&OS=PN/4177779&RS=PN/4177779)

Up top there is a red box that says [Images] 

If you click on [Images] you can see how far I get...

Thanks

---

### Post by Matt__ on 2011-08-03
> [FONT=Arial, Helvetica, sans-serif]The plug-in you use cannot be just any TIFF image plug-in. It must be able to specifically display TIFF files using *ITU T.6* or *CCITT Group 4 (G4)* compression.  [/FONT]and here is the plugin site they recommend.

[http://fredrik.hubbe.net/plugger.html](http://fredrik.hubbe.net/plugger.html)


I've not tried it so cant comment on if it works, but from the list it looks like you need GQview / [geeqie]("http://geeqie.sourceforge.net/")...its in the repos so you can install direct from the software centre to add it to plugger.(you may have to add some sources)


[[IMG]http://s3.postimage.org/2ukg6ix0/Screenshot.jpg[/IMG]]("http://postimage.org/image/2ukg6ix0/")

---

### Post by mrpeb on 2011-08-03
Thank you for the quick response and the help.

I now have the geeqie installed.

Honestly past that I have no idea what to do next.

I still can not see the images.

---

### Post by bryanl on 2011-08-04
Easiest is to use the USPTO for searches if need be and then use [Google Patent Search](http://www.google.com/patents) to view or download the patent in PDF format. That works until you get to the very old patents.

The USPTO only shows a page at a time and getting the whole thing can be a pain. -- not to mention their TIFF format.

See also [TCL blog search on USPTO](http://tcl.leipper.org/?s=USPTO&searchsubmit=Search) for some links and other information.

I have installed a plugin for Firefox on Ubuntu and there are some threads on the topic. Search or see the thread at [http://ubuntuforums.org/showthread.php?t=671267](http://ubuntuforums.org/showthread.php?t=671267)

---

### Post by beew on 2011-08-04
Install mozplugger from the Software Centre and restart Firefox, go to the website and click  the red box [image] and it will display the image in the screenshot.

---

### Post by Matt__ on 2011-08-04
Thanks Beew, I didnt really make it clear that plugger needed to be installed too :/
It had been a long day lol

---

### Post by beew on 2011-08-04
> **Matt__ said:**
> Thanks Beew, I didnt really make it clear that plugger needed to be installed too :/
It had been a long day lol

Actually you don't need geeqie. I haven't installed it, I didn't even know about it until I read your post. OP only needs mozplugger to display the image on that site.

---

### Post by rewyllys on 2011-08-04
> **beew said:**
> Actually you don't need geeqie. I haven't installed it, I didn't even know about it until I read your post. OP only needs mozplugger to display the image on that site.
You're right, beew; mozplugger solved the problem.  Many thanks!:popcorn:

---

