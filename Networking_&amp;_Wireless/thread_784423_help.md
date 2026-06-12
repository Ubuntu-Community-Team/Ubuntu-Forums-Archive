---
title: "help"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by Snappo on 2008-05-06
hi

---

### Post by Ayuthia on 2008-05-06
Can you post your lspci -nn?  It will help identify your wireless card.  Thanks!

---

### Post by Snappo on 2008-05-06
> **Ayuthia said:**
> Can you post your lspci -nn?  It will help identify your wireless card.  Thanks!
"Atheros Wireless Network Adapter" the sooner this is online the  better.

Thanks

---

### Post by Ayuthia on 2008-05-06
You might try this guide:
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Hope that helps.  I am not for sure if it matches the model of your Atheros card or not.

---

### Post by Snappo on 2008-05-06
I only have wireless so i am not able to download when linux is running only when i am running windows on this other disk and i move files via cd. Mind explaining this to me?

---

### Post by Ayuthia on 2008-05-06
Well, there is a 32-bit instruction guide and a 64-bit guide.  Both do require you to download a file.  

The 32-bit version requires you to have your LiveCD (so that you can install build-essential).  
You will have to do the first step in the i386 Users section and reboot.

Next, you will have to go into Synaptic and add the CD to the repositories.  I am a KDE user so I am not going to be able to guide you to the right place in Synaptic to add the CD.  Try to look for something about managing repositories.  If you can't find it, you can go to the Terminal and type:
```
sudo apt-cdrom add
```It will ask you to insert your LiveCD and press enter.  Once you do that, you will need to run an update:
```
sudo apt-get update
```.  

You can then install build-essential from Synaptic or do: ```
sudo apt-get install build-essential
```

You will need to get this file:
[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

Copy that file to your home directory.  You can then follow the steps after the wget portion.

The next steps will compile a driver for you and install it.


Hope that helps.

EDIT:

You might also want to print a copy of the instructions!!!

---

### Post by Snappo on 2008-05-06
Thanks for taking the time to help me out but when i run them commands in terminal i just get errors that the files are not their. I placed them on the desktop, I will wait for you to reply before i switch hd and boot up ubuntu. Do i have the disk in whilst running ubuntu off my hard disk?

---

### Post by Snappo on 2008-05-06
> **Ayuthia said:**
> Well, there is a 32-bit instruction guide and a 64-bit guide.  Both do require you to download a file.  

The 32-bit version requires you to have your LiveCD (so that you can install build-essential).  
You will have to do the first step in the i386 Users section and reboot.

Next, you will have to go into Synaptic and add the CD to the repositories.  I am a KDE user so I am not going to be able to guide you to the right place in Synaptic to add the CD.  Try to look for something about managing repositories.  If you can't find it, you can go to the Terminal and type:
```
sudo apt-cdrom add
```It will ask you to insert your LiveCD and press enter.  Once you do that, you will need to run an update:
```
sudo apt-get update
```.  

You can then install build-essential from Synaptic or do: ```
sudo apt-get install build-essential
```

You will need to get this file:
[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

Copy that file to your home directory.  You can then follow the steps after the wget portion.

The next steps will compile a driver for you and install it.


Hope that helps.

EDIT:

You might also want to print a copy of the instructions!!!

I'm lost on the download section down. I have no internet on the computer when i run linux so i downloaded the file before hand and put it on cd
then on the desktop. I then linked to the file but i didn't understand what you meant so if you could be clarifly that would be great. :)

---

### Post by Snappo on 2008-05-06
Please help i am on a very infected os right now waiting.

---

### Post by Ayuthia on 2008-05-06
Sorry, I had to reconnect--I am on dialup.

You said that the file is now on the Desktop.  You need to do the following:
```
cd ~/Desktop
tar xfz madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
```
By any chance have you already installed build-essential?  That is going to be needed for compiling.

---

### Post by Snappo on 2008-05-07
ok ok, I done what you said and I guess it worked because i got no errors and restarted. How do i know if it worked? i right clicked to the wifi editer but i did not see my network.

---

### Post by Ayuthia on 2008-05-07
Can you post the results of lsmod|grep ath, ifconfig, and iwlist scan?

---

### Post by Snappo on 2008-05-07
> **Ayuthia said:**
> Can you post the results of lsmod|grep ath, ifconfig, and iwlist scan?

I take it I am to run them commands in terminal?

---

### Post by Ayuthia on 2008-05-07
> I take it I am to run them commands in terminal? 
Sorry, yes.

---

### Post by Snappo on 2008-05-07
Ok I saved a text file to a dvd but doesn't work with windows so i took a screenshot for you.

[click here]("http://www.upload2world.com/pic86/upload2world_c204d.png")

---

### Post by Ayuthia on 2008-05-07
What happens when you type this into the Terminal:
```
sudo ifconfig ath0 up
```

---

### Post by Snappo on 2008-05-07
> **Ayuthia said:**
> What happens when you type this into the Terminal:
```
sudo ifconfig ath0 up
```

Ok i will do it. Please don't forget it takes me about 15 minutes to get windows back after switching hd etc.

---

### Post by Snappo on 2008-05-07
ok i done it and got an error device not connected.

---

### Post by Ayuthia on 2008-05-07
Ok. What we should try to do is figure out which device your wireless is connected.  This can be done by lshw -C network.  The results should look something like:
```
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:32:fc:24
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g
```
Check and see what the configuration line says.  The driver will tell you which module it is trying to use.  Hopefully you will have a logical name also.  That is the wireless name.  That is what will will need to turn on your wireless.  In my case it is wlan0 so I would activate it by: sudo ifconfig wlan0 up.

It might be possible that you will have to turn off the Atheros Hardware Access Layer in your Hardware Drivers, restart and see if you could turn on your wireless by using the ifconfig command.  

If this doesn't do it, I am not for sure about what the next step should be.

---

### Post by Snappo on 2008-05-07
> **Ayuthia said:**
> Ok. What we should try to do is figure out which device your wireless is connected.  This can be done by lshw -C network.  The results should look something like:
```
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:32:fc:24
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g
```
Check and see what the configuration line says.  The driver will tell you which module it is trying to use.  Hopefully you will have a logical name also.  That is the wireless name.  That is what will will need to turn on your wireless.  In my case it is wlan0 so I would activate it by: sudo ifconfig wlan0 up.

It might be possible that you will have to turn off the Atheros Hardware Access Layer in your Hardware Drivers, restart and see if you could turn on your wireless by using the ifconfig command.  

If this doesn't do it, I am not for sure about what the next step should be.


Ok i done what you asked and it listed information for my erthernet which i don't use. I'm thinking it is connected some other way as when i ran this command during install it done nout.

sudo modprobe ath_pci

---

### Post by Ayuthia on 2008-05-07
If it does nothing, that means that it is loaded.  If you take a look at lsmod|grep ath, you will see that ath_pci is there.

I am currently out of ideas.  Sorry.

---

### Post by Snappo on 2008-05-07
> **Ayuthia said:**
> If it does nothing, that means that it is loaded.  If you take a look at lsmod|grep ath, you will see that ath_pci is there.

I am currently out of ideas.  Sorry.

Oh no?, is there any more information i can get you?

---

### Post by Ayuthia on 2008-05-07
The problem that we have right now is that we don't know how to bring up the wireless.  Normally, lshw -C network provides us an idea about which device it is.  Without that, it is hard to bring it up.  I was thinking that the device could be wlan0, eth1, or ath0.

You can try and check:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```It sometimes contains some information about network cards.  You would find the device under NAME=.

---

### Post by Snappo on 2008-05-07
> **Ayuthia said:**
> The problem that we have right now is that we don't know how to bring up the wireless.  Normally, lshw -C network provides us an idea about which device it is.  Without that, it is hard to bring it up.  I was thinking that the device could be wlan0, eth1, or ath0.

You can try and check:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```It sometimes contains some information about network cards.  You would find the device under NAME=.

Well thanks for your help, you have been the only one out of this large community to troubleshoot it with me. I will get you them results after i finish this report.

---

### Post by Snappo on 2008-05-07
Ok i can some testing and "ifconfig" fails to show information relating to the wifi card.

---

### Post by Snappo on 2008-05-08
bump

---

### Post by Snappo on 2008-05-10
bump

---

### Post by alzeih on 2008-05-12
Do you have a hardware switch on the front for wifi? 

Switch that (the light may not change), then use the following commands in the terminal:

sudo modprobe -r ath_pci
sudo modprobe ath_pci 

If it seems to stutter a bit when running the second command, it may be working now... give it a minute or two to scan for wireless networks (and try ifup again)

Else flip the switch again and repeat.


Another thing to try is the command
dmesg | grep "wifi"   
or
dmesg | grep "ath"

If you get something like error #13 hardware revision not supported, then you might need to update your drivers... though using modprobe fixes it for me.

hth.

---

### Post by Snappo on 2008-05-14
> **alzeih said:**
> Do you have a hardware switch on the front for wifi? 

Switch that (the light may not change), then use the following commands in the terminal:

sudo modprobe -r ath_pci
sudo modprobe ath_pci 

If it seems to stutter a bit when running the second command, it may be working now... give it a minute or two to scan for wireless networks (and try ifup again)

Else flip the switch again and repeat.


Another thing to try is the command
dmesg | grep "wifi"   
or
dmesg | grep "ath"

If you get something like error #13 hardware revision not supported, then you might need to update your drivers... though using modprobe fixes it for me.

hth.

Is the wifi manager the edit wifi when i right click networks?

---

