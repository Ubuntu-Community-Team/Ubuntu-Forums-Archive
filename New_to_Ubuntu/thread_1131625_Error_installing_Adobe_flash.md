---
title: "Error installing Adobe flash"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by nlinggod on 2009-04-21
I tried installing Adobe flash using Synaptic but firefox kept freezing whenever i try to watch youtube.

I seem to be able to watch flash on other sites sometimes but they too eventually freeze firefox.

Any idea what's going on?

Thanks in advance.

---

### Post by mitchellweston23 on 2009-04-21
when i got my laptop it was already ubuntu ready. once i got my wireless internet connection i noticed that there was no adobe flash player installed. i would suggest going to the adobe flash player website and getting via there when you go to download choose an OS (operating system) in this case ubuntu or linux. then after you download it it might not work. i found that i had to go to adept manager or some other application manager and it said there was a flash player install. un-install it then it should work. also you will know that downloading it from the adobe website worked because a trailer for a new flashplayer will play. :)

---

### Post by supererki on 2009-04-21
uninstall your current flash player.
download adobes drivers from 
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))

then run 
dpkg -i file_name.deb to install it
or
dpkg --force-achitecture -i file_name.deb if you are 64bit.

---

### Post by Sef on 2009-04-21
>  dpkg --force-achitecture -i file_name.deb if you are 64bit.

There is a 64-bit flash for Linux.  Also there is deb package for Ubuntu 8.04+.

---

### Post by gn2 on 2009-04-21
Easy [64-bit flash how-to]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml") works on 8.04 too.

[Download it here]("http://labs.adobe.com/downloads/flashplayer10.html").

---

### Post by sooperspook on 2009-04-22
I have tried every single one of those methods.

Firefox still freezes and goes grey.

I'm about ready to give up. :(

This is op btw.

---

### Post by llamabr on 2009-04-22
Did you just try:

```
sudo apt-get install flashplugin-nonfree
```

and restarting firefox?  

Also, what version of firefox are you working with?

---

### Post by sooperspook on 2009-04-22
> **llamabr said:**
> Did you just try:

```
sudo apt-get install flashplugin-nonfree
```

and restarting firefox?  

Also, what version of firefox are you working with?

Tried that. Still the same. At the status bar below it gets to "Transferring data from vl5.lscache6.googlevideo.com..." then it goes grey.

ANd I've got firefox version 3.0.8

---

### Post by anim on 2009-04-22
Try removing all traces of flash player from your system.

Remove the firefox plugin / remove the package under add/remove (if there is one). 

If it all worked out alright, there should be no file called libflashplayer in your /home/username/.mozilla/plugins/ folder. If there still is, delete it.

Disable all other extensions (just to make sure).

Make sure your system is fully updated.

Close firefox and restart your computer after doing this.

Once you are logged back in again, run the command (in terminal)
```
uname -a
```

If you see x86_64 near the end follow the directions below. If not, skip down to the next section. 

If you're running 64bit...
Download this file
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
uncompress the libflashplayer.so file into the folder /home/username/.mozilla/plugins/

Start firefox, flash should work.

SKIP DOWN TO HERE FOR OTHER INSTRUCTIONS

Click here
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))

Save file on desktop and run it.

Should install normally. 

Check to make sure that you see the file libflashplayer.so in your /home/username/.mozilla/plugins/

restart firefox and flash should work.

---

### Post by sooperspook on 2009-04-22
Nope. Still the same problem.

I used the x86_64 solution you gave.

---

### Post by MFinkel on 2009-04-23
Hi All, The subject line says it all. How do I get root access so I can actually Apply Changes after I choose and install a program in Adept Manager?????

---

