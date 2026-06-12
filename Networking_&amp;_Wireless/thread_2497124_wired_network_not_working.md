---
title: "wired network not working"
date: 2024-04-24
forum: Networking &amp; Wireless
---

### Post by gnu-buntu on 2024-04-24
Hello, I don't know much about networking anymore, so advice is welcome in solving this problem:

I recently installed Xubuntu 20.04 LTS on my dual-boot system with Windows 10.
It shows no network connection whatsoever, so I can't use apt to install anything, at least not via a network.
The corresponding live CD works works fine with the wired network, and so does Windows.

I ran the suggested script to collect "wireless" info on both the live CD and the installed, no-network system.

[LIST]
[*]The live CD results are here: (deleted) 
[*]The installed, no-network system results are here: (deleted) 
[*]The diff (live_CD vs. installed) result between the two files is here: (deleted) 
[/LIST]

I hope it's pretty obvious what's wrong or where to look next.
Please advise!

Thanks,
-Peter

---

### Post by gnu-buntu on 2024-04-24
While still dozing in bed this morning, it occurred to me that it might be possible to set the live CD *apt* repository to the one that the installed Linux uses. Then boot to the installed Linux and run *apt install* there. This could be a way to install necessary or desired packages -- until I can bring up the network for the installed system.

---

### Post by #&amp;thj^% on 2024-04-24
Part of the problem is Xubuntu 20.04 has hit EOL>>
Codename
    Focal Fossa
Release Date
    April 23, 2020
End of Life
    April 29, 2023
    
So no driver to install for your network.
Won't 22.04 work for you?

---

### Post by gnu-buntu on 2024-04-24
By golly, you're absolutely right. Thank you!
So I'll upgrade to 22.04 LTS and report back -- with "solved", I hope.

---

### Post by praseodym on 2024-04-24
sudo apt install r8168-dkms dkms build-essential

should do the trick

---

### Post by #&amp;thj^% on 2024-04-24
> **gnu-buntu said:**
> By golly, you're absolutely right. Thank you!
So I'll upgrade to 22.04 LTS and report back -- with "solved", I hope.

You should be good to Go with 22.04.
```
Network:
  Device-1: Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet
    driver: r8169

```

On your first wireless report, shows:
```
Kernel driver in use: r8169
```

---

### Post by gnu-buntu on 2024-04-24
Thank you all!

Yes, the upgrade to 22.04 fixed it.
My bad, but there were reasons mostly having to do with overlooking critical details. :-)

---

