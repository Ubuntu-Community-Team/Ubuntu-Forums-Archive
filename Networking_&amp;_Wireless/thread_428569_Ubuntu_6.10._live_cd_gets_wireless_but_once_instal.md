---
title: "Ubuntu 6.10. live cd gets wireless but once installed it doesn't"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by timmybobmorgan on 2007-04-30
Hey guys

I have just installed Ubuntu 6.10. from a live cd my mate gave me came up fine and wireless worked so i know it ain't the hard ware that is giving me the problem i tried to mimic the live cd's set up of networking and i somtimes get signal but under connection properties status it says disconnected and later it will say sending/reciving with 0% signal in the same place either way i can't get on to the world wide web!:confused: 

What is wrong with it i have tried to set up with changes in the networking area but it still won't work :mad: 

Please can sombody help me

Timmy

---

### Post by timmybobmorgan on 2007-04-30
Why won't anyone help me:( :cry: 

oh well i will just have to try again tomorrow

---

### Post by dolphin_oracle on 2007-04-30
I've heard of this.  On the 6.10 live CD there are restricted modules in the Kernel by default.  For some reason, these modules are not installed when you do an install.  At least, I think thats right, anybody please correct me if possible.  At any rate, the modules in question affect certain wireless cards.

I don't know much about configuring wireless except for cards based on Ralink RT61 chipsets, which I am running.  But the folks here know lots, so post what type of card you have and I'm sure someone will chime in!

---

### Post by timmybobmorgan on 2007-04-30
I have an Intel PRO/Wireless 2200 BG network 32bit device 2701

or thats what it said when i typed lspci -v |less command into the terminal

---

### Post by timmybobmorgan on 2007-04-30
Thanks for at least saying somthing :)

---

### Post by dolphin_oracle on 2007-04-30
this thread may help:

[http://ubuntuforums.org/showthread.php?t=309041](http://ubuntuforums.org/showthread.php?t=309041)

about half way down llamashoes directs to another link and that how he got his card to work.

Good luck!

---

### Post by timmybobmorgan on 2007-04-30
Has all life on this forum just gone off for tea?  this is meant to be an IRC not an internet reapeat post!

( sorry for the really bad joke don't ban me :) )

---

### Post by timmybobmorgan on 2007-04-30
Thanks i will try that happy trawling the interwebs:popcorn:

---

