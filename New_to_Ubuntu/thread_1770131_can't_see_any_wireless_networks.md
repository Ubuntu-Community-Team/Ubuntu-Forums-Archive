---
title: "can't see any wireless networks"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by hopefulkayaker on 2011-05-28
Hello, I just installed Ubuntu 10.10 on my new ASUS Eee PC netbook, but when I click on the wireless icon at the top-right on the desktop, no wireless networks appear. 

On the current laptop I'm on, I see my network, as well as several others that are nearby.

The netbook has a wireless button, but it's not a switch. That makes me thinks it's a software toggle, which would work with the default BS operating system (Gateway Cloud or something).

---

### Post by wildmanne39 on 2011-05-28
> **hopefulkayaker said:**
> Hello, I just installed Ubuntu 10.10 on my new ASUS Eee PC netbook, but when I click on the wireless icon at the top-right on the desktop, no wireless networks appear. 

On the current laptop I'm on, I see my network, as well as several others that are nearby.

The netbook has a wireless button, but it's not a switch. That makes me thinks it's a software toggle, which would work with the default BS operating system (Gateway Cloud or something).

Hi, you always have to install drivers for wireless cards, I do not know if there is one for your laptop but I would do a search for drivers for the type of wireless card you have. You can also post back the information that these commands give and see if someone who knows about your exact wireless card shows up to look at them.
```
sudo lshw -c network 
```
```
nm-tool
```
```
lspci
```
```
lsmod
```
```
ifconfig
```do these one at a time. Put those commands into the terminal and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by grahammechanical on 2011-05-29
Hi

When you right click the wireless icon do you see a tick mark against the two lines Enable Networking and Enable wireless? Is there a red exclamation mark against that icon?

If that wireless button that you speak of is not a switch for switching the wireless adapter on and off, then what is it for? Switching off the wireless adapter on a netbook will prolong battery life. So, that wireless button may just be the switch that is preventing your wireless adapter from working under Ubuntu.

Regards.

---

