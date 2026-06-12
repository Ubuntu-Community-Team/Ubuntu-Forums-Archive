---
title: "Turn on Network Controller - BCM4318"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by foolio2000 on 2008-06-09
I am running Hoardy Heron. I went through the wireless troubleshooting wiki. In doing so, I believe that my wireless controller is turned off. 

The device is recognized and a driver is listed but I cannot find any wireless networks in the network manager when I know there are some. 

The controller is installed in a HP laptop that has a button to turn it on. In windows the button glows blue when turned on however in ubuntu it has not turned blue and the button does nothing.

Any advice would be greatly appreciated. Thank you for your time.

---

### Post by Ayuthia on 2008-06-09
> **foolio2000 said:**
> I am running Hoardy Heron. I went through the wireless troubleshooting wiki. In doing so, I believe that my wireless controller is turned off. 

The device is recognized and a driver is listed but I cannot find any wireless networks in the network manager when I know there are some. 

The controller is installed in a HP laptop that has a button to turn it on. In windows the button glows blue when turned on however in ubuntu it has not turned blue and the button does nothing.

Any advice would be greatly appreciated. Thank you for your time.

If you have a wired connection, you can install the firmware for your card.  You can check System->Administration->Hardware Drivers and see if your card is listed.  If it is not there, open up Terminal and type:
```
sudo apt-get install b43-fwcutter
```The application will ask to find the firmware for you.  Say yes and it will install the firmware for you.

---

### Post by Rocket2DMn on 2008-06-09
As far as I am aware, this card does not work in Hardy (I've certainly never been able to get mine to work).  If you DO get it to work, PLEASE PLEASE post back, otherwise I would appreciate it if you posted on my bug report and set the status to Confirmed - [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197)

May you have better luck than me!

---

### Post by Ayuthia on 2008-06-10
> **Rocket2DMn said:**
> As far as I am aware, this card does not work in Hardy (I've certainly never been able to get mine to work).  If you DO get it to work, PLEASE PLEASE post back, otherwise I would appreciate it if you posted on my bug report and set the status to Confirmed - [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197)

May you have better luck than me!

I thought that I have seen a couple of threads that have gotten this card to work with the b43 drivers, but I have also seen the a few where it did not work and some went the NDISwrapper route and I think that there might have been a few that went the bcm43xx route too.  I generally try to use the easy methods first and then if it does not work, go the NDISwrapper route.

---

### Post by Rocket2DMn on 2008-06-10
From what I saw, ndiswrapper wasn't working either.  Maybe there is a difference between the cards in laptops and the cards in desktops (mine is a desktop).  I would love somebody to confirm that bug for me so developers can get on with fixing the problem.

---

### Post by Corrupt3d on 2008-06-10
> **foolio2000 said:**
> I am running Hoardy Heron. I went through the wireless troubleshooting wiki. In doing so, I believe that my wireless controller is turned off. 

The device is recognized and a driver is listed but I cannot find any wireless networks in the network manager when I know there are some. 

The controller is installed in a HP laptop that has a button to turn it on. In windows the button glows blue when turned on however in ubuntu it has not turned blue and the button does nothing.

Any advice would be greatly appreciated. Thank you for your time.

Hey, I had a similar situation. My Notebook is an HP Pavillion with the same 4318 Broadcom chip. When I first installed Hardy my WiFi light did not come on. I skipped trying to use the B43 drivers and decided to go with the NDISWrapper. 
This thread worked for me [http://ubuntuforums.org/showthread.php?t=25683]("http://ubuntuforums.org/showthread.php?t=25683")

I had to modify a few of the steps, but it did work.
> 4. Reboot your PC. On restarting, the light on your wireless card should come on. If not, try entering sudo modprobe ndiswrapper


If you decide to go w/ the NDISWrapper and have any troubles let me know and I'll try to help.

On a side note: 'System>Administration>Hardware Testing', also managed to turn my Wifi light on, but it provided no functionality.

---

### Post by Ayuthia on 2008-06-10
Can you all post your lspci -nnm|grep 14e4 info?  I would like to see the subvendor information.  It might help in seeing why some work and some don't.

---

### Post by Corrupt3d on 2008-06-10
> **Ayuthia said:**
> Can you all post your lspci -nnm|grep 14e4 info?  I would like to see the subvendor information.  It might help in seeing why some work and some don't.

$ lspci -nnm|grep 14e4
> 06:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Hewlett-Packard Company [103c]" "Unknown device [1355]"

---

### Post by knownuthin on 2008-06-10
HP Pavilion zv6000 and bcm4318 wireless

I recently had this same problem after installing Ubuntu 8.04. (Worked great previously in Ubuntu 7.10) After 2 days of frustration and reading different forums I finally got it to work and thought I'd share my experience.

NOTE:
Being a knownuthin person I use MC (Midnight Commander) to move about from the terminal window. My file locating and edit skills need a crutch and MC running in the "sudo mc" mode allow me to view all directories and files plus edit anything. 

What I discovered was that apparently the new improvements (b43 and ssb) create a problem if running when ndiswrapper is installed.

My sequence and solution was to uninstall ndiswrapper completely using the Synaptic manager. Check /etc/modules file and make sure ndiswrapper was not listed to load at boot. 

1. Reboot
Open a terminal window
2. Edit /etc/modprobe.d/blacklist ... where it says 
"# replaced by b43 and ssb." 
"blacklist bcm43xx"
Add these 3 additional lines (no quotes) 
"blacklist b43"
"blacklist ssb" 
"blacklist b43legacy"
Save the file.

3. Next I removed installed modules b43 and ssb
sudo rmmod b43
sudo rmmod ssb

4. Reboot
5. See if the blacklist worked by looking at the wireless interface.
sudo lshw -C network

configuration: will show "driver=b43" and "module=ssb" if blacklist failed and reloaded the modules. I found that if these modules were loaded when ndiswrapper installs they will continue to be the controlling alias driver for the wireless card. 

Don't install ndiswrapper if b43 and ssb are still loaded and running. 

6. Use the Synaptic Package manager and install ndiswrapper again.
7. Change to the directory where the "bcmwl5.inf" driver is located and enter the following.  
 sudo ndiswrapper -i bcmwl5.inf
 sudo modprobe ndiswrapper
 sudo ndiswrapper -m

8. Check the network card again 
sudo lshw -C network

If all went correctly the "configuration:" will now list among other things... driver=ndiswrapper+bcmwl5 and module=ndiswrapper
and the wireless button light on the laptop should lite once ndiswrapper has loaded the driver.

9. Go to System->Administrator->Network
From there you should be able to (unlock) and select the Wireless Connection and configure the properties for your card.

A final test..........

10. Shutdown. The wireless button on the laptop will turn off.
11. Restart the laptop. The wireless button will turn on if all worked properly. 

sudo lshw -C network 
From there all your descriptions and setting should be listed.

I must have got lucky as my wireless now starts and runs everytime without additional scripts or modifying the rc.local file. 

Hope this helps someone.

---

