---
title: "dell d610 wireless not working"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by josephmills on 2011-02-06
before you go any further I would like to say, that on a scale of 1 to 10 (1 low 10 high)my skill level is a 1, That said here the problem.  The wireless wont work on my dell latitude d610, So I have looked all over the place for help on this and am at my wits end. Here is what I am working with 

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I tried to blacklist this and find a windows driver but to no luck, all of the links for them I have found are bad. 

these are some links to which I have been trying to use for help.

[http://www.linuxquestions.org/questions/showthread.php?p=2736853](http://www.linuxquestions.org/questions/showthread.php?p=2736853)

[http://en.community.dell.com/support-forums/software-os/f/3525/p/18470288/18593279.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/p/18470288/18593279.aspx)
 
[http://ubuntuforums.org/showthread.php?t=133149](http://ubuntuforums.org/showthread.php?t=133149)

here are some of subject  that I am confused about (?could of messed up?) 
1) blacklisting items 
2) ndiswrapper 
3) being the root 
4) some program also downloaded (auto)called firmware b4 

well any help is good help at this point thanks for your time

---

### Post by bkratz on 2011-02-06
The B43 driver should work for your card. The threads you are following are pretty old!  Try this one.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by josephmills on 2011-02-06
ok so here is where I am STA - Internet access
Step 1.

Install the STA hybrid drivers/firmware from the restricted repository using the Software Centre or the Synaptic Package Manager (Under the desktop menu System > Administration > Synaptic Package Manager) and search for the bcmwl-kernel-source package and install or in a terminal (under the desktop menu Applications > Accessories > Terminal) issue the following commands:


~$ sudo apt-get update
~$ sudo apt-get install bcmwl-kernel-source
Step 2.

Under the desktop menu System > Administration > Hardware/Additional Drivers, the STA drivers can be activated for use.

Note: A computer restart may be required before using the wifi card.

LiveCD/LiveUSB
For temporary use with the LiveCD and LiveUSB environments, simply use the Software Centre or the Synaptic Package Manager to search for and install the bcmwl-kernel-source package. Refer to Step 1 and Step 2 of the instructions above.


after this point when I try my wireless nothing. Could it because I blacklisted it? If so then how do I reverse that? thanks again for your time

---

### Post by bkratz on 2011-02-06
Why aren't you looking at the B43 section of the thread? It says it is for the BCM4318

quote


Installing b43 drivers
8.04 (Hardy Heron), 9.10 (Karmic Koala), 10.04 (Lucid Lynx), 10.10 (Maverick Meerkat)
Supported models include:

BCM4301 BCM4306/2, BCM4306/3, BCM4311, BCM4312, BCM4318, BCM4320

---

### Post by josephmills on 2011-02-06
Ok so I am this far...

Step 1.

Install the STA hybrid drivers/firmware from the restricted repository using the Software Centre or the Synaptic Package Manager (Under the desktop menu System > Administration > Synaptic Package Manager) and search for the bcmwl-kernel-source package and install or in a terminal (under the desktop menu Applications > Accessories > Terminal) issue the following commands:


~$ sudo apt-get update
~$ sudo apt-get install bcmwl-kernel-source
Step 2.

Under the desktop menu System > Administration > Hardware/Additional Drivers, the STA drivers can be activated for use.

Note: A computer restart may be required before using the wifi card.





every thing looks good and under System > Administration > Hardware/Additional Drivers, it says that the driver is activated and in use.
But I still dont get any wireless.do I have to enable my wireless now and if so could someone send me a link or walk me though it thanks 
thanks again for your time

---

### Post by PRC09 on 2011-02-06
As posted above,why are you trying to use the STA driver?? I have a Dell d610 and it works fine with the b43 driver.......

---

### Post by josephmills on 2011-02-06
ok so what do I do then should I uninstall things then or where do I go from here

---

### Post by PRC09 on 2011-02-06
Just took a quick look at the links you have followed unless you know what files you have altered or blacklisted and what other files you have changed I dont know if you will get this straightened out without a great deal of difficulty.I personally would just re-install the OS again and follow the guide for the b43 install as in post#2.Assuming you have a hardwire connection,after the install check under system > admin > additional drivers and the driver should be there to activate.IF not, do whatever updates are available and then check again for the driver.Sorry I cant be more helpfull than re-install......

---

### Post by josephmills on 2011-02-06
ok so I re-installed ubuntu and started working on the driver I typed in 


sudo apt-get install b43-fwcutter

and got this 



Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
b43-fwcutter set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 260 not upgraded. 



the part of the "text" I dont understand is the line ,b43-fwcutter set to manually installed. 

how do I manually install it? or do I ?

thanks again

---

### Post by PRC09 on 2011-02-06
Are you cabled in and did you check under System > Administration > Additional Drivers?

---

### Post by josephmills on 2011-02-06
yes my Ethernet cable is plugged, and under 

System > Administration > Additional Drivers 
it says this driver(broadcom b43 wireless driver ) is activated and currently in use.  but I cant enable wireless still. I tryed restarting  


and looked in 
System> Administration > Synaptic Package Manager 
I go to the "search bar" and type in Broadcom and these are the packages that are used 

b43-fwcutter

*Not Used *
bcmwl-kernal-source 
bcm5700-source
broadcom-sta-source
broadcom-sta-common
bcmwl-modaliases



So this is what I am guessing I have to check(install)bcmwl-kernal-source and restart computer Am I on the right track?
thanks again for your time

---

### Post by PRC09 on 2011-02-06
Maybe check that the wireless card is turned on by the fn+f2  keys other than that I am at a loss...I will look some more.....

---

### Post by PRC09 on 2011-02-06
When I look under broadcom in Synaptic I have bcmwl-modaliases installed.

---

### Post by waynefoutz on 2011-02-06
> **PRC09 said:**
> When I look under broadcom in Synaptic I have bcmwl-modaliases installed.

I have the same computer. I ONLY have bcmwl-modaliases and bcmwl-kernel-source installed. That's what I have installed and my wireless is working fine. If you go through System/Adminstration/Hardware Drivers, choose the STA driver.

---

### Post by josephmills on 2011-02-06
Winner proc9 thats what it was 
holy cow I over thought that one. countless hours. but boy it feels great. I am having a big old party right now by myself  thanks to all of you that helped me out I really appreciated it. Now to my printer :)

---

### Post by PRC09 on 2011-02-07
Great!!! Sorry couldnt reply,lost internet service while working on this(ironic).ISP fault tho.Glad its sorted.....

---

