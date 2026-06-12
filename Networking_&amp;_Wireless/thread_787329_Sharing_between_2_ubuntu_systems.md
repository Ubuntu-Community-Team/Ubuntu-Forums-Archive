---
title: "Sharing between 2 ubuntu systems"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by boandmichele on 2008-05-08
can anyone help me connect my laptop to my desktop?  

hardy 8.04 rc installed on both machines, running through a netgear wgt624.  i can connect to the internet and my windows media server through samba by nautilus'ing to smb://192.168.0.136 (static ip of windows box)

the desktop has a static ip of 192.168.0.138.  i dont know how to see the files on the desktop from the laptop.  samba is installed on both machines, i just am not good at configuring it.  any suggestions? 

(ive been learning my way around ubuntu for about a year, but networking is difficult for me, and we've given up windows completely other than the headless media server, soon to see xubuntu or DSL)

---

### Post by superprash2003 on 2008-05-08
are the machines able to ping each other? cause if you type smb://192.168.0.138 something should normally pop up

---

### Post by nanjil on 2008-05-08
i have a similar problem. I have two linux machines a fiesty one and newer hardy one and a windows laptop. the fiesty can see the hardy but the hardy cannot see either the fiesty or the xp laptop, I get NT_STATUS_ACCESS_DENIED
message.

it must be something to do with smb.conf in the hardy. i have tried all kinds of things and i am unable to make this work

---

### Post by boandmichele on 2008-05-08
> **superprash2003 said:**
> are the machines able to ping each other? cause if you type smb://192.168.0.138 something should normally pop up

if i type that in nautilus, absolutely nothing happens.  it just sits there and stares at me.  so...maybe im on the right track?

i am selected folders i need to access on the desktop, and chosen to share them, but that hasn't affected anything. :(

---

### Post by superprash2003 on 2008-05-09
and are they able to ping each other?

---

### Post by boandmichele on 2008-05-09
> **superprash2003 said:**
> and are they able to ping each other?

im not sure...how do i tell?

nothing happens when i smb://192.168.0.138

---

### Post by .rdg on 2008-05-09
First off - use terminal for some command line work. Don't be scared - it's also used in Windows to debug some networking problems.

You'll find terminal in Apps/Accessories/Terminal (I guess that would be the name in English Ubuntu, I use different translation).

Ping is the easiest tool to debug network problems - a program (ping, that is) sends a small amount of data to some network address you specify and that network host should (if it's not using any firewalling) respond to that.

In terminal run:

ping IP-address

where the IP address is anything, even the address of the PC you are pinging from. Just try - it's easy.

Now for the more important part. Please post the contents of file: /etc/smb.conf (samba configuration file) from both your desktop and laptop, so we can tell you more.

Regards,
.rdg

---

### Post by superprash2003 on 2008-05-09
well as .rdg said.. in the terminal type ping (ip) where (ip) is the ip of the machine you want to connect to.. you can find out your ip address by typing ifconfig in the terminal..

---

