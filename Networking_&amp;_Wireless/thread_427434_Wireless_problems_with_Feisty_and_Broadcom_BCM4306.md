---
title: "Wireless problems with Feisty and Broadcom BCM4306"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by jcorlew on 2007-04-29
Trying to get my wireless card to work with Feisty.  I was following the directions on this page: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29)

Got to Step 5 where I was assigning the driver to the card.  Here's the command I entered: 
**ndiswrapper -a 14E4:4320 bcmwl5**

**Output:**
couldn't create symlink for "14E4:4301.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4307.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4321.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf": File exists -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!

Here are the contents of my /etc/ndiswrapper/bcmwl5 directory:

14E4:4301.5.conf  14E4:4320.5.conf  14E4:4324.5.conf  bcmwl5.sys
14E4:4307.5.conf  14E4:4321.5.conf  bcmwl5.inf

Any ideas or pointers?

---

### Post by spd106 on 2007-04-30
What was the output of ```
ndiswrapper -l
```
If it says driver installed, harware present then you won't need to run the command you were getting errors with.

---

### Post by jputman01 on 2007-04-30
i did not use that command to get mine working. try using ```
sudo ndiswrapper -i bcmwl5.inf
```

make sure and do this command from the directory where the driver is stored.

after that run ```
ndiswrapper -l
``` and you should see something to the effect of "driver present, hardware detected"

let us know if that works!

---

### Post by AJL on 2007-04-30
I used [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) to get my 4306 up and running.

---

### Post by jcorlew on 2007-04-30
Thanks for the replies!

AJL:
Here's the output of **ndiswrapper -l**:
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


So it looks like the driver is there, it just doesn't make any difference when trying to use the card :-/

jputman01:I uninstalled the driver and followed your suggestions and got the same results.  Driver looks to install but I can't get it to function:

root@MrPoopy:~/bcm4311# ndiswrapper -i bcmwl5.inf 
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
root@MrPoopy:~/bcm4311# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


Taking a different path, I tried using the fwcutter tool, and got it to work once.  Sadly, after rebooting it was broken again and following the same steps I'm unable to get the connection back.

Here's what I did to get it working:

```

yum -y install bcm43xx-fwcutter
/usr/bin/bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
/sbin/depmod -a
/sbin/modprobe bcm43xx

```

After I did this I was actually able to see the available wireless networks with the NetworkManager Applet, but after a reboot I lost it all.  I tried repeating the commands, and while the wireless network option appears in the NetworkManager, I'm not about to see any available networks or use it to connect.  Also, my wireless light isn't on like it was when it worked the first time.  I'm pretty sure they're related but not sure how to make Ubuntu recognize my card is there and ready to be used.

Thanks so much for your help already, any further assistance will be greatly appreciated.

---

### Post by jcorlew on 2007-04-30
Oh, also I used this page suggested by a coworker to accomplish the above

[http://www.fedoraforum.org/forum/showthread.php?t=102697&highlight=broadcom+bcm43xx-fwcutter](http://www.fedoraforum.org/forum/showthread.php?t=102697&highlight=broadcom+bcm43xx-fwcutter)

---

### Post by AJL on 2007-04-30
jcorlew, if you want to try and use ndiswrapper go back and run 
[B]
sudo modprobe ndiswrapper[/B]

if all of the sudden, your wireless comes to life, go and edit your /etc/modules file and make sure it contains ** ndiswrapper**

---

### Post by AJL on 2007-04-30
I guess the same goes for the firmware module, if you want to use it..

try **sudo modprobe bcm43xx**

if that works, make sure it is in your** /etc/modules** file.

That is a list of modules to load at boot.

---

### Post by jcorlew on 2007-04-30
Hey guys, thanks for the help so far!  I tried both of those, and neither brought the wireless to life.  It really bothers me that it worked for 15 minutes this morning until I rebooted.  The only thing I can think that changed was that I enabled Desktop Effects and turned the Workspaces on a Cube feature on which caused my panels to freak out (flashed a few times and then disappeared) so I rebooted.  When it came back up the wireless was down and hasn't come back since.  So weird.

---

### Post by mattTheNewb on 2007-05-01
Hey, I had the same problem when I upgraded to Feisty. Here's how I fixed it:

1) Make sure bcm43xx is blacklisted: add "blacklist bcm43xx" in **/etc/modprobe.d/blacklist**
2) Make sure ndiswrapper loads at startup: add "ndiswrapper" in **/etc/modules**

Reboot...

That pretty much did it for me. I noticed that my signal is a littler weaker with Feisty than Edgy. Anyone else noticed this?

---

### Post by jcorlew on 2007-05-01
The bcm43xx was already in the blacklist file.  I did add ndiswrapper to /etc/modules and when I rebooted got the same effect as runnung modprobe ndiswrapper.  Here's a screenshot of what I'm seeing:
[IMG]http://www.swingdancenashville.com/screenshot.png[/IMG]

The wireless is showing up in the network manager but it's not available to use.  My wireless light on the front of the machine isn't lit either.

---

### Post by netreg on 2007-05-18
> **mattTheNewb said:**
> Hey, I had the same problem when I upgraded to Feisty. Here's how I fixed it:

1) Make sure bcm43xx is blacklisted: add "blacklist bcm43xx" in **/etc/modprobe.d/blacklist**
2) Make sure ndiswrapper loads at startup: add "ndiswrapper" in **/etc/modules**

Reboot...

That pretty much did it for me. I noticed that my signal is a littler weaker with Feisty than Edgy. Anyone else noticed this?



After trying for hours to get my wireless card working, i eventually tried the above instructions, did a reboot, and it kicked into life...   Thanks Guys.:KS

Just gotta see if i can get it to WPA rather than WEP :)

thanks again
Darren

---

### Post by stchman on 2007-05-18
> **jcorlew said:**
> Trying to get my wireless card to work with Feisty.  I was following the directions on this page: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29)

Got to Step 5 where I was assigning the driver to the card.  Here's the command I entered: 
**ndiswrapper -a 14E4:4320 bcmwl5**

**Output:**
couldn't create symlink for "14E4:4301.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4307.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4321.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf": File exists -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!

Here are the contents of my /etc/ndiswrapper/bcmwl5 directory:

14E4:4301.5.conf  14E4:4320.5.conf  14E4:4324.5.conf  bcmwl5.sys
14E4:4307.5.conf  14E4:4321.5.conf  bcmwl5.inf

Any ideas or pointers?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

This guide is usually right.

---

### Post by 00ber n00b on 2007-06-07
I'm about to start this process with my hp dv1000 it has a bcm 4306 (rev 3) and i was just collecting all of the information and weighing the factors of which path to take.  I was thinking about going the ndiswrapper route because I hear that it gives you a stronger connection.  but if its not the best route to take,  someone let me know why and what are the advantages and disadvantages.

---

