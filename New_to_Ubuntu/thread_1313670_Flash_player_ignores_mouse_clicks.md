---
title: "Flash player ignores mouse clicks"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Dapilot1 on 2009-11-03
Hey I cant seem to get flash to work right on 64-bit ubuntu. I've tried the install button from inside firefox and uninstalling that and putting the 64-bit one into .mozilla/firefox/plugins. Movies will play and other stuff will work if it autostarts, but it ignores my mouse clicks. It still knows where the mouse is. For instance, the volume slider will come up when I hover over the right spot, but I cant grab it and pull it down. Any insight?

---

### Post by jimmy the saint on 2009-11-03
Here is the fix as well as the bug report that deals witht he issue



Edwards fix for Linux noobs (like me...)

1. Starta a Terminal window.
2. Type: cd /usr/lib/nspluginwrapper/i386/linux/
3. Type: sudo mv npviewer.bin npviewer.bin.real
4. Type: sudo pico npviewer.bin
5. Add these two lines of text to the file, i.e. Pico:
#!/bin/sh
GDK_NATIVE_WINDOWS=true /usr/lib/nspluginwrapper/i386/linux/npviewer.bin.real $*
6. Press "Ctrl+x" to exit and save.
7. Type: sudo chmod 755 npviewer.bin

Done! Now enjoy the full splendor of flash-clicking!

Bear in mind that even though you are on a 64 bit system, these instructions are correct.  npviewer.bin is in that folder.


[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all)

---

### Post by cariboo on 2009-11-03
I'm not sure if you are using the alpha from Adobe labs, but libflashplayer.so should be located in /usr/lib/mozilla/plugins. I found that the version installed from the repositories didn't work for me, so I downloaded it from [here]("http://labs.adobe.com/downloads/flashplayer10.html"), extracted it and copied it to the correct directory. I can fully interact with the mouse using this version.

---

### Post by 3rdalbum on 2009-11-03
I just noticed this problem last night. I'm using 64-bit Flash Player alpha in Opera, with the libflashplayer.so file in /usr/lib/mozilla/plugins, and this directory is referenced in Opera's "pluginpaths.ini" file.

Keypresses still work and the mouse location works.

I don't have nspluginwrapper so the above instructions are useless.

---

### Post by sambita on 2009-11-03
Have you tried the solutions [**here**]("https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all")?

There are a couple workarounds there. 

[This one]("https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/143") seems to have solved it for many people, although not me :(

My current (mildly annoying) workaround is to hold down button mouse while out of flash controls and drag it inside, then clicking in the desired control. (I dont remember who came up with this)

Edit: Seems like my reply became obsolete! hehe, thats what happens when you take too long to write it :)

---

### Post by Dapilot1 on 2009-11-04
Points to jimmy for being a saint, that script thing worked.
Thank you everyone for your help.

---

### Post by Excedio on 2009-11-04
+1 to Jimmy for sure!

That worked perfectly! An i love the way youtube videos go to and from full screen. :-)

---

### Post by rifak on 2009-11-07
im not sure, i think you guys are running 64-bit..is this correct? i tried to use the fix from above, but im not running 64bit and have no npviewer file on my computer, so im not sure what to do now..any advice?

---

### Post by lookitseman on 2009-12-20
Jimmy got it spot on.

Be sure to close and restart your browser(s) after applying the fix.

---

