---
title: "Uninstall No disk problem"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by debale on 2011-06-30
**Uninstall problem no disk** 
Hi All
 
I am new to this and a dumb blonde when it comes to computers so bare with me!
 
I installed Ubuntu 10.4 approx 1 yr ago (installed within windows but not WUBI and not seperarate partition) it was running side by side with windows quite happily (which I acquired, if you know what I mean) it was only a beta version so has now expired. I, now wish to ditch windows altogether as I am very happy with Ubuntu but, I do not have a windows disk. I also think there is a problem with my pc as it will no longer burn cd/dvd and there are 4 x bad sectors on the disk!!! I do still have a disk with 10.4 version on but, the computer will not boot from the disk?
 
I just start again with a clean slate! I have been searching the net and tried almost everything posted for the past 3 days now!!! I cannot get an option to restore to factory settings, on my pc (Acer Aspire 1650) only to reboot from windows disk (which I do not have) which, is what I am trying to get rid of!!! I just want Ubuntu nothing else!!!
 
Please, help a damsel in distress!!!! Debs:confused:#-o](*,):cry:

---

### Post by frankbooth on 2011-06-30
The easiest way would be, as you said, start from a clean sheet.

[SIZE="3"][COLOR="Red"]**You might want to backup your things before following the instructions below.**[/COLOR][/SIZE]

**1)** Burn a CD with Ubuntu (you might want to stick with 10.04 since it's LTS) or make a [bootable USB-drive]("https://help.ubuntu.com/community/Installation/FromUSBStick").

**2)** Boot the CD/USB (you can usually enter a boot-menu by hitting F12 when your laptop is booting up) and follow the VERY simple installtion of Ubuntu. 

**[COLOR="red"][SIZE="3"]BE CAREFUL WHEN YOU REACH THE PARTITIONER IF YOU HAVE SEVERAL HARD DRIVES![/SIZE][/COLOR]**

---

### Post by debale on 2011-06-30
I have already backed everything up onto external drive.  I am unable to burn a disk due to some corruption I think and the disk I have of Ubuntu 10.4 (which I had burnt previously) pc will not boot from.  I have checked and double checked all the boot options and they are all pointing to cd/dvd boot.:(

---

### Post by no2498 on 2011-06-30
? you try the cd in windows 
linux/ubuntu has a burner just for windows on/at the down load site

---

### Post by debale on 2011-06-30
Tried that too!!!  didn't work!  I think I have a problem with my cd/dvd burner.  There are 4 x bad sectors on my disk and although I can read cd/dvds I am unable to burn, have tried in both OS and with several different burning programmes.

I need to restore to factory settings without a disk!!!  I have managed to download 11.04 into windows (WUBI) but, I want the disk space and speed the system up a bit.:confused:

---

### Post by frankbooth on 2011-06-30
I'm not sure if flashing your BIOS would provide new features such as booting from USB, but you might want to look into it? 

Or just ask one of your friends to burn a CD for you? :)

You're mentioning bad sectors on your HDD, maybe it wouldn't be a bad idea to replace it? But only you really know how damaged it really is, so only you can call that decision.

---

### Post by debale on 2011-06-30
Not sure what flashing BIOS is but, this laptop does not have the facility to boot from USB, I already tried that.  There are 4 bad sectors on the HDD I don't think that is a high, is it?

I have since managed to download Ubuntu 11.04 WUBI style.  So, when I boot I get 3 options now.!!!
Thought I may be able to then format the free space and create a partition put, Ubuntu onto that, then delete the other partition including windows?  When I tried to format the free space, it stated there was an error so, was unable to so,that didn't work either!!!

I am beginning to think I need a new pc but, I do not want to buy one unless I really have to (due to lack of funds) and if I do really have to purchase a new one I do not want to pay for Windows either lol

Any other suggestions or advice, would be gratefully received.  

Debs:rolleyes::-k

---

### Post by wildmanne39 on 2011-06-30
> **debale said:**
> Not sure what flashing BIOS is but, this laptop does not have the facility to boot from USB, I already tried that.  There are 4 bad sectors on the HDD I don't think that is a high, is it?

I have since managed to download Ubuntu 11.04 WUBI style.  So, when I boot I get 3 options now.!!!
Thought I may be able to then format the free space and create a partition put, Ubuntu onto that, then delete the other partition including windows?  When I tried to format the free space, it stated there was an error so, was unable to so,that didn't work either!!!

I am beginning to think I need a new pc but, I do not want to buy one unless I really have to (due to lack of funds) and if I do really have to purchase a new one I do not want to pay for Windows either lol

Any other suggestions or advice, would be gratefully received.  

Debs:rolleyes::-k
Hi, the reason you can not just format the partition and wipe windows out is because you are running ubuntu through your windows partition as in wubi, I am going to give you a link for migrating a wubi install to a normal install then if you get your cd drive working you can get rid of the windows partition and reclaim the space.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by dFlyer on 2011-06-30
If you have back sectors, I would recommend you back up your data and get a new drive asap. Once a drive starts to fail your asking for trouble if you continue to use it. I would also agree that if you want to dump windows you do a fresh install either via usb or cd/dvd if possible.

---

### Post by egalvan on 2011-06-30
> **dFlyer said:**
> If you have back sectors, I would recommend you back up your data and get a new drive asap. Once a drive starts to fail your asking for trouble

That is more than right...
modern drives will automatically map out bad sectors...
without informing the user...
when the map-space becomes full, then they start nattering about "bad sectors"...
so by that time, you may have many many bad sectors...

BAD sectors, BAD...:(

---

### Post by debale on 2011-07-01
There are only 4 bad sectors which, I thought was quite low and thought it had a bit more life in it yet???

---

### Post by debale on 2011-07-01
> **wildmanne39 said:**
> Hi, the reason you can not just format the partition and wipe windows out is because you are running ubuntu through your windows partition as in wubi, I am going to give you a link for migrating a wubi install to a normal install then if you get your cd drive working you can get rid of the windows partition and reclaim the space.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)


This is great but, there are no partitions already set up?  I am unsure how to go about this as ubuntu is operating within windows it will not allow me to unmount and format a new partition?

---

### Post by wildmanne39 on 2011-07-01
> **debale said:**
> This is great but, there are no partitions already set up?  I am unsure how to go about this as ubuntu is operating within windows it will not allow me to unmount and format a new partition?
Hi, while running ubuntu did you download the automation program it was talking about? and then just follow the directions, it has pictures.

---

