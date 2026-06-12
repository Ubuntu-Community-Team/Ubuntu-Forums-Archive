---
title: "Lenovo 3000 N100 Broadcom wireless (wifi) problems"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by dirtytoyota4x4 on 2007-07-12
I just installed feisty and I cant seem to get my wireless to connect to anything. When I type the command lspci in the terminal I see " Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)" amond all of my other components.  Its a Lenovo 3000 N100, why it has a broadcom dell card I have no idea.  I dont know much about Linux but it looks to me like the card is installed. My wifi light does not light up but the network manager seems to think that my card is there because it will let me attempt to connect to a wireless network but nothing happens.  Im pretty ignorant when it comes to Linux so I wish I could find one of those easy step by step copy and paste into the terminal guides like I found for my soundcard problems in the forums.  :)  So far I like Ubuntu much more than windows, it seems to run faster and this wifi problem is the only thing keeping me from converting.

Any help will be greatly appreciated, thanks

---

### Post by kevdog on 2007-07-13
Can you just make sure first that your wireless card is turned on.  Im not sure how to tell you to do this.  Possibly check in the BIOS (and activate it) or cntrl-F2 or alt-f2, or some button on the console.

---

### Post by dirtytoyota4x4 on 2007-07-13
Yeah, my laptop has a switch and a light that comes on when the wireless is activated. If I boot into windows it lights right up and everything works fine.

---

### Post by dirtytoyota4x4 on 2007-07-15
Im still crawling the forums and have not found a guide that fixes this stupid wifi problem. I really dont want to go back to using windows again.

---

### Post by MyR on 2007-07-15
this should help
[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29)
peace

---

### Post by El Viejo Lobo on 2007-07-15
> **dirtytoyota4x4 said:**
> Im still crawling the forums and have not found a guide that fixes this stupid wifi problem. I really dont want to go back to using windows again.

First, take it easy Ubuntu is to good to drop down. Just some job to do on the broadcom card (It took me a few weeks to get  BCM 4318 working on Edgy and then some good guy made it working with a few clicks.
Try here:[https://answers.launchpad.net/ubuntu/+question/3839](https://answers.launchpad.net/ubuntu/+question/3839)
[https://answers.launchpad.net/ubuntu/+question/9356](https://answers.launchpad.net/ubuntu/+question/9356)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/115375](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/115375)
I hope that it will help you..

---

### Post by dirtytoyota4x4 on 2007-07-19
Thanks for the suggestions, but I ran across this guide [http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom+1390]("http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom+1390")
and the network manager sees my access point called "network" but when I click on it all I get is spinning and eventually no connection.  So I thought maybe it was a problem with DHCP and after browsing the forums someone said to check it out by running the dhclient command. I did this and all of a sudden my internet works but the network manager still shows no connection and will not connnect if I click on it.  As of right now I have all network encryption turned off but I would like to use WPA and I would also like to use my network manager because its easier than having to go into the terminal and run the dhclient command.  If anyone else has any suggestions they would be greatly appreciated. Thanks

---

