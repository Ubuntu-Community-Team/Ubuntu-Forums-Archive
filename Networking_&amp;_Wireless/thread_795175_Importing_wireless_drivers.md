---
title: "Importing wireless drivers"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by geezerone on 2008-05-15
Hi

Is there any way of finding and installing fedora 9 drivers for a BT Voyager USB adapter which works with Fedora but not even seen in Ubuntu?

TIA

---

### Post by chili555 on 2008-05-15
What driver does FC9 use? Maybe we have it, but it's just not associating.

---

### Post by geezerone on 2008-05-15
Thanks for the reply. Not sure what or where the driver would be and was just using the live cd version of Fedora 9 for the minute anyhow. Any tips to see where this would be?

-------------------------------------------------------------

As a sidenote, maybe I will install FC9 as triple-boot with XP, Gutsy but will this work with the Grub installed as FC uses Lilo?

---

### Post by chili555 on 2008-05-15
Open a terminal on the FC9 and do:```
su
lshw -C network
```You will see a listing related to your BT Voyager which will have an item like *driver=whaddever*. Please tell us what it is.

---

### Post by geezerone on 2008-05-15
Thanks Chilli

I found this BT Voyager 1055 thread which solved my issue by just following the following link (courtesy of a post from another thread).


[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

Followed the download and installation instructions to load wireless database and then build it into my distribution and hey presto - could see my wireless network.

Will put FC9 on back burner for mo! :)

Thanks for the help.

---

