---
title: "ubuntu newbie needs help with installation"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by xs0u1x on 2010-11-28
I am running ubuntu 10.10 successfully off of the live cd, and liked it so much that I decided to install.


I got my partitions set up with the install manager, (dual booting my pc with vista home premium 32 bit) and during the install process, it seems to have hung on one particular process during the install with the message "getting the time from a network time server"

I am able to switch back and forth to select a different time zone, as well as select my keyboard layout and the "who are you" screen during install, where I can set up my user account and password. but at that last screen(who are you) the forward button will not activate so I can proceed with the installl. and the "skip" button next to the message "getting the time from a network time server"  will not light up either to where I can click it.


I'm not sure what more information would be of help, again i'm very new to linux. I thought maybe my router might be blocking a NTP protocol, so I went and opened up the udp port 123 on my router, and nothing has happened(i dunno if i can restart this process since i've opened the port somehow)

any help is greatly appreciated.

---

### Post by johnmay on 2010-11-28
Try disconnecting form the web while you install. If the problem is the getting time form network server, not connecting might allow you to get past that step.

---

### Post by xs0u1x on 2010-11-28
> **johnmay said:**
> Try disconnecting form the web while you install. If the problem is the getting time form network server, not connecting might allow you to get past that step.


Thank You.

 will try that now.

---

### Post by xs0u1x on 2010-11-28
> **xs0u1x said:**
> Thank You.

 will try that now.


tried this, and I got a different message instead of the getting time from network server. the new message was "ready when you are", but I still could not hit the forward button on the user account creation screen.

am I possibly missing something? or is this out of the ordinary?

---

### Post by johnmay on 2010-11-28
Other work around could be to download the 10.04 install, and then upgrade to 10.10 which is the latest release. As far as are you missing something, don't really have enough information. Sounds unusual though. It is possible that you did miss some type of configuration, if you can use the back button, verify that you have not missed any steps.

---

### Post by zeroseven0183 on 2010-11-28
Does your username include a capitalized letter? It shouldn't have.

I encountered the same issue before installing 10.10. But figured out after second try. (felt a bit ashamed)

---

### Post by xs0u1x on 2010-11-28
> **zeroseven0183 said:**
> Does your username include a capitalized letter? It shouldn't have.

I encountered the same issue before installing 10.10. But figured out after second try. (felt a bit ashamed)


My user name did have a capital letter. is that not allowed?

---

### Post by johnmay on 2010-11-28
That is true user name must be lower case, that might be what is stopping the install form continuing.

---

### Post by zeroseven0183 on 2010-11-28
> **xs0u1x said:**
> My user name did have a capital letter. is that not allowed?

Yes, it's not allowed. Make them all small letters and Forward button will activate.

---

