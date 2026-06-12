---
title: "wireless, does it work on Ubuntu?"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by kozmo on 2005-05-30
I'm posting on a windoze machine because wireless networking stopped working on Hoary.

I used **ndiswrapper-utils** to setup wireless networking on my laptop (broadcom driver); and wireless networking has been working. The only problem I had is on boot it would hangs on 'configurng network' and I would finally get an error message after a minute that hostname resolution failed. Even though I ran **ndiswrapper -m** so that the wireless module would load up on boot. To get wlan0 to work I would go into the network configuration properties for wlan0 and found that the setting were correct and that wlan0 is active. I would just have to select the default eesid again and click OK all the way out then I would have wireless networking working.

Now this isn't even working for me. It takes 2 or more minutes while Ubuntu "activates wlan0" -- even though it was already active. I cannot ping anywhere,  ifconfig does not show an ip address (using dhcp). The other computer on my network (windoze) is connected and can get out to the Internet. I have tried rebooting the machine and going through these steps again, and still wireless networking will not work. I even have a blue light on my laptop indicating that it can see a wireless network. In fact, in properties in network configuration it lists several wireless networks as being available -- but only one is mine.

Not to mention that Ubuntu keeps freezing the computer at least once a day. Sometimes when I used my usb mouse it will freeze. Another time when I'm away from the laptop the screensaver will freeze. Another time I was looking at the settings in Synaptic and it froze. 

I've never ran into these problems with other Linux distros. I'm wondering if Ubuntu is not ready for prime time.

---

### Post by kozmo on 2005-05-31
I have read several posts on the bcmwl5 broadcom driver -- evidently they are a pain in the arse to configure.

I was able to get wirelss networking working again by following the instructions in [HOW TO: Configure wireless cards with Broadcom chipsets](http://ubuntuforums.org/showthread.php?t=25683&highlight=bcmwl5). 

But I get ndiswrapper error when I boot up. 
[B]ndiswrapper driver not found
ndiswwapper driver invalid[/B]

When I go into System>Admin>Networking it shows that wlan0 is active and all the properties are correct. If I click OK all the way out it does run the "activating wlan0" then I am connected to my wireless network.

ect/network/interface displays:
iface wlan0 inet dhcp
wireless-essid default
auto wlan0

sudo ifup wlan0
interface wlan0  already configured

any suggestions on how to get the wirelss networking to boot up properly?
thanks!

---

### Post by kozmo on 2005-06-01
wi-fi on Ubuntu is very flaky. I didn't change anything and now wireless works fine. It loads the driver on boot, I don't have to play with my network setting - Great.

For those with a Broadcom bcmwl5 driver here is how I got it to work. No guarantees it will work for you.

Get the needed dev tools.
```
sudo apt-get install build-essential
```
Install the ndiswrapper utilities
```
sudo apt-get install ndiswrapper-utils
```
Copy bcmwl5.inf and bcmwl5.sys to your home directory and run the following command:
```
sudo ndiswrapper -i ~/bcmwl5.inf
```
run modprobe 
```
sudo modprobe ndiswrapper
```
verify that everything went fine
```
sudo ndiswrapper -l
```
Set the module to load when you boot up your machine:
```
sudo ndiswrapper -m
```

Go to System>>>Administration>>>Networking
and configure your network. You should see an interface for wlan0. Set the properties according to your network and activate wlan0.

Open up your web browser and start surfing!

---

### Post by slyboots on 2006-08-21
> **kozmo said:**
> wi-fi on Ubuntu is very flaky. I didn't change anything and now wireless works fine. It loads the driver on boot, I don't have to play with my network setting - Great.

For those with a Broadcom bcmwl5 driver here is how I got it to work. No guarantees it will work for you.

Get the needed dev tools.
```
sudo apt-get install build-essential
```
Install the ndiswrapper utilities
```
sudo apt-get install ndiswrapper-utils
```
Copy bcmwl5.inf and bcmwl5.sys to your home directory and run the following command:
```
sudo ndiswrapper -i ~/bcmwl5.inf
```
run modprobe 
```
sudo modprobe ndiswrapper
```
verify that everything went fine
```
sudo ndiswrapper -l
```
Set the module to load when you boot up your machine:
```
sudo ndiswrapper -m
```

Go to System>>>Administration>>>Networking
and configure your network. You should see an interface for wlan0. Set the properties according to your network and activate wlan0.

Open up your web browser and start surfing!
Hellow. I have some problem with the ndiswrapper.
I use Dapper on my HP nx6110. I have bcm43xx wlan card. 
The card wont function in my dapper installation. So i have installed ndiswrapper and with **sudo ndisgtk** used a windows driver. When i will 
use the driver, i need to make this before:

[COLOR="Red"]sudo rmmod bcm43xx[/COLOR]

[COLOR="Red"]sudo rmmod ndiswrapper[/COLOR]

[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]

after i make this all, the card is redy to use. But when i get reboot the computer i need to make the same before the using. 
I dont now what is the ground, why wont the card funcion correctly...

---

