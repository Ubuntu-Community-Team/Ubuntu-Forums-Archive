---
title: "Can't connect to wired network"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by hul on 2009-12-25
I'm currently booting from a LiveCD and Ubuntu is not detecting my wired network--I try pinging the router and get "Network is unreachable."  I know my router and connection is working--I'm using it to post this message on a Windows computer.

What steps should I take to figure out why my Ubuntu comp is not detected?  I don't want to install Ubuntu until I know that it'll pick up the Internet (I just did that with Freespire :( ).

---

### Post by tacantara on 2009-12-25
Well, for starters, information about your computer (specifically, your network card) would help in troubleshooting.  You might even try running a Google search to find out if there are any known issues with Ubuntu regarding your NIC and/or any other hardware in your setup.

---

### Post by Iowan on 2009-12-25
Check **ifconfig -a** to see if the interface has IP address (probably won't). **lshw -C network** may reveal more information (driver and alias).

---

### Post by hul on 2009-12-25
Well, after a couple hours research and fiddling with the network, I found out that particular LAN cable just didn't work.  Switched it out and now it's all good.

I feel dumb.  Thanks for your help all.

---

### Post by Iowan on 2009-12-26
Fixed is good... I don't suppose you discovered a crossover cable you didn't know you had.

---

