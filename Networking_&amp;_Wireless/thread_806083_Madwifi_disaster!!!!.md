---
title: "Madwifi disaster!!!!"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by penguins916 on 2008-05-24
Hi all, 
I reacently installed Ubuntu on my aspire 5570z laptop. 
this has a AR5007EG wifi card.

I installed madwifi and it worked. I then had problems suspending and I changed some settings, I forget what now, and now I am back to where I started. I tried installing and uninstalling it but to no avail.

I also tried to delete the partition and reinstall ubuntu, That still left traces of madwifi on it. 

I **Really** hope somebody can help me with this. 

Ubuntu is so great and I love it, but my laptop doesn't.

~penguins916

---

### Post by mavi_yelkenler on 2008-05-24
hi penguins916

I also have an Acer laptop with AR5007EG. Dowload this from the madwifi ticket --->> [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz) 

sudo make
sudo make install
sudo modprobe ath_pci

if you installed 7.10 -->> "blacklist ath5k"

if hardy installed , reboot the computer after installing the madwifi driver

ifconfig -a , now you should see ath0

regards

---

### Post by penguins916 on 2008-05-24
Yes thats what I did. When I type sudo make install it asks me : some files are the same and prompts me remove list or ignore them. I have tried all of them.
When ever I try modprobe ath_pci it returns nothing. 

I will try it again with that version madwifi, I have been using the newest off of there site.

Also should I disable any restricted drivers or leave them on?

Also have you been having the problem when madwifi is installed ubuntu doesn't suspend?

Thanks for the help, Penguins916

---

### Post by mavi_yelkenler on 2008-05-24
hi Penguins916,

> Also should I disable any restricted drivers or leave them on?
 yes,

> Also have you been having the problem when madwifi is installed ubuntu doesn't suspend?


no

please install the driver on that link and install it

if you fail again then reinstall ubuntu and try again

excuse me for my bad english .)

---

### Post by scottro on 2008-05-24
I have a page with my own step by step about that card.

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

One new twist is that later kernels, 2.6.26 I think, don't build with those snapshots.

---

### Post by penguins916 on 2008-05-25
Ok I did all of that. 

When I type make and make install I get errors.

And when I type modprobe ath_pci I get FATAL: could not open........

I have installed many versions of madwifi. if I uninstall with this one will that remove all?

Any suggestions?

also ifconfig shows no ath0.

---

### Post by chili555 on 2008-05-25
If you get errors at 'make' there is no way or reason to continue until you resolve the errors; it won't work. What errors did you get? We'll be glad to help you fix them.> if I uninstall with this one will that remove all?Any previous installations will be overwritten by this one. 

Do you have *build-essential* and *linux-headers-generic* installed?

---

### Post by penguins916 on 2008-05-25
Thanks.

It works great. 

Times like now I am like now I feel really stupid. The problem was when I reinstalled Ubuntu I forgot to reinstall build essential. so I was doing all this thinking it was installed. 

Also the suspend is working.

Thanks A ton all of you. 
:lolflag:\\:D/=D>=D>=D>=D>

---

### Post by mavi_yelkenler on 2008-05-25
> It works great. 
happy to hear it is working

> One new twist is that later kernels, 2.6.26 I think, don't build with those snapshots.

Scottro thanks for that info. I didnt know that. thanks

---

### Post by scottro on 2008-05-25
Neither did I till a Fedora upgrade (rawhide, so I brought it on myself) taught me the sad truth.  :)
For the moment, I've just put a hold on upgrading the kernel.

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

