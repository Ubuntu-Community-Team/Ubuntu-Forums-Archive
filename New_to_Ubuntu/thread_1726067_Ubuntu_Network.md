---
title: "Ubuntu Network"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by Makarov. on 2011-04-10
For the life of me I can't setup Networking for Ubuntu.

I currently Installed 10.4 "Inside of Windows". Whenever I go to the network manager, It says "Wireless Network ; Disconnected".

I try to connect to a hidden network, But then I get automatically disconnected.

I'm not sure what Samba is or even if I've installed it.

I've tried but I got "Broken Packages"

I know this has happened for years, as I've been going through this forum for a few days now. 

But if you could help, thank you.

---

### Post by marin123 on 2011-04-10
do you have wireless drivers installed?

you could connect with wire and try if its working...

what do you mean that you installed it inside windows? wubi or virtualbox?

you dont need samba for accessing internet. samba is for file sharing over internet...

to fix broken packages you can try:
```
sudo apt-get autoremove
```

to remove packages you dont need...

---

### Post by bodhi.zazen on 2011-04-10
I assume you mean you are using wubi.

Sounds like a problem with your wireless card as otherwise setting up a wired connection is trivial.

What wireless card is it ? Are you using WPA ? Have you tried using a wired connection ?

---

### Post by BertN45 on 2011-04-10
You have to connect to a wireless network first. Normally if you open the network applet starting on on the fifth row you will see the networks that the system detects. If no network names are displayed, probably you need to find the right driver, like in windows. 

Normally you can ignore the hidden network menu item, since it is only used by security freaks :) It would mean that in your wifi router, you have disabled the display of your the network name (SSID).

Samba is the programs that deals with file sharing, but first you have to get your wifi working.

If your package dependencies are broken you should start the terminal in the accessories menu and type:
sudo apt-get install -f 
and that will fix the broken packages. You can also use the synaptic package manager in the system menu and in synaptic go to edit menu where there is a "fix broken packages"

---

### Post by Makarov. on 2011-04-10
My Network Card is

"Dell Wireless 1397 WLAN Mini-Card"

I am using WUBI, And the Network is WEP.

I've tried:
sudo apt-get install -f 
already.

But since Samba isn't related to getting the network on, I guess we can skip that for now?

---

### Post by marin123 on 2011-04-10
> **Makarov. said:**
> My Network Card is

"Dell Wireless 1397 WLAN Mini-Card"

I am using WUBI, And the Network is WEP.

I've tried:
sudo apt-get install -f 
already.

But since Samba isn't related to getting the network on, I guess we can skip that for now?

connect computer with wire and you should be connected to the internet, then hit alt+f2, type jockey-gtk and see if there are any drivers you can install.. after installation of wireless driver you should see available networks.

---

### Post by Makarov. on 2011-04-10
Thank you so much guys, I'm not officially an Ubuntu user!!

---

### Post by yeats on 2011-04-10
Sounds like you have three different problems here: 1) an APT (package manager) problem, 2) a network card problem and 3) a need to get samba up and running.

Most importantly, you need to fix the "broken packages" error before you can install anything else to fix the other two issues.  Can you provide details about what's going wrong?  (If possible, copy and paste the output into your post, using CODE tags - click the # symbol when composing).

---

### Post by BertN45 on 2011-04-11
You might have to use and ethernet cable between your wifi router and the computer to be able to do this. You also have to make sure that only one of the drivers is installed at the same time.

Your card has the famous broadcom bcm43xx chipset and I know since I own a Dell laptop too. There are two drivers available for the wifi and in most releases only one of them will work. One driver is produced by broadcom and the other by the linux community. You have to check which driver is used by going to system menu and there you have an entry about drivers. I do not remember the exact name in 10.04, but probably it is hardware drivers or additional hardware. First check whether the Linux community driver is installed (see next paragraph). If no driver is activated or installed you should activate the broadcom STA driver. Afterwards you should be able to see the network names in the network manager applet. 

If that driver is not working, you can try the other one.  I had to use the other one with 11.04. In that case first deactivate the Broadcom STA driver and go in the system menu to the Synaptic package manager. Type b43 in the search / filter box and tick the boxes in front of "b43-fwcutter" and "firmware-b43-installer' and press the apply button. That should install the second driver. One of the two should work as far as I remembered. 

To un-install those drivers right click the above entries in the Synaptic Package Manager and select "mark for removal".

There is a third possibility by using the windows XP driver in Linux, but that is somewhat more complex and I remember from early 2010 that one of these two drivers did work n my Dell Laptop..

---

