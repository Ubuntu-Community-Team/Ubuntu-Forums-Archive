---
title: "WPA for DWL-G510 PCI (D-Link)"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by jaerune on 2006-08-03
I've just installed Dapper Drake, and I've been trying to get the WPA-PSK support on my card enabled. I've installed network-manager-gnome and under Network settings it sees a card, but it won't let me configure it to WPA, only WEP. The Network Manager icon has a (\) cross through it and says "No network devices have been found" if you left-click it. It's enabled.

I know my card, which is a Rev B1 4.10 SHOULD support WPA-PSK (it did under Windows 2000), but Ubuntu doesn't seem to know that. Any ideas?

Much appreciated!

---

### Post by jaerune on 2006-08-04
I got it working. How? Uhm... I, uh... I don't remember. I edited something or the other. O_O; I should probably have written that down...

I think it was /etc/network/interfaces

But I had to manually browse to that particular sub-folder before it would actually open with any information. I #'d out the aht0 and eth0 references, rebooted and BAM. Damn thing worked. :)

Here:

sudo apt-get install network-manager-gnome
cd /
cd /etc
cd /nework
sudo gedit interfaces

comment out ath0 and eht0 references. Restart. Boof?

---

### Post by for_serg on 2006-10-14
jaerune, just installed 6.06, the same problem. Card seems to be the same as yours.

I am a *nix newbee so could describe the solution in more detailed and easy way. 

Generally, is it a problem with driver of network interfaces config?

Thanks a lot in advance!! :)

---

### Post by jaerune on 2006-10-14
I'll be honest I cannot remember, and I got fed up with Ubuntu spamming my router so hard that it constantly knocked my XP Laptop off the network.

Here's what I remember doing:

First, you want to install network-manager-gnome by using the Software Repositories method, outlined here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Just look for gnome-network-manager and add it. You're going to need a hardwire connection for this, because your computer HAS to get the files from somewhere. If you don't have the ability to get the machine online, you're going to need to find the correct repositories online and download them with a computer that will connect and burn them down to a CD or something.

Out of the box, the version of gnm that I used failed to recognize my wireless card.

So I followed the other steps I outlined:

Open Terminal (under applications)

Type:

cd /
cd /etc
cd /nework
sudo gedit interfaces

Type in your password for your account. You'll get an entire page that has all kinds of crazy stuff in it. You want to look for every instances of ath0 (that's a zero) and put a hash mark (#) in front of it so that line is commented out. The line will start to look like:

#ath0 blah blah blah

Do the same to all lines that start with eth0 (also zero). Save your document by going to "File -> Save", then close the page. Reboot Ubuntu normally. When you log back in, you'll see the WiFi Manager at the upper-right of your screen up near the time and everything. It'll look like an atom as it's loading.

When it's done, if your network has zero security you'll be automatically connected. If you're paranoid like me, you'll have AT LEAST WPA-PSK TKIP security enabled, if not WPA-2. In which case you're going to have to add a wireless network connection and specify the name and everything, like the password and such.

I'm fairly sure that at one point I had to edit fstab. I can't remember why, but I'm pretty sure I had to do it to get the method to work. I'm sure there are much cleaner ways out there, and I've got a PCI-based D-Link DWL-G510 H/W ver B1 F/W ver 2.11 that is free to anyone that is willing to pay the shipping cost and will work to add this to the documented and supported hardware list, as it's a highly sold item at OfficeDepot.

---

