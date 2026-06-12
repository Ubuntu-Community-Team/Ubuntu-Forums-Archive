---
title: "New user Wifi issue"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Cameron Murray on 2010-08-23
I've just set up a dual boot Vista/ Ubuntu Dell Inspiron 1545 laptop. I'm afraid I've only run Ubuntu for a few hours now so I'm a total novice with this OS.

I tried using the hardware driver tool (preinstalled with the OS) to find the driver, it poped up with two Broadcom drivers, I tried both but I found that neither were compatible with my wireless network card. 

Then after trailing through a few forums and yahoo answers, I discovered the Windows wireless driver tool. I downloaded it and set it up. I managed to connect to my network. Wifi started working normally (as far as I know). 

After a reboot, I discovered I couldn't find any networks,  I tried reinstalling the driver with the windows wireless driver tool, as before. This time it still came up with  "hardware present" although I still can't see any wireless networks. 

When I go into the wireless tab in network options, I can see the name of my network (accessed an hour ago). 

I have found a thread on this site who says he/ she had issues with making Ubuntu recognise the wireless card on the same laptop I am using.

The laptop does have a wireless button (enable/ disable) although I find no effect after pressing.

I'm afraid I'm a total novice, I may be doing something very trivial wrong, any help or advice would be much appreciated. 

Cheers
 Cameron Murray

---

### Post by redbook4574 on 2010-08-23
> **Cameron Murray said:**
> I've just set up a dual boot Vista/ Ubuntu Dell Inspiron 1545 laptop. I'm afraid I've only run Ubuntu for a few hours now so I'm a total novice with this OS.

I tried using the hardware driver tool (preinstalled with the OS) to find the driver, it poped up with two Broadcom drivers, I tried both but I found that neither were compatible with my wireless network card. 

Then after trailing through a few forums and yahoo answers, I discovered the Windows wireless driver tool. I downloaded it and set it up. I managed to connect to my network. Wifi started working normally (as far as I know). 

After a reboot, I discovered I couldn't find any networks,  I tried reinstalling the driver with the windows wireless driver tool, as before. This time it still came up with  "hardware present" although I still can't see any wireless networks. 

When I go into the wireless tab in network options, I can see the name of my network (accessed an hour ago). 

I have found a thread on this site who says he/ she had issues with making Ubuntu recognise the wireless card on the same laptop I am using.

The laptop does have a wireless button (enable/ disable) although I find no effect after pressing.

I'm afraid I'm a total novice, I may be doing something very trivial wrong, any help or advice would be much appreciated. 

Cheers
 Cameron Murray


By windows driver tool, do you mean ndiswrapper??

---

### Post by Cameron Murray on 2010-08-23
Yes, its labeled Windows Wireless Driver Tool in the menu, but that is the software I downloaded.

Thanks for the reply.

---

### Post by beew on 2010-08-23
Take a look at

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

and 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

There should be a better way than to use ndiswrapper for the newer broadcom cards (and also some legacy ones, see the first link)

---

### Post by bkratz on 2010-08-23
> **Cameron Murray said:**
> I've just set up a dual boot Vista/ Ubuntu Dell Inspiron 1545 laptop. I'm afraid I've only run Ubuntu for a few hours now so I'm a total novice with this OS.

I tried using the hardware driver tool (preinstalled with the OS) to find the driver, it poped up with two Broadcom drivers, I tried both but I found that neither were compatible with my wireless network card. 

Then after trailing through a few forums and yahoo answers, I discovered the Windows wireless driver tool. I downloaded it and set it up. I managed to connect to my network. Wifi started working normally (as far as I know). 

After a reboot, I discovered I couldn't find any networks,  I tried reinstalling the driver with the windows wireless driver tool, as before. This time it still came up with  "hardware present" although I still can't see any wireless networks. 

When I go into the wireless tab in network options, I can see the name of my network (accessed an hour ago). 

I have found a thread on this site who says he/ she had issues with making Ubuntu recognise the wireless card on the same laptop I am using.

The laptop does have a wireless button (enable/ disable) although I find no effect after pressing.

I'm afraid I'm a total novice, I may be doing something very trivial wrong, any help or advice would be much appreciated. 

Cheers
 Cameron Murray

Well, if you have tried both the recommended Broadcom wifi driver and also ndiswrapper you may actually have two competing drivers trying to access the same card. I am surprised the Broadcom drivers didn't work for you, but glad you got it working with ndiswrapper.

Regarding the button you might look at ( in the terminal---Applications>>Accessories>>terminal ) and see it it shows "hard-blocked" that would indicate that the switch is not "on".

```
rfkill list
```


You might also want to copy/paste the outputs received from the following back here using # ( code tags) for ease of reading:

```
lspci | grep Wireless 
sudo lshw -C network
lsmod
ndiswrapper -l

```


the l's above are lowercase L's not 1's>  The sudo command will require your password which will not be echoed (not even ***) back to you-just press enter when done.

---

### Post by Cameron Murray on 2010-08-23
Now I believe the problem was the windows wireless driver, conflicting with the reccomended broadcom driver.  After removinging the windows driver and uninstalling and reinstalling the broadcom. 

Now my only issue is that whenever I log off the broadcom driver becomes inactive, I have to reinstall the driver when ever I log on with the hardware driver tool. A little annoying but there you go. 

I am now online on Ubuntu thanks to you. =) 

Much appreciated.
Cameron Murray

---

