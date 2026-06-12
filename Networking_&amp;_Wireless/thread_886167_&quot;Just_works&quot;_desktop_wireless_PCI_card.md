---
title: "&quot;Just works&quot; desktop wireless PCI card?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by Bartender on 2008-08-10
Good day!
Does anyone know of a desktop PCI or PCI Express wireless card that just works out of the box?
Looking at the numerous PCI wireless cards on Newegg, it looks like most of them are Broadcom or etc.  I don't want to screw around with patches.
Can you even get an Intel wireless card on PCI?

---

### Post by pytheas22 on 2008-08-10
Most Atheros cards work well out-of-the-box--but there are a few exceptions, so if possible figure out exactly what the chipset model is and google it before buying.  Broadcom cards are also not bad these days.  I would actually prefer Broadcom over Intel, because it seems that every other update breaks the Intel wireless drivers.  I think Ralink may also have a chipset in PCI cards, which should work well.  Prism should be good, too.  Realtek has good native Linux drivers, but I don't think they're in the Hardy kernel, so you may want to stay away from that.

In general, just find out as much as you can about the card before buying--including the exact chipset model--and google first, and you should be alright.

---

### Post by 2CV67 on 2008-08-11
I just bought an Edimax EW 7128g with RT2561 chipset which is supposed to work “out of the box” with Hardy or up to date Gutsy, according to Linux Emporium [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/) and confirmed by Edimax Europe.

It worked immediately for me with Gutsy, but is currently proving very spotty (see my thread [http://ubuntuforums.org/showthread.php?t=886480](http://ubuntuforums.org/showthread.php?t=886480)).
It is perfect in XP…

I guess I could not recommend it at the moment, but the problem is probably mine!
I will update this if/when I find a fix. (hint!)

---

### Post by Bartender on 2008-08-12
> **pytheas22 said:**
> I would actually prefer Broadcom over Intel, because it seems that every other update breaks the Intel wireless drivers.

Well, I keep learning,but my experience has been the opposite.  The 4965 has been there for me thru several kernel updates.  I managed to get a Broadcom card working on my Dad's HP for a few minutes with madwifi until downloading the latest kernel update.  Then it was back to the drawing board again.

---

### Post by pytheas22 on 2008-08-12
> Broadcom card working on my Dad's HP for a few minutes with madwifi until downloading the latest kernel update.

I think you must be a little confused :) ... madwifi is for Atheros-based cards.  The driver for Broadcom cards in Hardy is named b43; in earlier releases of Ubuntu, it was bcm43xx (which is still in the Hardy kernel but is disabled by default).  Getting Broadcom cards to work can be confusing because there are these two different drivers, and while b43 works for most cards, there are some exceptions.  But once you figure out which driver supports your card, it's not hard.  You also need to get the firmware installed, which I guess adds to the confusion for a lot of people.

Also, Broadcom just reversed its years-long anti-Linux stance and released its own drivers (b43 and bcm43xx are reverse-engineered by the community); this [thread]("http://ubuntuforums.org/showthread.php?t=880218") has details on installing them.  I'm told that as Canonical works more with Broadcom and gets it to stop being so fascist about Linux support, Broadcom cards should be easier and easier.

That said, I guess Intel probably is the way to go as long as the updates don't break it.  I don't have any Intel cards myself; I just seem to read a lot here about bad updates on the Intel drivers.  But if it works for you, then I'd go with that...or Atheros, which does work well when madwifi supports it.

---

### Post by 2CV67 on 2008-09-09
Just an update on the Edimax 7128g PCI card with RT2561 chipset which was supposed to work out of the box with Gutsy & Hardy.

With Gutsy the connexion kept dropping out & eventually (long story) I was persuaded to upgrade to Hardy.

With Hardy it worked OK for a time, then I started getting freezes with Caps-Lock & Scroll-Lock flashing, every few hours or so.

After another long story I had to upgrade rt61pci from installed version (2.0.10) to a version (2.1.4) only available via backports...

Now it works OK but this is not what I call "just works" even by Ubuntu standards.
Presumably it will revert to freezing at the next Ubuntu update...

So cross this one off, until the updated rt61pci is included with an Ubuntu update.

Out of curiosity & when/if I need another one - I would sure like to see some clear "yes" answers to this crucial thread!

---

### Post by pytheas22 on 2008-09-09
>  	
Re: "Just works" desktop wireless PCI card?
Just an update on the Edimax 7128g PCI card with RT2561 chipset which was supposed to work out of the box with Gutsy & Hardy.

With Gutsy the connexion kept dropping out & eventually (long story) I was persuaded to upgrade to Hardy.

With Hardy it worked OK for a time, then I started getting freezes with Caps-Lock & Scroll-Lock flashing, every few hours or so.

After another long story I had to upgrade rt61pci from installed version (2.0.10) to a version (2.1.4) only available via backports...

Now it works OK but this is not what I call "just works" even by Ubuntu standards.
Presumably it will revert to freezing at the next Ubuntu update...

So cross this one off, until the updated rt61pci is included with an Ubuntu update.

Out of curiosity & when/if I need another one - I would sure like to see some clear "yes" answers to this crucial thread! 

As a side note: your card would probably work well if you installed the Ralink legacy drivers from [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads").  The drivers that ship with Ubuntu are the "next-generation" set and tend to have more problems.  The legacy drivers have been around for a long time and are solid (why Ubuntu doesn't use the legacy drivers by default is beyond me...eventually the next-generation set will have fancy features like access-point mode, but as of now none of that works, and in some cases, like yours, even managed mode doesn't work reliably).  If you don't know how to install the legacy driver, let me know.  Also remember that you will need to blacklist the next-generation drivers for the legacy ones to work.

---

### Post by 2CV67 on 2008-09-10
Thanks - I really appreciate your offer!

For the moment, I will stay with what I have because it is working OK now.
May come back to you next time Ubuntu updates...

I mainly wanted to avoid having to go through complicated special installations - that was why I dropped my troublesome old USB device (many guides say Linux users should avoid USB wireless) & went to great lengths to buy & install a PCI device which was "guaranteed" to work "out of the box" by a Vendor (Linux Emporium) & by its manufacturer (I contacted Edimax & they confirmed, before I bought it).

For all the Ubuntu dummies like me who just want (need) to get hassle-free wireless connexion, then there ought to be a short list (at least one!) of devices which will absolutely, no doubt about it, work OK straight off with current Ubuntu.
Even if it is an expensive device!
It would be nice to have a choice, but I don't want a list of ifs & buts, I have spent hours & hours with lists like that of maybe-compatible hardware.

The title of this thread looked like exactly what I was looking for, but does not seem to have produced the required answer yet!

Thanks again!

---

### Post by AndyCee on 2008-09-10
TP-link PCI card worked for me OOTB. I can't remember which one, off the top of my head. Hardware was recognised instantly, driver was downloaded and BAM!

---

### Post by Marshal0505 on 2008-09-10
Atheros DWA 556 or any other card with an AR5418 chip will work.Mine works great and i bought this one because of its good driver support under Linux.
Decision mainly based on this

[http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for)

---

### Post by 2CV67 on 2008-09-10
Thanks!

So do I count those as:
One "Yes but not sure which one"
One "Yes but need to install lots of stuff first" ? ;)

Sorry for that non-constructive remark!

Seriously, does Atheros DWA 556 "just work" or do you need to follow the links provided & instructions like> Get the code

ath9k is part of wireless-testing now.

To build wireless-testing, use the instructions in this page: en/users/Download

Enabling ath9k

To enable ath9k, you must first enable mac80211:

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

You can then enable ath9k in the kernel configuration under

Device Drivers  --->
  [*] Network device support  --->
        Wireless LAN  --->
          <M>   Atheros 802.11n wireless cards support

That may not be too difficult (??) but is not my idea of "just works"...

---

### Post by transporter_ii on 2009-02-01
> **2CV67 said:**
> For all the Ubuntu dummies like me who just want (need) to get hassle-free wireless connexion, then there ought to be a short list (at least one!) of devices which will absolutely, no doubt about it, work OK straight off with current Ubuntu.

Hey, I realize this is a thread for PCI cards, but I got to thinking about your request for something that "just works" no doubt about it and regardless of cost.

I flashed a linksys WRT54G with DD-WRT ([http://www.dd-wrt.com/](http://www.dd-wrt.com/)).

Works great as a wireless subscriber unit. I was looking on here for a wireless card that "just works," for a new computer, when it hit me to use my WRT54G (which wasn't in use at the moment).

No driver needed because the WRT54G takes care of that and Ubuntu will connect to it via 10/100 Ethernet. Driver problem totally solved...by eliminating the need for a driver!

DD-WRT is fairly feature rich, too. Can set power levels and do all kinds of things not found in normal wireless cards.

---

### Post by Bartender on 2009-02-06
I've got a plain old WRT54G and Ubuntu works fine with it.  No need to tweak it.  

I'm with 2CV67 - still waiting for someone to offer some options for a desktop PC.  A response like: "this worked without any hassles whatsoever, supported in the kernel, just get one and you won't be sorry" would be super!  If not an internal PCI card with external antenna, any suggestions for Wi-Fi-enabled motherboards or even USB plug-in adapters?

---

### Post by 2CV67 on 2009-02-07
News flash!

I upgraded to Intrepid with kernel 2.6.27-9 (since updated to 2.6.27-11, they both include rt61pci 2.1.8) & my Edimax 7128g PCI card with RT2561 chipset now works without needing any backports modules etc.

So I suppose that now counts as "works out of the box" for me, though I have long since lost the box!
Not sure all users confirm this?

I would still like to see a clear & limited list of W.O.O.T.B. items though.

---

### Post by callan79 on 2009-02-07
> **Bartender said:**
> Does anyone know of a desktop PCI or PCI Express wireless card that just works out of the box?


Hi Bartender,

Just pointing you to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

I found this a good place to start, plus a little googling. I added the link to that page for D-Link DWA-510. It works perfectly out of the box.

However, the current hardware is DWA-510 version 3, I'm not sure about that one.

Good luck!

CD

---

### Post by Bartender on 2009-03-04
On Newegg, this card

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833166021](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833166021)

worked out of the box with Ubuntu 8.10, claims one of the reviewers.  Reviewer Tim Holman, posted his comments on 2/26/2009.

---

### Post by Bartender on 2009-03-18
I can confirm that this card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16839121008](http://www.newegg.com/Product/Product.aspx?Item=N82E16839121008)
does work in 8.10.  
I recently picked up a Dell 470 Precision work station with a Xeon 3GHz CPU and 2GB RAM.  It reminds me of a big, noisy, gas-sucking '70's muscle car.  Installed Kubuntu 8.10 to it.  Installed one of these Gigabyte GN-WP01GS PCI cards.  Lugged the thing over to a friend's house on 3-17-09.  It went online and updated; something like 320 MB.
The router was in the same room as the Dell.  
I also went online at their house with an Acer 5920 Centrino laptop (Intel 4965 wireless card) running Ubuntu 8.10.
This is a very unscientific comparison, but it seemed like the Acer showed a stronger signal at roughly the same distance from the router.  The Intel 4965 went to 100% and stayed there.  The Gigabyte card wandered around a bit.
But the Gigabyte card showed higher peak transfer rates than the 4965.  
I have no idea what to make of that, or how many variables are involved when comparing the wireless xfer rates between two very different PC's.  
All I know is this PCI card worked with a basic install of Kubuntu 8.10, and it still worked after updates.

---

