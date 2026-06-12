---
title: "Problems with Broadcom 4310 wireless and ndiswrapper"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by NubKnacker on 2006-10-06
Over the last two days I have read several tutorials on how to use ndisrapper to install windows wireless adapters under linux and I have run into a problem with ndiswrapper which doesn't seem to have a solution which I can search for. I am a relative newbie to linux so please bear with me.

I upgraded my system to the latest kernel as well as other parts which the updater asked me to install by plugging my laptop into the router via ethernet. I also uninstalled ndiswrapper included with ubuntu, downloaded the latest version from sourceforge and installed it, all that went fine.

I copied over my windows laptop wireless driver([http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&cc=in&dlc=en&os=228&product=3195466&lang=en&softwareitem=ob-41607-1]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&cc=in&dlc=en&os=228&product=3195466&lang=en&softwareitem=ob-41607-1")) onto a folder under my home directory and then ran ndiswrapper on the inf file using "ndiswrapper -i bcmlw5.inf". ndiswrapper brings me to a prompt which says, "_DB_" and I have no idea what to do after this.

My laptop is a Compaq presario 3029AU with nvidia chipset. What should my next step with ndiswrapper be?

---

### Post by brainfry on 2006-10-06
Are you using 32bit or 64? I've got a HP Pavillion dv5046ea with an AMD Turion 64 running XP home. The drivers for that are 32 bit so they won't work in my Dapper 64 bit install. I got the driver from here [http://www.planetamd64.com/index.php?showtopic=21723](http://www.planetamd64.com/index.php?showtopic=21723) following the instructions. My card is a Broadcom bcm4318 and works fine if I don't use WPA PSK encryption which is the next step I want to sort out (nearly there!](*,))
Hope any of this helps

---

### Post by brainfry on 2006-10-06
Just re read your post and noticed you used bcmlw5.inf in your ndiswrapper command. The file name is bcmwl5.inf. I'm only checking to make sure you typed the right filename in case that's the reason it went wrong. :D

---

### Post by NubKnacker on 2006-10-07
Yeah, I typed it wrong in my post but correctly while trying to install the drivers.

3029 is AMD Turion 64 as well but i'm using the 32 bit version of ubuntu.

---

### Post by brainfry on 2006-10-07
Ok, I've literally just got this working after another re install this morning.
My differences are 64bit Dapper, ndiswrapper installed via Synaptic and a bcm4318 card but this is what I did;
sudo gedit /etc/modprobe.d/blacklist - added blacklist bcm43xx to make sure the native driver isn't loaded at boot I then rebooted and checked the network settings to make sure eth1 or wlan0 weren't listed.
sudo ndiswrapper -i bcmwl5.inf which installed the driver
ndiswrapper -l which should say the driver and hardware are present, if you get that, it should be good.
sudo modprobe ndiswrapper - which should say it's adding alias wlan0 to /etc/modprobe.d/ndiswrapper (or words to that effect, tried allsorts to get this working and seen a lot of messages)
I then opened network settings (system > admin > network) and my card was listed as wlan0. I selected it, click properties and added my essid and wep key (not figured wpa_supplicant yet but now i've got wireless it's next on my list) and clicked ok. I changed the default gateway device to wlan0 and clicked ok followed by a reboot.
During boot, the wireless light came on and I'm now writing this over the wireless connection.
One weird point though, on reboot, the card is listed as eth1 instead of wlan0, but it works, so I'm going to see how everything pans out.
Hoped any of this helps.

---

### Post by NubKnacker on 2006-10-07
This is what I get 
```

gaurav@gaurav-laptop:~/Wireless$ ndiswrapper -l bcmwl5.inf

Loading DB routines from perl5db.pl version 1.28
Editor support available.

Enter h or `h h' for help, or `man perldebug' for more help.

main::(/usr/sbin/ndiswrapper:26):       my $WRAP_PCI_BUS = 5;
  DB<1>

```

DB<1> is a prompt where I can type, I don't know what to do with it. :(
Thanks fo all your help till now fry, really appreciate it.

---

### Post by brainfry on 2006-10-07
No probs, sorry I can't help more but I'm a noob with this wireless. It's taken me weeks trying different distro's and different methods. In the end I dropped my router encryption from WPA PSK to WEP and it seems to be behaving (works just as well in Dapper as it does in Windows)
I noticed you compiled ndiswrapper yourself. Nice one, I tried that in FC5 and just kept getting errors which is why I downloaded ndiswrapper-utils using Synaptic and went from there. Maybe thats the way to go for you.
Sorry I can't help you anymore but good luck with it.

---

### Post by lyceum on 2006-10-07
I am having the same problem. I am not totally at the solution yet, but here is where I'm at. First, Compaq's drivers page is not complete. Go to Broadcom and down load their Linux drivers from source. From there you will have to compile everything yourself. ](*,) It is not as hard as it sounds, they have directions. However, you will need to go to termanal first and :

sudo apt-get install build-essentials

After that, skip down on their instructions to the installing from tar part. I waisted too much time trying to figure out what the first part was talking about. I guess it is for red hat? A friend of mine who knows nothing about computers looked further down the page and pointed out that I had been waisting my time. ](*,) 

That is as far as I've gotten, I have not had time to do more. I desided to put Edgy on so I could upgrade from beta later this month, so I am starting over. I will let you know more after I get it working. Let me know if you get further than I did, I won't be jumping back on mu laptop 'til tomorrow. Hope this helps!

---

### Post by InCheck Adam J on 2006-10-08
I am having a similar problem as well. After loading ubuntu on the laptop I purchased yesterday and finding out of this problem I loaded it from the cd onto my HP laptop and its wireless worked perfect. Solution to me was to return it and buy a different laptop. However Fry's decided to not return it because I deleted Windows. 

So I tried using ndiswrapper and got it installed, called HP/Compaq to find out what device was in my laptop and they didn't know!!! I decided to try the linux drivers off the Broadcom site and it appears to say its working but it is still using the old driver. Anyone know how to dispose of the previous driver? Or maybe a better solution for this? Thanks for the good advice so far, it has helped alot of us.

---

### Post by NubKnacker on 2006-10-08
This is really weird, lspci says that my card is a "Broadcom Corporation 4310 UART" but there is NO 4310 on the broadcom site, I have gone through the entire product list. A google search on their site also doesn't turn up anything. I thought I was lost before but ....

---

### Post by NubKnacker on 2006-10-08
Could someone more knowledgable about Linux please tell us how to get out of the DB prompt problem. if I can get past that step I can find out if the method works or not....

---

### Post by lyceum on 2006-10-08
I loaded Edgy onto my computer and my Broadcom WiFi now works. Just switch to Edgy and you will be fine. I know it is beta, but it should be ready by the end of the month, so rather and go down the long hard roads, you may want to wait for the easy path. :-D If you are in a hurry, get the beta now. It is REALLY nice. 
I am sorry I can't help you more, but networking and compileing from source are not my greatest field of knowledge.

---

### Post by lyceum on 2006-10-08
Sorry, one more thing. If you make the switch to Edgy and need help setting up your WiFi, let me know and I will post a walk through right here of what I did to get everything working so you don't have to keep looking around the forum. Like I said, I am not an expert, but I am writting down what I am doing in case I need the info again.

---

### Post by InCheck Adam J on 2006-10-08
That is the UART on your wireless card, not the card itself I would imagin. UART is just one piece of hardware on your chip. It stands for Universal Asyncronous Receive/Transmit which is used for all communication types (232, 485 etc) You are probably using the Broadcom BCMxxxx card of some type.

---

### Post by NubKnacker on 2006-10-09
Edgy it is then, a laptop without wireless defeats the purpose of the laptop alltogether.

Anyway, I really want to switch over to ubuntu asap so I have a handle on things (I'm still a newbie to linux) by the time vista comes out.

---

### Post by NubKnacker on 2006-10-14
Some good news, I just installed Edgy on my laptop and it detects my card just fine. :) I was really smiling from ear to ear when I saw the wireless card but I have other problems now, problems I think are Edgy specific. Just wanted to let you guys know that edgy atleast detects the card.

---

### Post by lyceum on 2006-10-15
Not that I have gotten a handle on things I can say that the problem with laptop wifi (mine anyway) has nothing to do with Edgy, it is a problem from Broadcom. I guess they have support for Linux detection but not for Linux use? From everything I have read, manufactures use Broadcom parts in the laptops, as it is a cheap (cost) part. But it is not a good choice if you want to use Linux. I opened my box up and it does not look too hard to replace. If you want to use Linux on your laptop, Ubuntu works great, just make sure your parts are Linux compatible, just like you would a desktop PC. I have found unlike a desktop, it is hard to walk into a store and just pick up internal parts for a laptop, other than the memory or hard drive.

---

### Post by lzwcomp on 2006-10-17
I too am having a similar problem.  I've installed the broadcom driver into ndiswrapper.  I can connect to my access point only if I have no security enabled.  The NetworkManager applet sees my access point (as well as others) but if I enable WEP in any of its options (Open/Shared, 64bit/128bit, different channels, etc.) my laptop will not connect.

My laptop is a HP nx6325.  I'm running 32bit Edgy Eft.  If anyone has a pointer on what it would take to get wireless working with WEP, I would greatly appreciate it.

Fred

---

### Post by x64Jimbo on 2007-02-12
Ok, so I'm seeing similar problems on my nx6325 laptop. The broadcom card is on-board, not replaceable (i opened up the panel on the bottom). 
I have downloaded the drivers from HP, cabextracted them, deleted the AMD64 directory so that it can't use the wrong driver (Edgy 32 bit) and then did this:
$ sudo ndiswrapper -i bcmwl5.inf
$ sudo ndiswrapper -l
bcmwl5          driver installed, hardware present 
$ sudo modprobe ndiswrapper
$ ifconfig -a
lists only eth0, lo, and sit0
I have already blacklisted the kernel module for the bcmw43xx, so that's why it doesn't show up in there for that, but shouldn't ndiswrapper be loading an interface into ifconfig? I have rebooted and re-tried over and over. 
The blue light on the wlan button turns on and off when I press it, so something must be working correctly. Anyone have any ideas?

---

