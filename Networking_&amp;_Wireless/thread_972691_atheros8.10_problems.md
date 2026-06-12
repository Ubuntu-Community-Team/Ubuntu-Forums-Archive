---
title: "atheros/8.10 problems"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by brodiesel on 2008-11-06
hello all

i did a soft upgrade from hardy to intrepid, and low and behold, my wireless stopped working. it would appear that i am missing the driver, even though it worked on hardy and continues to work "out of the box" with the hardy live disc. the device manager and hardware testing are confirming the existence of the Atheros 802.11 WLAN but the hardware drivers section does not list that driver, which is easily found by the hardy live disc. 

so whats the deal? more importantly, how can i install or activate this driver without having to download it (since it obviously exists somewhere on my computer)? Ive tried looking for some command line tools to help with this, but didnt get far...

---

### Post by Petrock6 on 2008-11-06
Try a Madwifi driver.

---

### Post by brodiesel on 2008-11-06
again, i'm not sure how i should go about doing that without having an internet connection in intrepid. 

to make this scenario more annoying, i am currently running off a live disc of intrepid where the wireless works perfectly. can someone explain to me why the version i downloaded a few short days ago does not have the "Support for Atheros 802.11 Wireless LAN Cards" driver that the live disc has? And can someone also explain to me how I can use this functioning and online version of Interepid to dowload an appropriate driver to somewhere I can access from the installed Intrepid?

sorry for the tone, its been a long day... and it sometimes dawns on me that im not getting any better with computers...

---

### Post by yamagami on 2008-11-06
I have the same problem on a thinkpad t61p. 
Infact, I've had this in hardy as well, but managed to overcome it by installing the latest madwifi and wpa_supplicant off svn every time i upgraded a kernel. In interpid i'm not so lucky. 
at this moment the drivers (either madwifi ath_pci or ath5k) load fine, but the card cannot connect to any wifi network. it keeps asking me for the passphrase for either wpa or wep. after all my attemps it can now no longer show any network in network manager. I have to connect ot an 'invisible' one selecting one of my previous connections which are still rememebered.
I'm tearing out my hairs here. literally.

---

### Post by brodiesel on 2008-11-06
yeah, I hear you. i've had this problem for five days now with no resloution. i just dont understand why the live disc would work when the install doesnt. 
as far as installing the madwifi driver, is that something you did from the live disc? where's a good place to save that so that intrepid can find it when i boot that up?

---

### Post by nothingspecial on 2008-11-06
Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz	
```

Unzip it
```

tar -xvf madwifi-hal-0.10.5.6-r3861-20080903.tar.gz	
```


navigate to the extracted file

```

cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you`ve not got the tools necessary for compiling get them
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it

```
sudo make

``````

sudo make install
```

load the module/driver

```
sudo modprobe ath_pci
```

make it load every time you boot
```

gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file
```

ath_pci
```

save
exit 
reboot

---

### Post by brodiesel on 2008-11-06
thanks. i am going to try this, but first a couple noob questions:

how do i specify a directory on my hd to save it to? once i do that, how do i activate that driver from within the installed version?

---

### Post by brodiesel on 2008-11-06
uhoh. 

failure:

```
ubuntu@ubuntu:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
--2008-11-06 21:52:30--  http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz [following]
--2008-11-06 21:52:31--  http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz/
Resolving snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz... failed: Name or service not known.
wget: unable to resolve host address `snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz'
ubuntu@ubuntu:~$ 


```

---

### Post by eks on 2008-11-06
> **brodiesel said:**
> to make this scenario more annoying, i am currently running off a live disc of intrepid where the wireless works perfectly. can someone explain to me why the version i downloaded a few short days ago does not have the "Support for Atheros 802.11 Wireless LAN Cards" driver that the live disc has? And can someone also explain to me how I can use this functioning and online version of Interepid to dowload an appropriate driver to somewhere I can access from the installed Intrepid?

I don't know, but someone asked exactly this same question here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288148](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288148)

I suggest you also post a complaint, your point is interesting and strongly valid.

And anyway, you can plug an ethernet cable to your laptop, somehow, and do the information available on the wiki:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

So far, the built-in solution using the linux-backports-modules, worked for a fair amount of people. But if you installed other driver manually first you will need to blacklist the others and make sure ath5k is not blacklisted. And if you have problem connecting to a WEP network, see the post bellow.

---

### Post by eks on 2008-11-06
> **yamagami said:**
> I have the same problem on a thinkpad t61p. 
Infact, I've had this in hardy as well, but managed to overcome it by installing the latest madwifi and wpa_supplicant off svn every time i upgraded a kernel. In interpid i'm not so lucky. 
at this moment the drivers (either madwifi ath_pci or ath5k) load fine, but the card cannot connect to any wifi network. it keeps asking me for the passphrase for either wpa or wep. after all my attemps it can now no longer show any network in network manager. 

Try setting the wpa supplicant to wext. It worked for me.

---

### Post by nothingspecial on 2008-11-06
madwifi have just updated. 
Go here and follow my instructions but with the new snapshot.
hope it makes sense.


[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

---

### Post by brodiesel on 2008-11-06
> **eks said:**
> 
And anyway, you can plug an ethernet cable to your laptop, somehow, and do the information available on the wiki:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

so i finally went into the neighbors house to use their ethernet cable, and got online, and went to the hardware drivers, and what happened was very aggravating. under hardware drivers the only pertaining to the card is known generically as "software modem" which is a smartlink bundle that, if not installed, prevents my wireless from working. mind you, this particular driver is not on the list of hardware drivers in the live disc version of intrepid that actually works. the "want to kill yourself" aspect of the software modem, however, is that everytime I attempted to install and enable this driver, my computer crashed. dead freeze with a screen saying "downloading 0%".

so at this point, i'm feeling done with my current install, and i think i'm going to reinstall from the live disc that i know works. any advice? will it work to copy /home to an external hd and then replace the new /home with the old? do i need to erase everyhting on the partition? whats the best way to wipe and reinstall? (maybe i need a new thread...)

---

### Post by nothingspecial on 2008-11-07
Updated my original post.
It will work now.
Disable any wifi drivers in system > administration > hardware drivers first.

---

### Post by brodiesel on 2008-11-07
eks: i somehow just now read that bug thread you pointed me too, and i must say i'm more confused than ever. it will take me more time than i have right now to figure out what i'm supposed to do, but thank you for posting that. 

and yet, one thing i till didnt see addressed: why does the live disc work? is the live disc, which i downloaded the ISO of two days ago, a different version than the upgrade i downloaded on the day 8.10 officially came out? it is this thinking that makes me just want to reinstall, but i'm still trying to figure out how to do that.

and nothingspecial, i appreciate the help, and i'm not trying to be unkind, but i'm not sure if you read through this thread. it appears to go a little deeper than that, but once again, i do appreciate the effort.

---

### Post by eks on 2008-11-07
brodiesel: I've read the thread but... I cannot fully understand the problem you are having. I've never seen a "software modem" listed anywhere, but indeed, my experience with Ubuntu is not extensive and I have just an Atheros card. You can try to be sure about your card by running "lspci" or "lspci -v" on a terminal. "dmesg", and/or "dmesg | grep ath" also might help you debug your problem, in short [dmesg]("http://en.wikipedia.org/wiki/Dmesg") shows the "boot log" of your computer, so you can try to find what's going wrong. Grep ath only lists entries with ath somewhere, so you can cut trough the babble.

I know that, currently, there are 3 ways to make Atheros wifi work:

1) with the ath5k module that is on the linux-backports-modules-intrepid, and is the easiest solution on a brand new install.

2) install the madwifi driver nothingspecial mentioned above.

3) use ndiswrapper and the windows driver, which according to what Paul O'Keefe on that launchpad bug said, still has the best performance, but it also might be the hardest way to make it work. This is not listed on the wiki, but I think you might find it searching on the forums.

Plus, regarding your question about the driver working on the live disc but not on the upgrade, from what I could understand on that bug on Launchpad, it seems the driver on the live disc is indeed a different one, that was taken out soon after release because, for a Ubuntu developer, it was not fully working. It actually "seemed" to be working when it did not. So they decided to take it out and put a new version on the linux-backports-modules-intrepid package, which is a package where they release new drivers in between Ubuntu releases. Problem is they decided that and didn't announce anywhere. Ubuntu actually does not seem to have an "official announce channel", the ubuntu-devel list never shows up on Google search and even if it did, you would have to cut through the noise to find the information you want.

Regarding your /home, yes, making a backup and copying it over might probably work. The best solution is, during install, make /home on its own partition, so everytime you reinstall the system you preserve that partition and data. I left 16gb, which is a bit over what you will probably need, for the system and everything else for /home. Here's a nice blog entry about the subject: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

If you have any other question ask away, but as this post shows, I'm not sure I will be able to solve your problems... :P

---

### Post by ScottyJavea on 2008-11-08
Thanks, Nothing Special,

It worked a treat.

Best Regards,
Scotty in Javea, Alicante, Spain

---

### Post by directcharitycontribution on 2008-11-09
[http://ph.ubuntuforums.com/showthread.php?t=839215](http://ph.ubuntuforums.com/showthread.php?t=839215)

---

### Post by brodiesel on 2008-11-11
> **eks said:**
> brodiesel: I've read the thread but... I cannot fully understand the problem you are having. I've never seen a "software modem" listed anywhere, 

so, in the installed version, if i go to "Hardware Drivers" it only lists two: one is a graphics driver, and the other is listed only as "Software Driver." Here's the description:

> **evil death machine]
The smartlink software dameon.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.
[/QUOTE]

as i said, both times i tried to install this, (i don't know the code for it, so i used the Hardware Drivers), the computer crashed.

[QUOTE=eks said:**
> 
I know that, currently, there are 3 ways to make Atheros wifi work:
1) with the ath5k module that is on the linux-backports-modules-intrepid, and is the easiest solution on a brand new install.


where does one find the linux-backports-modules? i looked in software sources to no avail, and i am woefully inept at using command line (its a project of mine).

> **eks said:**
> 
2) install the madwifi driver nothingspecial mentioned above.


i actually have a madwifi driver installed. This is what I ahve installed:

madwifi tools version 1:0.9.4~rc2+dfsg-1
linux-restricted-modules: 2.6.22-14 generic version 2.6.22.4-14.9


is there a manner of enabling it i dont know about? why dont either of these show up on the hardware drivers list? do i have to remove one to get the other to work?
> **eks said:**
> 
3) use ndiswrapper and the windows driver, which according to what Paul O'Keefe on that launchpad bug said, still has the best performance, but it also might be the hardest way to make it work. 

this makes it the least likely for me to ever actually achieve success with. :)


> **eks said:**
> 
If you have any other question ask away, but as this post shows, I'm not sure I will be able to solve your problems... :P

thanks . i appreciate it.

---

### Post by blitzer on 2008-11-15
Fixed me up perfectly :guitar:

Thanks for your time and effort on our forums.

And Thanks goes to the linux community for just making it work and dealing with hardware venders   :lolflag:

> **nothingspecial said:**
> Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz	
```

Unzip it
```

tar -xvf madwifi-hal-0.10.5.6-r3861-20080903.tar.gz	
```


navigate to the extracted file

```

cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you`ve not got the tools necessary for compiling get them
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it

```
sudo make

``````

sudo make install
```

load the module/driver

```
sudo modprobe ath_pci
```

make it load every time you boot
```

gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file
```

ath_pci
```

save
exit 
reboot

---

### Post by dipaish on 2008-11-15
Atheros ath5k wireless driver not enabled by default

"The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. "

So inorder to enable type the following command in terminal mode 

deep@deep-laptop:~$ sudo apt-get install linux-backports-modules-intrepid-generic 


And disable any other wireless driver if enabled by going to system----administration--hardware drivers ---(in my case i need to disable support for atheros 802.11 wireless lan cards  )

Reboot and then enjoy ,,,you get ur wireless  working...

---

