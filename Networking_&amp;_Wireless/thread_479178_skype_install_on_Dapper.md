---
title: "skype install on Dapper"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by jrev on 2007-06-20
Hi all,

I am trying to install skype via synaptic on my laptop but I get the following message :

[[img]http://www.enregistrersous.com/images/vignettes_images/103001150220070619181358.png[/img]](http://www.enregistrersous.com/images/3/103001150220070619181358.html)

What can be the problem ?

I registered the following line in my sources.list :

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

then I typed : sudo apt-get update 
then I selected the package in Synaptic and asked to install it
the message comes immediatelly after my confirmation of this install

Got a clue to help me out ?

Thanks anyway :D

---

### Post by tgoose on 2007-06-20
The new version of Skype depends on packages that I guess aren't available for Dapper (specifically, QT4 and a couple of others.) You can still use the old 1.3 beta of Skype, which should run fine, but I don't think it would be very easy to get QT 4 to run on Dapper, unless you're happy compiling things. Is there any reason you're not running Edgy or Feisty yet?

---

### Post by jrev on 2007-06-20
Yes,
I couldn't make Feisty to run as a NFS client with my ICS PC server

To be more precise it worked but the boot operation was altered in such a way that the windows needed more or less a minute to open.
So I could'nt run feisty on a laptop that was OK with Dapper.;)

---

### Post by jrev on 2007-06-20
The problem is : i cannot find  the Skype version 1.3.0.53 on Skype site luckily I found this old package at home ...;)

---

### Post by magnus07 on 2007-07-30
jrev,
could you share your 130 package :-)
magnus

---

