---
title: "problem connecting via Realtek RTL 8139"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by hg75 on 2011-06-02
hi 
i am using ubuntu 10.04 along with windows xp, dual booting. recently i could not connected to my ADSL via Realtek RTL 8139 which was working fine in Windows XP. I have tried powering off/unplugging my machine but  to not avail. please help.

---

### Post by gandaran on 2011-06-02
> **hg75 said:**
> hi 
i am using ubuntu 10.04 along with windows xp, dual booting. recently i could not connected to my ADSL via Realtek RTL 8139 which was working fine in Windows XP. I have tried powering off/unplugging my machine but  to not avail. please help.
the Realtek RTL 8139 chip works fine with linux so its not the problem.
how do you connect in windows to adsl? via a always-on ethernet (or usb?) router or does the computer use a pppoe setup connection.

---

### Post by Matt__ on 2011-06-02
Is it possible windows is putting its default state to OFF on shutdown and its not waking when Ubuntu boots?

you could try this;

- Boot up Windows
- Right click on My Computer
- Click on Properties -> Hardware -> Device Manager
- Expand your network card section and double click on your Realtek    network card
- Set "Wake-on-lan after shutdown" to enabled

But more likely is that as this chipset has several drivers under linux you may have two trying to run so try:
```
lsmod | grep 8139
```
and see what is loaded for your card. If you get more than one return do;
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and blacklist one of the driver modules by adding a line at the end of the file like this-
   blacklist 8139cp (or whichever one you are trying to block...may be 8139too)
Save and close gedit and reboot.

Finally there is [this post to look at.](http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10)


#an ex-8139 owner :P

---

### Post by hg75 on 2011-06-05
i am using ethernet and pppoe on my adsl
thanks for response

---

### Post by dineshs on 2011-06-07
What do you get for ```
sudo lshw -C network
```and```
cat /etc/network/interfaces
```?

---

### Post by jtarin on 2011-06-07
Also post the results of "lspci" and "lsmod".

---

