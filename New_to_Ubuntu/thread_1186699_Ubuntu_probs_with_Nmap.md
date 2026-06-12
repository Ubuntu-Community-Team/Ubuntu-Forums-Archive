---
title: "Ubuntu probs with Nmap"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Paperthing on 2009-06-13
Hello, 

I recently decided to use Linux for my computer instead of windows, however i had some problems with fedora and decided to use Ubuntu instead. I do have experience with Linux.

I have installed Nmap using the following code:

apt-get install nmap

the installation goes well and nmap works however when ever i scan i get the following message 

nmap -sL -v 192.168.1.105

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-06-13 15:57 MDT
Initiating Parallel DNS resolution of 1 host. at 15:57
Completed Parallel DNS resolution of 1 host. at 15:57, 0.06s elapsed
Host 192.168.1.105 not scanned
Read data files from: /usr/share/nmap
Nmap done: 1 IP address (0 hosts up) scanned in 0.25 seconds

i have tried to see if any one has incounterd this same problome but have not seen any thing, thank you for any help you can provide.

---

### Post by Mark Phelps on 2009-06-14
Sorry for the obvious question, but is your PC on the same local subnet, meaning, IP of 192.168.1.nnn?

Because if it's not, I don't believe that you will be able to connect to the other subnets to scan them.

---

