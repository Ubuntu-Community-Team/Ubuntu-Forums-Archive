---
title: "installing latest 64bit adobe flash on 9.10 for chrome browser"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-12-09
does anyone have some info on installing the 64bit version of flash for google chrome.   can i just uninstall the old flash from software center?

thanks

---

### Post by northwestuntu on 2009-12-09
bump

---

### Post by JamesParnell on 2009-12-09
I thought that google chrome was a dev release with no plugin support?

---

### Post by Martin Marshalek on 2009-12-09
I recently found this PPA and it's great for flash player on 64 bit. Firs, you need to remove the 32bit wrapped plugin by running the command(s):

```
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
```

...and you'll probably want to throw in apt-get autoremove after that too.

Then go into the terminal and type: ```
sudo add-apt-repository ppa:sevenmachines/flash
```.

Then, either use synaptic or the terminal to install flashplugin64-installer.

I use this and can verify that the updated Google Chrome works with this as it installs the same way as the 32 bit one, just using the alpha from adobe labs.

PS: Don't remove any of the nspluginwrapper things if you have adobe reader or something like that installed.
PSS: I would assume you are running Karmic, right? If not you wont be able to use this PPA and you will need to use the script from the first post in the Adobe Flash thread in x86-64 section of the forums.

---

### Post by oldos2er on 2009-12-09
If you already have flash installed, copy libflashplayer.so to /usr/lib/chromium-browser/plugins

---

### Post by tom.swartz07 on 2009-12-09
> **Martin Marshalek said:**
> I recently found this PPA and it's great for flash player on 64 bit. Firs, you need to remove the 32bit wrapped plugin by running the command(s):

```
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
```

...and you'll probably want to throw in apt-get autoremove after that too.

Then go into the terminal and type: ```
sudo add-apt-repository ppa:sevenmachines/flash
```.

Then, either use synaptic or the terminal to install flashplugin64-installer.

I use this and can verify that the updated Google Chrome works with this as it installs the same way as the 32 bit one, just using the alpha from adobe labs.

PS: Don't remove any of the nspluginwrapper things if you have adobe reader or something like that installed.
PSS: I would assume you are running Karmic, right? If not you wont be able to use this PPA and you will need to use the script from the first post in the Adobe Flash thread in x86-64 section of the forums.


This post seems to be fairly valid, albeit a few little tweaks that you will have do do for your system.

Could you specify if you have the flashplugin-installer or ubuntu-restricted-extras packages installed?

I installed both of those packages, and chrome worked great right from the get-go.

---

### Post by fooman on 2009-12-09
64 bit karmic + chrome + ubuntu-restricted-extras and flash just works for me.

---

### Post by oldos2er on 2009-12-09
AFAIK installing ubuntu-restricted-extras on 64-bit Ubuntu installs 32-bit flash with nspluginwrapper. If you want 64-bit flash, you still need to jump through one more hoop.

---

### Post by northwestuntu on 2009-12-09
> **oldos2er said:**
> If you already have flash installed, copy libflashplayer.so to /usr/lib/chromium-browser/plugins

so i should be able to download the latest version of 64bit flash and copy that to the directory?

---

### Post by northwestuntu on 2009-12-09
like from here
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by clhsharky on 2009-12-09
HI

This is the new 64bit flash
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

extract to ~/usr/lib/mozilla/plugins 
chrome will look at this location, firefox all so.


Sharky

---

### Post by northwestuntu on 2009-12-09
should i uninstall the 32bit version 1st?

---

### Post by Martin Marshalek on 2009-12-09
To all who said use the ubuntu-restricted-extras that will theoretically work, but your mileage will vary with the wrapped version.

As for using the libflashplayer.so from the Adobe Labs page that will also work but, by using the repository, it is easy to uninstall when (and hopefully in Lucid) the Ubuntu devs include the native 64 bit plugin in the repos whereas you will have to locate everywhere you linked and placed libflashplayer.so and manually remove them if you just copy the file from Adobe labs. 

To each his own, but for me, this works the best.

BTW: To remove the 32 bit flash, simply copy and paste the commands from my first post.

---

### Post by northwestuntu on 2009-12-09
> **Martin Marshalek said:**
> To all who said use the ubuntu-restricted-extras that will theoretically work, but your mileage will vary with the wrapped version.

As for using the libflashplayer.so from the Adobe Labs page that will also work but, by using the repository, it is easy to uninstall when (and hopefully in Lucid) the Ubuntu devs include the native 64 bit plugin in the repos whereas you will have to locate everywhere you linked and placed libflashplayer.so and manually remove them if you just copy the file from Adobe labs. 

To each his own, but for me, this works the best.

BTW: To remove the 32 bit flash, simply copy and paste the commands from my first post.

i agree the 32 wrapper works ok, but using the 64bit version is way better for me.  thanks for the info.

---

### Post by Martin Marshalek on 2009-12-09
No problem, hopefully adobe will make the 64 bit flash stable before April.

---

### Post by joes7 on 2009-12-09
Go to Add/Remove Applications. Search for "adobe flash". Now, for Google Chrome, I am not sure if there is a Linux release, but you can always install Wine (same procedure for Adobe) and run it.

---

### Post by northwestuntu on 2009-12-09
> **Martin Marshalek said:**
> No problem, hopefully adobe will make the 64 bit flash stable before April.


that would be nice.

---

### Post by northwestuntu on 2009-12-09
i uninstalled the nswrapper and the adobe flash and then dropped the liflashplayer.so in to the firefox/plugins and worked great!

the performance is so much better :p

---

### Post by 3rdalbum on 2009-12-10
> **joes7 said:**
> Go to Add/Remove Applications. Search for "adobe flash". Now, for Google Chrome, I am not sure if there is a Linux release, but you can always install Wine (same procedure for Adobe) and run it.

That installs 32-bit Flash; and there is an official Linux beta of Google Chrome (and there have been open development releases for ages). No offence Joes, but you should read the thread before posting to avoid confusing the original poster.

Just chuck the 64-bit plugin into /usr/lib/mozilla/plugins if it isn't already there - I can confirm that Google Chrome will find all your Firefox plugins.

---

### Post by tom.swartz07 on 2009-12-10
> **joes7 said:**
> Go to Add/Remove Applications. Search for "adobe flash". Now, for Google Chrome, I am not sure if there is a Linux release, but you can always install Wine (same procedure for Adobe) and run it.

There is!

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel)

Scroll down and pick your flavor- x86 or x64.

Im using it right now, as a matter of fact

---

### Post by warden976 on 2009-12-10
> **oldos2er said:**
> If you already have flash installed, copy libflashplayer.so to /usr/lib/chromium-browser/plugins

Hi

I already have 64 bit flash installed and working in firefox but just can't seem to crack it with 64 bit chrome.

I've seen various posts and and have tried copying libflashplayer.so to /usr/lib/chromium-browser/plugins/ as well as /opt/google/chrome/plugins/, and it is already in (working for firefox) /usr/lib/mozilla/plugins/.

I have tried running it with and without --enable-plugins too with no luck - what am I missing?

cheers

---

### Post by Martin Marshalek on 2009-12-10
First, verify that you are running the latest version of Google Chrome (just run apt-get update).

I'm not sure how you installed the 64 bit flash so that might be a problem. If you can uninstall it do that and then reinstall using either my method or, if you don't want to use a repo, you can do a Google search and the Debian repository result for "flashplugin-nonfree" will have a non-32-bit wrapped version as the Debian Unstable maintainers have much less strict requirements for packages than the Ubuntu developers (which has it's pros and cons).

---

### Post by warden976 on 2009-12-10
hi,

to install 64 bit flash i just downloaded it from adobe.com, unpacked it and copied libflashplayer.so into /user/lib/mozilla/plugins - worked straight away (and still does) with firefox.

to install chrome i went to google.com/chrome and downloaded the 64 bit deb and installed it.

---

### Post by sittingpenguin on 2009-12-11
The latest December beta from Adobe works really well and uses just 30% CPU. I don't remember the exact number for the previous one but it was about twice as much. Full screen also works smoothly now. 

At this point i really do hope that Lucid gets rid of the horror 32 bit wrapped version. It makes it impossible for me to use restricted-extras, because that will pull in all the patchwork of flash 32 bit, nspluginwrapper and 32 bit libs; what I do is take note of what restricted-extras would install and install everything separately leaving out the Flash part, then add the 64 bit Flash from Adobe Labs, a pain down there.

---

### Post by sexyclient2 on 2009-12-11
I downloaded the latest flash 64-bit plugin and put it in the /user/lib/chromium-browser/plugin folder, but whenever I run flash it's super-slow, and it loads the process "EXE" which, I'm assuming, is WINE.  Videos aren't even watchable at all...  Am I doing something wrong?  I'm using the chromium-browser daily ppa and am updated.

Edit:
I uninstalled the google-chrome-beta (not chromium) and flash worked quite well.  The "EXE" process is still running, however...  Is that normal?  It's taking up 60% of my cpu (though I'm on my laptop which has a ULV processor.)

---

### Post by tom.swartz07 on 2009-12-11
> **sexyclient2 said:**
> I downloaded the latest flash 64-bit plugin and put it in the /user/lib/chromium-browser/plugin folder, but whenever I run flash it's super-slow, and it loads the process "EXE" which, I'm assuming, is WINE.  Videos aren't even watchable at all...  Am I doing something wrong?  I'm using the chromium-browser daily ppa and am updated.

Edit:
I uninstalled the google-chrome-beta (not chromium) and flash worked quite well.  The "EXE" process is still running, however...  Is that normal?  It's taking up 60% of my cpu (though I'm on my laptop which has a ULV processor.)

EXE is the flash player process. There has been some chatter that this will be either fixed soon, or that the browsers (mostly chrome) will be patched to fix it.

---

### Post by sexyclient2 on 2009-12-11
> **tom.swartz07 said:**
> EXE is the flash player process. There has been some chatter that this will be either fixed soon, or that the browsers (mostly chrome) will be patched to fix it.
I see, thanks.  One more thing: did sound break for anyone else after using the latest flash?  It did for me...

Edit:
A quick restart solved that right up.

---

### Post by warden976 on 2009-12-12
> **sittingpenguin said:**
> The latest December beta from Adobe works really well and uses just 30% CPU. I don't remember the exact number for the previous one but it was about twice as much. Full screen also works smoothly now.

cheers for the tip on the new 64 bit flash release - removed previous version of libflashplayer.so from /usr/lib/mozilla/plugins and copied the 8th December version in and flash now works in chrome!

---

### Post by LuisGMarine on 2009-12-12
> **3rdalbum said:**
> That installs 32-bit Flash; and there is an official Linux beta of Google Chrome (and there have been open development releases for ages). No offence Joes, but you should read the thread before posting to avoid confusing the original poster.

Just chuck the 64-bit plugin into /usr/lib/mozilla/plugins if it isn't already there - I can confirm that Google Chrome will find all your Firefox plugins.

I'm curious as to where you are getting your information.  Where can you verify your statement that the repo version of flash is 32 bit?

---

### Post by oldos2er on 2009-12-12
> **LuisGMarine said:**
> I'm curious as to where you are getting your information.  Where can you verify your statement that the repo version of flash is 32 bit?

```
apt-cache show flashplugin-installer
```

64-bit flash has never been in the repos.

---

### Post by LuisGMarine on 2009-12-12
Cool I guess I didn't post the link to this guide for nothing ...

[http://ubuntuforums.org/showthread.php?t=1352617]("http://ubuntuforums.org/showthread.php?t=1352617")

---

### Post by PeteLong on 2011-01-31
I think that version has been pulled :(

you can install it with the x32 bit version though

[Chrome (Linux) Installing x64 bit Flash Plugin]("http://www.petenetlive.com/KB/Article/0000385.htm")

Pete

---

### Post by volaer on 2011-02-17
I don't know if this one will work with Chrome, but it does worked in Firefox:
[http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/](http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/)

---

