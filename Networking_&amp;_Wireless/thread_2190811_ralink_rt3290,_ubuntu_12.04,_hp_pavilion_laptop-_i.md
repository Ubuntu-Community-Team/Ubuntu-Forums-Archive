---
title: "ralink rt3290, ubuntu 12.04, hp pavilion laptop- i can't change the wlan0 channel"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by hafiz043 on 2013-11-29
Hai! I have a problem to change the wlan0 channel. It was said by changing the channels can help to fix slow internet connection (i am using my university's wifi).
when i tried to change the channel i got this output:

```
deen@deen-HP-Pavilion-g4-Notebook-PC:~$ sudo iwconfig wlan0 channel 1Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Device or resource busy.
```

How to solve it?  
(sorry for my poor grammar)

---

### Post by varunendra on 2013-12-01
Welcome to the forums hafiz!

Changing channels is something that is done in the router/access-point itself, not at the wifi card or driver. You certainly can't do that on a router that you don't own or have admin access to. But there may be other workarounds to the problem you are facing. To determine if there are any that you may try, we need a detailed information about your wireless setup.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It should give us enough info to figure out a solution or workaround if it is possible.

---

### Post by hafiz043 on 2013-12-03
Hai Varunendra! Thanks for the reply..
This is my attachment:

[ATTACH=CONFIG]248297[/ATTACH]

---

### Post by varunendra on 2013-12-03
The only option you can try with your current driver is to disable hardware encryption (thus shifting it over to 'software encryption'). Please try this -
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800pci.conf
```

This will create a .conf file that will make the driver load with "nohwcrypt=Y" option each time. For this change to take effect, either reboot, or do -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci
```
If this seems to help, nothing more is needed. If not, also try setting "IPv6" in Network Manager to "Ignore". Additionally, you can permanently disable it by following [post=12640479]this post[/post].

If none of these help, you may try installing the proprietary driver for this card by following this post by praseodym : [http://ubuntuforums.org/showthread.php?p=12862284](http://ubuntuforums.org/showthread.php?p=12862284)

---

### Post by hafiz043 on 2013-12-03
The channel is still the same. I think, I need to give up. :)

---

### Post by varunendra on 2013-12-03
I didn't say any of that would change the channel. That is set by the router and the router is not under 'Your' control.

The changes and the alternative suggestions in the linked thread were supposed to possibly help despite the non-optimal channel and encryption. Did you try the proprietary driver as well? If yes, and it didn't help, feel free to post in that thread where praseodym posted about that driver, since you have the same card.

---

### Post by hafiz043 on 2013-12-04
I thought it was for changing the channel. I misunderstood. 
So I tried to do the modprobe again, and checked the down speed. It seems good but not as good as the connection in Windows(when I compared with my friend's laptop).
Do you think my problem is solved? 



I also tried to  install the proprietary of the driver but got an error at dkms build:
```
deen@deen-HP-Pavilion-g4-Notebook-PC:~$ sudo dkms build -m Ralink_3290sta -v 2.6.0.0

Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' -C src/ all.................(bad exit status: 2)
ERROR (dkms apport): binary package for Ralink_3290sta: 2.6.0.0 not found
Error! Bad return status for module build on kernel: 3.8.0-34-generic (x86_64)
Consult /var/lib/dkms/Ralink_3290sta/2.6.0.0/build/make.log for more information
```


I read the make.log but I didn't understand :grin:

---

### Post by varunendra on 2013-12-04
Solved or not depends upon whether the speed and connection's stability are satisfactory or not. "Not as good as windows" isn't a good enough description for us here to make a personal opinion on that, don't you think so? :)

You can perform some online speed test and post its result or if you can post the comparative speeds of your connection and your friend's while downloading something or a similar activity, only then I can formulate an opinion on whether you can expect more or not from your card.

As for the proprietary driver, I believe that dkms package is a creation of praseodym himself, so he would be your best help with that. Post in that thread or PM him to look at the error you got.

I don't have much experience with dkms, so if I have to help with that, I'd suggest to install the plain, vanilla driver from Ralink's official site which you'll need to compile each time a kernel upgrade occurs. On the other hand, the benefit of using praseodym's package is that it will compile itself automatically whenever a kernel upgrade happens. I suggest you PM him and if he doesn't have time to look at your thread (sometimes we do get too busy to be able to reply back), I'd be glad to help as long as I have enough time. :)

The proprietary driver is never 'guaranteed' to perform better than the native one, but if the current driver is unable to give you a decent performance, the proprietary one may be worth a try.

---

### Post by hafiz043 on 2013-12-04
> **varunendra said:**
> Solved or not depends upon whether the speed and connection's stability are satisfactory or not. "Not as good as windows" isn't a good enough description for us here to make a personal opinion on that, don't you think so? 

Yes, I think so. Apologize me.. hehe.


Anyway, I'm glad that I still can connect to the network while others can't. I'm also wondering why my "Ubuntu" can connect to the network but not for the "Windows"


> **varunendra said:**
> 
[COLOR=#000000]The proprietary driver is never 'guaranteed' to perform better than the native one, but if the current driver is unable to give you a decent performance, the proprietary one may be worth a try.
[/COLOR][COLOR=#000000]
I will take note for that.[/COLOR]

---

### Post by hafiz043 on 2013-12-04
> **varunendra said:**
> Solved or not depends upon whether the speed and connection's stability are satisfactory or not. "Not as good as windows" isn't a good enough description for us here to make a personal opinion on that, don't you think so? 

Yes, I think so. Apologize me.. hehe.


Anyway, I'm glad that I still can connect to the network while others can't. I'm also wondering why my "Ubuntu" can connect to the network but not for the "Windows"(I installed both)


> **varunendra said:**
> 
[COLOR=#000000]The proprietary driver is never 'guaranteed' to perform better than the native one, but if the current driver is unable to give you a decent performance, the proprietary one may be worth a try
[/COLOR][COLOR=#000000]
I will take note for that.[/COLOR]

---

### Post by varunendra on 2013-12-04
> **hafiz043 said:**
> I'm also wondering why my "Ubuntu" can connect to the network but not for the "Windows"(I installed both).

You mean Windows on the same laptop is unable to connect to the same network? If so, it maybe due to a wrong driver or improper settings, because almost all the devices and their drivers are designed with special care to make sure they work on windows.

Maybe ask on a Windows forum to get help with that. My wifi troubleshooting skills on windows are extremely limited.

---

