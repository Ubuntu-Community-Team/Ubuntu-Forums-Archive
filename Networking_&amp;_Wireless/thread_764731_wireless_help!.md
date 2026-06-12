---
title: "wireless help!"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by ja660k on 2008-04-24
hey guys, 
i have a sorta old laptop with a wireless card, not an inbuilt one. and the manufacturer doesnt have linux version of the drivers needed... the ubuntu knows that the card is there, it just doesnt know what to do with it...

any tips please?

---

### Post by Patsoe on 2008-04-24
Can you give more info? Brand and model, and whatever Ubuntu tells you about it?

---

### Post by ja660k on 2008-04-24
okay, i live in Australia, and i got the computer from a company called protac.

the manufacturer for the card is "Marvel"
finding it in the hardware info

ubuntu regognizes that its there...
device says "88w8335 [Libertas] 802.11b/g Wireless"
and status says "status"
but the capibilities and device type are both unknown

:confused:

---

### Post by marufaberlin on 2008-04-24
Please pst results of:

```

cat /etc/network/interfaces
sudo hwlist

```

and right after a boot:

```

sudo dmesg

```

---

### Post by marufaberlin on 2008-04-24
do you have a windoze driver for the device? I would suggest using ndiswrapper, there are a lot of tutorials on the www.

---

### Post by ja660k on 2008-04-24
yeah i do, 
yeah thanks alot... ill hit back if i cant seem to figure it out, but thankyou big step in the right direction

---

### Post by twright on 2008-04-24
> **ja660k said:**
> yeah i do, 
yeah thanks alot... ill hit back if i cant seem to figure it out, but thankyou big step in the right direction
make sure to install it from the repos (sudo apt-get install ndiswrapper), not compile :)

---

### Post by ja660k on 2008-04-24
the problem im getting is

john@ubuntu:/$ ndiswrapper -i ~/Desktop/Mrv8000c.inf
couldn't create /etc/ndiswrapper/mrv8000c: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
john@ubuntu:/$ 


uhhh? i dont know how do i change this so im root user?

---

### Post by twright on 2008-04-24
```
**sudo** ndiswrapper -i ~/Desktop/Mrv8000c.inf
```

---

### Post by ja660k on 2008-04-24
sorry, im still noob lol
ill pick it up eventually...

john@ubuntu:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present


but when i look at the hardware info again... it still has the same as my previous post

---

### Post by marufaberlin on 2008-04-24
you need to put sudo in front of the command. Make sure to load the ndiswrapper module using sudo modprobe ndiswrapper.

---

### Post by twright on 2008-04-24
and add the word ndiswrapper to the end of the /etc/modules file (gksu gedit /etc/modules)

---

### Post by ja660k on 2008-04-24
success!
thankyou to everyone who helped especally marufaberlin & twright

 i still have alot to learn... teach me
:guitar:

---

### Post by gambituk on 2008-04-24
Hi all, first post on here, is it ok if i hijack the end of this post, as it is sofar identical to my situation, i have followed it to the end, but i cant see whether mine is working or not... i am a total newb. i really would appreciate any help with this, just tell me what info you need. 

Gambit|uk

Actually.. scratch that, inasmuch as its now identical to ja660k's post ie it works!! :D

---

