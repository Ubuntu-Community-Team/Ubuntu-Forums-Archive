---
title: "Wireless: Kubuntu vs Ubuntu vs Xubuntu"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by manilaph on 2009-07-25
I happily use Kubuntu 9.04 on my desktop with a wired-internet connection.

I tried the livecd of Kubuntu 9.04 on my Compaq Presario laptop but could not connect to my own secured home network (WEP). But the livecd of Ubuntu 9.04 and Xubuntu 9.04 had no wireless issues.

Right now, I am using the Mandriva 2009.1 KDE on my laptop and wireless works perfectly with a very strong signal (stronger than Ubuntu's)but still I want to switch to Kubuntu 9.04.

I've read about the topic regarding Kubuntu 9.04 wireless issues... and many suggest installing WICD. If this is the solution... why can't WICD be included as default in Kubuntu?

Is the problem only with regards to connecting to secured networks? Or also to unsecured networks? Is this a KDE bug or just with Kubuntu?

The Kubuntu team should study the wireless system of Mandriva... because it simply works out-of-the-box... which the end-users really appreciate.

Any simple fix... besides having to use a wired-connection then manually install wicd for Kubuntu?

---

### Post by manilaph on 2009-07-26
If there is no simple-fix to this wide-spread problem (bug)... then WICD should just be installed as default. Is this too hard to do or are there issues about installing WICD as default?

---

### Post by Durden on 2009-07-26
If you're looking for a more solid KDE experience you may wanna try OpenSUSE. I've had nothing but problems with Kubuntu personally to the poin I wont even try KDE anymore on any Ubuntu distro. I have very little faith in the Kubuntu team right now for this reason and many others.

---

### Post by gunksta on 2009-07-31
I've not had any problems using wired or wireless connections with Kubuntu. Are you sure your wireless card is configured the same way under both systems?

---

### Post by izizzle on 2009-07-31
Just...Use...WICD.

---

### Post by swoll1980 on 2009-07-31
Kubuntu seems to give some. people problems with there wireless connections. Ubuntu would be the best bet.

---

### Post by gunksta on 2009-07-31
> **manilaph said:**
> If there is no simple-fix to this wide-spread problem (bug)... then WICD should just be installed as default. Is this too hard to do or are there issues about installing WICD as default?


WICD brings along some GTK dependencies which is generally not going to happen on a default Kubuntu installation.

Given the sporadic nature of the problem, it seems reasonable to look at configuration differences on the wireless card or to look upstream to see if they have identified specific cards/combos that don't work well with the KDE front-end to network-manager. Arguing that a user should just use Ubuntu doesn't seem logical since they both use network-manager to manage wired/wireless connections.

---

### Post by Ji Ruo on 2009-07-31
The problem is the new network plasmoid used in the latest version of KDE. Apparently it's quite buggy for wireless and mobile broadband connections. This isn't the only problem as the new package installer is also buggy. Hopefully the KDE team will fix these bugs before the next release of Kubuntu is due out, as 9.04 is unusable for me at the moment.

---

### Post by gunksta on 2009-07-31
Has anyone tried using the plasmoid n the 4.3 PPA? The version packaged by Kubuntu works fine for me, so I can't really test the newer version for improvement, but this could be an option for some people.

---

### Post by Liolikas on 2009-07-31
> **Ji Ruo said:**
> The problem is the new network plasmoid used in the latest version of KDE. Apparently it's quite buggy for wireless and mobile broadband connections. This isn't the only problem as the new package installer is also buggy. Hopefully the KDE team will fix these bugs before the next release of Kubuntu is due out, as 9.04 is unusable for me at the moment.
We still have old school way (card is like wlan0 etc.):
```

sudo iwlist scan 
(find points)
sudo iwconfig card essid "point"
(connect)
sudo dhclient card
(get settings)
ping -c 4 google.com
(check with 4 "balls" if everything is ok)

```

---

### Post by Ji Ruo on 2009-07-31
> **Liolikas said:**
> We still have old school way (card is like wlan0 etc.): ...


Could this be adjusted for mobile broadband? (my only way of getting online at home).

---

### Post by Liolikas on 2009-07-31
I use WLAN and LAN only. And I use DSL but DSL modem do all job and PC gets net trough LAN cable. So can not advice much about other types just my general Linux knowledge.

---

