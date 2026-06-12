---
title: "Firefox and Flash problems..."
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Guffmeister on 2011-02-10
Hi all,

firstly, I apologise if this gets ranty. I'm getting so disillusioned with Linux at the moment after a number of problems in a row, so this is just getting really irritating for me (even though it's a comparatively small problem). I hope someone can help.

I have Ubuntu 10.10, and I was just browsing the internet earlier when I clicked on a silly little game, which prompted me to download an additional add-on to play it. I thought nothing of it, but once I downloaded it, the game still didn't load. Odd. Now, though, anything that uses flash won't work. Any Youtube videos, games, etc, and additionally Firefox will no longer save my tabs when I shut down, so I get the homepage rather than my previous tabs, even though in preferences it still says "Open tabs from last session".

I disabled the Shockwave SWF player, and Youtube videos prompt me to download Adobe Flash, but none of the options work. If I download a .deb file Ubuntu complains that it's the 'wrong architecture 'i386'', and the APT file complains that 'Package 'adobe-flashplugin' is virtual.'.

Any help will be useful.

---

### Post by Linyx on 2011-02-10
Ubuntu-64 has some problem with Flash-Player, Any way, here is the Solution > [http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

---

### Post by jmszr on 2011-02-10
Guffmeister,

This Firefox add-on, FLASH-AID: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) , will "Remove conflicting flash plugins from Ubuntu Linux systems, install the appropriate version according to system architecture and apply some tweaks to improve performance and fix common issues".

I use it and it works very well.

---

### Post by Guffmeister on 2011-02-10
Hi! Yeah, thanks. I managed to sort the flash problem using a shell script from a different site, but thanks for the link. If I can find the one I used again I'll post it here.

However, the firefox tab problem still exists. It won't save the tabs once I close it down.

---

### Post by woodmaster on 2011-02-10
> **jmszr said:**
> Guffmeister,

This Firefox add-on, FLASH-AID: [url] , will "Remove conflicting flash plugins from Ubuntu Linux systems, install the appropriate version according to system architecture and apply some tweaks to improve performance and fix common issues".

I use it and it works very well.

I tried this and it didn't help @ all.  Granted my gfx chip sucks, it Flash worked fine in XP before I went all ubuntu.

---

### Post by woodmaster on 2011-02-28
bump?  Any other help on Fla stuttering and playing @ weird speeds.  My audio also plays too fast.  Maverick install fully updated.

---

### Post by woodmaster on 2011-03-14
fixing the audio also fixed my flash...fixed audio via:
[http://ubuntuforums.org/showthread.php?t=1592093](http://ubuntuforums.org/showthread.php?t=1592093)

---

