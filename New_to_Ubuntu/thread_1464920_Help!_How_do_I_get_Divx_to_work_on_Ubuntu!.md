---
title: "Help! How do I get Divx to work on Ubuntu?!"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by kogagrl on 2010-04-28
Hi, so I want Divx videos to play on my Ubuntu computer but I have tried installing the synaptic package vlc for mozilla but it did nothing. And then I tried to follow the steps indicated by "RORI" on this forum post  [http://ubuntuforums.org/showthread.php?t=157238](http://ubuntuforums.org/showthread.php?t=157238)  but I can not extract the contents.dat package thing in the folder, it asks me for a password. The password was not mentioned in the post so I was thinking I had to extract something else?But that is the only extractable thing in the folder. Please help! I want to watch ninjavideo videos!
One more thing, what is the best antivirus program to install in an ubuntu computer? OH and make it free :) Thanks soooo much, this is my first post so I hope this works! :D

---

### Post by craig10x on 2010-04-28
Just add Ubuntu Restricted Extras Package which you will find in the Software Center..that will give you mp3s divx, flash, java...etc....
You'll be able to get radio streams, you tube videos, everything...(I think if you type in the word "Restricted" in the search function on there it should bring it right up)...

You will then be able to play those divx videos right in Totem Movie Player...

I wouldn't mess around with extracting stuff...just download things in the Software Center or Package Manager...it will automatically install it just like you are use to in windows...and they can be removed just as easily...

Antivirus? You don't see them in in Software Center or Package Manager because unlike windows, Linux doesn't need it...you can't get windows viruses...and linux viruses are extremely rare and linux has fantastic security to help keep anything out...

You might also want to add the simple firewall (called GUFW..just type it in the search in Software Center) and turn it on...makes you Stealth (invisible) on the internet...

Linux also has no registry to get corrupted either... 
Welcome to the peaceful world of Linux and Ubuntu...this is a whole different world then Windows... :)

---

### Post by 2hot6ft2 on 2010-04-28
Welcome to the forum.

First there is already an anti-virus installed but it's not needed unless you want to scan windows.

The password it asked for is the one you used to login to ubuntu. You have to use it to make system changes (it's a security feature).

For the Divx. The DivX codec is propriety meaning closed source. I actually have a license for it from my windows days for encoding but the Xvid codec will decode divx movies. And since you're new and you're going to want all the other stuff as well like mp3s playing dvd's flash, java and all the other things that make computing more fun lets just do it all at once.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to accept the Java terms of use since Oracle now owns Sun.
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And you're done.

EDIT: I'm looking into that link for DivX for linux and will post back. Interesting.

UPDATE: [Click this to download DivX for Ubuntu linux]("http://rapidshare.com/files/139388717/divx4linux_6.1.1_zolerubuntu1_all.deb")
Save the file somewhere. When it finishes downloading it double click on it to install it.
During install you will need to agree to the terms of use and click Forward.
That's it.

More on ubuntu and Anti Virus
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

