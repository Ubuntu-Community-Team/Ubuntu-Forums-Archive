---
title: "WiFi password asked TWICE"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2008-01-24
I have installed Ubuntu on several machines, two of those having wireless internet access. One of them suddenly started asking the wireless password twice. So even though the password is in the keyring manager, I still have to give the wireless key too.

I removed the key from the keyring more than once, to make sure NetworkManager had the right key in the keyring, but the behaviour stays the same. What is going on?

And another question: can I automatically open the keyring at boot? I already log in automatically, and having to fill in a password just to connect to the internet is silly in my case (home use).

---

### Post by peabody on 2008-01-24
I think this is a known bug on launchpad.  only advice I'd have is to wipe your keyring out and reboot.  (rm .gnome/keyrings/*) and try again.

The asking for the password has been deemed necessary by the devs of gnome-keyring I believe because the password acts as a cipher and basically encrypts the keyring so your wireless network passwords are never stored in plain text on the hard drive.

Myself, I use [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/).  Much nicer than network manager in my opinion.

---

### Post by DFreeze on 2008-01-28
I just fought with this machine once more and I just can't understand what is going on. To explain matters somewhat:

I installed Ubuntu on my mothers computer. Her wireless network is called the same as mine and I suspected the problem to be in that area. But I removed the key from the keyring, removed the SSID of my wireless router in "gconf-editor" (there were two SSID's so I REALLY thought the problem would be there).

But I still had to log in the wireless twice! So I just renamed her wireless router to something else, but again: two times typing the key... I'm going nuts here!

I have her computer on auto-logon to relieve her of typing her password on startup, but now she has to type two passwords: one for her keyring and one for the wireless! (auto-logon not unlocking the keyring is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/181281"), also [this one]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/140755"), and [this one]("https://bugs.launchpad.net/ubuntu/+source/pam-keyring/+bug/137247").

---

### Post by peabody on 2008-01-29
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) is the way to go man.  Really easy to install, only hitch is you have to manually add it to launch after it's installed, via the session control panel.

---

