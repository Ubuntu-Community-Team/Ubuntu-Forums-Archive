---
title: "BBC iPlayer, Flash &amp; Shockwave problem"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by figi22 on 2008-12-21
Using Hardy, trying to install BBC iPlayer, but it keeps saying that I need to download the latest version of Flash even though I have done that already.

I can see in Firefox the Shockwave plugin is using the old version of Flash, but I don't know how to update that (or even remove it to reinstall).  There isn't a supported version for Linux at the moment, so I presume this is an old version.  I get the feeling that this is the problem.

I've got both adobe-flashplugin and flashplugin-nonfree installed (not sure why, or if that is a problem).  No other Adobe packages are installed.

---

### Post by jbrown96 on 2008-12-21
Flash tends to be out-of-date, so you should get the version from adobe's website. 

First thing to do is to remove both of those packages. 

I believe there are instructions available there, but the process is fairly straight forward. You can do it in Nautilus. Just navigate to where you downloaded the "tarball" from adobe. Right click, and select "extract here". You should get a file with the name libflashplayer.so or something very similar. "Cut" it. Show hidden folders (in view) and go to your home folder. Find the .mozilla folder. In it, there may be a folder called plugins; if there is, just paste libflashplay.so inside, otherwise, create the folder and paste it inside.

If you are still having trouble, check out this page from the BBC [http://news.bbc.co.uk/2/hi/technology/7787335.stm]("http://news.bbc.co.uk/2/hi/technology/7787335.stm")

---

### Post by capnthommo on 2008-12-21
hi figi22.  i had a similar problem a couple of weeks ago with shockwave and BBC iplayer under the thread [ [ubuntu] [SOLVED] swf x-shockwave-flash wont play ] .  if you look at the thread the solutions proposed and also the suggested links should help.  i'm sorry i can't be very clear but it's all a bit foggy.  if you have any specific questions relating to it post me a question and i will try to help more.  anyway, as a side effect of getting shockwave swf to play i found i had fully functioning BBC iplayer.  it seems to be to do with installing the windows version of firefox on wine.  again, sorry i can't be more helpful but feel free to come back.
good luck
capnthommo

---

### Post by figi22 on 2008-12-22
hi capnthommo - I had a look at your thread, but I don't want to install Firefox under Wine.   I had already installed the latest version of Flash from the Adobe website in the way the last poster had posted.

hi jbrown96 - yeah that BBC News story was what got me trying to do all this in the first place.  I have been able to use the streaming iPlayer, but it was the download version that I wanted to try.  I get the error message that my Flash isn't up to date when trying to access the Download Manager to install it.

I will try removing everything and starting again, but I'm pretty sure it's down to this old Shockwave plugin using an old version of Flash.  I need to remove it before installing Flash again, but not sure how to do this as I can't find a related package.  I can't update the Shockwave plugin because Adobe don't do that for Linux anymore.

---

### Post by figi22 on 2008-12-22
OK well I went back and removed both adobe-flashplugin and flashplugin-nonfree packages (think the latter was probably the problem as it didn't come from the Adobe website), then reinstalled from the Adobe website, and that worked.  I must have done things in the wrong order previously.

---

### Post by Tom--d on 2008-12-22
There has been an update to the Linux verion of Fash 10.

If you uninstall Flash now and install the version from Adobe's website, BBC iPlayer will install.

---

### Post by antonbee on 2009-01-05
I have recently installed BBC iPlayer on my own and my daughter's computers. Both run Ubuntu Hardy Heron 8.04 and are fully updated with the releases which are regularly notified. The version of Firefox they run is 3.0.5, again kept uptodate. I had quite a lot of trouble getting the Player to work on each machine (6 hours + 4 hours ??) but eventually succeeded. A most important consideration is to remove any Flash players which you already have loaded. I didn't realise this to start with and did not realise that there are several alternatives). I had SwfDec and my daughter had Gnash. Either of these, if present as the default (or alternative ?) flash player, prevent Adobe flash player 10 from running. I found the easiest way to find them and remove them was to go into

(Top left hand corner of desktop) 
Applications > Add/Remove > Show installed applications only

If either Swfdec Flash Player or Gnash SWF Viewer
is present (box at left is ticked), untick it to remove it

If Adobe Flash Plugin 10 doesn't show then you have not successfully installed it yet.
You may be able to install it by searching for it using the 
   All available applications tab
   Search box set to 
            adobe flash
   Tick the box when adobe flash is found

I didn't do this as I had earlier installed Flash 10 from 
[http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)
I selected the 
  .deb for Ubuntu 8.04
version and chose the download option to install directly on my system - deb packages seem to offer a very simple way to get hold of fully installed & working software

Good luck
AntonBee

---

