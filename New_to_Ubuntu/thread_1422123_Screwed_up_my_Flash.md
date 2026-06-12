---
title: "Screwed up my Flash"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by myolbug on 2010-03-05
I was reading this; [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407) which discusses the intermittent flash button problem, and I did this:


Quick followup. I did the 64 bit Adobe workaround as well, and it works great now. However, there were many steps to kill the old Flash plugin (I had installed based on this article originally [http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)).

Here's the commands I ran from my history (after extracting the adobe .tar.gz download to ~/Temp):
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

sudo cp ~/Temp/libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp ~/Temp/libflashplayer.so /usr/lib/firefox-addons/plugins

I'm now able to watch fullscreen HD from Youtube & scroll around, play/pause without issues.

P.S. I'm running the NVidia 185.18.36 drivers on a Geforce 8600GT on a Core 2 Duo CPU w/ 4Gb of RAM.


And now my flash doesn't work.  I have the flash plugin in my .mozilla> Plugins, but nothing is working.

What should I do.  The stupid thing is that I had my Flash working great, and for some stupid reason I did this. [Facepalm]  I also need help upgrading to FF3.6 as I thought, again, like a dumb*** that if I unistalled FF then I would be able to start over.  Well, I just made it worse I think.

When I got to the Flash site to run their APT installer it says; Could not find package 'adobe-flashplugin'

Right now I feel like a total idiot.

---

### Post by myolbug on 2010-03-05
Never mind my dumbassness, I solved it by following this:
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

This solved both of my screw ups.

---

