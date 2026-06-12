---
title: "Adobe Flash player installation"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by annakalsi on 2009-01-10
Hi

I have tried to install adobe flash player using the command sudo apt-get install adobe-flashplugin
 But get the error message 'Counldn't find package adobe-flashplugin'

How do I fix this? I need simple instructions - apologies.

Many thanks

---

### Post by Biggy on 2009-01-10
from terminal :

> sudo apt-get install flashplugin-nonfree

---

### Post by annakalsi on 2009-01-10
Thanks - I tried this. However I am still being told that I need to install flash. The main reason I am installing flash is because I want to use bbc i player.

Thanks

---

### Post by ibizatunes on 2009-01-10
the easy way is to install ubuntu restricted
```
sudo apt-get install ubuntu-restricted-extras
```

[http://www.medibuntu.org/](http://www.medibuntu.org/) 
will allow you to play dvd, have adobe reader, skype google earth etc

---

### Post by annakalsi on 2009-01-10
Apparently this is already installed. Sorry.

---

### Post by ibizatunes on 2009-01-10
have you got Mozilla vlc plug-in installed?
or real player installed

---

### Post by annakalsi on 2009-01-10
Dont think so. The plug ins I have listed are:

Java
Quicktime 7.2.0
Divx webplayer
Windows media player plugin 10
Totem web browser plugin 2.20.0
Shockwave flash 9.0 r152
Shockwave flash 9.0 r48

---

### Post by ibizatunes on 2009-01-10
Do you have vlc installed? What mediaplayers do you have installed?
If you have vlc install run this command
sudo apt-get remove mozzilla-plugin-vlc

---

### Post by annakalsi on 2009-01-10
Do not have vlc. Media players:

Amorak
LinDvd
Movie player
Serpentine
Sound juicer

---

### Post by mikewhatever on 2009-01-10
What version of Ubuntu do you have? From what you posted, you seem to have two versions of flash plugin installed. Remove them and install the new one.

---

### Post by ibizatunes on 2009-01-10
The reason i ask is vlc can break the iplayer, i dont know im affraid, i would guess that shockwaves is trying to run the flash applet and cant!
Sorry

---

### Post by annakalsi on 2009-01-10
Thanks. WIll try and uninstall and then reinstall again. Have version 7.10

---

### Post by ithanium on 2009-01-10
my flash installation didn't work without a restart of the system, maybe you have the same problem as I had!

---

### Post by ibizatunes on 2009-01-10
In 7.10 i had flash issues, it uses firefox 2,
8.04 and 8.10 are much better now because adobe now do a .deb version, and firefox 3
and i know in 8.10 that is the available in repo's, i think its in 8.04 backports (but not 100% sure)

Maybe look at upgrade your system to 8.04 even 8.10

---

### Post by annakalsi on 2009-01-10
I am trying to uninstall the plugins but they are not showing up where the filepath says that they are.

---

### Post by stanz on 2009-01-10
I went for the fresh install of 8.10
Everything gets the upgrade - conflicts are pretty much null.

Good HowTo's...
                                  [**Comprehensive Multimedia & Video Howto**]("http://ubuntuforums.org/showthread.php?t=766683")             

Hope it helps!

---

### Post by dje on 2009-01-10
if you want to use the iplayer desktop (not the online streaming service, although 7.10's version may also be too old even for this) you need the latest flash from the [adobe website]("http://get.adobe.com/flashplayer/"). Uninstall all versions you have installed now and install the latest

dje

---

### Post by mikewhatever on 2009-01-10
> **annakalsi said:**
> I am trying to uninstall the plugins but they are not showing up where the filepath says that they are.

Excuse me, but you are being rather vague. It's hard to help you this way. I am not sure how you managed to install two different plugins, can you tell? Try running <sudo apt-get remove flashplugin-nonfree>, then post the output of <ls /usr/lib/mozilla/plugins> and <ls .mozilla/plugins>.

---

