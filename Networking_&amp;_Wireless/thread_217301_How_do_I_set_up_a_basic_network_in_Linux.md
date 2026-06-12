---
title: "How do I set up a basic network in Linux?"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by dragon1964m on 2006-07-16
I have DSL. A 4-port router / gateway. 2 printers. 2 Windows computers and 2 Windows/Ubuntu computers (dual boot OS). When I had all Windows I just used a basic workgroup config. Now that I have 2 Linux machines things are different. 
How do I set up my network so all my machines can "See" each other and share resources, files, etc.?
(When I had just one Linux machine it saw Windows but Windows could not see it).
HELP!! :confused:

---

### Post by zedster on 2006-07-16
I think you are looking for something called samba. 

There is a way to make your linux machine part of the workgroup, as I found here:
[http://ubuntuguide.org/wiki/Dapper#How_to_change_computer_Domain.2FWorkgroup]("http://ubuntuguide.org/wiki/Dapper#How_to_change_computer_Domain.2FWorkgroup")

There is also a guide for samba linked from there that can help.

---

### Post by MrHorus on 2006-07-17
Yup, you will have to set up the workgroup properly in Samba or else the Linux and the Windows machines won't be able to see each other properly in a network browser although you will still be able to mount shares from the command line if you know how using (I think) smbclient.

---

### Post by dragon1964m on 2006-07-17
Ok, I got Samba up and running. I still have a problem though, I can't get remote printing to work. I enabled the "Cups" settings and did the restart. No luck. Any ideas?

---

