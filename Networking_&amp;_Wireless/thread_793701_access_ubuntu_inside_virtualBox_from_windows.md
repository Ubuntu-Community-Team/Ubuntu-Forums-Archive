---
title: "access ubuntu inside virtualBox from windows"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by asifsehzaad on 2008-05-14
Hello everyone,

I am new to ubuntu/linux or let's say I am not very good at linux... but know the basics of networking... 

I have installed Ubuntu 8.04 LTS Server Edition, on [virtualBox]("http://www.virtualbox.org/") ... I intend to use this machine as a developer image... now my image is successfully communicating with the internet.... like if i do a ```
lynx www.google.com or wget "some file or internet addres"
```... i am able to do that.... (i am going to use this machine "virtualBox installation" as a slaughter house for some of my code which I develop every now and then)

and when I do a ```
ifconfig
``` I can see that the ip address for my ubuntu box ( virtualBox :KS) is somewhere in the 10.*.*.* range.... and my wireless router is running on a 192.168.*.* network, and during installation i asked my ubuntu instllation program to pick it's ip address from dhcp... and my wireless router is just a mix of something adsl modem +wireless router...
any ideas regarding this... what step am i not doing right... as i need to connect to this machine using an IP address (basically do a code drop, and run some shell scripts to bounce my web or some application servers....)

I tried editing the ```
etc/init.d
``` and removing the dhcp from that file and putting in the static IP information  (could not find the location, where I got that from)and my resolv.conf... and then put the new ip ( for example 192.168.10.34) in my host file on windows.... i am still not able to connect....

---

