---
title: "Just installed yesterday; newbie! One question baffles me"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by hollowtd on 2009-01-31
I have a Dell D600 latitude laptop. I partitioned the HD with Ubuntu and XP. My only problem is I cannot access the wireless network for the internet. I cannot find the internet anywhere. I've went through basic steps and followed the help menu on Ubuntu. I get a good signal with Windows but can find nothing with UBUNTU. I need help. I am a newbie and understand how to open and type in Terminal. I do not understand a lot of the lingo yet though. I am computer savvy but totally new to this. I've checked for hours on other threads and have tried to identify a network, but cannot find anything. Please help me so I can have an awesome UBUNTU experience. Cheers to all you!:p

---

### Post by stalkingwolf on 2009-01-31
Your internal wireless may not be working.  In xp check device manager
and see if you can identify your wireless card.  Then search here for
that card.  There is a command to use to do this in Ubuntu but I am having a brain fart and cant remember what it is.


I am getting to that point in life and suffer more and more from CRS.:D

---

### Post by 73ckn797 on 2009-01-31
In terminal enter:

```
lspci
```

See if the device is listed.

---

### Post by hollowtd on 2009-01-31
I'll try both of those and get back with you. I know that when I have XP as my OS, the wireless connection works great. I'll get back soon. Thanks

---

### Post by hollowtd on 2009-01-31
I have a Dell Wireless 1450 dual band wlan mini pci card. I typed the lspci in terminal and don't see this one listed. I see something for modem and something for ethernet controller but not for wifi. Do I have to download a driver from dell.com perhaps? Thanks so much so far. 

Terry

---

### Post by MarblePanther on 2009-01-31
Try going to System, Administration, Hardware Drivers in Ubuntu.  Are there any drivers listed there?

---

### Post by hollowtd on 2009-01-31
It says "No proprietary drivers are in use on this system." NOthing listed in either the top small rectangle box nor the bottom bigger box.

---

### Post by MarblePanther on 2009-01-31
In that case you will have to use ndiswrapper

Try installing ndisgtk   in synaptic package manager

This is a front-end to ndiswrapper.  It will allow you to use your windows wireless drivers.

After installing, go to System, Administration, Windows Wireless Drivers

But make sure you have your windows wireless drivers with you. Either pop in your drivers cd if you have one or download your wireless driver from your pc manafacturer's site.

ndisgtk will ask where your driver's inf file is, so make sure you have your drivers.

---

### Post by ugm6hr on 2009-01-31
Before doing anything else, can you get online from ubuntu with wired access?

It would be helpful to confirm what chipset that card has - I suspect it is a Broadcom card... Did "lspci" list any Broadcom results?

It would be helpful to see the results of a few commands copied and pasted here.  You can either do this using wired internet from within Ubuntu (easier), or copy / paste into a text.txt file on USB and upload from Windows.

```
lshw -class network
ifconfig
lspci
iwconfig
```

---

### Post by MarblePanther on 2009-01-31
nvm delete this post

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> I have a Dell D600 latitude laptop. I partitioned the HD with Ubuntu and XP. My only problem is I cannot access the wireless network for the internet.

This could be useful :
[http://www.linlap.com/wiki/Dell+Latitude+D600](http://www.linlap.com/wiki/Dell+Latitude+D600)

---

### Post by MarblePanther on 2009-01-31
The only way you are going to get this working on Ubuntu is by using the ndiswrapper method I went over.

---

### Post by ugm6hr on 2009-01-31
> **MarblePanther said:**
> The only way you are going to get this working on Ubuntu is by using the ndiswrapper method I went over.

Indeed - a quick search revealed this - ndiswrapper should work:
[http://ubuntuforums.org/showthread.php?t=372775](http://ubuntuforums.org/showthread.php?t=372775)

However, I thought most Broadcom chipsets were now supported by the b43 driver.
[http://wireless.kernel.org/en/users/Drivers/b43/devices](http://wireless.kernel.org/en/users/Drivers/b43/devices)

And it looks like it can work:
[http://ubuntuforums.org/showthread.php?t=979717](http://ubuntuforums.org/showthread.php?t=979717)

Generally, native drivers are recommended ahead of ndiswrapper, but the choice remains.

---

### Post by hollowtd on 2009-01-31
I've followed some commands I've found trying to install the ndiswrapper-common "sudo apt-get install ndiswrapper-common" but it says "E: Couldn't find package ndiswrapper-common. I've got the driver now saved onto a USB storage device and have it saved zipped (exe) on the desktop. (I cannot get on the inet with UBUNTU, so I use my mac to talk to you and then try to do what you say, but I'm really new so some of the language I don't understand, though I do understand some of the things were getting  at--trying to do here.  Should I follow this, though I've tried and failed: [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper#1._ndiswrapper_installation](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper#1._ndiswrapper_installation)

Thanks many a times over

---

### Post by MarblePanther on 2009-01-31
> **ugm6hr said:**
> Indeed - a quick search revealed this - ndiswrapper should work:
[http://ubuntuforums.org/showthread.php?t=372775](http://ubuntuforums.org/showthread.php?t=372775)

However, I thought most Broadcom chipsets were now supported by the b43 driver.
[http://wireless.kernel.org/en/users/Drivers/b43/devices](http://wireless.kernel.org/en/users/Drivers/b43/devices)

And it looks like it can work:
[http://ubuntuforums.org/showthread.php?t=979717](http://ubuntuforums.org/showthread.php?t=979717)

Generally, native drivers are recommended ahead of ndiswrapper, but the choice remains.



He wouldve found it in the Hardware Drivers section if it uses B43
----------


As i said in a previous post, install the ndisgtk from the synaptic package manager (system, administration, synaptic package manager)

Follow the instructions on my other post:

> In that case you will have to use ndiswrapper

Try installing ndisgtk in synaptic package manager

This is a front-end to ndiswrapper. It will allow you to use your windows wireless drivers.

After installing, go to System, Administration, Windows Wireless Drivers

But make sure you have your windows wireless drivers with you. Either pop in your drivers cd if you have one or download your wireless driver from your pc manafacturer's site.

ndisgtk will ask where your driver's inf file is, so make sure you have your drivers.



EDIT:














Here is the driver file you will need when ndisgtk asks:  [ATTACH]101708[/ATTACH]

---

### Post by hollowtd on 2009-01-31
Sorry, I am totally new. I go to the Synaptic Package Manager and search for the ndisgtk but there is nothing. How do I install this if it's not there?

---

### Post by ugm6hr on 2009-01-31
> **hollowtd said:**
> Sorry, I am totally new. I go to the Synaptic Package Manager and search for the ndisgtk but there is nothing. How do I install this if it's not there?

If you cannot get online with a wired connection, it is slightly trickier.

That would also explain why there is nothing listed in "Hardware Drivers"

Any chance of using a cable to connect, just until you install the drivers?

PS: Which version of Ubuntu are you using (version / 32 vs 64 bit)?

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> Sorry, I am totally new. I go to the Synaptic Package Manager and search for the ndisgtk but there is nothing. How do I install this if it's not there?

You can get it also here :
[http://packages.ubuntu.com/search?keywords=ndisgtk](http://packages.ubuntu.com/search?keywords=ndisgtk)

---

### Post by MarblePanther on 2009-01-31
[ATTACH]101709[/ATTACH]

It is in there, try going to Settings, repositories, then go to the Third Party tab and check the box next to the first listing (the one with "partner" at the end.

Then hit the reload button and search again. make sure it is spelled right



I just assumed you were connected to the internet with ethernet.  Othewise you will have to find another computer to download all this stuff.

---

### Post by MarblePanther on 2009-01-31
> **MarblePanther said:**
> 


Here is the driver file you will need when ndisgtk asks:  [ATTACH]101708[/ATTACH]

Here is the driver inf file you will need. Download it to your desktop and right click "extract here".

Do you have internet access at the moment?

If you don't that *would* explain why it is not showing up in Hardware Drivers...

---

### Post by handydan918 on 2009-01-31
Seems to me that if the OP would just post the output of ```
lspci[CODE]or[CODE]lshw
``` or some other apropos detection-info command, we wouldn't be guessing.

---

### Post by MarblePanther on 2009-01-31
We know his wireless device, I even have the .inf uploaded.

We just need to know if he/she is online right now.

---

### Post by hollowtd on 2009-01-31
I'm not on the internet with Linux computer. I am using 8.10 Ubuntu. I have found the partner thing you're looking for, but there is no reload button. Also, I am getting ready to put the driver on.

---

### Post by hollowtd on 2009-01-31
I don't have a cable. Just wireless. Sorry forgot to answer that.

---

### Post by MarblePanther on 2009-01-31
Can you find an ethernet cable to connect to a router with?  Do you have another pc to download things with?  You need internet access to do any of the stuff we mentioned.

---

### Post by MarblePanther on 2009-01-31
> **hollowtd said:**
> I'm not on the internet with Linux computer. I am using 8.10 Ubuntu. I have found the partner thing you're looking for, but there is no reload button. Also, I am getting ready to put the driver on.

after you check the box, hit close, then find the reload button on the left in synaptic.

---

### Post by hollowtd on 2009-01-31
I have this dell, with xp on it and the wireless connection on it. I also have my mac, which Im using now to communicate to you as we work on this. I don't have a cable to the router but get a good signal. On xp, the wireless works great. I have the bcmwl5.inf file now on my desktop but am not sure how to "extract" as there is no option for that. At any rate, sorry to not post the terminal stuff here as that is near impossible, but I could if you really needed something. thanks

---

### Post by hollowtd on 2009-01-31
did that. thanks

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> but am not sure how to "extract" as there is no option for that. At any rate, sorry to not post the terminal stuff here as that is near impossible, but I could if you really needed something. thanks

Please use some usb-stick to copy things (software and output) across :)

---

### Post by hollowtd on 2009-01-31
I have put the bcmwlf.inf file onto a usb stick and put it onto by ubuntu desktop. I right click on it but there is no option for extract. NOt sure what to do now.

---

### Post by ugm6hr on 2009-01-31
I will leave you to it, since you are going down the ndiswrapper route.

Nevertheless, this may prove a useful reference for you if it fails:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

---

### Post by MarblePanther on 2009-01-31
Go here on your mac and download the 32 bit version for intrepid to your usb key: [http://linuxappfinder.com/package/ndisgtk](http://linuxappfinder.com/package/ndisgtk)

Then you will need to also download these 2 to your usb key:

[http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download](http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download)

and

[http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)

So in all move these three .deb packages to your usb key and move them to your Dell and install them.  You may need to install them in a certain order.  If one says needs dependency "so and so" then install that dependency first.  To install these .deb packages you just move them from your usb to your dell desktop and click on them and hit install when it pops up.

---

### Post by MarblePanther on 2009-01-31
> **hollowtd said:**
> I have put the bcmwlf.inf file onto a usb stick and put it onto by ubuntu desktop. I right click on it but there is no option for extract. NOt sure what to do now.


Dont worry if it just says bcmwlf.inf, then you are fine.  Leave it be.

---

### Post by MarblePanther on 2009-01-31
> **ugm6hr said:**
> I will leave you to it, since you are going down the ndiswrapper route.

Nevertheless, this may prove a useful reference for you if it fails:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

Once he/she gets the ndiswrapper set up, we can help him/her install the native driver in Hardware Drivers.  We need to get him/her access first on the computer he/she needs it on.

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> I have put the bcmwlf.inf file onto a usb stick and put it onto by ubuntu desktop. I right click on it but there is no option for extract. NOt sure what to do now.

Install the ndisgtk package, but we need to know whether you're using 32 or 64 bit Ubuntu.
```

uname -m

```

You can find the 32 or 64 bit package here :
[http://packages.ubuntu.com/intrepid/ndisgtk](http://packages.ubuntu.com/intrepid/ndisgtk)
you also need this :
[http://packages.ubuntu.com/intrepid/ndiswrapper-utils-1.9](http://packages.ubuntu.com/intrepid/ndiswrapper-utils-1.9)
Assuming that you're using Ubuntu 8.10.

---

### Post by ugm6hr on 2009-01-31
> **MarblePanther said:**
> Once he/she gets the ndiswrapper set up, we can help him/her install the native driver in Hardware Drivers.  We need to get him/her access first on the computer she needs it on.

There is no point in that.  The post I gave explains how to install b43 without internet.

If ndiswrapper works OK - just use it.  I don't think b43 is necessarily any better, it merely allows future upgrades etc without too much messing around.

---

### Post by albinootje on 2009-01-31
> **MarblePanther said:**
> Once he/she gets the ndiswrapper set up, we can help him/her install the native driver in Hardware Drivers.

Ndiswrapper and "native driver" is an oxymoron :)

In FreeBSD the equivalent of Ndiswrapper has the nickname Project Evil.
[http://lists.freebsd.org/pipermail/freebsd-current/2004-January/019486.html](http://lists.freebsd.org/pipermail/freebsd-current/2004-January/019486.html)

---

### Post by hollowtd on 2009-01-31
I've got all 3 now and will put them on my dell now. trying...

---

### Post by MarblePanther on 2009-01-31
> **albinootje said:**
> Ndiswrapper and "native driver" is an oxymoron :)

Native linux driver versus the ndiswrapper windows driver, its not an oxymoron

---

### Post by hollowtd on 2009-01-31
ive got them extracted on my desktop on the dell now. Now what..thanks...a lot

---

### Post by MarblePanther on 2009-01-31
> **MarblePanther said:**
> 

So in all move these three .deb packages to your usb key and move them to your Dell and install them.  You may need to install them in a certain order.  If one says needs dependency "so and so" then install that dependency first.  To install these .deb packages you just move them from your usb to your dell desktop and click on them and hit install when it pops up.

Follow this^^^

---

### Post by albinootje on 2009-01-31
> **MarblePanther said:**
> Native linux driver versus the ndiswrapper windows driver, its not an oxymoron

Hmm, yes, I realised too late what you meant to say, I guess I got confused by using two different methods to go online via wifi so quickly after one another.

---

### Post by MarblePanther on 2009-01-31
Yeah, I don't blame you, this thread is getting confusing :)

---

### Post by hollowtd on 2009-01-31
I'm doing it. Don't leave me yet. I've got them all installed. Geesh, you guys are awesome.

---

### Post by MarblePanther on 2009-01-31
Okay now go to System,Administration, Windows Drivers (or something to that effect)

--you're almost there!  ;)

---

### Post by hollowtd on 2009-01-31
I've got the ndiswrapper and the ndiswrapper util one to work. The ndisgtk.deb says discrepancy on it. Should I get another one of those and try again?

---

### Post by MarblePanther on 2009-01-31
what exactly does it say?



Did you download ndisgtk from here? 


[http://packages.ubuntu.com/intrepid/i386/ndisgtk/download](http://packages.ubuntu.com/intrepid/i386/ndisgtk/download)

---

### Post by hollowtd on 2009-01-31
Error:  Dependency is not satisfiable: menu  (it's all in red letters)

---

### Post by MarblePanther on 2009-01-31
Okay I'll find the deb package for that, hold on a second

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> Error:  Dependency is not satisfiable: menu  (it's all in red letters)

Download the application called "menu".
[http://packages.ubuntu.com/search?keywords=menu](http://packages.ubuntu.com/search?keywords=menu)

And perhaps it's better install from a terminal with this :
```

cd Desktop  (hit enter, assuming you copied all files to your desktop)
sudo dpkg -i *deb (after also putting the "menu" deb package there)

```

---

### Post by MarblePanther on 2009-01-31
Here it is:

[http://packages.ubuntu.com/intrepid/i386/menu/download](http://packages.ubuntu.com/intrepid/i386/menu/download)

---

### Post by hollowtd on 2009-01-31
i just got it to work. Can you walk me through it now. I have them all three with no discrepancies. Thank You

---

### Post by ugm6hr on 2009-01-31
> **MarblePanther said:**
> [http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download](http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download)

and

[http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)

These are Hardy .debs - that is why the Intrepid ndisgtk complains about dependencies.

You need (install in this order):
[http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download](http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download)
[http://packages.ubuntu.com/intrepid/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/intrepid/i386/ndiswrapper-utils-1.9/download)
[http://packages.ubuntu.com/intrepid/i386/ndisgtk/download](http://packages.ubuntu.com/intrepid/i386/ndisgtk/download)

---

### Post by MarblePanther on 2009-01-31
> **MarblePanther said:**
> Okay now go to System,Administration, Windows Drivers (or something to that effect)

--you're almost there!  ;)

Do this, then when it asks where your inf file is located, just select that .inf file you downloaded to your desktop.

---

### Post by MarblePanther on 2009-01-31
delete this post

---

### Post by hollowtd on 2009-01-31
So close, It says bcmw15 INvalid Driver! with a red cross through it. I just have the icon on my desktop with a lock on it. Must I do something there?

---

### Post by MarblePanther on 2009-01-31
Do you have the .exe you had earlier from dell.com?

If you do, then right click on the .exe and click "extract here".

Then go into the Drivers folder in that folder and use the .inf file in there

Delete the inf file i gave you, it must be the wrong one.




If you dont have the driver yet, go to support.dell.com and find your laptop model and download the wireless driver: [http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=LAT_PNT_PM_D600&os=WW1&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=LAT_PNT_PM_D600&os=WW1&osl=en&catid=&impid=)

---

### Post by hollowtd on 2009-01-31
im with you so far but can't get the freakin thing to show my desktop when I click on "Install new driver" so close...

---

### Post by hollowtd on 2009-01-31
Got it. says Hardware Present: Yes NOw what?

---

### Post by MarblePanther on 2009-01-31
What does it say or do now?  If there are no other dialog boxes then try and reboot your computer then turn your wireless switch on and see if it works

---

### Post by hollowtd on 2009-01-31
Ok, so I've done all that and the Hardware is Present under the "wireless Network Drivers" If I push configure network, it says Could not Find Network Configuration Tool. Is that how I make it work or should I take another route?

---

### Post by MarblePanther on 2009-01-31
> **hollowtd said:**
> Ok, so I've done all that and the Hardware is Present under the "wireless Network Drivers" If I push configure network, it says Could not Find Network Configuration Tool. Is that how I make it work or should I take another route?

Turn your wireless switch on the side of your computer on and reboot your computer first.

---

### Post by hollowtd on 2009-01-31
restarting now

---

### Post by hollowtd on 2009-01-31
I restarted but nothing. What should I try?

---

### Post by MarblePanther on 2009-01-31
Have you pushed the wireless switch forward?  Do you see a lit up "wifi" light next to your power light?  Click on your Network Manager applet in your system tray and see if it shows any wireless networks.

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> I restarted but nothing. What should I try?

Post the output of :
```

iwconfig
sudo iwlist scan
lsmod|grep ndis

```

---

### Post by hollowtd on 2009-01-31
This may sound stupid but there is no Network Manager anywhere that I can find under System. Also, there is no wifi switch. When I have it using xp, there is no light or anything on either or switch to move.

---

### Post by MarblePanther on 2009-01-31
No, network manager is in your system tray next to your clock (a little icon on your panel)

---

### Post by hollowtd on 2009-01-31
I feel really stupid but don't know Network Manager or see it anywhere, on the top bar or the bottom or under the System pull down menu or anywhere. I've even searched for it.

---

### Post by MarblePanther on 2009-01-31
Hit alt+f2 and type Network and see if network manager is in the choices or if while you're typing it autocompletes the word network manager

It should be a little icon next to your sound icon next to your clock in the top panel

---

### Post by hollowtd on 2009-01-31
I've got three lines, a double computer with an eclamation symbol, the date, time and my name. sorry to keep you here. Ifoundnothing with the f2 option.

---

### Post by hollowtd on 2009-01-31
The wireless network is greyed out.

---

### Post by MarblePanther on 2009-01-31
Okay do this command in your terminal:

lsmod|grep ndis

and paste what it says

---

### Post by hollowtd on 2009-01-31
it says ndiswrapper 196380 0 
usbcore 1488848 7 btusb,ndiswrapper, usb_storage, libusual, ehci_hcd, uhci_hcd

---

### Post by MarblePanther on 2009-01-31
Okay you should be working then.

Try left clicking and try right clicking on the Network Manager icon and tell me what pops up.

---

### Post by hollowtd on 2009-01-31
It says" wired network auto etho0 wirless network (these are all greyed out) then it says vpn connectins and conect to hidden and create new wireless

---

### Post by MarblePanther on 2009-01-31
For future reference, this distro works out of the box for your computer:
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php) (download the main edition)

It is a linux distro based on Ubuntu.  Wireless is supposed to work out of the box with it.  So just for future reference...

---

### Post by hollowtd on 2009-01-31
right click says enable and enable netowrking and wireless and they are both checked. conection info is greyed out. edit conntions and about

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> right click says enable and enable netowrking and wireless and they are both checked. conection info is greyed out. edit conntions and about

The command "iwconfig" and "sudo iwlist scan" didn't show anything at all ?

---

### Post by hollowtd on 2009-01-31
The first says no wireless extensions all the way down

---

### Post by hollowtd on 2009-01-31
The second says interface does not support scanning

---

### Post by MarblePanther on 2009-01-31
Okay, the driver is installed but it seems your radio for the wireless is not on. You can try rebooting once more and checking iwconfig again or click on network manager to see if it shows anything.  

I would recommend trying  linuxmint out in the future, it works with your wireless out of the box.  Try downloading the iso for it in the background on your mac if you have any spare cd's.  You might just have to use it instead if we dont get this working

---

### Post by hollowtd on 2009-01-31
Im gonna check this later and call it a night. A bit late now where I'm at. I'm gonna write you tomorrow and I really want to thank you all for helping me so much. I will do more of this tomorrow and will see you. Thanks so much for your help and I'm gonna figure out a way to thank you somehow with a gift, especially once we get this thing going. I will try the background thing tomorrow. Thanks so much again!!!!!!!

---

### Post by MarblePanther on 2009-01-31
No need for any gifts...I'm glad to help.

Hope we get this worked out.  Good night!

---

### Post by albinootje on 2009-01-31
> **hollowtd said:**
> I'm gonna write you tomorrow and I really want to thank you all for helping me so much. I will do more of this tomorrow and will see you. Thanks so much for your help and I'm gonna figure out a way to thank you somehow with a gift, especially once we get this thing going. 

I think that in the future you should give yourself a present, and that is a computer which is fully supported by Linux :)

Meanwhile check this video of a happy Linux user : [http://www.gnu.org/fry/](http://www.gnu.org/fry/) and donate to the FSF if you like.

---

### Post by 73ckn797 on 2009-02-01
See if any info here will help you figure things out:

[https://help.ubuntu.com/community/TitleIndex#idxN](https://help.ubuntu.com/community/TitleIndex#idxN)

[https://help.ubuntu.com/community/NdiswrapperIpn2220](https://help.ubuntu.com/community/NdiswrapperIpn2220)

---

### Post by stalkingwolf on 2009-02-01
The method I use to insure I have wireless right from the off is,
I keep a USB adapter (netgear wg111 or knock off) and a wireless card
( DLink DWL G650) at hand.  Both have worked OOTB with every version
since 7.04, and every laptop Ive tried.

Try going to System > Administration > Network,  see if it shows
your wireless connection.  You might need to activate your wireless
connection .

---

### Post by hollowtd on 2009-02-01
Would you guys recommend I reinstall a different version of UBUNTU? I mean, I now have the three files on my comptuer but no wireless. I'm not sure how it doesn't work as I installed the ubuntu 8.10 from the CD I got in the mail from the same website. Can I reinstall something different that will work? What is a linux supported machine? Thanks

Terry

---

### Post by MarblePanther on 2009-02-01
Yes as I mentioned earlier: LinuxMint (it based off of Ubuntu)

[www.linuxmint.com](www.linuxmint.com)

Make sure you install the main version in downloads

It supports your wireless out of the box, as i mentioned earlier

Just download the .iso file and burn it to a cd using Brasero Disk Burner on you Ubuntu desktop.  Then boot it and install it over your Ubuntu installation.

It is basically Ubuntu with better hardware support and such

---

### Post by hollowtd on 2009-02-01
> **MarblePanther said:**
> For future reference, this distro works out of the box for your computer:
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php) (download the main edition)

It is a linux distro based on Ubuntu.  Wireless is supposed to work out of the box with it.  So just for future reference...
What is a distro? Can I get this now or is it too late? If I have to put a different version of Ubuntu (with all the things) then let me know. I don't have a problem with re-doing it over again, as I'm not worried about losing anything.

---

### Post by MarblePanther on 2009-02-01
Ubuntu is a *distribution* of the Linux operating system.

Distros are basically Linux with different looks, packages, and configurations.

LinuxMint is free just like Ubuntu, just burn it to a cd and boot like your Ubuntu cd.

---

### Post by hollowtd on 2009-02-01
So, Ubuntu will be gone forever if I put linuxmint on my computer. What If I have to put the linuxmint on a Cd using my Mac and then put it in the Cd drive on my dell (the one I want to be Linux)? What do you recommend? Is this the best one that I should use--for a newbie and everything? I will take your advice, so what do you think is the best distribution?

---

### Post by MarblePanther on 2009-02-01
Yes I recommend it.  It works just like Ubuntu. No need to worry.

Just download it on your mac and burn it to a cd.  

Pop in the cd on your dell and boot it like you did with Ubuntu.

Install it just like you did Ubuntu.

(Make sure you back up any personal files like pictures and music and documents you may have on your Ubuntu machine)--because it will overwrite ubuntu

---

### Post by albinootje on 2009-02-01
> **hollowtd said:**
> Would you guys recommend I reinstall a different version of UBUNTU?
Imho it would make more sense to find out why it doesn't work, since you seem to be pretty close, but if on the other hand Linux Mint would make this all easier, then why not use it.
Linux Mint is based on Ubuntu, I've tried Mint some weeks ago, it has a different design and a different approach, I can imagine that 
some people will be pleased with it.
I'm curious about how well this (Linux Mint installation) would solve your specific wifi problems, so please post updates here, thanks.

---

### Post by hollowtd on 2009-02-01
I'll give it a go. I'll have to get some CDs. I am not worried about losing anything as the computer is new to me and has nothing personal on it. You think I'll be able to use linuxmint then to get on the internet wirelessly without having to deal with the other problems? Thanks for all your continuous help.

---

### Post by hollowtd on 2009-02-01
I will let you know. I like Ubuntu too. I could try a couple things before I just give up, as we are very close. I'll have to try later though as I'm on the train now. I'll keep you posted.

---

### Post by MarblePanther on 2009-02-01
LinuxMint works out of the box with your wireless.

The reason for this is that it includes your proprietary driver that Ubuntu's policies dont allow for.

LinuxMint should work without any tweaking, it is even easier to use than Ubuntu in my opinion.

---

### Post by golusweet on 2009-02-01
Have you tried Ubuntu 8.10?

---

### Post by chamber on 2009-02-01
> **golusweet said:**
> Have you tried Ubuntu 8.10?

That's what they're using at the minute.

---

### Post by ugm6hr on 2009-02-01
> **hollowtd said:**
> I will let you know. I like Ubuntu too. I could try a couple things before I just give up, as we are very close. I'll have to try later though as I'm on the train now. I'll keep you posted.

You could try the b43 driver if ndiswrapper is not playing nice:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

Just remove ndiswrapper first:
```
sudo apt-get remove ndiswrapper-common
```

Linux Mint has ndiswrapper installed as default too.

---

### Post by hollowtd on 2009-02-01
I will try that before I totally give up on ubuntu 8.10. Cheers to all for your help.

---

### Post by hollowtd on 2009-02-02
Does anyone know how really quick to copy a file I downloaded (now extracted on my desktop) to a "home directory"

---

### Post by hollowtd on 2009-02-02
Does anyone know how really quick to copy a file I downloaded (now extracted on my desktop) to a "home directory"? I'm trying to do this with the b430fcutter for ubuntu 8.10. Thanks

---

### Post by ugm6hr on 2009-02-02
Your "home directory" is in Places -> Home Folder

Just drag and drop.

PS: If you are following my link - you do not need to extract anything - the commands to extract are given in the How-to.

---

### Post by hollowtd on 2009-02-02
Thanks. I'm trying what you said with the b43fwcutter.

---

### Post by ugm6hr on 2009-02-02
> **ugm6hr said:**
> PS: If you are following my link - you do not need to extract anything - the commands to extract are given in the How-to.

^^

---

### Post by hollowtd on 2009-02-02
Im not extracting, I'm doing what your link says to do. I'm trying to "open" the file fwcutter but I get this: 
dpkg: error processing b43cutter_011-4ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 b43cutter_011-4ubuntu1_i386.deb

---

### Post by hollowtd on 2009-02-02
The thread says that the 011 number might be wrong

---

### Post by ugm6hr on 2009-02-02
> **hollowtd said:**
>  b43cutter_011-4ubuntu1_i386.deb

Your spelling could do with a bit of help! ;)

> b43-fwcutter_011-4ubuntu1_i386.deb

A useful tip to prevent such problems:

```
sudo dpkg -i b43-f <press Tab key here>
```

The Tab key looks at all the potential files and fills in the rest for you.  Assuming you only downloaded the 32-bit fwcutter, that should work!

---

### Post by hollowtd on 2009-02-02
It did all kinds of cool stuff and then did said extracting b43/bogoinitvals.4.fw or something to that nature. Now what? Yes, my spelling is off today. I have to admit that I am a writer of sorts for my living--ironic, eh? Ha. Thanks so far. How do I check to see if the b43 fixed my wireless problem then? Tahnks

---

### Post by ugm6hr on 2009-02-02
Did you follow all the advice re: firmware etc?  It won't work without it.

If yes - try rebooting and then left-click on Network Manager (icon in top-right corner - looks like 2 computers).

---

### Post by hollowtd on 2009-02-02
Dude!!! You did it. You helped me. Wow, thanks so much. Hours and hours and it worked. This was my last measure and it worked. Thanks so much for your help. This is great. Thanks so so so so much for helping me. This is why i want to use linux, people are so great at helping. Mac and microsoft would never do this. Thanks so much.

---

### Post by hollowtd on 2009-02-02
Thanks so so so much. Again. Wow it's working. I can't believe with your help we did it and i was actually able to get it working. What a feat, for me at least (only with all your help and the others!!!) thanks

---

### Post by ugm6hr on 2009-02-02
No problem.

Glad to have you on board.

The Ubuntu community is indeed pretty fantastic...

Everything with Ubuntu becomes 100 times easier with internet working - just stop by here to ask for advice whenever necessary!

---

### Post by hollowtd on 2009-02-02
GREAT. thanks so much again. Also, you mentioned a place to donate to the linux/ubuntu cause. Where might that be again? Cheers once more times infinity.

---

### Post by ugm6hr on 2009-02-02
Up to you...

Financial support for Ubuntu is by Canonical, which is a profit-making company.  They sell support services, and a few other items (e.g. shirts, mugs etc).  Donations are also possible: [http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate) (see donate link in menu on left)

Ubuntu is based on Debian Linux, which is run by a non-profit-making organisation: [http://www.debian.org/donations](http://www.debian.org/donations)

If you want to donate to a non-profit-making organsiation, the FSF is a good choice: [http://www.fsf.org/](http://www.fsf.org/)  They support a multitude of GNU opensource software, including GNU Linux.

---

### Post by Dougie187 on 2009-02-02
Lol you should donate to yourself and go out and buy an ethernet cable. That way in the future you can hardline your computer.

---

### Post by hollowtd on 2009-02-03
Thanks for that. I will look into those this week. I just have one more question, and I do have an ethernet cable now. Ha. If I bought an Acer One computers and they have Linux Lite on them, it is possible to put Ubuntu on it? Or is this distribution of linux a good one? What would you recommend? (I want to get a super small laptop and put linux on it, like Ubuntu 8.10? Any recommendations as I travel a lot these days. Cheers again  for all the help. It's working great now!

---

### Post by albinootje on 2009-02-03
> **hollowtd said:**
> If I bought an Acer One computers and they have Linux Lite on them, it is possible to put Ubuntu on it? 

Check this : [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

I have an AAO myself with Ubuntu, and it's OK, the battery time is less than with Linpus, about 2 hours is what I get.
But I prefer Ubuntu on it rather than Linpus Linux.

---

### Post by ugm6hr on 2009-02-03
In the UK, the Dell Mini 9 is only marginally more expensive than the Aspire One.

It comes with Ubuntu (Hardy) pre-installed.

I bought one just a few weeks ago :)

---

### Post by hollowtd on 2009-02-03
PLEASE HELP, AGAIN. I just did a bunch of updates and now no wireless signal. How can I check this? I don't get anything when I click on the network manager anymore. Please help ...thanksssss again

---

### Post by ugm6hr on 2009-02-04
Please be more specific.

Are you updating only from the standard Ubuntu repositories?

What do you mean you "don't get anything"?

Plug in your ethernet cable to get online and provide the output from:
```
ifconfig
iwconfig
sudo iwlist scan
lshw -class network
lsmod
```

And have a look in System->Admin->Hardware Drivers to see what's available.

---

### Post by sofasurfer on 2009-02-04
This thread got 121 posts in 3 days. That is amazing!! I'm jealous. Is that a record? My best thread got 71 posts in 1 day, which would be 216 in 3 days but it died after the first day.

---

### Post by MarblePanther on 2009-02-04
i still recommend Linux Mint  ;)

(save ya a lot of trouble)

---

### Post by hollowtd on 2009-02-04
Yep, I tried to get it yesterday but my connection flubbed up. Plan on trying it today. (I had it working for a while.) I also plan on buying a computer with Ubuntu already on it. Got any ideas. I got some tips about the Dell mini 9 with ubuntu already installed. Sounds like a good deal for the price. Got any other ideas?

---

### Post by hollowtd on 2009-02-04
I just downloaded and copied linux mint to a cd. I put it into my dell and it will not boot up from the cd drive. I'm sure I did it right. Any thoughts or ideas so that I can boot up linux mint and install. (I have xp and ubuntu on the machine now.) Cheers

---

### Post by albinootje on 2009-02-04
> **hollowtd said:**
> I just downloaded and copied linux mint to a cd. I put it into my dell and it will not boot up from the cd drive. I'm sure I did it right. 

You did burn it as iso, right ?
Make also sure you do a md5sum check, and burn at low burning speed.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

