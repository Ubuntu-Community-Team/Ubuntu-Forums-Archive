---
title: "why can't i connect to my westell 2200 dsl modem?"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by northwestuntu on 2008-04-23
i just moved to verizon dsl and need to set my modem to bridge so i can use my vonage router.  for some reason though i can't reach my setup modem area. it's suppose to be 192.168.1.1 but that's not working and i have tried several others and nothing works?

the internet works fine through this modem as i am using it to write this, but why can't i access the modem?  could i just have the wrong address?

i am going crazy trying to figure this out, any help would be awesome!

thanks

---

### Post by Monicker on 2008-04-23
> **northwestuntu said:**
> i just moved to verizon dsl and need to set my modem to bridge so i can use my vonage router.  for some reason though i can't reach my setup modem area. it's suppose to be 192.168.1.1 but that's not working and i have tried several others and nothing works?

the internet works fine through this modem as i am using it to write this, but why can't i access the modem?  could i just have the wrong address?

i am going crazy trying to figure this out, any help would be awesome!

thanks

Is the Westell the next hop from your computer to the Internet?  If so, try netstat -rn, and see which ip is designated with UG, which will be your default gateway.  You could also try a traceroute to an external address.

---

### Post by northwestuntu on 2008-04-23
here's my setup.  phone cord to westell 2200 modem and right from there to computer.  that's all.

i tried your command.  is one of those numbers suppose to be my modem address?

---

### Post by Monicker on 2008-04-23
> **northwestuntu said:**
> here's my setup.  phone cord to westell 2200 modem and right from there to computer.  that's all.

i tried your command.  is one of those numbers suppose to be my modem address?


Did you see one designated as UG, as I mentioned previously?  It would be under the Flags column.

You could post the out of the command here, or to a pastebin site.

---

### Post by northwestuntu on 2008-04-23
here's the ug line

0.0.0.0         209.191.55.2     0.0.0.0         UG        0 0          0 eth0

---

### Post by Monicker on 2008-04-23
> **northwestuntu said:**
> here's the ug line

0.0.0.0         209.191.55.2     0.0.0.0         UG        0 0          0 eth0

Hrmm.  That is a public ip for Monmouth Internet.  Was that the only entry with UG?  

Does your computer have a 192.168.1.x ip address assigned to it?  If so, there should be something in the same subnet on the modem.  You could try installing nmap and using it to see what else is on that local subnet.

nmap -sP -PR 192.168.1.0/24

---

### Post by kerry_s on 2008-04-23
> **northwestuntu said:**
> i just moved to verizon dsl and need to set my modem to bridge so i can use my vonage router.  for some reason though i can't reach my setup modem area. it's suppose to be 192.168.1.1 but that's not working and i have tried several others and nothing works?

the internet works fine through this modem as i am using it to write this, but why can't i access the modem?  could i just have the wrong address?

i am going crazy trying to figure this out, any help would be awesome!

thanks

that is the right address, it's what i use to access mine.

---

### Post by northwestuntu on 2008-04-23
those are the only numbers in the ug line.  there is nothing that starts with 192.168.1.1 or looks like that?  i've accessed this modem before i don't understand what's going on?

---

### Post by northwestuntu on 2008-04-23
> **kerry_s said:**
> that is the right address, it's what i use to access mine.

yep that's what i used to use. i've been in there before.  the last time i accessed it was years ago.  how it can't connect with nothing in between my computer and the modem just doesn't make sense?

---

### Post by Monicker on 2008-04-23
> **northwestuntu said:**
> those are the only numbers in the ug line.  there is nothing that starts with 192.168.1.1 or looks like that?  i've accessed this modem before i don't understand what's going on?

Try accessing it via the public ip address which you are seeing as the gateway: 209.191.55.2

If that does not work try the other step that I mentioned.

---

### Post by kerry_s on 2008-04-23
> **northwestuntu said:**
> yep that's what i used to use. i've been in there before.  the last time i accessed it was years ago.  how it can't connect with nothing in between my computer and the modem just doesn't make sense?

i would just reset it. i've seen it do that after it updates.

---

### Post by northwestuntu on 2008-04-23
gateway address did not work.

tried nmap

Socket trouble in massping: Operation not permitted (1)

that's what i got.


:(

---

### Post by northwestuntu on 2008-04-23
> **kerry_s said:**
> i would just reset it. i've seen it do that after it updates.

i turned the power off and held in the reset button for 30 seconds and still nothing.

i would say verizon is sending something weird in the system, but i have also tried to access the modem without the phone plugged in.

i just don't get it.

---

