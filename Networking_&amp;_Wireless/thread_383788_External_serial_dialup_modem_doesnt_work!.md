---
title: "External serial dialup modem doesnt work!"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by clance_911 on 2007-03-13
Im using a serial modem which is built-in of a CDMA telephone, to use internet on MS Windows.
In Windows it works fine with "Standard 19200bps Modem" drivers and connected over COM2.

But in ubuntu i cant connect to internet using it, i tried terminal based "pppconfig" procedure and GUI based Networking Admin.... too.

Tried both ttyS0 and ttyS1, jus in case if i've mistaken.

When i "pon myconnection" the terminal prompt goes down by one (as it is accepted) but nothing else happens. (If it dials i can see it on the phone display.)
 
Im using Ubuntu 6.06 LTS (just installed it!) and/but i cant find that Gnome-PPP GUI utility which everybody talk about. ("sudo apt-get install gnome-ppp" says something like -theres no such app)

Can anybody help me out. Please, i need internet on ubuntu and get rid of Windows.

---

### Post by Daneel42 on 2007-03-14
[http://packages.debian.org/unstable/net/gnome-ppp](http://packages.debian.org/unstable/net/gnome-ppp)

Use windows to download from this website. Go to the bottom where it says download gnome ppp. If u have an amd64 processor download the amd64 version. otherwise download the i386 version. Save it to cd or floppy. when u get into ubuntu find the folder where u stored gnome ppp. right click on it and select open with. Select the terminal. Then type

sudo dpkg -i gnome-ppp_0.3.23-1_i386.deb

This will install gnome ppp under internet in applications. As for configuring ur internet after that I cant help u just yet. I'm having troubles with my modem and haven't been able to get to that step yet. What is ur ISP?

---

