---
title: "quick question about firewalls"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-28
im new to linux and currently running ubuntu 8.04 on my personal desktop computer.

do i need to turn on the firewall in ubuntu?

im an IP noob and cant really deal with iptables, etc.

if i should consider running a firewall, should i use something like firestarter?

thanks for any suggestions.

---

### Post by thraxy on 2009-02-28
Well, since Ubuntu doesn't let you operate on the root account by default, a firewall is generally not needed for home computers. Applications you install usually come from secure and trusted repositories, and no virus or other infectious malware/spyware can install itself on your computer (unless you specifically go and type in your password and confirm that you really really want it on the computer... lol).

In Linux you're quite safe as long as you know where the software comes from.

Hope this helps :)

---

### Post by 3rdalbum on 2009-02-28
If you are not running any server software, then you don't need a firewall. A regular install of Ubuntu does not contain any software that listens to remote ports by default.

If you have installed some server software, you can use Ubuntu's inbuilt Uncomplicated Firewall (UFW) utility, or download a GUI for UFW (sudo apt-get install gufw). Also be aware that many broadband routers already contain firewalls that are protecting your whole home network, and a personal firewall is only necessary if you don't trust your own network traffic or if you use other people's networks.

And if you don't trust your own network traffic, that's a pretty bad situation!

---

