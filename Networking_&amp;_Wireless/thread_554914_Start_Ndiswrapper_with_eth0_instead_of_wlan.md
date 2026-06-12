---
title: "Start Ndiswrapper with eth0 instead of wlan"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by polygone on 2007-09-19
Hey guys and gals,

For some reason, when I set up ndiswrapper this time around, it recognized my wireless card as etho instead of wlan0.  I used 

```
sudo ndiswrapper -m
```

to make it load when "wlan0" loads...the thing is my wireless card is on eth0.

Shouldn't this work either way? or do I need to specify the device name?...

Any takers?

I am just sick of modprobing all the time.......

---

### Post by kevdog on 2007-09-19
Post your /etc/iftab file.  

does it matter if its eth0 or wlan0 to you?? Do you prefer one to the other??

---

### Post by polygone on 2007-09-19
I am kind of in a jam....it's on my laptop and it's not online.....I am at work.  I can post it later or something....it's a little large to copy manually


It doesn't matter to me what it's called, as long as ndiswrapper starts when I boot up.

---

### Post by kevdog on 2007-09-19
Look at the iftab file.  If the mac address listed with eth0 is the mac address of your card, then just change eth0 to wlan0.  That is probably the easiest thing to do.

---

### Post by polygone on 2007-09-19
Hey man...sorry the web went down at work.........i changed the etho to wlan0 and rebooted.....it didn't seem to work



Edit:  I had a o instead of a 0......I am trying again now.....

---

### Post by polygone on 2007-09-19
Is there a way to go in and see what the alias is for that?

I can't remember the name of the file........

When I run

```
sudo ndiswrapper -m
```

it says there is one already assigned.


that or can I unassign it and then re-assign?

---

### Post by kevdog on 2007-09-19
That sets up a file /etc/modprobe.d/ndiswrapper

within the file it states
alias wlan0 ndiswrapper

After you change the iftab file to wlan0, I dont think you will have to run this command anymore to get your network up and running.

---

### Post by polygone on 2007-09-19
I am leaving work..I'll give it a whirl....thanks for your help!!!!   :)

---

### Post by polygone on 2007-09-19
ok....I am home now....


odd.

iftab is set correctly and the alias is set to wlan0....

still doesn't load on boot.....


# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:11:50:06:7e:8b arp 1
eth1 mac 00:20:e0:69:a0:ff arp 1

---

### Post by kevdog on 2007-09-19
Make sure with the /etc/modules file you have the line
ndiswrapper

---

### Post by polygone on 2007-09-19
That was it man.....it wasn't in my modules....

thanks a lot....


If you were of the opposite gender, I'd kiss you......but you'll have to do with a high five!!

lol

:)

---

### Post by kevdog on 2007-09-19
What MAC address is assigned to eth1 in your iftab???

---

### Post by polygone on 2007-09-20
ummmm the eth1 was supposed to be wlan0....so I changed it.....but ndiswrapper wasn't in my modules....I added it and it worked.....do you want to know the actual mac address?  I mean it is working....

---

