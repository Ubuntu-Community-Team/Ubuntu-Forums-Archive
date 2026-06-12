---
title: "Cloning working system won't connect WiFi in new devices"
date: 2021-05-12
forum: Networking &amp; Wireless
---

### Post by amilcarcp on 2021-05-12
Hi everyone, this is my first post here.

I had read several posts and couldn't find anything related to my topic, but I don't know which words I should use for the searching so... sorry if this is a answered thing

The issue I'm finding is the following:
- We have to prepare several mini-computers every day to play simple content.
- All this devices goes with Ubuntu (a slightly modified version)
- All the devices will connect to the same SSID-Password WiFi (every one in it's place, but every place have the network with the same credentials.

We prepared one single computer in all configuration and aspects (all but the content ID)... including the WiFi. This original computer works as expected in every aspect.
Then we cloned the HDD of the computer, and we now use this clone to prepare the other computers (same hardware in every case).
The issue here is that the "new" computers aren't connecting to the WiFi automatically, we have to go to the WiFi settings and connect every device to the WiFi (we have a copy of the wifi in our lab so we can load content when preparing the devices)

After checking the settings, I see that the WiFi is linked to a WiFi device, identified with the MAC; and I believe this is the big issue.

How can I do so every new computer gets the WiFi credentials without we having to input them again or having to access the wifi settings?

Or is there a way to prepare a one-use script that will only run the next boot and check the MAC and changing the WiFi settings acording?
Or to save the WiFi to a network interface id (wlan0) instead of a MAC?

Maybe I'm facing all this wrong and there is another way, but I'm not very used to Ubuntu.

I'd like to do a simple manual for my coworkers so they can prepare the computer without having to worry about this kind of things.

I have permission to install things in the system (if it's not taking too much resources from the device

The Ubuntu version we are using is 18.04

Thank you very much

---

### Post by morrownr on 2021-05-14
> **amilcarcp said:**
> 

(same hardware in every case).



Networking hardware has to have different MAC addresses so you may think the hardware is the same but not totally.

You can search for "predictable network interface names" to get more information.

My notes show the following way to shut it down but please research the issue to make sure this is what you want to do and this is the correct way on the version of Ubuntu that you are using.

-----

Edit the following file:


$ sudo nano /etc/default/grub


Change the following line


GRUB_CMDLINE_LINUX=""


to


GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"


Save the file.


-----


Run update-grub:


$ sudo update-grub


-----


Reboot:


$ sudo reboot

---

