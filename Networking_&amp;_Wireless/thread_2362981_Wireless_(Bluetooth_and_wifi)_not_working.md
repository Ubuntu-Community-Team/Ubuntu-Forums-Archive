---
title: "Wireless (Bluetooth and wifi) not working"
date: 2017-06-04
forum: Networking &amp; Wireless
---

### Post by adhdluke on 2017-06-04
I've had to spend lots of time troubleshooting Ubuntu MATE 16.04 since I set it up to dual boot on my laptop. After running boot repair to get the GRUB bootloader back because of HP's Secure Boot deleting it, (yes, I disabled Secure Boot before running boot repair) everything is working fine except for networking and Bluetooth. It doesn't seem to recognize the Bluetooth adapter at all, and I can't get wifi to work. No connections show up at all. I'm assuming it's the same issue as the Bluetooth. 
I'm relatively new to Linux still.

---

### Post by wildmanne39 on 2017-06-04
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

I will do my best to help you get the wifi working but you should start a new thread for bluetooth it is easier to help you that way and they are to separate issues.

---

### Post by adhdluke on 2017-06-04
> **wildmanne39 said:**
> Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

I will do my best to help you get the wifi working but you should start a new thread for bluetooth it is easier to help you that way and they are to separate issues.
So it works when plugged in to the router. In the console when everything was finished I got this:

Errors were encountered while processing:
apport
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wildmanne39 on 2017-06-04
That is an update issue and not a network issue, you should not have got that message when running my script, but if you tried to install pastebin you could have if that is the case run the script and post the output here without installing pastebin.
Thanks

---

### Post by adhdluke on 2017-06-04
[https://pastebin.com/QGvSxABb](https://pastebin.com/QGvSxABb)

---

### Post by wildmanne39 on 2017-06-04
Please do the following by copying and pasting the lines one at a time and hit enter after each line.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Reboot and let us know if it is working.

Thanks

---

### Post by adhdluke on 2017-06-04
It's not working after running those commands and rebooting.

---

### Post by wildmanne39 on 2017-06-04
You have no internet at all through wifi? because even the first output of the script showed connected, and those commands should have fixed it, do you have your ethernet unplugged? it needs to be.

Go into your network manager settings and remove all networks then reboot, does it connect? make sure wifi is enabled in network manger. If after all the above it does not connect run the wireless script again and we will make sure the changes took effect.
Thanks

---

### Post by adhdluke on 2017-06-04
I had the Ethernet cable plugged in when I ran the commands. I cleared the networks and I'm rebooting. If it doesn't connect, should I run those commands to fix it again, this time with Ethernet unplugged?

---

### Post by wildmanne39 on 2017-06-04
No, you do not need to run the commands again, but wifi will not work as long as the ethernet is plugged in, it over-rides wifi.

---

### Post by adhdluke on 2017-06-04
I rebooted and there's no wifi. Ethernet isn't plugged in. Also, under the menu, where it says "wifi networks" (it's grayed out) under that it says "device not ready"

---

### Post by wildmanne39 on 2017-06-04
Did you remove all the connections from network manager before you rebooted? if not please do so, if you did please run the wireless script again and post the results, the information we see from is tells me us what we need to know more then anything else.
Thanks

---

### Post by adhdluke on 2017-06-04
I let my computer sit on the desktop for a while and it went to sleep. When I woke it, it recognized the wifi network. I have wifi now.

---

### Post by wildmanne39 on 2017-06-04
That is good, please reboot and see if it is still working.
Thanks

---

