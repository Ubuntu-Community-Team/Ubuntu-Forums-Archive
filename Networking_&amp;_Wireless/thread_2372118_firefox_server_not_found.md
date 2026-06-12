---
title: "firefox server not found"
date: 2017-09-21
forum: Networking &amp; Wireless
---

### Post by mbattis2 on 2017-09-21
I am building a linux machine fot the first time and have been running into several problens.  After finally installing and booting and establishing a. Onnection i get a "server not found" message from firefox.  I have looked at a few different threads and cant seem to make it work from what is posted (almost all fom versions previous to 17.04)  i have zero experience in linux so hopefully someone will have the patience hold my hand for a bit.

---

### Post by ajgreeny on 2017-09-21
Have you got a connection for upgrading or installing software, with just FF not making a connection, or is nothing connected?  We need a lot more info from you to be able to help, so give as much detail as you can.

Are you using wifi or ethernet cable connection, and is the problem the same on both?
What hardware do you have, particularly the network hardware?  Show us the output of terminal command ```
sudo lshw -c network
``` and then ```
ifconfig
``` and finally ```
iwconfig
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by johndough2 on 2017-09-24
Hi

To add to the excellent answer already given, this may just help...

You will need to find out the name(s) of the network interfaces, like wlan0 or enp0s3 or whatever.

```

ip addr show
ip route show
ip neigh
ip -s link

```

---

