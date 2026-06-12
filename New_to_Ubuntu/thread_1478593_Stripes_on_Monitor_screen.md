---
title: "Stripes on Monitor screen"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by phil66 on 2010-05-09
Dell 2007 fp monitor
Ubuntu Lucid 10.04
Nvidia 7900gs

Setting up Lucid 10.04

I downloaded and install the recommend Nvidia driver from hardware drivers

I rebooted when told to do so
Now my monitor has multicolored vertical stripes 
The program will not boot

Lucid working before I added the recommend Nvidia driver

How do I get into Lucid to remove and install another driver.

Ray

---

### Post by TheNerdAL on 2010-05-09
I'm guessing this happened after you updated the drivers, right?

---

### Post by phil66 on 2010-05-09
> **TheNerdAL said:**
> I'm guessing this happened after you updated the drivers, right?

After downloading I rebooted and the Monitor went directly to having stripes.

Have not been able to get back into Lucid

---

### Post by TheNerdAL on 2010-05-09
> **phil66 said:**
> After downloading I rebooted and the Monitor went directly to having stripes.

Have not been able to get back into Lucid

This might help: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by phil66 on 2010-05-10
Please help Ubuntu completely down

---

### Post by ankspo71 on 2010-05-10
Hi,
Try booting into recovery mode and choosing "failsafeX". To get to recovery mode try holding down the right shift key as ubuntu starts. Your grub menu will display and there you can select the recovery mode. Then a bright blue screen will appear with the recovery options. Choose failsafeX first.

If and when you get to a black screen asking for a username, enter your username and password. If nothing happens after that, type **startx**. But if it returns you to the recovery menu, choose "start ubuntu normally" (which should still be in failsafeX mode). 

Now ubuntu should boot with a generic graphic display and you should be able to go to the hardware driver manager and uninstall the bad driver.

If failsafeX doesn't work then it might be possible to start a root shell and uninstall the drivers by commands.

```
sudo apt-get remove nvidia-current
```

Hope this helps.

---

### Post by lkraemer on 2010-05-10
I had the same type thing happen on Ubuntu 8.04.4 when I installed
the drivers listed under Hardware Drivers.  My choice was to download
the latest Nvidia drivers from their site for my Video Card.

Try the information in this link:
[http://ubuntuforums.org/showthread.php?t=1474284](http://ubuntuforums.org/showthread.php?t=1474284)

Once you get the proper Nvidia drivers downloaded and installed for
your Video Card you shouldn't have any trouble getting the video 
resolution you want.

Or you can use Synaptics and search for nvidia-glx where you will find
nvidia-glx-96
nvidia-glx-173
nvidia-glx-180
nvidia-glx-185
and you can highlight one choice and look at the cards it supports,
and install it with Synaptics.

lk

---

### Post by phil66 on 2010-05-10
Hey Guys

Thanks for the rely's and suggestions
Tried everyone of them plus others
Nvidia 195 driver screwed everything up and would not correctly delete

So I delete 10.04 and reinstalled 
Used Nvidia 173 this time

All systems up and running

Thanks

---

