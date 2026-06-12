---
title: "Wanted: Recommendation for Wireless PC Card"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by mdcollier on 2007-11-30
Just installed 7.10 on a Dell Inspiron 8200, and everything seems to be working fine except for my wireless PCMCIA card, which is ancient. My question has two parts,

What is the exact process to get Ubuntu to recognize and install plug and play? Does the card need to be installed during installation?

I'm looking for a PCMCIA card that will work out of the box with 7.10. I've seen some on the supported hardware list, but, frankly, the list is a bit dated. Can somebody recommend a card that is relatively new and relatively cheap?

Thanks in advance for your help.

MDC

---

### Post by rustybronco on 2007-11-30
[http://ubuntuhcl.org/pub/categories.php](http://ubuntuhcl.org/pub/categories.php)
> What is the exact process to get Ubuntu to recognize and install plug and play? Does the card need to be installed during installation?
install the os with the card plugged in.
no, it does not have to be plugged in, you can insert the card after the install.

open the terminal and post the output of,   
lshw -C network   and    lspci -nn

---

### Post by mdcollier on 2007-11-30
> **rustybronco said:**
> [http://ubuntuhcl.org/pub/categories.php](http://ubuntuhcl.org/pub/categories.php)
open the terminal and post the output of,   
lshw -C network   and    lspci -nn

Please bear with me. I'm a Windows refugee. What does this mean? I've got a couple of old cards that worked with V6, so I may try those first.

Thanks!

---

### Post by peepingtom on 2007-11-30
Look for one supported by the MadWiFI Drivers.

---

### Post by mdcollier on 2007-11-30
Must be my lucky day! Just ordered a Netgear WG311T, which ships with the madwifi driver. :)

---

### Post by insineratehymn on 2007-11-30
I installed it on an Inspiron 8200 as well, how do you like it so far? Were you able to get the video drivers installed all right?

As for the wireless card;
I use an ancient SpeedStream PCMCIA card, but Ubuntu detected it perfectly. If I really want to reach out and touch my neighbors network, I have this little 5 dollar USB WiFi with a 5 inch antenna. 

What kind of card is the old card you are trying to use?

---

### Post by rustybronco on 2007-11-30
> **mdcollier said:**
> Please bear with me. I'm a Windows refugee. What does this mean? Thanks! Go to applications>accessories>Terminal right click and add launcher to panel (after a while you will love having it there ) then cut and paste the output of what you get here. (cut ctl+c, paste ctl+v )
Windows refugee? how many of us do you think were former users, I'm betting a lot... I was 13 months ago, green as, well real GREEN! and now just half green.

---

### Post by mdcollier on 2007-11-30
I appreciate the help. I love the newer distros of linux. I'm was running Fiesty on this computer, then crashed it when I tried to install Gutsy. I just couldn't get a clean CD. I finally ordered a DVD from Amazon and haven't had any more I/O problems.

Anyway, the computer is a Pentium IV with 1GB of RAM, and it runs 2-3 times faster than my other notebook with a dual core AMD and 2GB running Vista.

I really hope we are turning the corner on the MS rebellion.

I don't mean to appear obtuse, although both my ex-wives say I am, but is what you're saying is to type the command at the command prompt and see what response the system returns?

Thanks again.

---

### Post by rustybronco on 2007-11-30
> **mdcollier said:**
> I don't mean to appear obtuse, although both my ex-wives say I am, but is what you're saying is to type the command at the command prompt and see what response the system returns?
Thanks again. Yes, then cut and paste the output... you can cut (ctrl+c ) the input from my post into the terminal (paste, shift+ctrl+v ) it will save typing mistakes.

---

### Post by mdcollier on 2007-11-30
> **insineratehymn said:**
> I installed it on an Inspiron 8200 as well, how do you like it so far? Were you able to get the video drivers installed all right?

As for the wireless card;
I use an ancient SpeedStream PCMCIA card, but Ubuntu detected it perfectly. If I really want to reach out and touch my neighbors network, I have this little 5 dollar USB WiFi with a 5 inch antenna. 

What kind of card is the old card you are trying to use?

The video installed fine. The old cards are a Uniden and a Netopia. I can't remember which one, but one of them worked with Feisty. They are old, old, old.

Given the success we had reviving my old Inspiron, we are shopping for components for other candidates for retirement. Since I'm heading up this little R&D project, I keep all the choice gear for my computers. I can't wait to get my grimy mitts on the new Netgear card. It's only fair... :rolleyes:

---

### Post by mdcollier on 2007-12-01
I can't tell if I'm making progress or not, but I am encouraged that the system is responding.

First of all, the Uniden card, a PCW 300, is making a connection to the network. But, I cannot start the computer with the card in. I was going to install again (why not, it's R&D), but the computer wouldn't start with the CD and the Uniden card. What is going on?

My wireless network is set for WEP security with a 10 digit number as the password. Works with my Windows computer fine. On the Linux notebook, I've tried setting the Password type to WEP key (ascii) and WEP key hexadecimal. Neither seems to work. If I put the device on roam, I get a list of the two networks in my range. I select mine, and the wireless security in the prompt is WEP 128-bit Passphrase. If I select any other security type, the Login to Network prompt greys out. I put in the 10 digit number, the card ponders life for a while, sometimes even showing a signal graph. All of this, but I can't access the Internet.

As always, I appreciate any assistance.

M

---

### Post by mdcollier on 2007-12-02
:confused: 

Okay, I'm a man on the verge... I tried a USB wireless device that I had stashed away, and Ubuntu seems to like it just fine. I can see my network, but still can not connect. I've even tried turning off security (forgive me Father for I have sinned) and still can't connect. Is this a hardware issue or a configuration issue? Should I just bag this for now until my new Netgear card arrives?

---

### Post by mdcollier on 2007-12-02
OK, OK, I officially give up. This is an exercise in frustration that I don't want to repeat when my new card gets here.

I'll be back...

---

### Post by rustybronco on 2007-12-02
> **mdcollier said:**
> :confused: 

Okay, I'm a man on the verge... I tried a USB wireless device that I had stashed away, and Ubuntu seems to like it just fine. I can see my network, but still can not connect. 
Is this a hardware issue or a configuration issue? Should I just bag this for now until my new Netgear card arrives?sorry not getting back soon enough, compiling the 2.6.23.9 kernel in my laptop (old satellite pro) because of acpi=force issues and repairing the drywall in the ceiling at my house, plus a host of other things.

can you post the output of lsusb with that usb wireless device plugged in when you get a moment.
in answer to you second question it's more likely a driver issue but who knows yet.
I'm going to get a chunk of drywall to fix the clothes chute hole in the wall, will be back later.

you can always read the link in my signature about connecting for the command line, if you have the time.

---

### Post by mdcollier on 2007-12-02
It's okay, rusty. No need in wasting your time until I get the system fully assembled. I got Gutsy installed and working, which was no small effort.

Besides, I can't post the output of those commands unless I'm connected to the network, which is the whole problem.

When the final piece to my Ubuntu dream machine gets here, I'll be back...

---

### Post by rustybronco on 2007-12-02
> **mdcollier said:**
> 
Besides, I can't post the output of those commands unless I'm connected to the network, which is the whole problem.
.ethernet port and cable ?, all I am looking for is the chipset, bcm4318 ect.
have fun with your new install. (i'm still compiling, 5 hours and still running )

---

### Post by mdcollier on 2007-12-02
I don't know how I did it, but I had all this working with Feisty. I am, however, learning about the subtleties of wireless cards, which will be a good thing as I bring more of our Windows notebooks out of retirement.

As much as I hate to, I just need to cool my heels until the new card gets here.

(It did occur to me to hook up the computer with an ethernet cable, but that just seemed like a lot of work for a card I don't plan to use longer than a week.)

Thanks so much for the help. Like I said, I'll be back...

---

### Post by bliffle on 2007-12-02
It's not worthwhile wasting time on no-work Wifi cards. I picked up an Airlink101 PCMCIA card for $30 that's worked in every thinkpad I've tried it in.

---

### Post by rustybronco on 2007-12-03
> **bliffle said:**
> It's not worthwhile wasting time on no-work Wifi cards. I picked up an Airlink101 PCMCIA card for $30 that's worked in every thinkpad I've tried it in.The irony of the situation is, when I compiled my kernel... I lost wireless!

---

### Post by rustybronco on 2007-12-03
> **bliffle said:**
> It's not worthwhile wasting time on no-work Wifi cards.  on the contrary, it can help others, thats why I buy them and try them.

---

### Post by kevdog on 2007-12-03
When you compile your kernel you have the option to select a handful of linux drivers that are available.  Some of these drivers (from what I can remember -- its been a while) are the ipw2200, ipw 2100, bcm43xx (not the firmware part however), orinoco, prism, and a few others.  Im finding the majority of users do not have devices with these chipsets.  The ra drivers, broadcom firmware, and madwifi (atheros) kernel modules are not included in the vanilla kernel.  Ubuntu developers included these when they built their kernel. 

For an average user, if you compile your own vanilla kernel, you would have to compile your wireless card's drivers also, and add them to a kernel as custom kernel module.

Hope this helps.  It confused me the first time I found this out.

---

### Post by rustybronco on 2007-12-03
> **kevdog said:**
> 
For an average user, if you compile your own vanilla kernel, you would have to compile your wireless card's drivers also, and add them to a kernel as custom kernel module.

Hope this helps.  It confused me the first time I found this out. Kevdog it was my first attempt at it and having done it I have a better understanding of what it takes to do it. at least I got my acpi=force back and all the funtions like processor fan control.
yes I am going to compile the bcm4318 and acx111 drivers into the kernel.
***HI-JACK THREAD*** I think i will get the 7.10 source and down grade acpi to 7.04 level and compile that, what do you think?

---

### Post by kevdog on 2007-12-03
Glad you are branching out -- I needed to compile my first kernel like 9 times before I figured out what I was doing -- there were just so many options.  Needless to say, I really havent revisited the issue since.  I really didnt find anything new or great or any speed performance with my custom kernel.

For your broadcom card you use ndiswrapper??

acx111 -- Hmm cant remember the chipset for this one -- I dont run across this one to often.

---

### Post by rustybronco on 2007-12-03
> **kevdog said:**
> Glad you are branching out -- I needed to compile my first kernel like 9 times before I figured out what I was doing -- there were just so many options.  Needless to say, I really havent revisited the issue since.  I really didnt find anything new or great or any speed performance with my custom kernel.

For your broadcom card you use ndiswrapper??. I don't use at all. 7.10 it works native

> acx111 -- Hmm cant remember the chipset for this one -- I dont run across this one to often. T.I. acx-111 is the chipset, sorry I didn't make that clearer.

---

### Post by mdcollier on 2007-12-13
Hoo Ahh! My Netgear WG511TNA came in last night, and everything is sunshine and puppy dogs! I am cruising the net at scorching speed. Ubuntu automatically recognized the card, I put the device in roaming mode, connected, and I'm off to the races. I did, in frustration, turn off security (gasp), but I live out in the sticks. I will resolve this just because, well, it's there.

Many many thanks to everybody for their suggestions. I'm as happy as a kitten with a Q-Tip...

---

