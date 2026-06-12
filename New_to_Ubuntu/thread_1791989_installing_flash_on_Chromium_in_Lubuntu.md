---
title: "installing flash on Chromium in Lubuntu"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by LokeiZero on 2011-06-27
Hi,

How do you install flash for Chromium in Lubuntu?

I tried the command: 'sudo apt-get install flashplug-nonfree'

and received the results: 'Unable to locate package flashplugin-nonfree

---

### Post by shuttleworthwannabe on 2011-06-27
Flash Plugin should be in the software centre--search Adobe Flash player use that rather to install; it should work. 

Edit: enable all repo's in under sources (canonical partners)

---

### Post by rickyLOLZ on 2011-06-27
Did you try to go to Adobe's Flash Player website? Maybe they will let you download flash on every browsers.
By the way, this isn't a Lubuntu forum, it's a Ubuntu forum.
Have luck! :KS

---

### Post by rickyLOLZ on 2011-06-27
> **shuttleworthwannabe said:**
> Flash Plugin should be in the software centre--search Adobe Flash player use that rather to install; it should work. 

Edit: enable all repo's in under sources (canonical partners)

There's no software center on Lubuntu. Only Ubuntu.

---

### Post by wolfen69 on 2011-06-27
> **rickyLOLZ said:**
> 
By the way, this isn't a Lubuntu forum, it's a Ubuntu forum.


That doesn't matter. All forms of ubuntu are supported here.

---

### Post by shuttleworthwannabe on 2011-06-27
> **rickyLOLZ said:**
> There's no software center on Lubuntu. Only Ubuntu.
Holy...I was not aware of that. I last used Lubuntu 2 seasons ago. I usually install Ubuntu Tweak and get all  my extras there, even in Lubuntu.

---

### Post by crispy_420 on 2011-06-27
> **LokeiZero said:**
> I tried the command: 'sudo apt-get install flashplug-nonfree'


You got a typo there, should be 'flashplugin-nonfree' also you need to enable the repos in synaptic, think multiverse or partner are needed.

---

### Post by amjjawad on 2011-06-28
> **LokeiZero said:**
> Hi,

How do you install flash for Chromium in Lubuntu?

I tried the command: 'sudo apt-get install flashplug-nonfree'

and received the results: 'Unable to locate package flashplugin-nonfree

You shouldn't need it because it's already installed with Chromium. However, you can install it from Synaptic.

---

### Post by aeiah on 2011-06-28
it isn't already installed in chromium. chromium uses the same location as firefox, so if you have it installed there, it will also be installed for chromium. in addition, i think chrome installs flash.

---

### Post by Paul T. on 2011-06-28
> **aeiah said:**
> it isn't already installed in chromium. chromium uses the same location as firefox, so if you have it installed there, it will also be installed for chromium. in addition, i think chrome installs flash.

Chrome doesn't install Flash by default, use Synaptic.

---

### Post by LokeiZero on 2011-06-28
How do you use synaptic? I searched for 'flash' and 'adobe' and it came up with nothing.

---

### Post by amjjawad on 2011-06-28
> **LokeiZero said:**
> How do you use synaptic? I searched for 'flash' and 'adobe' and it came up with nothing.

flashplugin-installer

---

### Post by beew on 2011-06-28
Use the flash-aid addon for Firefox, it installs flash system wide so it doesn't matter which browser you actually use. It automatically downloads the latest flash, cleans up conflicting flash versions and optimize it for your system. It works on all debian systems. It is created by lovinglinux, who is a regular on this forum.

---

### Post by dFlyer on 2011-06-28
You must first enable all repo's under sources (canonical partners). This can be done from software center under edit software resources. You will have to refresh the repo's before they show up. This can be done from the command line with:

sudo apt-get update

---

### Post by amjjawad on 2011-06-28
I'm on Lubuntu 11.04 right now.

I have both Chromium (installed by default) and Firefox 5.0 (I have downlaoded it) but "adobe-flashplugin" is **NOT** installed.

**Edit**: I was wrong regarding [*my previous post*]("http://ubuntuforums.org/showpost.php?p=10989417&postcount=8"). Looks like it has to be done manually.

---

### Post by beew on 2011-06-28
Never mind the repo and Adobe, use Flash-Aid!!!!

---

### Post by benmayim on 2012-08-17
Here are the instructions for a Noob like me to install Flashplayer into Chromium Web browser:

1. Download latest "libflashplayer.so" file from adobe in a tar.gz file.
2. [http://www.adobe.com/go/getflashplayer?promoid=ISMRZ](http://www.adobe.com/go/getflashplayer?promoid=ISMRZ)
3. Use file manager in lubuntu to find the tar.gz file. In Lubuntu it's usually in "/home/this/Downloads"
4. unzip .tar.gz file (usually this will start by double-clicking on the tar.gz file. You'll get a window and just
     hit "extract" and this will extract the file  "libflashplayer.so" to the same folder ("/home/this/Downloads")
5. Use file manager to make sure you have a "/usr/lib/chromium-browser/plugins" folder
6. You have to copy this file from the downloads location to the plugins location
7. You have to use a terminal and "sudo" in order to copy that file from one location to the other
     because you do not have administrative rights in the file manager, and the file manager won't allow you
     to just drag and drop it there.
8. So go to start-accessories-LXTerminal and open a terminal window
8. Here's the command to copy the above file using a terminal:
    sudo cp /home/this/Downloads/libflashplayer.so /usr/lib/chromium-browser/plugins

    Just type that into the black terminal window

Of course your download may come to a different folder and maybe your destination folder will be different,
but once you get the .so file to the proper location the plugin will work.

---

### Post by wildmanne39 on 2012-08-18
Thanks for sharing. Thread Closed.

---

