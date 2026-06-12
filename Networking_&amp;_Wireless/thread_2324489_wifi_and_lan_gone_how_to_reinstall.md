---
title: "wifi and lan gone how to reinstall?"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by ubto66 on 2016-05-14
ubuntu 14.04 64bit

On a notebook with no built in display, instead an connected display usb wifi card and lan cable worked fine. After a restart wifi and ethernet is gone. Network icon in menubar is gone. In system settings -> network both wifi and wired are gone. No internet connection.
All hardware works because if I start debian 8 from a flash stick, usb wifi card works and so does internet connection.

What is the name of the default network package? How do I uninstall and delete configuration files?
More I can do than purge and reinstall?

Thank you.

---

### Post by Bashing-om on 2016-05-14
ubto66; Well ..

Perhaps you too are a victim of the latest update that broke network-manager .
see:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)

one fix that has worked for many in this instance:
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by joe_schell on 2016-05-14
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)


worked for me. I always us wireless with this particular laptop, so I had to connect a cable first, but ti fixed both WiFi and wired. 

Thanks

---

### Post by Bashing-om on 2016-05-14
joe_schell; Good deal /

Pleased it worked out for you.

As this incident has a happy conclusion:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by ubto66 on 2016-05-15
Thank you.
I got wifi and lan working this way.
 In synaptic package manager remove network-manager.
[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic) 
ip addr note what is eth number
Connect lan cable.
sudo stop network-manager
sudo ip link set dev eth0 down if eth number is 0
sudo dhclient eth0
Wait.
sudo /etc/init.d/networking restart
Close synaptic package manager. 
sudo apt-get --purge remove network-manager
In synaptic package manager install network-manager
Restart computer.

---

