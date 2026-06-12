---
title: "Wirelss woes"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Tainek on 2007-02-15
Hey

Well I've spent a good few hours searching, hoping i wouldn't need to be a bother, but if i carry on i'll develop male pattern baldness much sooner than i'd hoped :P

I have a MSI (Ralink) MS-6877 Wireless internal chipset , and i cannot get it to see any networks

My Networking menu shows i have

Wmaster0
Wlan0

the laptop has both a wireless card, and a mini-card slot for putting other wireless devices in

I Downloaded Kwifimanager and did a network search, which instantly came back negative (I am certain the network is there, due to pda)

so assuming the drivers were the fault, i did a search:

[http://ubuntuforums.org/showthread.php?t=323516](http://ubuntuforums.org/showthread.php?t=323516)

This guy has the same chipset as me, and helpful people have linked some guides

My problem is, when i follow the first step on one guide (the blacklist step) i come across an empty file, if i try to save it, i am informed the file does not exist (aaaah!)

as i continue on, i get errors doing everything (and im certain im typing them correctly)

i tried the NdisWrapper method, but my drivers are a .Exe , and the guides i find only mention .zip drivers

Please help an ubuntu noob! :) :confused:

(Ugh, just noticed the typo in the title :P)

---

### Post by renzokuken on 2007-02-15
firstly, which file is blank and does not exist, what is the location of it?

and secondly, you can extract the necessary files from an .exe using cabextract (i think its called that anyway) but it can definately be done.......

---

### Post by renzokuken on 2007-02-15
found this

Windows Executables can be several things.

Self-extracting zip file. Open this with unzip in the console, or Ark

Self-extracting rar file. Make sure you have unrar-nonfree (just unrar in newer releases) and use unrar from the console or Ark

Microsoft Cabinet file. Install 'cabextract' and use cabextract from the console to open it.

Installshield Cabinet file. Install 'unshield' and use unshield from the console to open it.

---

### Post by changcheng on 2007-02-15
Mate, it sounds really bad when you got Wmaster0. Last time I got Wmaster0 in my system and my Wireless was not working too. I think it is because you have to blacklist the driver that come with Ubuntu.

---

### Post by Tainek on 2007-02-15
> **renzokuken said:**
> firstly, which file is blank and does not exist, what is the location of it?

and secondly, you can extract the necessary files from an .exe using cabextract (i think its called that anyway) but it can definately be done.......


Ty for the reply

the file that is blank and doesnt exist the the blacklist file itself

(/etc/modprobe.d/blacklist )

so i cant blacklist the bad driver

i'm D/ling the exe now, and i'll try to extract it, taking over an hour (6kb/s, woo :|) and post when ive yanked it open

---

### Post by renzokuken on 2007-02-15
if its not there you can simply create it.........blacklisting only uses one line....for example, i blacklisted the rtl, r8187 and rtl8187 modules so my blacklist file looks like this

```

blacklist rtl
blacklist r8187
blacklist rtl8187

```

and thats it.......

---

