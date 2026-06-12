---
title: "Free Website building software?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by armoftheland on 2009-11-21
Hello,

Looking for a free (hopefully!) visual website builder that's linux based. Any suggestions? Not sure where to start. I know ubuntu isn't responsible for compatable software but it would be nice if someone knew of a product to point me to :)

Thanks all!

---

### Post by SPazzo on 2009-11-21
I've had luck with KompoZer.  [http://kompozer.net/](http://kompozer.net/)  It *is* a little hard to use, but it does the job.

Here's a list: [http://webdesign.about.com/od/htmleditors/tp/aatpwyslinux.htm](http://webdesign.about.com/od/htmleditors/tp/aatpwyslinux.htm)

By the way, if you are Googleing around and looking for one, try searching for a *WYSIWYG editor*.  That stands for *What You See Is What You Get*.  Basically you don't need to learn HTML to make a page.  (At least that's what I assume you want from your post.)

---

### Post by bilbo.san on 2009-11-21
It depends... If you need a WYSIWYG only, then SeaMonkey and Kompozer would be the best options you have right now... although, I have heard that many have successfully installed DreamWeaver on WINE,
Now, if you are comfortable with writing HTML, then I would suggest to use Aptana Studio and BlueFish.

Good luck!

---

### Post by rp3 on 2009-11-21
> **bilbo.san said:**
> It depends... If you need a WYSIWYG only, then SeaMonkey and Kompozer would be the best options you have right now... although, I have heard that many have successfully installed DreamWeaver on WINE,
Now, if you are comfortable with writing HTML, then I would suggest to use Aptana Studio and BlueFish.

Good luck!

I have an older ver of DreamWeaver working just fine on wine...

:)

---

### Post by lnxcat on 2009-11-26
Hello,

I wanted to confirm that Dreamweaver CS4 runs in wine-1.1.31
The DW installer works, you have to install it from the command line and after install the installer will complain of errors but Dreamweaver runs fine, been using it and it is stable. I noticed it is a little slow when making Mysql query code in the wizards but its not totally annoying.

I did not have to recompile wine-1.1.31 or do anything special except to install winetricks. So here you go this is how to do it, remember you need a Legit licensed copy of Dreamweaver and a licensed copy of Windows as I have been told.

Tested on Ubuntu Studio 9.10 and Ubuntu 9.10 Desktop x386 32bit - If you are using Ubuntu Studio make sure to completely un-install wine then follow the directions below


[LIST=1]
[*]Install wine-1.1.31 using the Synaptic Package Manager
System > Synaptic Package Manager - Search for wine and install version wine-1.1.31
[*]Launch Notepad once to make your .wine directory
Applications > Wine > Accessories > Notepad
[*]Open the Terminal
Applications > Accessories > Terminal
[*]Install winetricks in the Terminal, do each line separately
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
chmod a+x winetricks
sudo mv winetricks /usr/local/bin/
winetricks msxml6 gdiplus gecko vcrun2005 ie6 corefonts fontsmooth-rgb
[*]Restart your computer, doesn't make to much of a difference but do it just in case.
[*]Install Dreamweaver
cd /media/cdrom0/Adobe\ CS4/
wine Setup.exe
[*]Special Notes: When the install screen pops up some check boxes may be missing, just click where the box would normally be and it will check off.
[/LIST]
After Dreamweaver is setup go to the Wine menu under Applications you will find it there.

Troubleshooting: Accessing some Windows based program CD's in Ubuntu will have problems if the icons on the CD show a gray X over them. To fix this copy the contents of the CD to a flash drive or simular storage device using a Windows computer the us this copied version to install the program on your Ubuntu computer. You will need to access the setup program a little differently since the media will be located on a different mount point on your Ubuntu computer. ie: cd /media/cdrom0/Adobe\ CS4/ changed to cd /media/your-usb-device/Adobe\ CS4/

Hopes this works for you.

P.S. if you need a Flash editor this one works too!
SwishMax3
[http://www.swishzone.com](http://www.swishzone.com)

Links:
Wine
[http://www.winehq.org/](http://www.winehq.org/)

Codeweavers (Doesn't work with Dreameaver CS4)
[http://www.codeweavers.com/](http://www.codeweavers.com/)


Happy Thanksgiving! ;)

---

### Post by Tibuda on 2009-11-26
If you want WYSIWYG, try Amaya by W3C: [http://www.w3.org/Amaya/](http://www.w3.org/Amaya/)

---

### Post by Maheriano on 2009-11-26
Do you mean server side software? 
- Wordpress
- OSCommerce
- PHPBB3
- Joomla

---

### Post by armoftheland on 2009-11-29
Thanks for all of your suggestions everyone :) a WYSIWYG was what I was looking for. I'm going to try out amaya first, and failing that i'll get dreamweaver on wine.

---

### Post by arvevans on 2009-11-29
For those with very limited experience with building web content, and/or with HTML (or derivative) language, it is possible to use the word processor in Open Office and save your files as html.  This way you are simply doing word processing, but can add links and such where needed.

Arv
_._

---

### Post by Maheriano on 2009-11-30
- Quanta
- Bluefish
- NVU

I use these three.

---

