---
title: "Flash player question?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by MihailKukutanov on 2008-12-30
So I'm a total newbie in the linux world. I have formated my had drive and instaled an Ubuntu 8.04 Hardy Heron, I have downloaded the plugins for flash installed it but it still does not work :confused: so please help. Thanks Milo

---

### Post by tuxxy on 2008-12-30
How did you download flashplugin-nonfree? the following command should install flash and browser plugins for you;

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by taurus on 2008-12-30
Did you unpack and then install it after you have downloaded it?

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by cb34 on 2008-12-30
there are so many threads around the forum that give perfect instructions how to get flash working, i mean no disrespect, but a quick "flash", or "flash install", or "install flash", or "flash firefox".. etc. etc. somethin like that search will get you all the info you're lookin for.. probably quicker.

did u install from the ubuntu repository, did you download from adobe's website on your own, and did you just download it, or did you actually install it.. and if you did download from adobe's site, did you grab the .deb file, or a .tar.gz file? would help if you want help. :D

and what do you mean it doesn't work, what do you see on a flash page/site like youtube?

---

### Post by MihailKukutanov on 2008-12-30
Im using mozila and I have yust clicked Instal Missing Plugins

---

### Post by cb34 on 2008-12-30
when you are at youtube for example, what do you see, what is it that's not working? do you get the missing plugin alert again or no?

type [noparse]about:plugins[/noparse] in the address bar up top.. what do you see.. do you have a flash player installed in there? to make sure.

---

### Post by MihailKukutanov on 2008-12-30
well when I'm on you tube I don't get the new plugin alert but the video screen ig gone and i have "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.", and on other sites it still asks for the plugins.

---

### Post by cb34 on 2008-12-30
ok.. instead of fooling around with this for too long lets do it simple..

find any and all libflashplayer.so files on the computer. that is flash, thats all it is, 1 file.

if you have doubles all over, you dont need it, only 1 libflashplayer.so file so in a terminal do:
sudo updatedb && locate libflashplayer.so
it will locate that file.. you should put the libflashplayer.so file in /home/username/.mozilla/plugins, then look in your /home/username/.mozilla/firefox/(profile.name) direcotry for the file xpti.dat, delete it, all of this should of been done with firefox off, and MAKE sure firefox is really off and not loaded by typing in terminal "killall -9 firefox" before you do any of this.

basically make sure there are no multiple libflashplayer.so files in different places, just place one in ~/.mozilla/plugins dir, delete xpti.dat file so firefox will re-read its plugins when it loads.. should work.

if the locate command didn't find any libflashplayer.so files, that means you never really installed it and it's not on your computer. just download the .tar.gz(not .deb) from adobe's site if that's the case, unzip, and move the libflashplayer.so file to the mozilla plugins dir, delete xpti.dat, that's it.

---

### Post by MihailKukutanov on 2008-12-30
In home/milo(thats the username)/ there isnt a .mozila folder :S

I have found 2 libflashplayer.so files  but it shows them with a padlock.

---

### Post by taurus on 2008-12-30
Applications -> Accessories -> Terminal
```
ls -la ~/.mozilla
```

---

### Post by MihailKukutanov on 2008-12-30
Padlock is gone but it still doesn't allow me to delete the file.

---

### Post by MihailKukutanov on 2008-12-31
People please

---

### Post by mikewhatever on 2008-12-31
Can you please post the output Taurus asked for. Where did you find the the libflashplayer.so files?

---

### Post by MihailKukutanov on 2008-12-31
With this code "sudo updatedb && locate libflashplayer.so" i get this location 
/home/milo/.local/share/Trash/info/libflashplayer.so.trashinfo
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so

i have found the files in usr but i can not delete them and all the .(foldere name) like .mozilla and .local are not shown i can' see them

---

### Post by MihailKukutanov on 2008-12-31
I have just checked the root owns the files thats why i can't delete them i have tryed with this comand "sudo chown -R milo:milo libflashplayer.so" but it didnt do it, so how do I overtake the ownership from the root? and how do I unhide the hiden files

---

### Post by mikewhatever on 2008-12-31
You know, you don't have to do any of that to make flash work. Follow this guide and leave permissions as is.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by skathmandoo on 2009-01-01
m having a similar problem with flash. i downloaded it directly from adobe website.(its the flash player 10 linux.deb). i extracted the files in documents.i didnt know wat to do next. after readin some above post i tired this and got-

rajiv@Rajiv:~$ sudo updatedb && locate libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so

i couldnt find any Mozilla folder in my home/username .. ..!!!

wat do i do now?

i also tried --

sudo apt-get remove gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-gcjwebplugin liblame0 non-free-codecs openjdk-6-jre unrar

and got..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflash-mozplugin is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
E: Couldn't find package ia32-libs

PLEASE HELP !!thanks and happy new year!!

---

### Post by mikewhatever on 2009-01-01
> **skathmandoo said:**
> m having a similar problem with flash. i downloaded it directly from adobe website.(its the flash player 10 linux.deb). i extracted the files in documents.i didnt know wat to do next. after readin some above post i tired this and got-

You didn't have to extract the files. The guide I linked to explains how to install flash.

---

### Post by MihailKukutanov on 2009-01-05
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) I have used this link and the manual and still no results. Im sorry for bothering people but is this comon not being able to get the flash straight, is it somehow possible for the flash to be turned of from the mozilla or something?

---

### Post by MihailKukutanov on 2009-01-06
I have installed Opera and youtube works and flash games work so thank you guys for the help

---

