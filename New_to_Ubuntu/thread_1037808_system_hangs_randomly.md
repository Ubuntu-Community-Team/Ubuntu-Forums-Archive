---
title: "system hangs randomly"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by paddi on 2009-01-12
hi ,

was wondering if someone could help me out , ive decided to ditch my xp laptop and install latest ubuntu version i downloaded, but seem to be getting random system hangs when doing stuff, can be ok for ages and then hangs or can hang after 5 or 10 mins , at first i thought it was my wireless card playing up and maybe dropping connection , so i disabled it (using hotswitch on laptop) and plugged in with ethernet cable .

i can move mouse round no problem but will not allow me to select any of the panes and i have to power it off by holding down the power button...

i really dont have a clue what commands etc.. to try so any help would be great..

its an IBM T60 with 2gig centrino duo chipset,i gb memory,3945 for the wifi...

could it be the network manager side of things ??

thanks again 

paddi

---

### Post by cmnorton on 2009-01-12
Look in your logs.

Go to an X-terminal (command line), and enter

sudo tail /var/log/messages

sudo tail /var/log/syslog

dmesg | less

(one at a time)

Use your password, when prompted by sudo.

See if there is anything interesting in the logs. There is no need to post the logs here.

What is going on when the system hangs? Are you browsing?

What is your display configuration? You can find that out in the menus under either Preferences or Admin. I have forgotten which.

---

### Post by LowSky on 2009-01-12
I have the same laptop so I know its not a normal hardware issue.

just wondering How did you install ubuntu? Wubi or LiveCD?

Did you install the ATI drivers? Are you using Compiz? What other Applications are you using on a normal basis?

---

### Post by vagus on 2009-01-22
Hi,

I am having a similar problem with my Ibex installation. I cannot really see a pattern to it. The system hangs in between switching windows. It does not crash as such. There is simply a delay of a few seconds (~5) and then executes all the clicks/buttons that you may have pressed in that time. It happens often, but cannot find a trigger for it. I looked in various logs, but nothing obvious.

I have tried switching compiz off, but that did not help either. I have an Nvidia graphics cards and have the drivers installed. The funny things is I do not see this problem on my laptop with ATI card.

Does anyone have any ideas how I might be able to pinpoint the cause of this (whether it's hardware or software)?

Thanks

---

