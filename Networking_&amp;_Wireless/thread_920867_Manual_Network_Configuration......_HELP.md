---
title: "Manual Network Configuration...... HELP"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Nylo on 2008-09-15
I need some explanation.  Ive completed the previous requirements but Im stuck here and not too sure what to do.  I'm very new to Linux so don't laugh.   

----------------
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

---

### Post by darrelljon on 2008-09-16
Surf the internet. Does Google work?

---

### Post by qstraza on 2008-09-16
> **Nylo said:**
> I need some explanation.  Ive completed the previous requirements but Im stuck here and not too sure what to do.  I'm very new to Linux so don't laugh.   

----------------
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
i think u r missing essid thingie.

sudo iwconfig <interface> essid <name of the AP>

---

### Post by Nylo on 2008-09-16
> **darrelljon said:**
> Surf the internet. Does Google work?

I did but I when I found something it was over my head.  There just does not seem to be any info on this at the bonehead level.

---

### Post by Nylo on 2008-09-16
> **qstraza said:**
> i think u r missing essid thingie.

sudo iwconfig <interface> essid <name of the AP>

You are right ...  Im missing something.   :confused:

I'm not sure how it would even look if I did put the essid thingy in.  

I just need someone to tell me how to format the command line with my info.

---

### Post by qstraza on 2008-09-16
> **Nylo said:**
> You are right ...  Im missing something.   :confused:

I'm not sure how it would even look if I did put the essid thingy in.  

I just need someone to tell me how to format the command line with my info.
I gave you the command line, just run that before requesting for an ip from dhcp server.

---

### Post by darrelljon on 2008-09-17
> **Nylo said:**
> I did but I when I found something it was over my head.  There just does not seem to be any info on this at the bonehead level.

Seconded.
I tried to write [a simple guide here]("http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux").
And also a command line thingy [here]("http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux-Via-the-Command-Line").
See also [this guide]("http://ubuntuforums.org/showthread.php?t=684495").

---

### Post by Nylo on 2008-09-17
> **darrelljon said:**
> Seconded.
I tried to write [a simple guide here]("http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux").
And also a command line thingy [here]("http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux-Via-the-Command-Line").
See also [this guide]("http://ubuntuforums.org/showthread.php?t=684495").

Thanks.  Ill look it over.

---

