---
title: "ubuntu 18.04 - rc.local - need script to change ip address to static"
date: 2020-03-12
forum: Networking &amp; Wireless
---

### Post by crabbychicken on 2020-03-12
Hi,

I have a script that runs at startup in /etc/rc.local - it runs after a dd clone is copied to a sgdisk-zapped hard drive with a new gpt.

I can complete various tasks like set the hostname, create and share some folders, copy some files and connect to my network share folder.

I cannot for the life of me figure out how to configure the ip address to a static ip.

When I am logged in I cannot change the ip address using the terminal successfully.

Network manager is running and seems to control everything.

I have access to all the network, but after I run the following in the script:

```
sudo ifconfig enpls0 192.168.4.226
```

ifconfig shows the ip address changed - network manager shows the old unchanged address - and I cannot access the network anymore.

I used to configure /etc/network/interfaces - but I understand things and changed recently in ubuntu?

Any help would be much appreciated.

I used to be able to do this very task in the past easily.

Thanks.

---

### Post by him610 on 2020-03-12
> sudo ifconfig enpls0 192.168.4.226 Only sets it temporarily 

Static IP assignment is documented here, [https://help.ubuntu.com/lts/serverguide/network-configuration.html]("https://help.ubuntu.com/lts/serverguide/network-configuration.html")
Be careful if editing *yaml* files, spacing and indentation is important. Not sure about Ubuntu interface, but static IP address can be set in the NetworkManager utility by clicking internet icon on (Xubuntu) panel.

---

