---
title: "Cannot get Adobe Flash Player to work in Firefox - Ubuntu 10.10"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by tak5633 on 2011-05-05
Hi Everyone,

This is my first post, so I'm sorry if this was placed in the wrong section or if this is a repeat thread. I did my best to make sure that there weren't other threads out there similar to this that I haven't tried previously.

I am fairly new to Ubuntu, but I have acquired some basic skills from my experience so far. My question is in regards to Adobe Flash. I've searched for possible solutions to this, but none have worked for me.  I'm running Ubuntu 10.10 (Maverick Meerkat) 32bit and using Firefox 4. For whatever reason, Adobe Flash no longer seems to work. I've tried removing flash and reinstalling it, but that doesn't seem to work either. I've also checked for possible conflicts and even tried FlashAid. I'm really not sure what else to try and I was hoping someone might have an idea or possibly be able to help. Any responses would be greatly appreciated.

Thanks in advance,
Tom

---

### Post by mikewhatever on 2011-05-06
It would be helpful if you could post the outputs of the following commands:
```
locate libflashplayer.so

dpkg -l | grep -E flash\|gnash\|swfdec
```

---

### Post by beew on 2011-05-06
Just install the flash_aid addon for firefox and run it. It will  sort out conflicting flash and install the updated version and also optimize it. It is an amazing addon.

---

### Post by 73ckn797 on 2011-05-06
> **beew said:**
> Just install the flash_aid addon for firefox and run it. It will  sort out conflicting flash and install the updated version and also optimize it. It is an amazing addon.

The OP stated they already tried this. It has worked for me on 10.04 but now I use 11.04 and have had no flash issues.

---

### Post by garvinrick4 on 2011-05-06
Run these one at a time in a terminal: (just copy and paste and hit enter)
You are killing any firefox running
you are purging flash and all its by-products of attempting to install 3 or 4 different ways.
you are installing fresh copy.


```
sudo killall -9 firefox
``````
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common  mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
``````
sudo rm -f /usr/lib/mozilla/plugins/*flash*
``````
sudo rm -f ~/.mozilla/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
``````
sudo rm -rfd /usr/lib/nspluginwrapper
``````
sudo apt-get install flashplugin-installer
```**IF you have not installed all your gsteamer the good the bad and the ugly. Then run this below instead of previous flashplugin-installer
```
sudo apt-get install ubuntu-restricted-extras
```Here is what  the package adds: Includes flashplugin-installer:
```

Package: ubuntu-restricted-extras        
State: installed
Automatically installed: no
Version: 43
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 36.9 k
Depends: ubuntu-restricted-addons
Recommends: gstreamer0.10-plugins-ugly-multiverse, ttf-mscorefonts-installer,
            unrar, gstreamer0.10-plugins-bad-multiverse, libavcodec-extra-52,
            libmp4v2-0
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See http://www.ubuntu.com/ubuntu/licensing for
 more information.

rick@rick-HP:~$ 

```

---

### Post by rklapp on 2011-05-06
At first, I thought flashaid didn't do anything but then realized I had to run the addon to the right of the home icon. Doh! works now.

---

### Post by I2k4 on 2011-05-06
I'm pretty new, but installed Flash via the Synaptic Package Manager and haven't had trouble.  One thing that I do that I know  will interfere sometimes is use FireFox Extensions like NoScript and BetterPrivacy that do a number on Flash sites if not given a permission.  You might double-check your FireFox extensions.  

I suggest installing Google Chrome which comes with Flash preinstalled, to see if you have the same troubles with it.  That might help you isolate whether the problem is with Ubuntu, affecting both Chrome and FireFox, or only with your FireFox Flash install.

---

### Post by tak5633 on 2011-05-07
mikewhatever, I ran your commands and this is the output I get:

tom@vip07:~$ locate libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
tom@vip07:~$ dpkg -l | grep -E flash\|gnash\|swfdec
ii  flashplugin-installer                 10.2.159.1ubuntu0.10.10.1                             Adobe Flash Player plugin installer

 garvinrick4, I ran all your commands after I closed Firefox. Once I re-opened it flash player still didn't work. When I tried to play a video on youtube I still got only a black screen.

I2k4, I installed Google Chrome and flash does work in that. I guess it must be something explicitly related to Firefox rather than Ubuntu.

---

### Post by garvinrick4 on 2011-05-07
> **tak5633 said:**
> mikewhatever, I ran your commands and this is the output I get:

tom@vip07:~$ locate libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
tom@vip07:~$ dpkg -l | grep -E flash\|gnash\|swfdec
ii  flashplugin-installer                 10.2.159.1ubuntu0.10.10.1                             Adobe Flash Player plugin installer

 garvinrick4, I ran all your commands after I closed Firefox. Once I re-opened it flash player still didn't work. When I tried to play a video on youtube I still got only a black screen.

I2k4, I installed Google Chrome and flash does work in that. I guess it must be something explicitly related to Firefox rather than Ubuntu. 
Everything looks in the right place and the right version and no extra's far as I can tell. I have never had a problem with firefox myself so this one is a puzzler.
This will bump it up to the front of line in The Forums and I will look around to see if answer.
I imagine you have tried to purge firefox and reinstall by now. If you do run this so you get a fresh copy:
```
sudo apt-get clean
```
Cleans out your cache and gets a new one from repositories.
##Seems like you have a good attitude and think you will enjoy your Ubuntu Linux it is an amazing operating system and enjoyable to use.

---

### Post by garvinrick4 on 2011-05-07
This is under tools to Add-ons to Plugins: Thumbnail click on: MIne is 64 bit and is a 10.3 xxxxx instead of 10.2 xxxxx

---

### Post by tak5633 on 2011-05-07
I got flash to work!

I think my problem was that I wasn't uninstalling ubufox and xul-ext-ubufox, but I'm not totally sure. Essentially this is what I did:

I decided to try and reinstall Firefox again through the Synaptic Package Manager. As I was uninstalling Firefox it informed me that it would need to uninstall firefox-globalmenu too. However, it also told me it would leave language-pack-en, language-pack-en-base, ubufox and xul-ext-ubufox packages unchanged. I looked up what the function of ubufox was and on the ubuntu forums it said:

> "It is the plugin that handles installing codecs/flash/java through the package manager when the browser asks for them."

Therefore, I thought I would try removing ubufox and xul-ext-ubufox this time as well. Once these four packages were uninstalled I performed a ```
sudo apt-get clean
```

I then reinstalled Firefox through the Synaptic Package Manager and it worked! I'm not really too sure why it did. I'm guessing it was because whenever I tried to reinstall Firefox it kept leaving something behind that was corrupted or the installation would not update something that was missing.

Thanks for your help everyone. I really appreciate your efforts and hopefully I'll be able to contribute to the forums someday too.

---

### Post by mikewhatever on 2011-05-07
Glad you solved it. Take care.

---

### Post by birkopf on 2011-06-09
I'd like to ask. 

I have 64bit maverick and Firefox 3 series. Flash-Aid doesn't have anything to do with it as I have correct flash version. It works on Chrome, and doesn't work on Firefox. I used suggestion from other topic and moved plugins folder to my mozilla folder in home. Worked for few days and stopped again. 

What I just came across is interesting - TOR in enabled, turns-off flash. Firefox just doesn't see it and requests to install latest flash. 

What could be the cause ? I'd want to have flash when I am browsing with TOR on.


Please advise

---

