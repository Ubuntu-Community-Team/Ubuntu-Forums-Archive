---
title: "cisco managed switch to ubuntu"
date: 2016-07-04
forum: Networking &amp; Wireless
---

### Post by atux on 2016-07-04
hello everyone. i have a cisco switch (cisco small business 300 series) and an ubuntu server 16 that has only one ethernet card. I would  like to add the switch to the ubuntu so when i do ifconfig can see all the switch ports. i would need some advice on how to do it please.

---

### Post by DuckHook on 2016-07-04
I haven't had to do this in years so had to look up the current methodology. Your simple-sounding request is actually rather complex:

[LIST=1]
[*]There is no way I'm aware of to get an external device to show up in *ifconfig*. *ifconfig* only reports on devices owned by the system which means only devices connected to your system pci bus.
[*]Therefore, you are looking for an app that can query/manage your Cisco switch. Such management software is usually either console-based or browser-based.
[*]Following are the instructions for console management: [https://help.ubuntu.com/community/CiscoConsole](https://help.ubuntu.com/community/CiscoConsole) (Alert: these instructions are old and haven't been updated in years. I'm not sure how usable they still are).
[*]Following are the instructions for browser management: [https://supportforums.cisco.com/document/34201/how-install-rtmt-linux-client](https://supportforums.cisco.com/document/34201/how-install-rtmt-linux-client) (Note that the original thread is again years old. In the interim, the web client was broken for Linux due to Cisco deciding to only support Java for Windows. You must read the last two comments in which the users found a workaround by installing *icedtea* and a few other supporting libraries).
[*]
[/LIST]
Full disclosure: I got rid of my salvaged enterprise-level Cisco switch in 2010, replaced it with a cheap consumer-grade D-Link, and haven't managed a switch since. i.e. I'm not your best source of information on this. Take above references with a grain of salt.

---

### Post by atux on 2016-07-05
hi. thanks a lot for the reply. i am not looking to get a management tool of the cisco devices from the linux box. i am looking to create a trunk between switch and linux box. so i could assign all ports of the switch to the linux box. i have a bunch of different non-broadcast networks that i have to see from the linux box. all of them are in different routers and i have to see them in the server.

---

