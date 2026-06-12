---
title: "Sluggish Performance After Migration from Wubi"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by kennyschiff on 2009-03-29
I posted in another forum, but no responses, so forgive me for reposting...

I moved my Wubi install to a dedicated partition using LVPM. I was expecting that performance would be better, but it seems sluggish, especially when trying to read off of the network, or Firefox. My machine is a Thinkpad X61, which has 4GB of RAM, and is a dual core, so I should have plenty of horsepower.

I am wondering whether this is a swap file issue, and I'm not sure how to ensure that I'm properly using the space I allocated for swap (4.6GiB)

I did make a swap partition prior to migration (I created the partition using a Windows partition editor from my Windows partition). I am able to verify that the partition is there in GParted, but it reports nothing as used. How can I make sure that the swap space is being used?

I've done some FF tweaks that I've seen online, and also just disabled ip6, but wondering what else I can do to improve the speed.

Any clues would be appreciated...

---

### Post by HermanAB on 2009-03-29
Usually, this is caused by a lame domain name server.

Have a look at your Windows name servers:
c:\> ipconfig /all

and compare the list with the ones in /etc/resolv.conf:
$ cat /etc/resolv.conf

If different, edit the file and make the addresses the same as in Windows.

---

### Post by kennyschiff on 2009-03-29
My machine is on a small home network, behind in a d-link router. Networking is DHCP, so when I run: 

cat /etc/resolv.conf

It says that the "nameserver" is the IP of my router, which sounds right.

I will boot back into windows and see if it's any better, but I have VirtualBox installed and running, with an XP Pro image on it. That is actually quite perky.

---

