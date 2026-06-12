---
title: "Oops.  I removed Network-Manager"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by TimJBart on 2007-05-03
I removed network manager yesterday as I intended to install a different manager to sort my wireless network. 

However, once I removed it my network no longer worked so I can't download an alternative!!  How do I re-install Network Manager!?

Is there a way of synaptic package manager reading the Feisty CD, as I can't download any packages!

Is network-manager available as a.deb!?

Thanks

---

### Post by 5-HT on 2007-05-03
You can get the .debs from packages.ubuntu.com (should only need network-manager & network-manager-gnome if applicable). Network-manager is on the alternate install CD as well if you have it (put it in the drive, fire up synaptic, add the CD in the preferences/repositories and search for it). If you did an network upgrade to feisty you may find the .debs already in /var/cache/apt/archives if you haven't already cleaned them out.

---

### Post by chili555 on 2007-05-03
Have you gone to System -> Administration -> Networking to uncheck Roaming Mode? I think your network interfaces will reappear.

Put the CD in the tray and then you can enable the CD in apt-get and Synaptic with:```
sudo apt-cdrom add
sudo apt-get update
```

Some of us here are not fans of NetworkManager, so I would be in no rush to reinstall it.

---

### Post by TimJBart on 2007-05-03
> **chili555 said:**
> Have you gone to System -> Administration -> Networking to uncheck Roaming Mode? I think your network interfaces will reappear.

Put the CD in the tray and then you can enable the CD in apt-get and Synaptic with:```
sudo apt-cdrom add
sudo apt-get update
```

Some of us here are not fans of NetworkManager, so I would be in no rush to reinstall it.

OK thanks.

I use both wireless and wired, so what do you recommend now that I have removed network manager!?  What are the alternatives?

---

### Post by dca on 2007-05-03
Wifi-Radar is pretty good and its avail in one of the repos...  It's what I use because network-manager is quirky.  Alright, who am I kidding, I can't get it to work on any distro...

---

### Post by dca on 2007-05-03
...one more thing, 'right-click' on top panel and add the network monitor icon to the panel.  That way you can click on it and view/change NIC settings.  Then, install WiFi-Radar, move it (drag it) from the 'applications -> internet' menu to the panel where you added the network icon...

---

### Post by TimJBart on 2007-05-03
ok thanks foe the help guys.  I've just realised I was being stupid.

When I uninstalled network manager it disabled my network connection.  So I just went in and enabled it again :)

Sorry for being an idiot. 

Thanks for the help though, I'll try wifi-radar.  Cheers

---

