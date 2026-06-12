---
title: "Need help with network adapter!"
date: 2019-04-29
forum: Networking &amp; Wireless
---

### Post by epicperson04 on 2019-04-29
I recently bought a network adapter for my computer running Ubuntu (dual boot with OSX). I have tried multiple methods and Drivers but I just can’t get it to work. It works perfectly using a driver on OSX but just can’t get it to work on Ubuntu. It is a ‘600M Wireless USB Adapter’ by Realtek. Any help will be appreciated! Thanks

---

### Post by wildmanne39 on 2019-04-29
Hello and welcome to the forum!

Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by epicperson04 on 2019-04-29
Should I run with the adapter in or out of the computer?

---

### Post by wildmanne39 on 2019-04-29
With it in please.

---

### Post by epicperson04 on 2019-04-30
Sorry I took a while to reply as I was away.
[https://pastebin.com/v1J0catw](https://pastebin.com/v1J0catw)

---

### Post by wildmanne39 on 2019-04-30
Have a look here, this should help:

[https://ubuntuforums.org/showthread.php?t=2394959&page=2](https://ubuntuforums.org/showthread.php?t=2394959&page=2)

You also have a internal broadcom device is there something that you do not like about that device? you may have to blacklist the wl driver while using the usb adapter but I am not sure about that I vary rarely use an usb adapter. Post 20 tells you how to install the driver, if you have secure boot enabled you will need to disable it, the directions to do so are a couple of posts up from 20.

---

### Post by SeijiSensei on 2019-04-30
It certainly looks connected. Your machine has 192.168.1.137 as its IP address; the router is at 192.168.1.1.

Open a terminal and type "ping 192.168.1.1". Does the router reply or does the request time out?

---

### Post by epicperson04 on 2019-04-30
Yes the router does reply.

---

### Post by SeijiSensei on 2019-05-01
Then what do you mean when you say it's not working?

Can you ping an address outside your network, like ping 8.8.8.8?

Can you visit a web site using its IP address but not its domain name?  For instance, can you visit 91.189.94.16 with a browser but not [www.canonical.com?](www.canonical.com?)

---

