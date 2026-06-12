---
title: "using 2 nic: 1 wifi + 1 ethernet"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Djang0 on 2008-04-11
Hi Everybody,

I've been googled a lot and now I get a bit confused! Basically what I want to do is using an Ethernet nic for my main internet connection and sometimes switching to a PCI wifi device (using another internet connection). Both will be installed but I will mainly use the pci one. I'm using Gutsy for short time now and I don't have any Idea how to configure this. Does someone have an idea of the procedure I have to follow (wifi nic is not yet physically installed but the Ethernet one does and works perfectly)? If this has been already answered, I haven't found it (in that case, sorry for the noise).

thanks in advance,

---

### Post by Kebabman on 2008-04-11
From the sounds of it you don't want to use both of them at the same time so there shouldn't be any problem. Just disable the one you don't want to use. You can do this from the terminal or from a graphical app.

Make sure you have appropriate entries in your /etc/network/interfaces file for each card...

Terminal :

Set the state of a card to down (disabled) using -
 #sudo ifdown eth0

Set the state of a card to up (enable) using -
#sudo ifup wifi0

This should then configure the wife device based on your interfaces file.

To do it using a graphical app, run 'gksu network-admin' from a terminal and it will present you with a nice little network configuration app. (Sorry, not sure how to find this using gnome as I don't use it)

You can then enable or disable a connection using the checkboxes on the left hand side.

That was quite a long answer to a simple question but hope it helps :)

---

