---
title: "re-installation of  Ubuntu"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by beswatcher on 2009-02-28
I have just read through this thread
[http://ubuntuforums.org/showthread.php?t=1083254](http://ubuntuforums.org/showthread.php?t=1083254)

This is something that I've been wondering about, but with a twist. I originally installed 8.04 from the internet using a trial CD. If I ever have to reinstall, will I lose all the add-ons and programs that I have installed since then? I know that I could do it with Win 98SE, what about Ubuntu?

---

### Post by Ms_Angel_D on 2009-02-28
> **beswatcher said:**
> using a trial CD

Umm there is no trial ubuntu is free and always will be...lol



> **beswatcher said:**
> If I ever have to reinstall, will I lose all the add-ons and programs that I have installed since then? I know that I could do it with Win 98SE, what about Ubuntu?

As with any O.S. if you need to re-install yes you will lose your programs and software unless you have your home on a separate partition([SEE HERE FOR INFO]("http://www.psychocats.net/ubuntu/separatehome")).

---

### Post by beswatcher on 2009-03-01
Thank you Ms, Angel!! Of course I meant live CD, but I'm a bit tired from trying to find out who got my Yahoo password and hit all my contacts with what looks to be a .exe link. My machine wasn't even running at the time it was sent! Oh well, tomorrow's work.

---

### Post by Temposs on 2009-03-01
To do what you want to do, that is, reinstall but keep the programs you've installed, you can try this program called remastersys, which is described here: [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

I think you'll need to download it from that site, as it doesn't seem to be in the Ubuntu repositories(the Add/Remove program).

---

### Post by miegiel on 2009-03-01
Check point 2 in the 2nd post in [How to Idiot proof ubuntu?]("http://ubuntuforums.org/showthread.php?t=1081848") I haven't tried it myself yet though.

---

### Post by tgyorgyi on 2009-03-01
Remastersys is great, and it indeed saves you a lot of time - granted your customized OS fits at least on a DVD (too many extra software can bloat this up a lot).

If you enable third-party projects in System/Administration/Software sources, then add this under Third party: 

deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

then you will be able to install Remastersys through Synaptic package manager. Using the package manager has the plus that you get automatic updates for Remastersys.

(If you prefer to do the above manually, then add

# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

to your /etc/apt/sources.list)

---

