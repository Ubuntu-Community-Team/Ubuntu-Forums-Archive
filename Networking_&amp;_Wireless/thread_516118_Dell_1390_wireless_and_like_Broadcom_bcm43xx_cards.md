---
title: "Dell 1390 wireless and like Broadcom bcm43xx cards"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by michael37 on 2007-08-02
I have a Dell laptop with Ubuntu Fiesty 7.04 and with Dell 1390 wireless adapter.  My system is running perfectly using the native bcm43xx driver provided with the stock Ubuntu kernel.  I use WEP at home and at work.

I spent some time reading various posts, FAQs and such, and I can't figure out why there are two camps: one using the ndiswrapper (legacy -- worked before Fiesty, discussed in [thread=297092]this thread[/thread]) and another using the [bcm43xx native kernel](http://bcm43xx.berlios.de) driver.

What really bothers me is that FAQ items in the main wiki for these two approaches do not cross-link each other.  So, some users may be mislead to believe that there is only one way.

So, I would like to ask user opinion which way is better.  Which one do you use?  Should we (I?) put time unifying the Wiki approach to this family of wireless adapters?

---

### Post by nutz on 2007-08-05
The native driver seems to be really picky as to what it will actually work with. Due to the many revisions of the Dell 1390 wireless adapter it works with some but not all. I have found however that the windows driver works with all of them through ndiswrapper. The 1390 comes in many different hardware revisions...

I have installed Ubuntu on 14 laptops now for friends, family and coworkers and the native driver only worked in one instance. And it is worth mentioning that the one that worked was an older revision(1.01). I had to use the windows driver with the others which were all hardware revision 1.02 and later including mine which is hardware revision 1.04...

---

### Post by Snipersnest on 2007-08-05
On my laptop at first the only thing I could use was fwcutter from the windows driver.  But I would rather have full speed wireless G rather than settling for B.

On my laptop (HP dv9010us) the kernel ended up being the problem for every install except with Gusty Gibbon. Gusty uses the 2.6.22 kernel which has new stuff for wireless connections. 

So once I got Gusty installed I compiled NDISwrapper 1.48rc1 and used a 32bit driver.

If you need fwcutter this tutorial worked perfect with their driver and everything: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) for my 4311 card builtin. But if your wanting to use NDISwrapper this one worked with their driver as well: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope this helps people finding this in a search. They do work but you need to take the time to slow down and read each step closely.

---

### Post by blisterpeanuts on 2007-08-05
> **michael37 said:**
> I have a Dell laptop with Ubuntu Fiesty 7.04 and with Dell 1390 wireless adapter.  My system is running perfectly using the native bcm43xx driver provided with the stock Ubuntu kernel.

My system is precisely the same, purchased in June 2007, and did NOT work out of the box with native driver.  I was forced to download ndiswrapper.  It would be really nice to get the native driver to work out of the box, because it would be one more selling point for Ubuntu over Windows, but realistically if the card manufacturer and Dell don't work to support Linux in a timely manner, this will never happen.

As a long time Redhat/Fedora user, I'm really impressed with Ubuntu, overall.  The user experience is the smoothest and pain-free of any distro I've tried.  I like the openness of Fedora as a development environment, but as a Windows replacement, Ubuntu has the rest of them beat.

---

### Post by nutz on 2007-08-05
This seems obvious to me but perhaps it isn't so obvious to everyone else. Dell has been updating the Windows driver to include the later revisions of the 1390 wireless adapter where as the native Ubuntu driver has not received these updates. This is why the natve driver will work with older revisions of the 1390 but not newer ones. It seems to work perfectly on revision 1.01 of this wireless card but not any after that. Mine was revision 1.04 and it did not work with the native driver at all but the Windows driver works perfectly.

It isn't just a matter of what card you have but also the hardware revisin of that card. If you have revison 1.01 of the 1390 wireless adtapter it should work.

---

### Post by michael37 on 2007-08-05
> **nutz said:**
> It isn't just a matter of what card you have but also the hardware revisin of that card. If you have revison 1.01 of the 1390 wireless adtapter it should work.

I just checked and noticed that my card is revision 01.  This is strange considering that my laptop is brand new.  The native driver is working for me, but with Fiesty Fawn, it's running only at B speed.

---

### Post by michael37 on 2007-08-05
> **blisterpeanuts said:**
> My system is precisely the same, purchased in June 2007, and did NOT work out of the box with native driver.  I was forced to download ndiswrapper.  It would be really nice to get the native driver to work out of the box, because it would be one more selling point for Ubuntu over Windows, but realistically if the card manufacturer and Dell don't work to support Linux in a timely manner, this will never happen.

In my experience, Dell 1390 card **_NEVER_** works out of the box.  With native driver, it requires an extra step with fwcutter.  With ndiswrapper, it requires ndiswrapper installation procedure.  I am sure you know this, but this seems to be a popular misconception that Dell 1390 can work out of the box.

What I like about the native driver is that that fwcutter procedure is a trivial single command in Feisty:
```
sudo apt-get install bcm43xx-fwcutter
```
then reboot, and voila, your native driver is working.

---

### Post by nutz on 2007-08-06
> **michael37 said:**
> I just checked and noticed that my card is revision 01.  This is strange considering that my laptop is brand new.  The native driver is working for me, but with Fiesty Fawn, it's running only at B speed.

Just because your laptop is new doesn't mean EVERY peice of hardware in it is new. Feature-wise there doesn't seem to be any difference between the revisions. It is more along the line of what logic it uses and how it is packaged inside the laptop. Just because it is revision 1.01 doesn't mean it is inferior to a version 1.02 card of the same type. It just means that they made changes to the hardware so they could stick it in a different package or put it on a board with a different layout. The features and functionality should be exactly the same.

---

### Post by michael37 on 2007-08-27
The Wiki on the support of this chipset is a mess.   I found several unrelated branches, one talking about a driver installation utility (not even sure it works in Fiesty), one on a manual fwcutter installation for bcm43xx, and a few threads on ndiswrapper.  Should we put them all together in something link together and meaningful?  

I am asking for community input on 
[LIST]
[*]Advantages of using Linux bcm43xx driver
[*]Advantages of using ndiswrapper Windows driver
[*]When to pick one or another approach
[/LIST]

---

### Post by nutz on 2007-08-28
> **michael37 said:**
> The Wiki on the support of this chipset is a mess.   I found several unrelated branches, one talking about a driver installation utility (not even sure it works in Fiesty), one on a manual fwcutter installation for bcm43xx, and a few threads on ndiswrapper.  Should we put them all together in something link together and meaningful?  

I am asking for community input on 
[LIST]
[*]Advantages of using Linux bcm43xx driver
[*]Advantages of using ndiswrapper Windows driver
[*]When to pick one or another approach
[/LIST]

+1

I have noticed this too.

---

