---
title: "Dreamweaver CS4 Alert!"
date: 2009-11-26
forum: New to Ubuntu
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
[http://www.swishzone.com]("http://www.swishzone.com/")

Links:
Wine
[http://www.winehq.org/](http://www.winehq.org/)

Codeweavers (Doesn't work with Dreameaver CS4)
[http://www.codeweavers.com/](http://www.codeweavers.com/)


Happy Thanksgiving! :wink:

---

### Post by blazemore on 2009-11-27
Thanks for this: Dreamweaver CS4 was one application tying me to dual booting. Any news on Photoshop CS4? have you tried it?

---

