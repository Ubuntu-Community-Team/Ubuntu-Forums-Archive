---
title: "Wifi Adaptor Dongle Drivers 8198 Realtek Semiconductor Corp.RTL8187B (FokTech AC600)"
date: 2019-09-17
forum: Networking &amp; Wireless
---

### Post by antonyham on 2019-09-17
Hello! 

I have a wifi dongle from Amazon (see link: [https://www.amazon.co.uk/Foktech-802-11ac-Wireless-Network-10-5-10-13/dp/B06XZ5B5G9](https://www.amazon.co.uk/Foktech-802-11ac-Wireless-Network-10-5-10-13/dp/B06XZ5B5G9)) and wondered if it could be made to work with ubuntu.

I am running xubuntu 18.04. 

I know it is not working as I am unable to get a wifi signal from a distance that was possible while on a windows system. 

lsusb returns this: 

Bus 002 Device 003: ID 0bda:c811 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID **0bda:8198 Realtek Semiconductor Corp. RTL8187B Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have had a little look around and while I have a very vague idea of what to look for it seems there isn't much visible support for this hardware on linux.

I saw in amazon comments for this product that someone had managed to get it working. Here's that comment: 

"It  does not work out of the box - driver software needs to be installed.  This can be fiddly to make it work so don't buy if you are looking for  something that plugs in and works. The box includes a CD-ROM with Linux  driver software, which did not work for me **[I bought this a while ago so can't recall it coming with a disk]**. The following commands  worked for me on Mint 18.2 which is based on Ubuntu 16.04: 

$ sudo apt install linux-headers-generic build-essential git 
$ cd software-builds 
$ git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) 
$ cd rtl8812AU_8821AU_linux 
$ make 
$ sudo make install 
$ sudo modprobe rtl8812au "

I followed these command instructions, but got stuck on "cd software-builds" as the directory was not present in my home folders. I gave my disk a quick search to see if the directory was present elsewhere, but it returned no results. I then decided to create the software-build folder in the home directory and continue the instructions. It seemed to progress smoothly with no errors but after I got the the end the adaptor still didn't work or appear on "sudo lshw -c network". I restarted the computer, and once I confirmed it wasn't working I ran that commands again: still nothing. Was there anything I was supposed to do after reaching the end of the instructions? Was I supposed to put the "software-builds" folder in a specific place? Are these instructions unlikely to work to begin with?

Thanks for all your help in advance.

---

### Post by pcfan1234 on 2019-09-18
This would be a folder that you have to manually create. This is not necessary. Just ignore it.
EDIT:
Ignore $ cd software-builds.

---

### Post by jeremy31 on 2019-09-18
Moved to Network & WIreless

---

### Post by chili555 on 2019-09-18
I believe that your  0bda:8198 device is covered by the built-in driver rtl8187 in Ubuntu 18.04. Simply plug the device in and it should work.

If not, run and post:

```
rfkill list all
dmesg | grep -i rtl
iwconfig
```The rtl8812AU driver doesn't cover your device. I suspect that Amazon is a rather unreliable resource.

---

### Post by antonyham on 2019-09-18
Thanks Chilli,

I'll try that when I get back home.

Does xubuntu 18.04 still contain the same built-in drivers as Ubuntu? Also this is a 32-bit system. Not sure it matters but that tends to keep coming up as a factor in other problems I've had.

---

### Post by antonyham on 2019-09-18
Thanks Chilli,

Ah, I think I know where I'm going wrong. The rtl8187B is probably referring to the laptops old in-built adaptor, which has horrible range. 

The one I'm concerned with is actually the first listed: 0bda:c811, which already has a couple of forum posts on it. I'll try the solutions on there before I ask for more help.

Sorry for the mess-up and wasting your time.

---

### Post by chili555 on 2019-09-18
> **antonyham said:**
> Thanks Chilli,

Ah, I think I know where I'm going wrong. The rtl8187B is probably referring to the laptops old in-built adaptor, which has horrible range. 

The one I'm concerned with is actually the first listed: 0bda:c811, which already has a couple of forum posts on it. I'll try the solutions on there before I ask for more help.

Sorry for the mess-up and wasting your time.No problem at all. We just want to get you up and running.

Xubuntu uses the same drivers as vanilla Ubuntu.

Post back if you need further guidance.

---

