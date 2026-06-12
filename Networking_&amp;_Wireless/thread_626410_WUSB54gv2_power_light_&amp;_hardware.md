---
title: "WUSB54gv2 power light &amp; hardware"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by Wag on 2007-11-29
I followed the directions with regard to "how to" install the drivers for WUSB54gv2, and they are installed. But, Ubuntu does not see the hardware, when its pluged in, and the power light does not come on, when the card is plugged in.. Thanks in advance for the help.

---

### Post by Digger78 on 2007-11-29
What is the output of 

```
ndiswrapper -l
```

---

### Post by Wag on 2007-11-29
wusb54gsv2 : Driver installed

---

### Post by Digger78 on 2007-11-29
Thats all it says?

Are you sure the card works?

---

### Post by Wag on 2007-11-29
Yes the card works.. I have the HD partitioned with vista and Ubuntu. The card works on the vista side, but I had to install the drivers for Ubuntu using this forum; and the card isn't seen, nor does the power light come on, even though the drivers are installed.

---

### Post by wieman01 on 2007-11-29
Please post the results of:
> sudo iwlist scan

---

### Post by Wag on 2007-11-29
reply was...

lo   Interface doesn't support scanning.

eth0  Interface doesn't support scanning.

---

### Post by Digger78 on 2007-11-29
Did you "load" ndiswrapper?

```
sudo modprobe ndiswrapper
```

---

### Post by Wag on 2007-11-29
Yes it is set.

---

### Post by wieman01 on 2007-11-29
Please perform these steps, restart the PC, and do another scan:
> sudo depmod -a
sudo modprobe ndiswrapper
> echo 'ndiswrapper' | sudo tee -a /etc/modules
> sudo ndiswrapper -m
Have you blacklisted the native Linux driver?

---

### Post by Wag on 2007-11-29
I did all those commands and all were ok until 

sudo ndiswrapper -m 

 reply was

module configuration already contains alias directive

I did blacklist the native driver and here is the forum I followed to get the drivers installed

[http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GSC+device](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GSC+device)

maybe that will help?

---

### Post by wieman01 on 2007-11-29
Please post:
> sudo gedit /etc/network/interfaces

---

### Post by wieman01 on 2007-11-29
> **Wag said:**
> I did all those commands and all were ok until 

sudo ndiswrapper -m 

 reply was

module configuration already contains alias directive

I did blacklist the native driver and here is the forum I followed to get the drivers installed

[http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GSC+device](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GSC+device)

maybe that will help?
Oh oh... you have got version 2. That does matter. You might have another chipset and driver...

---

### Post by Wag on 2007-11-29
I double checked to make sure I had the native driver blacklisted, and I didn't. So, I blacklisted it, and then it wouldn't boot, so I removed the usb card; and then it booted, but then when I pluged it back in the laptop froze. Why would blacklisting the native driver do that?

---

### Post by Wag on 2007-11-29
sudo gedit /etc/network/interfaces

dialog box said

auto lo

iface lo inet loopback

iface eth0 inet dhcp

auto eth0

---

### Post by wieman01 on 2007-11-29
Are you on a 64-bit system? And are you running Ubuntu 64-bit by chance?

---

### Post by Wag on 2007-12-01
sorry I had to go out of town unexpectly.. I am running i386.

---

### Post by Wag on 2007-12-03
It's been a while since anyone posted on this thread.... I still have the issue and trying to figure it out... Should I declare this thread closed, since no one is really responding?

---

### Post by wieman01 on 2007-12-03
There is a Ralink tutorial shown in my signature which should work for you as well. Could you please check and see what steps you might have missed? I believe we are close, it's just that something is missing... Any idea?

---

### Post by Wag on 2007-12-03
OK I will check now

---

### Post by Wag on 2007-12-03
I went through each step, and I added all of those to my blacklist. And I added the wlan0, and now its not freezing up, when I plug in the USB card (woohoo); but the power light still isn't on, and the hardward isnt seen by niswrapper -l it still says wusb54gv2: driver installed. getting closer!

---

### Post by Wag on 2007-12-03
I attempted a reboot, with the card in the USB slot, and it froze again and wouldnt boot.. I thought I had had the wrong drivers in the blacklist, but I added all of the drivers that last time... Do you think the laptop freezing up when the USB card is plugged in is related it not being seen by ndiswrapper -l ?

---

### Post by Wag on 2007-12-03
In addition, when I plug in the USB card, after the boot, it freezes up...

---

### Post by wieman01 on 2007-12-03
> **Wag said:**
> I attempted a reboot, with the card in the USB slot, and it froze again and wouldnt boot.. I thought I had had the wrong drivers in the blacklist, but I added all of the drivers that last time... Do you think the laptop freezing up when the USB card is plugged in is related it not being seen by ndiswrapper -l ?
Yes, it is possible. I think you are probably blacklisting the wrong driver. Plus I believe that you have deployed the wrong Windows driver, is that a possibility? Have you used the one from Linksys' website?

I don't know what driver is loaded by default in your case. The only way you can find out is by installing the right Windows driver, then running "ndiswrapper -l". It should say that you have installed the driver correctly and should also mention that Linux driver (in bracket).

---

### Post by Wag on 2007-12-03
On this forum ...... 


[http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GSC+device](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GSC+device)

It says to use the 2kdriver on step #3. Is that wrong? When I issue the command ndiswrapper -l I get driver installed and nothing else. In addition, when I followed the forum listed above everything works as the forum says it should until step #5 under sudo modprobe ndiswrapper.. after that nothing works.. Thanks for the feed back you have been giving me so far, btw.

---

### Post by wieman01 on 2007-12-04
I don't think you have a WUB54G[COLOR="Red"]**S**[/COLOR] but a WUSB54G, right? Could you check please? I think you might be using the wrong driver.

Here is a list of compatible cards:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

_**EDIT:**_
Since "ndiswrapper -l" yields nothing, I believe the driver is not the right one. It also seems odd that you should use the Win2000 one, but I don't know... What chipset is your card? Broadcom?

---

### Post by Wag on 2007-12-04
On the bottom of the card it says WUSB54GS ver 2.1

---

### Post by Wag on 2007-12-04
the chipset is 13b1:0014

---

### Post by Wag on 2007-12-04
It seems I am not the only one with this issue look at this..

[http://ubuntuforums.org/showthread.php?t=225206&page=20](http://ubuntuforums.org/showthread.php?t=225206&page=20)

but I don't see how they corrected it?

---

### Post by wieman01 on 2007-12-04
They have included drivers there... Could you try those? I think your's defective somehow.

---

### Post by Wag on 2007-12-04
Ok, I am going to delete all the files,start over, and see if it was a defective driver. I attempted to use the rt73 driver listed on the other thread, but it didn't work. Didn't it seem they were having the same issue as me? Their computer(s) crashed when they pulged in the USB card. Thanks again for the help thus far!

---

### Post by Wag on 2007-12-05
OK I deleted all the file and in the ndiswrapper dir

> 
sudo make uninstall
make
sudo make install


Then 
> sudo ndiswrapper -m

Next, I downloaded the file from 

[http://www.belkin.com/support/downlo...ad=1871&lang=1](http://www.belkin.com/support/downlo...ad=1871&lang=1)

I unziped it then

> 
unshield x DATA1.CAB
unshield x DATA2.CAB

 
then I downloaded the Linksys v2 exe and for the card and 

> 
unzip WUSB54GS_20050428.exe
sudo ndiswrapper -i WUSB54GSv2.inf
sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsv2/
sudo cp rndismp.sys /etc/ndiswrapper/wusb54gsv2/
ndiswrapper -l


it returned wusb54gsv2 : driver installed

then I 

> 
sudo modprobe ndiswrapper


then I pluged in the USB card and the laptop froze up like before so I had to 

> 
Ctrl+Alt+SysRq+S
Ctrl+Alt+SysRq+U
Ctrl+Alt+SysRq+B


=) at least im learning? Trying to find something good about this!

---

### Post by wieman01 on 2007-12-05
Ok, here is another suggestion, Wag. Download 'ndiswrapper' from [here]("http://sourceforge.net/projects/ndiswrapper/") and compiled it from source. As the driver does not seem to be the issue (or let's say I begin to believe that), it could have to do with the version of 'ndiswrapper' that is in the repositories. I have seen it all before.

Do you know how to compile your own stuff?

---

### Post by Wag on 2007-12-05
OK I will let you know soon as I finish compiling it and have everything reinstalled.

---

### Post by wieman01 on 2007-12-05
> **Wag said:**
> OK I will let you know soon as I finish compiling it and have everything reinstalled.
Sorry, you have to go through such a hassle, but in rare cases (like yours) that is necessary. Stay with us, once wireless is fixed you'll enjoy it much more.

---

### Post by Wag on 2007-12-05
Thanks for the encouragement! Before I was using ndiswrapper 1.49 but I went to the link and downloaded ndiswrapper 1.5 and went through the same steps as before. However I had the same result minus the laptop freezing up. 

as far as the driver I have now tried to get it 4 different ways

#1 I got it off the linksys installation cd

#2 downloaded the exe from their site

#3 install it with wine and then retrieved it from the wine system dir

#4 I copied it from my vista partition onto the ubuntu side...

and with each driver I went through all the steps, but with the same result.
since 99% of all computer problems are user error i'm sure its something i'm doing or not doing I just don't know what.. but again thank you for helping with me on this and giving me direction!

---

### Post by wieman01 on 2007-12-05
After having gone throught is once again could you please post:
> sudo iwlist scan

---

### Post by Wag on 2007-12-05
It returned 

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

---

### Post by wieman01 on 2007-12-05
Man... I don't know what else we can try, seriously. I don't understand why this adapter is such a nightmare to configure. Have you got any other smart ideas?

---

### Post by Wag on 2007-12-06
I am going to keep working with it... half the fun of ubuntu is learning right?? So I am going to try to have fun =)... If I ever manage to figure it out I will post "how to" here.. in case im not the only one having this type of issue... And thank you for all your help!

---

### Post by wieman01 on 2007-12-06
> **Wag said:**
> I am going to keep working with it... half the fun of ubuntu is learning right?? So I am going to try to have fun =)... If I ever manage to figure it out I will post "how to" here.. in case im not the only one having this type of issue... And thank you for all your help!
No problem, welcome, dude. Hope you'll succeed and have lots of fun (as much as I have at least). :-)

---

