---
title: "How to for Sprint Compass 597"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by super61 on 2008-10-17
Alright, well heres what you need to have, 

[COLOR="Red"]I must warn that the max down is 500kbps so be aware it will not be as fast as it would on a regular windows or mac computer.  [/COLOR]

Ubuntu 8.07 Hardy
KPPP
Please make sure that the USB adapter is already activated on a windows based OS and calmed working. 

and that it. Im sorry for not Putting screen shoots. Ill add them later when i have time. 

So install KPPP and insert the USB adapter into any usb serial. 

Open your terminal program and type the following and you should get what comes afterward. 

sudo modprobe -r usbserial

[sudo] password for ___: 

FATAL: Module usbserial is in use.


this is what you should get with this, After this command do this one and you should get this following. 

____@ubuntu:~$ sudo modprobe usbserial

____@ubuntu:~$ sudo dmesg|grep -i ttyUSB

[   47.061361] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB0

[   47.061585] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB1

[   47.061720] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB2


After open KPPP and go as followed. 

For KPPP go to configure and hit manual. and on the account. Under connection name you can put anything but I just Put EVDO connection. On the side hit add and as a number put #777 and then click OK

Now click on the modems tab and click new.  And under modem name put anything. I put Seirra Wireless.  As for Modem device it should be /dev/ttyUSB0  Once done go to the Modem tab and click Quey Modem. You should get a list of ATI if about 8 lines or code. If you get this then it is work properly. Now click OK on both windows so your at the main Window and make sure that the Connect to is the Connection you have made for your modem which mine is EVDO connection. As for login and password use anything. It does need a login but the program needs it so put anything. 

You should get a connection box that show the time or running and as for signal it should say nothing. 
Now, if you try a web application it wont work. We have one more thing to do, go to the Network config and for the Wired connection go in and disable roaming and as for a connection put DHCP and save settings. Now open up Firefox or anything else and There you go! Enjoy your new wireless internet. 

I must warn that the max down is 500kbps so be aware it will not be as fast as it would on a regular windows or mac computer.  

Please post feedback and I will try and help with anything I can.      

                  super61

---

### Post by Tom.Servo on 2008-11-06
VERY helpful! Thank you SO much! I had to end up using Gnome PPP as KPPP was crashing, and I had to change permissions on the etc folder, but I have it working now!

---

### Post by MizzleDizzle on 2008-11-18
Just wanted to say thanks works like a charm. I did however do a speedtest from speakeasy.net and got back 1850 download and 450 up. You may not be within REV A coverage

---

### Post by Tom.Servo on 2008-11-18
FYI. I have found as of Intrepid 8.10, you can add your 597(And a few other Wireless Broadband devices) via your network manager with only a few steps See [this]("http://ubuntuforums.org/showthread.php?t=963529") post for details.

---

