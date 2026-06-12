---
title: "pft no help from netgear"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by mad chey on 2007-10-10
today i am very dissappointed, as i emailed netgear support with a request for help from them regarding configuring a Netgear WN311T wireless pci adapter, as the file on the cd it comes with is autorun.inf and ive found absolutely nothing on the net, i explained to them the type of file i needed and what i would be doing with it and that it didnt have to be compatible with linux etc, but 

this is the reply i got

Dear Chey,

My name is Neeta and I am following up on your support case. Thank you for writing back.

We really apologize to inform you that we don't have the particular file that you asked for.

Again, thanks for choosing NETGEAR and we appreciate your continued patience.

Regards,

Neeta
NETGEAR Support

so we have just been out and bought 2x25m cat 5 cables and a switch and thought naf it to wireless ever again!!!!

:(

---

### Post by rustybronco on 2007-10-10
If you are trying to use ndiswrapper I don't think you want autorun.inf
you want the "driver".inf deeper in the disk, look for it.

---

### Post by mad chey on 2007-10-10
using ndiswrapper it says that autorun.inf is not the correct one, cant remember the exact error of the top of me head tho

i did have a root around the disk and found no other .inf files, but i will have another look case i was just being blind

ive had success using this method on older netgear wireless products just not having much luck with this one

---

### Post by kevdog on 2007-10-10
Cant you just download the windows XP drivers from their website??? Who actually uses the installation CD anyways?

---

### Post by rustybronco on 2007-10-15
[http://kbserver.netgear.com/products/WN311T.asp](http://kbserver.netgear.com/products/WN311T.asp)

---

### Post by Electric_Cowboy on 2007-10-15
Have you tried using the "tulip" driver on your Linux install disk?

I have an old Netgear ethernet card and the "tulip" driver has worked
for me on Xubuntu 6.06, ubuntu server 7.04, Mandrake Linux 7.0
Red Hat Linux 6.0, and Turbo Linux 4.04.

It's an old card though which is to say, you might have a newer model
of Netgear that might not work with the "tulip" driver, it shouldn't
hurt anything to give it a try.

---

