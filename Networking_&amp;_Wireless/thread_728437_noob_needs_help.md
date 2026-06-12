---
title: "noob needs help"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by wolfwood707 on 2008-03-18
I just installed Ubuntu today on my brand-new Acer Extensa 5420. The O/S came highly recommended from a friend. 

I really want it to work, but I don't know much about computers. I'm having trouble getting it to connect wirelessly to the network. It did it last night when it was running Vista with no issues.

So I either need to know a (fairly) easy way to connect wirelessly or how to uninstall the O/S because I have to be able to hook-up at home, school and elsewhere. 

Thanks for the help.

---

### Post by andradx on 2008-03-18
What is your wireless card?
type "lspci | grep Wireless"  in terminal and paste here the output

---

### Post by uberlube on 2008-03-18
What type of wireless card do you have?

---

### Post by uberlube on 2008-03-18
Hah, he beat me to it lol

---

### Post by wolfwood707 on 2008-03-18
"Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)"

Is that the right info?

---

### Post by uberlube on 2008-03-18
Yup it is. Use the howto in my signature and you'll be good to go! :)

---

### Post by wolfwood707 on 2008-03-18
Do you need to type it EXACTLY like that? If so, how do you get to the next line? (without pressing 'enter', obviously)

---

### Post by uberlube on 2008-03-18
Type them in 1 at a time and press enter

---

### Post by wolfwood707 on 2008-03-18
"bash: /etc/modprobe.d/blacklist: Permission denied"

Bad thing...? Maybe...?

---

### Post by uberlube on 2008-03-18
type in:

```
sudo su
```

and type in your password. This will enable a root shell.

---

### Post by wolfwood707 on 2008-03-18
When I got here:
echo "alias eth1 ndiswrapper" >> /etc/modprobe.conf

It said this:
bash: alias eth1 ndiswrapper: command not found

Should I try wlan0 instead? And do I have to start over from the beginning, heh?

---

### Post by uberlube on 2008-03-18
Ya try starting over and use exactly what it says. Then if that doesnt work, try the whole thing over again with eth1

---

### Post by wolfwood707 on 2008-03-18
I *think* it worked... I'll update in a few minutes...

---

### Post by wolfwood707 on 2008-03-18
Ah crap, nope it sure didn't.

System > Administration > Network

No option for wireless now. 

HELP

---

