---
title: "Need help with setting up wireless in T42"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by rolpa on 2010-02-28
Hy, obviously I'am a first time user and have difficulties. 
I installed Ubntu 9.10 on my IBM ThinkPad T42, but I can't set up wireless.
If i look at the desktop on the top right corner there should be a icon that looks like two monitors inset against each other, but there isn't any. Insted I have a small icon that looks like antenna and says no network connection! It dosen't show any wireless at all.
I have Intel Pro/Wireless 2200BG networkcard. Can this be driver problem ? 
If I wired my laptop with ethernet cable, it immediately connected to the internet.(though my touchpad stopped working:D) 
Or am I stupid enough not to be able to configure my wireless.
Any help at all will be welcomed.

Thank you.

---

### Post by themusicalduck on 2010-02-28
Try going to System > Administration > Hardware Drivers and see if you can install a driver from there. You'll need to be connected by ethernet to install them though.

---

### Post by asmoore82 on 2010-02-28
I used to have a T42 from work, now I'm on a T61.

They do indeed require the Atheros WiFi driver but it is blacklisted in 9.10.
To enable it, you need to edit the file "/etc/modprobe.d/blacklist-ath_pci.conf" ...

```
gksudo gedit "/etc/modprobe.d/blacklist-ath_pci.conf"
```
and put a comment mark(#) in front of the line "blacklist ath_pci"

so the original file looks like this:
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
```
and the modified version looks like this:
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
#blacklist ath_pci
```

Save and Close, then restart the machine and run "System -> Administration -> Hardware Drivers"
and use it to enable the Atheros Driver.

I'm currently running the Alpha/Beta release of the next version Ubuntu due out in April
and I'm happy to report that the pure open source driver now works "out-of-the-box" on my T61.

P.S. I reeeeally hope your T42 has that same chipset as mine did :D

---

### Post by fevemo on 2010-02-28
Hi, [asmoore82]("http://ubuntuforums.org/member.php?u=341737")

i did what you said but since the file is read only it doesn't let me save the changes
please help (I'm new to Ubuntu)

---

### Post by louieb on 2010-02-28
> **fevemo said:**
> Hi, [asmoore82]("http://ubuntuforums.org/member.php?u=341737") ...the file is read only...

Did you try to open it for editing like asmoore82 mentioned? It has a small typo. 

should be (missing the the 1st /)

```
gksudo gedit "/etc/modprobe.d/blacklist-ath_pci.conf"
```

---

### Post by asmoore82 on 2010-02-28
Ooo, The Shame! :oops:

Thanks a heap, louieb :popcorn:

---

### Post by rolpa on 2010-03-01
Hy,

Thanks guys I got my problem solved! 
Really nice forum!
This is mu first reply from my laptop which uses Ubuntu. Hope there will be many more so i can give back to the community. 

Good luck.

---

### Post by fevemo on 2010-03-01
hey, [louieb]("http://ubuntuforums.org/member.php?u=120176")

yes, I have already tried and it doesnt work, I get this message:
[COLOR=Red]bash: /etc/modprobe.d/blacklist-ath_pci.conf: Permission denied[/COLOR]
is there an other way????

---

### Post by fevemo on 2010-03-01
Ok now I was able to make the change but it still doesn't work

---

### Post by asmoore82 on 2010-03-01
I would burn a CD of the pre-release Ubuntu 10.04 just to see
if it works "out of the box" like my T61.

[http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)

---

