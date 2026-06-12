---
title: "How can I search for wireless internet?"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by rolandoislas on 2009-11-27
I have Ubuntu 9.10 and I need to figure out how to search for wireless internet. Sometimes I want to connect to a network but I don't know the SSID. On my PSP I can search for it automatically. Is there anyway I could get my laptop running on Ubuntu 9.10 to do it?

---

### Post by Buuntu on 2009-11-27
If the wireless card is configured correctly, it should show all available networks when you click on the network manager on the top right of your screen.  If not, there are a couple of possibilities:

1) You haven't installed the necessary proprietary drivers for your wireless card.  This can be done by running 'sudo apt-get update && sudo apt-get upgrade' in the Terminal and then checking for drivers in System > Administration > Hardware Drivers.  (you'll have to restart afterwards.
2) Your card doesn't work with Linux, but don't worry - there is a solution.  Check out Ndiswrapper for running windows drivers under Linux.  It works well and in fact is how I get my wireless card to work under Linux :D.  Here is the wiki site explaining more about ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If the first option doesn't work, will you please list your wireless card so I can see if it works with Linux or not before trying to use Windows drivers for it?

---

### Post by rolandoislas on 2009-11-27
> **Buuntu said:**
> If the wireless card is configured correctly, it should show all available networks when you click on the network manager on the top right of your screen.  If not, there are a couple of possibilities:

1) You haven't installed the necessary proprietary drivers for your wireless card.  This can be done by running 'sudo apt-get update && sudo apt-get upgrade' in the Terminal and then checking for drivers in System > Administration > Hardware Drivers.  (you'll have to restart afterwards.
2) Your card doesn't work with Linux, but don't worry - there is a solution.  Check out Ndiswrapper for running windows drivers under Linux.  It works well and in fact is how I get my wireless card to work under Linux :D.  Here is the wiki site explaining more about ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If the first option doesn't work, will you please list your wireless card so I can see if it works with Linux or not before trying to use Windows drivers for it?
I don't know what wireless card I have, but I do know it's the one that came with my Eee PC 900A. It worked with the Linux OS that I was running the netbook before.

---

### Post by Buuntu on 2009-11-27
Then maybe it's just a matter of activating proprietary drivers for it?  Did you try updating from the terminal like I said and checking Hardware Drivers?

---

### Post by brij on 2009-11-28
it looks like you have either atheros or ralink card all you need to do is run update if that doesnt help open synaptic and install all the drivers for atheros or ralink

To see what wireless card you have run the following
lshw -C network

---

### Post by azebuski on 2009-11-28
On my Eee PC 900 wireless internet and the webcam were turned off in the BIOS by default.  Try rebooting and pressing F2 to enter the BIOS. I forget the exact menu names in the BIOS setup, but somewhere there is a menu for turning on wireless networking.

---

