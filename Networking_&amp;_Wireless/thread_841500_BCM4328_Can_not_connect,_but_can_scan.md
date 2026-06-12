---
title: "BCM4328 Can not connect, but can scan"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Mugendai on 2008-06-26
Running Kubuntu 8.04 Hardy with latest stable updates
Machine:
HP Pavilion tx2000 CTO Tablet PC
Wireless BCM4328 (rev 03)

Here is the issue:
The card "looks" like it is working using ndiswrapper.
lshw -C network shows it using the right module, without ssb
KNetworkManager shows the available networks.
I can choose to join a network.
It recognizes the appropriate security configuration for the selected network.

I can almost never get past the stage that says "Activation stage: Configuring device."

I know it HAD worked but then it simply stopped.

It works fine in windows.

I've looked at several tutorials and forums, and have not been able to get it to work, eg:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Having very little luck.  I've come across a couple of cases of people in my situation where it is scanning, but wont associate with secured networks, but have not seen any results.

Minimum goal: get it to work on my home WPA2 wireless(DD-WRT router)
Desired goal: works everywhere windows does, including the PEAP secured network at work.

Please help, I'll do pretty much anything anyone can suggest.

Thanks

---

