---
title: "I need network drivers for an HP DC7600 - Please help"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Trebz50 on 2009-11-09
Hi All

New to the forum and Ubuntu...

I just installed Ubuntu onto an HP DC7600 and as i feared it does not recognise the onboard network device.

I also installed it onto my Samsung R60 laptop and it's the same, it does not have drivers for the laptop network device.

I wanted to have a look at Linix to see if it was better than Windows but im not liking it so far. It does not recognise any of the devices on my motherboard.

Can anyone help?

I only really need the network device drivers.......

Thanks in advance.

Trebz

---

### Post by sdpiowa on 2009-11-09
First of all, what version of Ubuntu did you install?

Did you try the Live CD before you installed?

---

### Post by Trebz50 on 2009-11-09
Hello...

Thanks for the prompt reply.

I borrowed the installation CD from a friend, it states Ubuntu 10.01 on the disk.

Im sorry to say that i opted for the straight installation so no, i didn't run the 'Live CD'.

:-(

---

### Post by egalvan on 2009-11-09
> **Trebz50 said:**
> ...

I borrowed the installation CD from a friend, it states Ubuntu 10.01 on the disk.


First...
No such thing as Ubuntu 10.01

Next, are you talking about the wireless network,
or the wired network?

And what else is not detected on the motherboard?

---

### Post by Trebz50 on 2009-11-09
> **egalvan said:**
> First...
No such thing as Ubuntu 10.01

Next, are you talking about the wireless network,
or the wired network?

And what else is not detected on the motherboard?

Yes, you're right, no such thing as 10.01, i just downloaded the latest version '9.10' from the Ubuntu website. I am part way through installing it on the DC7600 so i can't tell you which devices are not recognised yet.

I meant the wired network. I have my other Windows PC (typing on it now hehe) up and running so i know the network is ok, when i installed the 'other' version of Ubuntu i could not get the internet via Mozilla or see the usual green light on the onboard network device.

---

### Post by egalvan on 2009-11-09
So it's a wired network card?

I can tell you this....

in the close to one hundred Linux installs I have done,
on HP, Dell, IBM and others, both desktops and laptops,
I have never, not ever, had Linux not find the ethernet adapter.
From ancient 10Bt (10Mb) to the latest 1000Bt (1000Mb) (giganet)
Never failed once.

Can't say the same about wireless... :)

Although even there, it's been far more hits than misses.

I use an HP Media Laptop, Pavilion DV8135NR, and *everything* was detected out-of-the-box...
all media controls, all lights, wireless nic, wired nic, usb, firewire, card reader.... *everything*.

---

### Post by Trebz50 on 2009-11-09
Ok, understood, i'll cross my fingers for the new install then hehe.

I'll have a chat with my 'Friend' about his 10.01 install CD !!

I can only think that the version he gave me was a veeeery old one.

I'll post my findings here when im done.

Should i expect, post installation and re boot, that the network device will be auto detected and active. Should i just be able to 'Plug and Go' with a network connection. I only ask this as the DC7600 i am using has been in storage for over a year and may be faulty.

Thanks for the info matey.

Trebz

---

### Post by coffeecat on 2009-11-09
**Trebz50**, let's get some things straight about your network connection.

When you say "wired", do you mean the ethernet connection? If so, just plug it in and **it will work**. You don't even have to do anything. If you are using the ethernet connection and you are not getting onto the internet, either you have done something wrong, or the cable is faulty, or the router is faulty.

Next...

If by "wired" you mean the dial-up modem, then please say so. This will be a different matter and we will need more information.

And if you really do mean wireless, then in all probability it will work out of the box, but some wireless chipsets are problematic, but not unsolveable. Again we need more details.

Perhaps you could clarify.

---

### Post by Trebz50 on 2009-11-09
> **coffeecat said:**
> **Trebz50**, let's get some things straight about your network connection.

When you say "wired", do you mean the ethernet connection? If so, just plug it in and **it will work**. You don't even have to do anything. If you are using the ethernet connection and you are not getting onto the internet, either you have done something wrong, or the cable is faulty, or the router is faulty.

Next...

If by "wired" you mean the dial-up modem, then please say so. This will be a different matter and we will need more information.

And if you really do mean wireless, then in all probability it will work out of the box, but some wireless chipsets are problematic, but not unsolveable. Again we need more details.

Perhaps you could clarify.

A quick reply as dinner is ready...

I mean the Ethernet RJ45 / CAT5 connection from the PC to the router NOT wireless..

I am using a CAT5 patch lead which has been tested and is working fine on my Windows desktop PC.

The router is fine as i am using it now to message you all. The girlfriends laptop is connected wirelessly downstairs so it can't be a problem with the router.

Back soon.....

NOM NOM NOM

---

### Post by egalvan on 2009-11-09
> **Trebz50 said:**
> Ok, understood, i'll cross my fingers for the new install then hehe.

"Crossed fingers have a powerful influence on weak hardware"

> 
I'll have a chat with my 'Friend' about his 10.01 install CD !!

I can only think that the version he gave me was a veeeery old one.


It's either 

January 2010
or
October 2001

neither of which exist as Ubuntu releases... :)

> 
I'll post my findings here when im done.

Should i expect, post installation and **re boot** (sic), that the network device will be auto detected and active. Should i just be able to 'Plug and Go' with a network connection. I only ask this as the DC7600 i am using has been in storage for over a year and may be faulty.

Thanks for the info matey.
Trebz

Have the network cable connected to a working Internet setup, while the install is running.
If the hardware is working, odds are *very* good that it will be detected.

And re-boots under *nix are rare birds...
Machines have0 been known to run months, even years, between re-boots.
Yes, *nix *is* that stable.

Also remember that some laptops have a hardware switch to turn the **wireless** network card on and off. I've *never* seen one for a **hardwire** one, but it never hurts to look, hey?

---

### Post by coffeecat on 2009-11-09
> **Trebz50 said:**
> A quick reply as dinner is ready...

I mean the Ethernet RJ45 / CAT5 connection from the PC to the router NOT wireless..

I am using a CAT5 patch lead which has been tested and is working fine on my Windows desktop PC.

The router is fine as i am using it now to message you all. The girlfriends laptop is connected wirelessly downstairs so it can't be a problem with the router.

Excellent! It will work - both machines. Enjoy your dinner. :wink:

---

### Post by egalvan on 2009-11-09
> **Trebz50 said:**
> A quick reply as dinner is ready...

Back soon.....

NOM NOM NOM

You abandon your machine and Ubuntu for food???
Such a lack of discipline...
such heresy...
this will make your journey to Linux Ranger most difficult.

Allowing yourself to be turned away by mere sustenance...
now a "come-hither" look from a bonnie lass, aye, now that is another thing, mate.

But *food*???

What is this new generation of geeks coming to???

:lolflag:

---

### Post by Trebz50 on 2009-11-09
Hehe

Im 40 years old in April....and im a 'Windows' techie.....

*Is Shamed*

I feel like a new born with all this Linux malarkey.

You'll be glad to know that the Ubuntu box is now on the network and running fine. I re tested the CAT5 patch and it was faulty !!! Replaced it and all is well.

I now have Nagios installed and 'nearly' running. What a load of faffing about. Half of the instructions don't work properly !!

Error 404 shown when accessing the Web GUI via [http://localhost/nagios](http://localhost/nagios)

But then thats another problem altogether...guess i'll be off to the Nagios forum now heheeh

And as for your comment about food.... we had smoked Finney Haddock, steamed carrots and peas with boiled potatoes drowned in black pepper and butter.

Believe me, it was worth the time out hehe

Cheers for the help lads. Im sure i'll be back...... ;-)

---

