---
title: "cannot update 7.10"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by windless on 2008-12-12
am unable to use update manager(Ubuntu 7.10)

following a 'tip' was going to find the 'www.getautomatix.com..' line and delete it, but found in etc/apt/sources.list that ALL the 22 debs entries have been commented out (#) by the installer.

Wuld it be safe for me to uncomment (restore) all these debs entries? 

Without updates Ubuntu actually works OK for my needs but I'd like to get updates working again.

(Please keep it fairly simple, folks....thanks!)

---

### Post by Peter09 on 2008-12-12
Check in

System->Admin->Synaptic Package Manager

Not sure for your version, but somewhere there will be a field which defines what type of upgrade that you want. May be yours is set to none.

---

### Post by theozzlives on 2008-12-12
ALT+F2 type in update-manager -d

---

### Post by windless on 2008-12-12
Sorry, **theozzlives**...this works OK but update manager duly appears and tells me 'Your system is up-to-date' and that 'distribution release '8.04 LTS' is available.

Since I've had no updating for MONTHS (and I** don't** intend putting 8.04 on my HD), I must conclude that support for my version has now ceased.

I've got the live CD of 8.10 so I'll just have to bite the bullet and install this now!....but tempted to carry on with the petrified 7.10 as it still does (almost) all I require at the moment.

---

### Post by PriceChild on 2008-12-12
system > administration > software sources

Make sure that you have at least main & universe on the first tab, and at least -security & -updates on the third(?). Then try it again.

---

