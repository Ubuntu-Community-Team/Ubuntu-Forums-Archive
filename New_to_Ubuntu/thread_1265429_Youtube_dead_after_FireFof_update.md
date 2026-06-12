---
title: "Youtube dead after FireFof update"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by myolbug on 2009-09-13
Hello
I did an update to FF 3.0.14 as part of the regularly released updates and now YouTube doesn't display.  Works Fine in Shiretoko.

Ideas?  It worked flawlessly before.

---

### Post by myolbug on 2009-09-13
Bumpinski!

---

### Post by arrange on 2009-09-13
COuld you elaborate a bit? Do you see a blank screen or what?

---

### Post by myolbug on 2009-09-13
Yeah, sorry...
When I am in Firefox and I go to a YouTube page, the window to show a video is missing.  Everything else is there.  Basically it looks like a Flash corruption.

It kinda sux because prior to this update, it was working flawlessly.  no pauses, no interference if I moved the mouse when it was in full screen.  I had followed directions on a thread here that allowed me to tweak my flash and that made YouTube seamless.  I have no idea which thread it was though.

---

### Post by kansasnoob on 2009-09-13
> **myolbug said:**
> Hello
I did an update to FF 3.0.14 as part of the regularly released updates and now YouTube doesn't display.  Works Fine in Shiretoko.

Ideas?  It worked flawlessly before.

Since you mention both FF and Shiretoko I assume you must be using Jaunty, eh?

Regardless, go to Synaptic and click on Search, then type "flash". Be certain you have NO swfdec-* or gnash installed. On mine all I have is ubuntu-restricted-extras and adobe-flashplugin.

Remember Firefox must be restarted before any changes take effect!

Most importantly, IMHO, why not just upgrade Firefox using Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by myolbug on 2009-09-14
I unchecked swfdec-* and it fixed it.  I think it was swfdec- Gnome.

Thank you!

---

### Post by myolbug on 2009-09-27
And it is down again!:confused:

As a matter of fact, most flash is down.  I have already done what was recommended in this thread and the settings are still the same.  

What now????

---

### Post by myolbug on 2009-09-27
Okay so I did the Ubuntuzilla thing (which I hadn't done before) and it upgraded my Firefox to 3.5.3, finally!, but, now I get a message on YouTube that says: > Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 

Now what?

---

### Post by myolbug on 2009-09-28
Per the instructions for [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation"), should I remove the Mozilla version of Firefox and does this then leave the Ubuntuzilla version in it's stead?
> Here are the steps to use this script to uninstall the Mozilla build of Firefox, Thunderbird, or SeaMonkey:

    * Completely exit Firefox or Thunderbird prior to installation (just in case).
    * Open a terminal
    * Enter this command to run the script (choose one depending on which software you want to remove; copy and paste to avoid typos): 

ubuntuzilla.py -a remove -p firefox

ubuntuzilla.py -a remove -p thunderbird

ubuntuzilla.py -a remove -p seamonkey

    * Read the instructions and follow the prompts. 
It is a bit vague on this point.

---

### Post by ElSlunko on 2009-09-28
I had the same problem. I uninstalled flash non-free and have no flash app installed. For some weird reason flash works even better now! I can actually click on youtube videos to make them full screen, advance in the timeline, etc.

---

### Post by myolbug on 2009-09-28
Well I removed the Mozilla version and it left the Ubuntuzilla version and youtube is working just fine again!  AS a matter of fact, it is all working better, Flash wise!

---

