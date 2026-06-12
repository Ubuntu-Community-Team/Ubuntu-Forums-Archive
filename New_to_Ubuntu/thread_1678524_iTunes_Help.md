---
title: "iTunes Help"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by evantoman on 2011-01-30
Hey Guys.
I know that there are numerous posts with similar questions, but after searching through them I can't seem to find the right answer. Hopefully somebody can help me. Here is my situation:

I am running Ubuntu 10.10. After installing Wine, I tried to install iTunes 10.x. The installer said that it had completed, and when I went to start up iTunes it wouldn't work. Error Code 7. I tried to reinstall it, and there was no difference. So then I tried uninstalling it. The uninstaller actually **installed** it again, although there was still no difference. After looking through these forums, I found out I should try uninstalling iTunes from Wine. This did the same thing as before. So I returned to the forums, and read that I should manually delete the files. This is did. **Now**, I have recently discovered that iTunes 10.x does not install on Ubuntu, and that only version 9.0.2 will work. So i downloaded the installer for iTunes 9.0.2 and it says "A newer version of iTunes is already installed on this computer." I tried uninstalling Wine, then re-installing it. After noticing no change, I have uninstalled it again, in hopes that somebody can give me detailed instructions right from the start.

I would like to **uninstall iTunes 10.x** and **install iTunes 9.0.2**, and re-install **Wine**.
I would greatly appreciate any help, thank you.

---

### Post by davidmohammed on 2011-01-30
wine installs its stuff in a hidden folder on your home directory called .wine

open nautilus (home folder) - use "View - show hidden files" and the find the folder .wine

Delete it.

then install itunes 9.02

---

### Post by speedwell68 on 2011-01-30
What Apple device are you using.  You could use a native application to manage it.

---

### Post by davec64 on 2011-01-30
To be honest depending what you want to do it looks like iTunes is a waste of time under wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

Nothing is rated higher than a silver and then the connection to an iPod/iPhone doesn't appear to work, so syncing would be an issue.

The alternative if you want to use iTunes is to run it in a Windows virtual machine using something like Virtualbox (this is what I do).
If you do decide to use Virtualbox use the PUEL version as this provides USB support for connecting your device.  :)

---

### Post by andymorton on 2011-01-30
From my experience it's a waste of time trying to install itunes on Ubuntu. Even if you get it to launch without crashing it will almost certainly be unusable anyway. 

You'd be much better of using Rhythmbox, Banshee or one of the other native Linux music players. 

andy

---

### Post by asmoore82 on 2011-01-30
> **andymorton said:**
> From my experience it's a waste of time trying to install itunes on Ubuntu. Even if you get it to launch without crashing it will almost certainly be unusable anyway. 

You'd be much better of using Rhythmbox, Banshee or one of the other native Linux music players. 

andy

[SIZE="5"]+1[/SIZE]

All native Linux music apps are for playing music.
iTunes's chief purpose is selling music and iPods.

---

### Post by evantoman on 2011-02-01
> To be honest depending what you want to do it looks like iTunes is a waste of time under wine:

[http://appdb.winehq.org/objectManage...ation&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

Nothing is rated higher than a silver and then the connection to an  iPod/iPhone doesn't appear to work, so syncing would be an issue.

The alternative if you want to use iTunes is to run it in a Windows  virtual machine using something like Virtualbox (this is what I do).
If you do decide to use Virtualbox use the PUEL version as this provides USB support for connecting your device.  :smile:

Thanks Davec64. I like the idea of Virtualbox. :D

Thanks everyone for your input.

---

