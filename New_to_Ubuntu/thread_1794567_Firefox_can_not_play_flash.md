---
title: "Firefox can not play flash"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by ice2000feng on 2011-07-01
system:ubuntu server, 32 bit.
firefox: firefox 4 version or firefox 5 version.

I have downloaded install_flash_player_10_linux.tar.gz and extract the file, and put the libflashplayer.so copy to ~/.mozilla/plugins and /use/lib/firefox-5.0/plugins/.
When I use firefox to open a video which is on the youtube.com, there is not audio and video; click right mouse key, it show "moive not loaded".
when I use the method on the ubuntu desktop,32 bit system, the firefox can play the flash.

I type "about:plugins" on the address bar, it show:
Shockwave Flash
file:libflashplayer.so
version:Shockwave Flash 10.3 r181
MIME type                                  description                                                                            suffix
application/X-shockwave-flash            Shockwave Flash                                                      swf
application/futuresplash                                FutureSplash Player                                              spl


I don't why?

---

### Post by robertc36 on 2011-07-01
Have a look at [flashaid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") plug-in for Firefox it will install the correct version for you.

---

### Post by shibu_sawyer on 2011-07-01
> **ice2000feng said:**
> system:ubuntu server, 32 bit.
firefox: firefox 4 version or firefox 5 version.

I have downloaded install_flash_player_10_linux.tar.gz and extract the file, and put the libflashplayer.so copy to ~/.mozilla/plugins and /use/lib/firefox-5.0/plugins/.
When I use firefox to open a video which is on the youtube.com, there is not audio and video; click right mouse key, it show "moive not loaded".
when I use the method on the ubuntu desktop,32 bit system, the firefox can play the flash.

I type "about:plugins" on the address bar, it show:
Shockwave Flash
file:libflashplayer.so
version:Shockwave Flash 10.3 r181
MIME type                                  description                                                                            suffix
application/X-shockwave-flash            Shockwave Flash                                                      swf
application/futuresplash                                FutureSplash Player                                              spl


I don't why?
install the current version of firefox and try again and there are many plugins in the software center of ubuntu try it,
if nothing works,try ubuntu restricted extras,sometimes if anything doesnt works installing the restricted extras makes it works.

---

### Post by techno-mole on 2011-07-01
Curious indeed flash should work using the version in the repos with firefox 5.
My advice is to enable the restricted extras in synaptic and also make sure you have the follow also enabled using synaptic.

open synaptic (enter password)

then go to settings ---> repositories ---> other software

make sure both the independent and partner repos are enabled, then go to ---> updates and enable the following - important security updates, recommended, proposed and unsupported.

also make sure flash is installed in synaptic, just search for flash, you should have the plugin and the plugin installer installed.

I had some issues with flash but mainly because I'm using 64bit natty, and despite every other flash site working I still can't get any of the videos on the Independents website to work, even in chrome,chromium and firefox going to try opera as well.

---

