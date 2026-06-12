---
title: "Naming my comp?"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by Culito on 2006-09-28
On my router's DHCP client list, my linux comp comes up as "unknown".  In Windows you can change your computer name.  How do I how do I do that in the world of the Tux?

-Thanks!

---

### Post by jmmcd on 2006-09-29
Your computer's name is stored in /etc/hostname. Use the "hostname" program to see it or to set it.

```
$ man hostname
```

---

### Post by keithweddell on 2006-09-29
You probably need to edit /etc/dhcp3/dhclient.conf.  Look for the line that starts #send host-name.  Remove the # and your router should pickup the computer name.


Keith

---

### Post by dannyboy79 on 2006-09-29
you can do this with a gui if you prefer. simply go to the system pull down, then administration, then networking. i'll bring up a dialog. click on the interface you want to change, normally if this is a wired ethernet connection it'll be eth0, then click on properties, in there you'll see a place for your computer name. i am not at my ubuntu machine so I can't tell you exactly which field it is but I know it's there. that's it. no need to go and edit config files and what. that's the whole point in having a window manager, so us linux newbie's don't have to ALWAYS use the terminal. Although I must say that I have learned pretty fast hot to use the terminal. having to edit my fstab file, commented out extra interfaces with my /etc/network/interfaces file, obviously for compiling new stuff and installing stuff using python scripts and pretty much a lot of stuff that you can't do with a gui.

---

### Post by Culito on 2006-09-29
Thanks guys.  Actually, there isn't a field under system>admin>networking.  I checked that.  The only things there are fields for DHCP/Static, IP address, Subnet Mask, and Gateway address.
It looks like Keith's answer will work, as my /etc/hostname was already set.
I'm off to reboot.

---

### Post by Culito on 2006-09-29
And yep, that did it.  Thanks!!

---

### Post by dannyboy79 on 2006-09-30
I am sorry but I have to disagree with you, when you go into system, admin, networking, there is a tab for your hastname. here is a picture of it.

---

