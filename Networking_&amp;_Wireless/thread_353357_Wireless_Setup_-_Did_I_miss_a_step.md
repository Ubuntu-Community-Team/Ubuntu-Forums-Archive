---
title: "Wireless Setup - Did I miss a step???"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by themilstead on 2007-02-04
Hey, all. I just bought a Zonet **ZEW2500P** and recently read that it was supported by Ubuntu. I was excited to hear this, as I have been trying on and off to get Linux connected to my network for years now. I think I've gotten pretty far from lurking around here, but somehow I still can't get an Internet page to load or an application package to download with Synaptic. Here's what I've done so far:

- Installed ndiswrapper and loaded the latest driver from the Zonet website (well, really from my flash drive)
- Configured the adapter under the Network section with the IP, ESSID, etc
- It showed up in "iwconfig"
- Ran a ping on my IP and it seemed to be running fine
- Did a "iwlist rausb0 scan" and it detected my home network as well as my neighbor's (like it's supposed to) :roll: 

But, somehow, after all of that, I still can't get any websites or anything to respond. Was there something else that I neglected to do? The only thing that comes to mind is that while the hardware is operating fine and I can ping stuff, I'm not connected specifically to my network. I'm certain all the settings in "Network" are correct, though. Any help would be greatly appreciated, as I was really looking forward to finally being able to install and use Ubuntu online.

Thanks!

---

### Post by phansiizwe on 2007-02-04
Is your network using any protection protocols (WEP or WPA)?

---

### Post by themilstead on 2007-02-04
Hmm...yes, WEP is enabled, but I've already got the hexadecimal key entered in...so I should have access.

---

### Post by tturrisi on 2007-02-04
try using a hyphen after every 4 characters:
1234-5678-90 etc.

---

### Post by themilstead on 2007-02-04
Okay, update. Earlier I temporarily disabled WEP, and everything worked perfectly. So, it's just not accepting any of my keys, it looks like.

I'll try it with the hyphens like you suggested...Hopefully that's all I need!

---

### Post by themilstead on 2007-02-04
Hmm...Doesn't work with the hyphens either, so I have WEP disabled until either:
a) I can figure out a solution
b) I find an old thread addressing a similar issue on the forum
c) My dad gets impatient and turns WEP back on

If anyone else has any ideas, let me know! I am 100% sure my keys are valid, as they all work in Windows.

---

### Post by themilstead on 2007-02-04
Okay...I'm one step closer!

I was finally able to connect with WEP enabled by starting from a fresh reboot and giving the terminal "**sudo iwconfig rausb0 essid *MYESSID* enc *MYPASSWORD***", theeennnnn going into System>Administration>Networking and simply entering my ESSID there also. I'm not sure why the terminal accepts my password, but the GUI equivalent does not. But I'm just happy it works, lol. Now here's my only question at this point, and if I can get this, I think I'll be home free. :D

Is there a way to have the terminal command I posted above somehow execute itself on boot so I don't have to type it every time? Like a line to add to a startup file or something? I'm really hoping so. :)

---

### Post by tturrisi on 2007-02-04
> **themilstead said:**
> Okay...I'm one step closer!

I was finally able to connect with WEP enabled by starting from a fresh reboot and giving the terminal "**sudo iwconfig rausb0 essid *MYESSID* enc *MYPASSWORD***", theeennnnn going into System>Administration>Networking and simply entering my ESSID there also. I'm not sure why the terminal accepts my password, but the GUI equivalent does not. But I'm just happy it works, lol. Now here's my only question at this point, and if I can get this, I think I'll be home free. :D

Is there a way to have the terminal command I posted above somehow execute itself on boot so I don't have to type it every time? Like a line to add to a startup file or something? I'm really hoping so. :)
post the contents of /etc/network/interfaces
which is the file that brings up networking during boot.

---

### Post by themilstead on 2007-02-05
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface rausb0 inet dhcp
wireless-essid BAHMA

auto rausb0

iface rausb1 inet dhcp
wireless-essid BAHMA

auto rausb1
```

Hmm...it looks to me like it would automatically load. Is this right? (Not in a position to reboot and test it at the moment)

---

### Post by tturrisi on 2007-02-05
There should not be 2 rausb devices.
For WEP, change to:

auto rausb0
iface rausb0 inet dhcp 
wireless-essid BAHMA 
wireless-key 1234567890
# or 1234-5678-90 a hyphen after every 4 characters

---

### Post by themilstead on 2007-02-05
> **tturrisi said:**
> There should not be 2 rausb devices.
For WEP, change to:

auto rausb0
iface rausb0 inet dhcp 
wireless-essid BAHMA 
wireless-key 1234567890
# or 1234-5678-90 a hyphen after every 4 characters

Sorry to bump this so late, but I just tried it and it worked beautifully! Thanks a lot for your help! :)

---

