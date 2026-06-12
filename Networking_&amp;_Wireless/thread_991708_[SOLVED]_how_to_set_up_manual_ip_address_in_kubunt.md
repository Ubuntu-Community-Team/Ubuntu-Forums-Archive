---
title: "[SOLVED] how to set up manual ip address in kubuntu"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by halovivek on 2008-11-24
hi
i am using internet connection which comes with static ip address. 
i have configured that one in ubuntu and it is working fine. i want have steps in kubuntu to give the ip address and to get connected to internet.
please help
thanks

---

### Post by automaton26 on 2008-11-24
I'm new to kubuntu, and I'm also using a static IP. I had to do the following things to get my connection working, after a lot of searching online...

1) Disable Network Manager:

```
sudo update-rc.d -f NetworkManager remove
sudo apt-get remove network-manage
```

2) Edit /etc/network/interfaces:

```
auto lo eth0
iface lo inet loopback

iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

dns-domain 192.168.2.1
```

3) Edit /etc/resolv.conf:

```
domain Home
nameserver 192.168.2.1
```

4) Restart networking:

```
sudo /etc/init.d/networking restart
```


Finally, I installed the "guarddog" package to configure the firewall. I enabled the following protocols for the *Internet Zone*:

  a) FileTransfer -> FTP,HTTp,HTTPS
  b) Network -> DNS


I hope that helps you.

---

### Post by feelshift on 2008-12-02
Thanks automaton26, it worked for me! :smile:

---

### Post by eager2know on 2008-12-08
Thx for the post. I have just one quick question: once you did all that, does your machine connects to network as soon as it reboots or do you still need to login first and then it will get connected? 
Thanks again for info...

---

### Post by jetpeach on 2009-12-19
thanks automaton26! i look forward to when this can be configured in the plasma widget, but it sounds like there are bugs right now that stop static from working...hopefully they fix soon...

for, when i first tried i got the error:
 * Reconfiguring network interfaces...                                                                                SIOCADDRT: No such process
Failed to bring up eth0.
when i restarted the networking.

after a bit of fooling around, i figured out that the static ip i was trying to set wasn't in the appropriate range (even though my router said it would assign it), i had tried 192.168.1.16 and had to use 192.168.0.16 instead. then it worked for me

Thanks again!

---

