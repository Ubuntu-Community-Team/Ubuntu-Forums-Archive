---
title: "Flash Plug-In Cannot Be Installed On my Laptop"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by TX_F2 on 2009-08-06
I am a Linux/Ubuntu newbie so I am pretty much lost here. I installed Ubuntu 9.04 onto my laptop (running Vista) a few days ago using Wubi. I did a search but I either can't find the same problem I am having or I don't understand the replies to fix the problem. :(


All I get is a blank black screen whenever I try to watch a video when using Firefox in Ubuntu. It can be a video on CNN.com or YouTube, ect. 

 So I went to Applications>Add&Remove>Third Pary Applications>Adobe Flash Plugin 10

From the searching I have done here, I think that I have to install this in order to make the videos work ?  Well when I go to install it, I get this message:

[COLOR=Red]**Adobe Flash Plugin 10**

Adobe Flash Plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

Adobe Flash Plugin 10 is available in the third party software channel 'jaunty-partner'. To install it, please click on the checkbox to activate the software channel.[/COLOR]

[COLOR=Black]I also get this same message when I go to try and install Adobe Reader 9.

I am running:

 Firefox version 3.0.13  Mozilla Firefox for Ubuntu canonical - 1.0 

Gnome version 2.26.1

Ubuntu 9.04  (Jaunty Jackalope)

All the above is what came in the Wubi install I did.


So how can I install the Flash player so that I can view videos when it tells me that it cannot be installed on my laptop ???


TIA 
[/COLOR]

---

### Post by wencin on 2009-08-06
I never had the same experience too, but referring to
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)
states that adobe players run in either intel 32 bit or amd 64 bit.

maybe you should try downloading directly from adobe website
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
select adobe flash player 10, then select linux as the OS, then select the .deb debian installer (install_flash_player_10_linux.deb)

when installing, you may be asked to use the installer provided by software sources (means you should install from the add/remove program) just ignore it and continue installing.

hope this works

---

### Post by Clorow on 2009-08-06
Adobe doesn't have a Flash Player for amd64 yet. In the meantime, try [Gnash]("apt:mozilla-plugin-gnash") if you just use it for watching YouTube.

---

### Post by VastOne on 2009-08-06
> **Clorow said:**
> Adobe doesn't have a Flash Player for amd64 yet. In the meantime, try [Gnash]("apt:mozilla-plugin-gnash") if you just use it for watching YouTube.

Actually they (Adobe) does.

Instructions here  [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Direct Download here

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)


It is in Alpha state but after running it for nearly a year, I am totally pleased with it.

---

### Post by wencin on 2009-08-06
ow i just pick this out from another thread...
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

scroll to the bottom of the page and find
Download 64-bit Plugin for Linux (TAR.GZ, 3.64 MB)

or maybe...
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

thanks for the real author just quoting to make things easier
[http://ubuntuforums.org/showthread.php?t=1233185](http://ubuntuforums.org/showthread.php?t=1233185)

---

### Post by TX_F2 on 2009-08-06
> **wencin said:**
> ow i just pick this out from another thread...
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

scroll to the bottom of the page and find
Download 64-bit Plugin for Linux (TAR.GZ, 3.64 MB)

or maybe...
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

thanks for the real author just quoting to make things easier
[http://ubuntuforums.org/showthread.php?t=1233185](http://ubuntuforums.org/showthread.php?t=1233185)

Much thanks for all your guys help.

I went to the softpedia link **wencin** provided (the link in the middle of the three), and it was very easy to understand. 

I can now play YouTube videos and I get audio as well, the video is noticeably not as smooth as when played in Vista,instead it's a little choppy and I still get nothing but a black screen when trying to play video on CNN.com

But I got one more Ubuntu/Linux problem solved which puts me one step closer to making a full migration from Vista to Linux, thanks again for the help.

---

