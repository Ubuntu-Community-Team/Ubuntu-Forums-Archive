---
title: "[SOLVED] Shorewall, canot find /default-config/ :("
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by pietjorritsma on 2008-09-26
Hi, got a silly question. I want to install a firewall on my Ubuntu server 8.04. I chose Shorewall because everybody is saying its the best firewall. So i got my self a manual and opened a console and wrote "apt-get install shorewall" and got it on my system. 

Now the problem, the manual say's :

[I]Note to Debian and Ubuntu Users

If you install using the .deb, you will find that your /etc/shorewall directory is empty. This is intentional. The released configuration file skeletons may be found on your system in the directory /usr/share/doc/shorewall/default-config. Simply copy the files you need from that directory to /etc/shorewall and modify the copies.[/I]

Bud if i go to /usr/share/doc/shorewall/default-config it say's directory not found, i went there and could not find the default-config dir. 

So my question, where can i find/get it ? 
So i can setup the firewall (need it because i am new to Shorewall and don't know much about it)

---

### Post by annatar on 2008-09-26
Make sure you have installed the 'shorewall-common' package (do so by sudo apt-get install shorewall-common)
the skeleton files are included in there

---

### Post by pietjorritsma on 2008-09-26
Thanks for the reply, bud already got 'shorewall-common' installed (so he say's)

---

### Post by pietjorritsma on 2008-10-02
Found the solution, the reason why i could not find it is because. 

In version 3.x the address is /usr/share/doc/shorewall/default-config/

And in version 4.x the address is /usr/share/doc/**shorewall-common**/default-config/

For people who have the same problem, there is the solution. It's also in the manual only it's telling you first to go to /usr/share/doc/shorewall/default-config/ without saying it's 3.x only (well about 20 sentences later :P )

GreatingzZz

---

