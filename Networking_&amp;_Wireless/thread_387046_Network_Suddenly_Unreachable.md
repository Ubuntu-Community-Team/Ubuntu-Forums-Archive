---
title: "Network Suddenly Unreachable"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by brandg on 2007-03-17
I just installed Ubuntu yesterday, I got all the updates, and installed new programs all night long. Seriously, I was really enjoying looking through all the programs I could grab, seeing all the potential in this system. I mounted the NTFS partition of my Windows drive, got access to networked computers, I was rocking.

However, as the night wore on, I decided it was time to go to bed. I put my system into suspend mode, and left it until morning.

This morning, I noticed that I'd lost wireless access. To be clear, I can see that eth1 is still working, it's got strong signal strength, and it says it's receiving. However, no network programs work. Firefox says it has no connection, I can't find my networked drives, and when I try to ping my router, I see "Network is unreachable".

I installed something last night called "Network Manager" that I hoped would help me switch between wireless home and wireless work. Just in case that was the culprit, I've removed the program, but with no positive result.

Could I have installed a program that disabled wireless in such a strange way? And if so, have you ever heard of any software that has caused this?

Thanks,

Brand

---

### Post by dbott67 on 2007-03-17
It could be network manager.  Some people have experienced difficulties in the past, as network manager tended to nuke your /etc/network/interfaces file and manage the settings itself.  Can you post the output of:
```
cat /etc/network/interfaces
```If your missing reference to eth0, eth1, wlan0, or ath0 in the file, I would suspect this as the problem.

See this page: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) for an explanation as to the commenting out of entries in the interfaces file.

There is a better package that I use called network-manager-gnome:
```
sudo apt-get install network-manager-gnome
```

-Dave

---

### Post by brandg on 2007-03-17
Dave,

First, thank you for your prompt reply. I did the "cat" call as you asked, and I've posted the output, but there's been another wrinkle since I wrote the first post.

I suddenly got the idea that, if the network manager didn't uninstall properly, it might have left some files tainted. So, on a lark, I re-installed network manager. Now, I'm back to working wirelessly. Now I'm nervous that I can't ever un-install it again. :) 


here's the output (after re-installing):

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface eth1 inet dhcp
wireless-essid MyNet
wireless-key **** removed for obvious reasons ****

auto eth1









auto eth0

```

I can tell that it recognizes eth1 in this list. Maybe, if I uninstall Network Manager again, I can check the new version of this file against the previous dump?

Again, thank you very much for your help.

---

### Post by dbott67 on 2007-03-17
If you remove it again, make sure you 'purge' the configuration files.  Check the man pages for apt-get (man apt-get) to see the syntax for purging.

Back up your interfaces file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

If you ever have difficulties you can uninstall network-manager and then replace the existing file with your know-working backup.

-Dave

---

### Post by chili555 on 2007-03-17
There are quite a few posts on this forum related to wireless not coming back after suspend. Some seem to be related to specific cards and ACPI, some not. Network Manager is often involved, maybe because it doesn't play well with suspend or maybe simply because it's used by almost everybody.

I don't use it, because I don't roam, except around the house. Either you love it or you hate it.

I would search the forums for wireless suspend before I took more elaborate measures, like a Sawz-All.

---

### Post by brandg on 2007-03-17
Dave -

Great. Thanks again!

I've already made the backup, and now I'm copying this entire thread to a text file, so I don't forget which file it is, if something else goes wrong. :)


Chili -

Now that I've got it working again (and Dave has shown me how to protect from uninstalling), I'm going to be running some experiments (suspending and reviving with and without the Network Manager). If I can find a consistent thread of issues, I'll post it up here.

Sadly, I've got WiFi at home and at work, both with their own WEP keys, so Network Manager is a real boon to me, providing it works.

---

### Post by dbott67 on 2007-03-18
During your experimentation, give the network-manager-gnome package a try.  It's quite easy to use (I'm running it on my laptop).

The package is in the repos (but you probably should remove & purge network-manager:
```
sudo apt-get install network-manager-gnome
```

Details & screenshots here:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

