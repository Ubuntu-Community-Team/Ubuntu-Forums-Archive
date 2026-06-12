---
title: "Belkin 7001 - Given Up!"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by SuperExtreme on 2007-09-08
Hi there all Ubuntu Users,

How is everybody doing today? I just want to say that I've nearly given up hope on Ubuntu since I've brought my new Belkin G+ 7001 Wireless Card. On Ubuntu, all the options are there, like WPA, COnnect, etc..  but when I click Connect to my network, it just says "Connecting to (Null)" and does nothing, it just stays there and then at the end cancels itself :(. I have searched Google, Ubuntu forums for ages now and I still havent found a solution :(. Somebody please help me.

Many Thanks.

Best Regards,
Jay

---

### Post by SpiritIsReality on 2007-09-08
howdy
until someone knowledgeable shows up I've got this quote from P235
I do not know which guides you've read, but I suggest you read these two as well:

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) [For downloading and installing ndiswrapper via make]

[http://ubuntuforums.org/showthread.php?t=361917](http://ubuntuforums.org/showthread.php?t=361917) [Installing ndiswrapper w/ repos]

The basics can be found in these two treads and they've helped me get my wireless card working. For threads that address particular cards, visit:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs) "

trails

---

### Post by kevdog on 2007-09-08
Before installing anything can you post the following:

lspci -nn
lshw -C network

That will give us the info to know what driver to install.

---

