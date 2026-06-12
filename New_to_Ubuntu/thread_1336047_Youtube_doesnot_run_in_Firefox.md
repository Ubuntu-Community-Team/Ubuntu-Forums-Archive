---
title: "Youtube doesnot run in Firefox"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by ovroniil on 2009-11-24
I am using Ubuntu 9.10. I've just installed Gnome Mplayer and after that I can't watch any youtube video in my Firefox. If I go to Firefox I find 2 buttons, one is STREAM on the above of the video window and another is DOWNLOAD just below the video window. Nothing happens if I click them. Then I removed the Gnome Mplayer but no luck, still the same situation. But Youtube can be viewed with other browsers like Epiphany.

I've attached one screenshot of my firefox browser with youtube. Any suggestion??

---

### Post by bilalakhtar on 2009-11-24
Do you have Adobe Flash plugin installed???
If you don't, enter this command in the terminal to install flashplayer.
```
sudo apt-get install flashplugin-installer
```
Hope this helps.:p

---

### Post by ankspo71 on 2009-11-24
Hi,

I can't seem to recreate your problem by installing Gnome Mplayer. Have you installed any firefox addons lately? To me it looks like a firefox addon making the stream and download buttons for the youtube videos. If downloading flash videos is what you were wanting to do then search the firefox addons site for 'Video DownloadHelper'.

The best thing to use to view youtube videos is either by installing ubuntu-restricted extras OR flashplugin-installer OR flashplugin-nonfree. You might already have one of these installed already if Epiphany is working on youtube.

Flash players like swflash (swdec) and gnash will have to be disabled or uninstalled to use the above properly. 
Hope this helps.
James

---

### Post by garvinrick4 on 2009-11-24
If you have ubuntu-restricted-extras installed. Just make sure
Partners is checked in software sources and if you upgraded check
the disabled on upgrade to Karmic. Install medibuntu and keyring, google it if you do not have them. If you want Chromium google that
and install and keyring. And then you should have everything working. If you got sound and X is working fine you are in the pink with all your repositories installed.
 If you have to reinstall anything  "sudo apt-get clean before you do and "sudo apt-get update after reinstalling.
 Sounds like you should be fine.

---

### Post by ovroniil on 2009-11-24
Ok guys it is solved! Just got an addon in firefox that I've installed for downloading embedded video from youtube. I have removed that, now it's working.

Thanks you all... specially to [ankspo71]("http://ubuntuforums.org/member.php?u=734190")

---

### Post by brij on 2009-11-24
can you please mark this thread as solved. Thanks

---

