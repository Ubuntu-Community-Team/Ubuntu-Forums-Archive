---
title: "airlink101 awlh6070 install guide"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by Cresho on 2008-08-10
this is messy typing but i don't use it.  I'm placing this here incase someone or I need it.  I just built a pc and this is what I did to get a new 7 dollar wifi working.

wifi installation guide for the airlink101 awlh6070

to start, hardware network ethernet to internet is needed the first time.


********************************************************************************
fixing the repositories in hardy heron******************************************
********************************************************************************
fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  add 3rd party stuff for source files.  refresh with button on top or close and click reload.  in add and remove programs, under show, select "all available applications"

********************************************************************************
installing required libraries for compiling or developing softwares*************
********************************************************************************

this section is not needed but good to have.


copy these into terminal with highlight and ctrl+c and in terminal you ctrl+shift+v and hit enter

In terminal you do this first
sudo aptitude remove automake1.4

(click y to approve)

then this(not all needed but it helps to keep these around for other apps)
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev

(click on y to approve)  this will take a while and make sure you hit y if it asks you.
********************************************************************************
software wifi install guide*****************************************************
********************************************************************************
open add remove program from the applications menu
search for "windows wireless drivers" and install it

if you did an lspci in terminal, you would find that the wifi card is really
"03:07.0 Network controller: RaLink Unknown device 0701"

seach the internet for the driver "AWLH6070_package.zip"  if not, i couldnt find it but airlink has it hidden...sort of

[http://www.airlink101.com/support/index.php?cmd=files&id=128](http://www.airlink101.com/support/index.php?cmd=files&id=128)

download, right click after download is complete and extract here.
AWLH6070_package.zip

go to Administration->Windows Wireless Drivers and install new driver.  Navigate to the extracted folder and into the winxpx86 and highlight rt2860.inf and open.  It is now installed.

go to Administration->synaptic package manager and search for madwifi.  Install madwifi-tools

Reboot.






you can now access wifi in the upper right hand corner of your network manager.  right click disable or enable toggles, leftclick assign wifi.

THAT EASY!

---

### Post by Warpnow on 2009-05-16
I found this extremely helpful. Also bought one of these cards, but hadn't installed it as I had heard it had bad linux support. Now that I've heard otherwise, I'll be trying it.

---

