---
title: "Intrepid BCM4318 AcerHK Aspire 5020"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by *g!t5^_)*(H on 2008-11-04
Hi,  
New Ubuntu means new ways to set up wireless. 
These steps worked for me:  

1- Install Intrepid normally 
2- Connect using a wired connection 
3- Update (System>Administration>Update Manager>Check>Install Updates) 
4- Restart computer 
5- Connect again using a wired connection 
6- Activate B43 (System>Administration>Hardware Drivers>Broadcom B43...) 
7- Open a terminal (Applications>Accessories>Terminal) 
8- Get permissions (Type: "[COLOR="DarkOrange"]sudo bash[/COLOR]" and enter your password) 
9- Add acerhk module (Type: "[COLOR="DarkOrange"]echo acerhk >> /etc/modules[/COLOR]") 
10-Turn on wireless when booting (Type: "[COLOR="DarkOrange"]gedit /etc/rc.local[/COLOR]") 

Add "[COLOR="DarkOrange"]echo 1 > /proc/driver/acerhk/wirelessled[/COLOR]" before "exit 0" line 

My "rc.local" file, looks like:  

[COLOR=Green]#!/bin/sh -e 
# # rc.local 
# # This script is executed at the end of each multiuser runlevel. 
# Make sure that the script will "exit 0" on success or any other 
# value on error. 
# # In order to enable or disable this script just change the execution 
# bits. 
# # By default this script does nothing.  
echo 1 > /proc/driver/acerhk/wirelessled 
exit 0[/COLOR]

11 - Restart computer

Done ! I hope this thread helps someone :D

---

### Post by miche11 on 2008-11-05
Thank you, i'll try the procedure as soon as i get a wired connection.
Do you think is it the same procedure for the Hardy here ?
[http://ubuntuforums.org/showthread.php?t=773179&highlight=5020](http://ubuntuforums.org/showthread.php?t=773179&highlight=5020)

Would this procedure go also for Ibex, in order to have a "working" wifi key ?
Thank you again and again

---

### Post by j4ni on 2008-11-05
Nice! Works for my Acer Aspire 5024WLMi. Thanks a lot!

---

### Post by miche11 on 2008-11-05
j4ni, is still working after the reboot or you have to give the command to switch the wifi on ?
or had you already an available script to do that ?

---

### Post by *g!t5^_)*(H on 2008-11-05
Hi

After every new Reboot, the file "/etc/rc.local" will turn on the wireless automatically, using the command "echo 1 > /proc/driver/acerhk/wirelessled".

If you don't want to have wireless ON by default when booting, skip step number 10, but then you will have to turn it ON typing:

sudo echo 1 > /proc/driver/acerhk/wirelessled

See u

(PD: No, is not the same procedure than the one for Hardy Heron, some parts are similar but I think the old procedure doesn't work anymore)

---

### Post by miche11 on 2008-11-05
it works wonderful !!!
thank you !!!
and with a 3023 (yeah, ok, it's i.e. a 5024 with a sempron processor)
a question more: are you using wicd or network manager ?

and now to fix the next issue !!!!

---

### Post by tthorb on 2008-12-31
I had to echo "1" in the file here:

/sys/devices/platform/acer-wmi/

It wouldn't work here: /proc/driver/acerhk/

---

### Post by kiokoman on 2009-01-02
thankyou tthorb i have to do the same to activate my wireless

---

### Post by cathectic on 2009-01-04
Please do not use acerhk on laptops that are supported by acer_acpi (bundled with *buntu 8.04) / acer-wmi (included in the kernel as of 2.6.25, *buntu 8.10 and above).

acerhk is:

1) Not actively maintained
2) Is not as fully featured as acer-wmi
3) Doesn't work on x86-64

All you need to do is, as tthorb pointed out, is add this to rc.local:

echo 1 > /sys/devices/platform/acer-wmi/wireless

(acer-wmi is actively maintained & developed on my Aspire 5020, so it does work rather well on the 5020/ 3020 series, for obvious reasons :)

---

### Post by arm-c on 2009-02-02
For those that have an older Acer that does use the AcerHK driver, you may find my little utility helpful:

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

Contributors welcome.  I am very new to programming and this is my "FIRST" release of anything and contribution to the opensource community.

CARLOS:  Is there a list of what hardware shouldn't use AcerHK?

Warm Regards to All!
ARM-C

---

