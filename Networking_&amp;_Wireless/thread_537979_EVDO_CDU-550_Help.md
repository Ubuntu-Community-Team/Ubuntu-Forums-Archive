---
title: "EVDO CDU-550 Help"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by darkwave80 on 2007-08-29
I found a post about the EVDO CDU-550 USB CMDA cellular internet card which provides hi-speed internet in areas with good singal....I want to get this to work with ubuntu and the only instructions I could find is pasted below.....

I think that this is the instructions on how to use the card but I dont understand...I need step by step help......espessally the part about "attached shell script to create node and ect...... if below isnt useful ...How can i get this to work for ubuntu? I have the newest version 7.04......thanks for help....

_____________________________________________________
Here is the information (direct from Franklin) for getting the Franklin USB EVDO CDU-550 Modem working with Linux.

Quote:
Linux systems already have USB modem driver but needs to assign a device to a special node. After the assignment, user can use the node as a modem device.

Attached file is a shell script to create a node for "C-motech" modem. The script produces nodes which mount modem as a serial device. The CDU-550 modem will be mounted on /dev/ttyACM# where # is a number, for example, /dev/ttyACM2.

Code:
#!/bin/bash
# usb : acm
echo -e "\033[32mMake Modem Device\033[0m"
for i in `seq 0 2` ; do
   mknod /dev/ttyACM$i c 166 $i
done

echo -e "\033[32mMake Dual Mode Device\033[0m"
for i in `seq 0 2` ; do
   mknod /dev/ttyUSB$i c 188 $i
done

echo -e "\033[32mMake driver rule\033[0m"
/sbin/modprobe usbserial vendor=0x16d8 product=0x5511
/sbin/modprobe usbserial vendor=0x16d8 product=0x5512
/sbin/modprobe usbserial vendor=0x16d8 product=0x5513
/sbin/modprobe usbserial vendor=0x16d8 product=0x5521
/sbin/modprobe usbserial vendor=0x16d8 product=0x5522
/sbin/modprobe usbserial vendor=0x16d8 product=0x5523
/sbin/modprobe usbserial vendor=0x16d8 product=0x5531
/sbin/modprobe usbserial vendor=0x16d8 product=0x5532
/sbin/modprobe usbserial vendor=0x16d8 product=0x5533
/sbin/modprobe usbserial vendor=0x16d8 product=0x5541
/sbin/modprobe usbserial vendor=0x16d8 product=0x5542
/sbin/modprobe usbserial vendor=0x16d8 product=0x5543
/sbin/modprobe usbserial vendor=0x16d8 product=0x5551
/sbin/modprobe usbserial vendor=0x16d8 product=0x5552
/sbin/modprobe usbserial vendor=0x16d8 product=0x5553
/sbin/modprobe usbserial vendor=0x16d8 product=0x5561
/sbin/modprobe usbserial vendor=0x16d8 product=0x5562
/sbin/modprobe usbserial vendor=0x16d8 product=0x5563
/sbin/modprobe usbserial vendor=0x16d8 product=0x6011
/sbin/modprobe usbserial vendor=0x16d8 product=0x6012
/sbin/modprobe usbserial vendor=0x16d8 product=0x6013
/sbin/modprobe usbserial vendor=0x16d8 product=0x6021
/sbin/modprobe usbserial vendor=0x16d8 product=0x6022
/sbin/modprobe usbserial vendor=0x16d8 product=0x6023
/sbin/modprobe usbserial vendor=0x16d8 product=0x6511
/sbin/modprobe usbserial vendor=0x16d8 product=0x6512
/sbin/modprobe usbserial vendor=0x16d8 product=0x6513
/sbin/modprobe usbserial vendor=0x16d8 product=0x6521
/sbin/modprobe usbserial vendor=0x16d8 product=0x6522
/sbin/modprobe usbserial vendor=0x16d8 product=0x6523
/sbin/modprobe usbserial vendor=0x16d8 product=0x6531
/sbin/modprobe usbserial vendor=0x16d8 product=0x6532
/sbin/modprobe usbserial vendor=0x16d8 product=0x6533
/sbin/modprobe usbserial vendor=0x16d8 product=0x6541
/sbin/modprobe usbserial vendor=0x16d8 product=0x6542
/sbin/modprobe usbserial vendor=0x16d8 product=0x6543
/sbin/modprobe usbserial vendor=0x16d8 product=0x6551
/sbin/modprobe usbserial vendor=0x16d8 product=0x6552
/sbin/modprobe usbserial vendor=0x16d8 product=0x6553
/sbin/modprobe usbserial vendor=0x16d8 product=0x6561
/sbin/modprobe usbserial vendor=0x16d8 product=0x6562
/sbin/modprobe usbserial vendor=0x16d8 product=0x6563

---

### Post by thomasbaker on 2007-09-24
did you get this to work?  I also have a cdu-550 card that i would like to use in ubuntu.

---

### Post by darkwave80 on 2007-10-05
Nope not this card, but I did get the verizon USB one to work , its very very easy.

Plug it in, it will make a device called ttyUSB0

but if you have KPPP or a dialer that has auto detect then it will find it.

Alltells one unless the above code can be figured out dont seem to work to easy.

but the verizon 720 one is awesome!!

---

### Post by Jewfro_Macabbi on 2007-12-08
I was able to get my CDU 550 - Alltel version working using the above code.

Copy the code, and paste it into gedit (or the text editor of your choice). Save the file as a shell script - filename.sh

open up a terminal and cd into the directory where you saved the script. make it executable:

sudo chmod a+x filename.sh 

run the script:

sudo sh ./filename.sh

It will give you some output. The modem should now work - and can be configured via networking panel.

---

