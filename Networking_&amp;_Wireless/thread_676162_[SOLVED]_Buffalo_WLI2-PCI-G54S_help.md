---
title: "[SOLVED] Buffalo WLI2-PCI-G54S help"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by maxhoward on 2008-01-23
I installed the Buffalo wireless card in my PC running XP and Ubuntu.  It works fine in XP (ie communicates with the net without any problems).  However I can't make it work in Ubuntu.  I followed the instructions posted in #1699599 by Drags111 and I am almost there.  I can ping to the router but cannot connect to a web address (eg [www.ubuntu.com](www.ubuntu.com)).  I think it must have something to do with the Wireless Network Settings but haven't found what all the settings mean or what the correct entries should be.  Any help will be GREATLY appreciated.  PS:  I am a newbie. :confused:

---

### Post by hahahan on 2008-01-23
Since you can ping the router we presume the driver isue is oke.
It looks like you miss a decent nameserver entry in your /etc/resolv.conf file. Could you post some output from:

ifconfig -a 
iwconfig
route
ping  -c 3 64.233.167.99

Hopefully we can help you further then.

---

### Post by Hightide on 2008-01-23
> **maxhoward said:**
>  PS:  I am a newbie. :confused:

Hi Maxhoward

hahahan has put you on the correct path. For your own learning have a look at Kevdog's tutorial. You may find it useful

[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

:)

---

### Post by maxhoward on 2008-01-24
Here are two screen shots which show the commands you suggested.  They are attached as jpg files.  I don't know how else to send them.  Thanks in advance.

---

### Post by hahahan on 2008-01-25
Tx for the information, it seems dhcp didn't workout right. Is your router dhcp enabled? Is any WEP/WPA encryption enabled on the router?

Regards.

---

### Post by maxhoward on 2008-01-26
Problem solved.  THANK YOU very much.

I tried to find the answers to your questions but I was not sure how to get the answers.
So I went to System> Admin > Network  > Properties for the wireless connection. I changed the "connection type" to "DHCP" from the drop down list and then it worked.

I don't know what encyrption system is used, but I do remember setting it up when I installed the router for Windows XP last year.  It worked immediately at that time on my PC as well as my wife's which is the client.  When I installed Ubuntu on both PCs (dual boot) Ubuntu was able to connect to the internet via the router with no trouble.  But the trouble began when I tried to connect to the web using Ubuntu as a client on my wife's PC.

Now that issued is finally solved.  Thank you again.

---

