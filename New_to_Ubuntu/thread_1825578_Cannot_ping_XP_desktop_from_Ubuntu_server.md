---
title: "Cannot ping XP desktop from Ubuntu server"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by AnnainOK on 2011-08-15
I am very new to Ubuntu server, and to servers in general. Using Ubuntu Server 10.04, I installed LAMP, OpenSSH, and Samba on a Dell Optiplex GX270, allowing for the default configurations. My immediate goal is to utilize the second 250GB hard drive as a file server for storing backup images. I am using Putty on my XP Pro desktop; I also have an Ubuntu desktop and a dual-boot, XP/Ubuntu laptop connected to the router. (They are not "networked")

I've consulted Ubuntu documentation and on-line tutorials, with varying degrees of success. If the truth be told, I'm on my third install in as many days. This time I've created backups of any files I've reconfigured and written down each step. 

When I'd gotten to the point where I'd edited /etc/hosts and entered the IP address I've assigned to my server, and after restarting, I was unable to do apt-get update, nor could I ping my XP desktop. I could ping internet addresses and the other computers, and they could all ping the Ubuntu server. 

I decided to restore my original (default) /etc/hosts file. This resolved the apt-get update problem. I can still ping everything BUT my XP desktop from the Ubuntu server. I have a couple questions at this point:

1. Is this actually a problem?
2. Do I need to modify /etc/hosts and replace the default:

127.0.0.1 localhost
127.0.1.1 server1.myisp.com server 1

with:

127.0.0.1 localhost
192.168.1.200 server1.myisp.com server 1

or something else?
3. Any ideas as to what else may be causing this ping issue? I've also edited /etc/network/interfaces and /etc/resolv.conf

Thanks for the time!

---

### Post by skatinjj on 2011-08-15
Just to try and clarify, can the XP desktop ping your server?

If so, does XP have a firewall up or AV program that may be blocking your ping requests?

---

### Post by AnnainOK on 2011-08-15
> **skatinjj said:**
> Just to try and clarify, can the XP desktop ping your server?

If so, does XP have a firewall up or AV program that may be blocking your ping requests?

Brilliant! I'd never thought to look at those. I'd assumed I had screwed up the configuration

Avast wasn't blocking it, but when I turned off Windows firewall it worked just fine. Now to put in the exclusion! For some reason, the firewall on the laptop didn't block it, nor did it notify me of the block as it is supposed to. Why is it that we forget the simple stuff sometimes? Thank you.

---

### Post by skatinjj on 2011-08-16
No problem, glad it got taken care of.  Being a technician and working day in and out on computers, I always check the simple things first hence KISS (keep it simple stupid).

---

