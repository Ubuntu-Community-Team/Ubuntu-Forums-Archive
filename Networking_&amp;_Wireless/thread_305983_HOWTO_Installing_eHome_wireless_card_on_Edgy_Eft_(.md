---
title: "HOWTO: Installing eHome wireless card on Edgy Eft (the $1.99 CompUSA special)"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by megamark16 on 2006-11-24
Hey everyone, I am a Linux newbie but I actually got something to work by tweaking several different posts and walk throughs and since this card is so cheap ($1.99 after rebates) and I couldn't find anything specific to the card itself, just other cards with similar chipsets, I thought I would post a HOWTO to hopefully help any others who have this same card.  

Here's the info on the card: 
Box Name: eHome Wireless G Notebook Adapter
Model: EH101

As it shows up in the Device Manager of Ubuntu:
Vendor: Marvell Technology Group Ltd.
Device: 88w8335 [Libertas] 802.11b/g Wireless
OEM Vendor: D-Link Systems Inc.

So Linux detected it but doesn's automatically install any drivers for it so it won't show up under the Networking utility.

Just for reference, I'm running Ubuntu 6.10 Edgy Eft on a Toshiba Tecra8000 laptop with 256MB ram.

Here's what I did:
I installed "ndiswrapper" off of Synaptic Package Manager.

I put the driver CD that came with it in the cdrom drive.

I opened up a Terminal screen and typed the following: 
```
cd /cdrom/driver/winxp_2k (browse to the location of the driver file)
sudo ndiswrapper -i mrv8335.inf (your INF file name may vary)
sudo ndiswrapper -l (shows if the driver installed successfully, this should show "mrv8335 - driver installed, hardware present)
sudo ndiswrapper -m (write the configuration to modprobe)
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```

And after I did this it popped up under my device manager as a network device.  I rebooted to make sure that it would stick and it did, now I haven't tried connecting to anything wirelessly yet because I'm at work and there aren't any wireless connections nearby, but when I get home I'll try it on my home network and let you know if I run into any problems.  

I hope this HowTo is helpful to anyone who purchased one of these little gems (at least I'm hoping it's a gem, for $1.99 it's sure looking like one...).  Also if anyone sees any mistakes, I wrote this up from memory of what I did, so let me know if you have any problems.

Thanks
Mark Ransom

---

### Post by greghmerrill on 2007-01-07
Great post!  I have an eHome wireless adapter (desktop variety), and these instructions worked for me, to the letter.  

Thanks,
Greg M

---

### Post by dsegarra on 2007-01-15
was that desktop version a 64bit??

---

### Post by Pitbull11188 on 2007-01-28
Thanks alot!!!!!! Believe it or not I found this post at first while I was in CompUSA browsing the net on one of their laptops looking to see if the ehomes adapters were compatible with linux. :D This was perfect.

---

### Post by Ajd on 2007-01-30
I got  the USB adapter to work with similiar steps.

---

### Post by celloyd on 2007-07-31
> **megamark16 said:**
> Hey everyone, I am a Linux newbie but I actually got something to work by tweaking several different posts and walk throughs and since this card is so cheap ($1.99 after rebates) and I couldn't find anything specific to the card itself, just other cards with similar chipsets, I thought I would post a HOWTO to hopefully help any others who have this same card.  

Here's the info on the card: 
Box Name: eHome Wireless G Notebook Adapter
Model: EH101

As it shows up in the Device Manager of Ubuntu:
Vendor: Marvell Technology Group Ltd.
Device: 88w8335 [Libertas] 802.11b/g Wireless
OEM Vendor: D-Link Systems Inc.

So Linux detected it but doesn's automatically install any drivers for it so it won't show up under the Networking utility.

Just for reference, I'm running Ubuntu 6.10 Edgy Eft on a Toshiba Tecra8000 laptop with 256MB ram.

Here's what I did:
I installed "ndiswrapper" off of Synaptic Package Manager.

I put the driver CD that came with it in the cdrom drive.

I opened up a Terminal screen and typed the following: 
```
cd /cdrom/driver/winxp_2k (browse to the location of the driver file)
sudo ndiswrapper -i mrv8335.inf (your INF file name may vary)
sudo ndiswrapper -l (shows if the driver installed successfully, this should show "mrv8335 - driver installed, hardware present)
sudo ndiswrapper -m (write the configuration to modprobe)
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```

And after I did this it popped up under my device manager as a network device.  I rebooted to make sure that it would stick and it did, now I haven't tried connecting to anything wirelessly yet because I'm at work and there aren't any wireless connections nearby, but when I get home I'll try it on my home network and let you know if I run into any problems.  

I hope this HowTo is helpful to anyone who purchased one of these little gems (at least I'm hoping it's a gem, for $1.99 it's sure looking like one...).  Also if anyone sees any mistakes, I wrote this up from memory of what I did, so let me know if you have any problems.

Thanks
Mark Ransom

Are you still using and having success with this card?  I'm not able to get security set up on it...

---

### Post by bob365 on 2007-09-03
i am new to linux. how do you install ndiswrapper? thanks

---

### Post by don durito on 2007-09-03
Hi,

just open add and remove software and search for ndiswrapper. Then just check the checkbox and accept with apply.

But why do you need ndiswrapper. And who knows perhaps there is an easier why to install your wireless card. 
If you don't know the chipset of your card just type ```
lspci
``` into your terminal and search for your wireless card. post your wirelless output here and i am sure you ll find some help.

---

### Post by bob365 on 2007-09-03
i am using an eh101 card. and thanks so much for the installation help.

---

### Post by bob365 on 2007-09-03
Thank you!! I got it to work!

---

### Post by chetanw on 2008-01-09
Thanks a ton!!

I used exactly the above steps and got it to work. Now I'm struggling with the WPA

BTW, I used it with Gutsy on a desktop.

---

### Post by NoThanksM$ on 2008-02-25
Anyone else have some difficulties with this in Gutsy?

It worked flawlessly for me in Feisty, but after upgrading to Gutsy my wireless connection was broken.  After much troubleshooting, I determined that it would only work if I broadcasted my SSID and shortened it as well.  (I shortened it to 8 characters with no spaces - previously it was about twice as long with a space.  I'm not sure exactly how long I could have made it but I know for sure that shortening it vs not made a difference.)

It didn't seem to matter in my testing, but I'm using WPA.

---

### Post by psainsbury on 2008-03-13
Hey,

Just wanted to say Thanks for a great post... even though I have an Asus WL-169gE, I hadn't found the modprobe stuff elsewhere, so this post helped me a lot.  Now I have a working USB wifi adapter.  

In case anyone with a WL169-gE ever reads this, you need to also follow the steps on the NDISWrapper sourceforge page at - [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)  (or just search in the list of supported cards for the correct card/device and follow the instructions.  

Before running "sudo ndiswrapper -l", I had to copy the files into the locations specified in the sourceforge page.

From
  Paul

---

### Post by flypen on 2008-05-01
Just want to thank you again for the OP. 

I used these instructions to successfully install the eHome card on both Gutsy (6 months ago on a Thinkpad T21) and now Hardy (on a Thinkpad T23). 

Not that it should have a problem, but just want to let you know that I had no problems in both Gnome(Ubuntu) and Xfce (Xubuntu). Hopefully, the hibernation works properly too. Had a little issue the first time around.

---

### Post by OMEGA303 on 2008-06-23
hi

cd /cdrom/driver/winxp_2k (browse to the location of the driver file)
sudo ndiswrapper -i mrv8335.inf (your INF file name may vary)
sudo ndiswrapper -l (shows if the driver installed successfully, 
    this should show "mrv8335 - driver installed, hardware present)
sudo ndiswrapper -m (write the configuration to modprobe)
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

I did this in Ubuntu 7.4 everything went fine i boot the computer and the card turn on automatically, but in Ubuntu 7.10 i follow that same instructions because the installation took out the driver and went i turn the computer the card doesn't turn on any more, and i have to keep doing this part to turn the card on went i boot the pc:

sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

how I am able to save this so the card turn on went the machine stars any help would be nice!!! right at this moment I am installing Ubuntu 8.4 :confused: hope that it re-cornice the configuration again:)

---

