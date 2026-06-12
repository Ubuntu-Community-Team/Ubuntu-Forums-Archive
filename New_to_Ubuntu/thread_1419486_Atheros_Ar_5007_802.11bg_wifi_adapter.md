---
title: "Atheros Ar 5007 802.11b/g wifi adapter"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Jonathan 56 on 2010-03-01
Ive got Atheros Ar 5007 802.11b/g wifi adapter on my latop and ubuntu wont turn it on. Please help me to get this working.

---

### Post by kemsiro on 2010-03-01
i remember getting this chipset working using ndiswrapper

---

### Post by 3rdalbum on 2010-03-01
Get an internet connection (wired, or mobile broadband) and refresh your package list (click the Reload button in Synaptic Package Manager). Go to System > Administration > Hardware Drivers and you may have a driver offered for you there.

Can you please clarify, the problem is that you are not picking up any wireless networks?

---

### Post by k3lt01 on 2010-03-02
You really need to provide us with more information. What version of Ubuntu are you using? My fathers laptop has this chipset and it has worked OOTB since 9.04 (Jaunty). 8.10 (Intrepid) needed madwifi modifications while 8.04 (Hardy) needed ndiswrapper and Windows drivers.

A little bit of advice, in your signature section (see mine at the bottom of my post) you can add information about your system(s). This helps others to help you without asking questions like "what is your system?"

---

### Post by Jonathan 56 on 2010-03-02
Thanks for the help. Im comply new to this website so still learning. Open to advice. 
My Problem is that I can not turn on my wireless adapter to pick up a net work. Im new to ubuntu ( yesterday) so still working my way around it. Im running a compac presario cq60 with a amd athlon dual core ql- 62 2.00GHZ Ram 4.00 ( 2.75 usable because running windows 7 32bit.) Wifi atheros AR5007 802.11b/g wifi adapter.  Im using Ubuntu 9.10 64bit. I have a Nvidia graphics card. So far im running ubuntu of live cd. Im considering puting it on to a dual boot. I dont know if I have the light on the computer which tells me wifi is on or is there a way which is differnt to ubuntu to turn it on. or if its not picking it up
It tell me there is a problem with wifi apater. With get more info about it when i next boot it up.. Im on a school network. Ill try to conncet threw a cable. 
How do i put on a sigerture. Thanks for ur help. Ill try to get any other info u ask for thanks Please help me to work ubuntu

---

### Post by k3lt01 on 2010-03-02
Ok now that gives me something to work with.

You are, unfortunately, going to have to change a settings file and because you are running off a LiveCD it wont remember the change if you reboot. You will have to follow the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") to get your connection working. Just remember it will "forget"the change when you turn the PC off.

With your signature, you change that through the User CP link at the top of the page.

---

### Post by lkraemer on 2010-03-02
Jonathan,
Please don't double post........

The information everyone is waiting for is located at your
first posting:
[http://ubuntuforums.org/showthread.php?t=1417947](http://ubuntuforums.org/showthread.php?t=1417947)
Posting #6.

Why are you making this so hard?  Just run the Terminal
Commands in Posting #6, and post the output here.

You should be able to Open Synaptics Package Manager, Reload,
and install the Hardware Drivers for Ubuntu 9.10.  DONE!

lk

---

### Post by 3rdalbum on 2010-03-02
The "Wifi On" or "Wifi Access" light won't necessarily turn on in Ubuntu. The people developing drivers tend to make the device work properly first, before reverse-engineering the way to make the little light flicker.

---

### Post by k3lt01 on 2010-03-02
> **lkraemer said:**
> Jonathan,
Please don't double post........

The information everyone is waiting for is located at your
first posting:
[http://ubuntuforums.org/showthread.php?t=1417947](http://ubuntuforums.org/showthread.php?t=1417947)
Posting #6.

Why are you making this so hard?  Just run the Terminal
Commands in Posting #6, and post the output here.

You should be able to Open Synaptics Package Manager, Reload,
and install the Hardware Drivers for Ubuntu 9.10.  DONE!

lk@lkraemer, Mate don't give him a hard time in 2 threads. Also the ndsiwrapper command in post 6 isn't required as the correct driver is part of 9.10 anyway.

@Jonathon, just follow my suggestion it should work for you but remember while you are using the LiveCD it will forget your changes when you reboot.

---

### Post by Trinity33 on 2010-03-02
i have atheros to and there is support for that chipset. remove network manager and install wicd it was working straight away. don't know why but network mgr doesn't see my card.

---

### Post by k3lt01 on 2010-03-02
> **Trinity33 said:**
> i have atheros to and there is support for that chipset. remove network manager and install wicd it was working straight away. don't know why but network mgr doesn't see my card.If you choose to install Wicd it will cause further issues. Just do a search for Wicd and Network Manager and see how many people end up wishing the never installed Wicd and you will see what I mean.

---

