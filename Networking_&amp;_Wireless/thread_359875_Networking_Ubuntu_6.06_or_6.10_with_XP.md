---
title: "Networking Ubuntu 6.06 or 6.10 with XP"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by geotrouvetout on 2007-02-12
Hello,

Is it possible to establish a small wireless home network between 1 machine on Ubuntu 6.06 or 6.10 and onother one Win XP, share folders and a printer? If yes, would you please explain how to do it? 

Thank you in advance.

---

### Post by newlinux on 2007-02-12
You can share files and printers using SAMBA.

Search for SAMBA in [http://ubuntuguide.org/](http://ubuntuguide.org/)

I'm assuming you know how to setup the wireless network. If you are using a wireless router it should be straight forward.

---

### Post by geotrouvetout on 2007-02-12
Thanks, I'll look at Samba. I know how to set a network up on Windows but not Ubuntu if it's any different. Ubuntu is a totally new animal for me, try'n to tame it.

---

### Post by greyspoke on 2007-02-13
I was in the same position as you about a week ago geotrouvetout.

I found stormbringer's thread [by here]("http://www.ubuntuforums.org/showthread.php?t=202605") very helpful, it didn't work until I replaced the smb.conf file as suggested there.

Once you have set up shares on your Unix and/or Windows machines, Ubuntu will find them via Places -> Network Servers and Windows will if you ask it to find computers on the network.   That seems to be the best way for an ad-hoc network where no machine is permanently on and you will have forgotten what folders you have shared on various machines and what you called the shares. (Xubuntu doesn't seem to be able to seek out shares like this, you have to mount the shares yourself, it must be Nautilus doing the clever bit I think).

---

### Post by newlinux on 2007-02-13
If you run into any problems with Samba (and lots of people do because there are a lot of options and configurations) just ask here. The other benefit is that lots of people use Samba and can help. I've taken my lumps, and now can help a bit.

---

