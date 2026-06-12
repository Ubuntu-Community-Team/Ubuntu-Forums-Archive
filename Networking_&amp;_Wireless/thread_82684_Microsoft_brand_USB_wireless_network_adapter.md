---
title: "Microsoft brand USB wireless network adapter"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by macleod185 on 2005-10-27
I have a Microsoft brand wireless network adapter which is USB. I need to know how to make this work with my Ubuntu OS, I am running a Two hard drive dual boot system, but i can only use the internet when using XP. How do I get ubuntu to recognize the device and log onto my home wireless network??? are there any drivers for this? I am a noobie so i need step-by-step instructions.



any help would be greatly appreciated.
Thanks

---

### Post by ccsalesman on 2005-11-01
i have the same exact adapter, the mn-510
first you have to find the drivers in windows for this card, there is an .inf file and a .sys file- copy those from windows, and put them on a thumb drive or cd.

then i found this, from vcelis on another post
> - Get ndiswrapper-utils by typing "sudo apt-get install ndiswrapper-utils" in a terminal.
Give the root password when necessary.
- Get the Microsoft Windows drivers. Copy the .inf and .sys file. Paste these into a folder. 
(eg. /home/<USERNAME>/Desktop/driver/)
- Open a terminal
- Type the following commands:
cd Desktop/driver/
sudo ndiswrapper -i <name>.inf
sudo modprobe ndiswrapper


i have the drivers installed but i'm stuck at this last part tho.  when i type in 'sudo modprobe ndiswrapper' i get: 'Fatal: error .........  operation not permitted'

i emailed vcelis this morning so hopefully he'll email me back, if i can get it to work, i'll post up for you :)

EDIT: i found this: [http://www.linuxquestions.org/hcl/showproduct.php?product=673&sort=8&cat=146&page=1]("http://www.linuxquestions.org/hcl/showproduct.php?product=673&sort=8&cat=146&page=1") , and here's the driver [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/linux-wlan-ng-0.2.1-pre11.tar.gz]("ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/linux-wlan-ng-0.2.1-pre11.tar.gz")

will this even work, i'm not sure what i'm doing?

---

### Post by teaker1s on 2005-11-01
just a thought guys if you fail to install the microsoft elements check the vendor id and product id as you may find that the 'microsoft' branding is infact a product built by someone else

---

### Post by mxyzptlk on 2005-11-01
its so sad to see that most of you dont read all the threads about a specific topic like yours.

any way once again.

you have to make sure that your device has a Linux driver it would be easier.

ndiswrapper is a powerful tool but it doesnt work with al devices as i said before here in this forum. 

forget about if your device says Microsoft, try to find what kind of chip it has in it.

then search for the driver (of the chip ofcourse) in ubuntu database.

last thing what version of ubuntu you are using.

---

