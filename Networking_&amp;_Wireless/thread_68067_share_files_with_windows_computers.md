---
title: "share files with windows computers"
date: 2005-09-22
forum: Networking &amp; Wireless
---

### Post by DarkManX4lf on 2005-09-22
ok...i have a home network setup with a modded xbox, a winxp laptop, a winxp desktop and this linux desktop. i want to share files from this linux desktop to the other items connected to my network mentioned above....and im pretty sure samba should do the trick right?

if so...i have a problem...i cant install it....i go to synaptic and try to install samba and this is the error it gives me...

samba:
  Depends: samba-common (=3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed


how do i get samba installed?

---

### Post by paul.hamlin on 2005-09-22
Hi there

Just joined the forum and your problem seems similar to mine. In my case I can network to Win machines but they cant "see"the Ubuntu machine, although everyone can ping each other. I am assigning my own IPaddresses till I sort this.

And I am very new to Ubuntu and  love it.

Will watch with interest.

---

### Post by xristos on 2005-09-22
[QUOTE=DarkManX4lf]

if so...i have a problem...i cant install it....i go to synaptic and try to install samba and this is the error it gives me...

samba:
  Depends: samba-common (=3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed


how do i get samba installed?[/QUOTE]

try this from the command line 

```
apt-get -f install
```

---

### Post by kevin_hill54 on 2005-09-22
To install Samba with Synaptic first remove the Samba-Common 3.0.14 and then install Samba.

It will automatically install the Samba-Common 3.0.10.

---

### Post by DarkManX4lf on 2005-09-22
[QUOTE=kevin_hill54]To install Samba with Synaptic first remove the Samba-Common 3.0.14 and then install Samba.

It will automatically install the Samba-Common 3.0.10.[/QUOTE]


if i try to remove Samba-Common it says:

To Be Removed:
-Ubuntu Desktop
-Kubuntu Desktop


is that ok ?

---

### Post by fordfan753 on 2005-09-22
[QUOTE=DarkManX4lf]if i try to remove Samba-Common it says:

To Be Removed:
-Ubuntu Desktop
-Kubuntu Desktop


is that ok ?[/QUOTE]

Yep, that's fine, they are only metapackages.

---

