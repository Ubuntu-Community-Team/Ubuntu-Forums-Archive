---
title: "VPN Question"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by srt5 on 2007-02-16
Hi all,

I'm wondering if someone can help me. I am in a transition stage between Windows XP Pro and Ubuntu, and it's going well so far thanks to the help and support I have received from this amazing community.

On windows, I was able to connect to the office via VPN by setting up a new connection, then I was able to map network drives in order to work on projects remotely. I was wondering what the Linux equivalent of this would be and can anyone offer me any advice on where to start?

I have seen the terms vpnc and PPTP floating around this forum, is this what I'm looking for? Excuse my ignorance, I'm still a bit new to this!

Thanks

---

### Post by x64Jimbo on 2007-02-16
vpnc is probably what you're looking for, though you'll probably want to use a graphical front-end for it like kvpnc. NetworkManager also has a plugin for vpnc, but I have had mixed luck with it.

---

### Post by maxamillion on 2007-02-16
this one is good:
[http://www.ubuntuforums.org/showthread.php?t=28396](http://www.ubuntuforums.org/showthread.php?t=28396)

if that one doesn't work, try here:
[http://www.ubuntuforums.org/showthread.php?t=91249](http://www.ubuntuforums.org/showthread.php?t=91249)

---

### Post by fraktalek on 2007-02-16
It dpends on what kind of vpn client you used on Windows I think. I had luck with Kvpnc but found NetworkManager literally useless.
And as for the drive mapping - again, it depends... if it's windows shares (samba) then you'd use something like ```
mount -t smbfs //remote_pc/tmp /media/local_dir
```
and similarly for NFS, etc.

fraktalek

---

