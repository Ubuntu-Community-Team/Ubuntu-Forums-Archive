---
title: "Blackmail: get coupons.com printing or XP comes back"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by seedlings on 2009-01-21
I really do need more help.  Several of you have resolved other issues for me, but here I am again on this days old ubuntu install.

[www.coupons.com](www.coupons.com)

They require a "Coupon Printer for Windows" and generally don't like linux at all.  (What's the big deal, I wonder, with not supporting linux.  Surely it can't be hard for them to write another little program?  I digress...)

I barely know anything about ubuntu.  I can go to terminal.  I can follow directions.  That's about it.

First, I have User Agent Switcher, and use that whenever I go to sites like this who prefer Microsoft.

Second, I've installed, uninstalled, reinstalled Wine a few times.  Every Wine window has the words all jumbled together, so I can't read anything it says.

Third, I downloaded the Coupon Printer, and tried to open it with Wine.  It seems to install, but I can't read any of the words (Wine problem).  The Coupon Printer shows up under Applications>Wine>Programs>Coupons .

Every time I try to print a coupon, the site asks me to download the Coupon Printer again.

I tried to uninstall the Coupon Printer, but it won't go away.  So, once again I uninstalled Wine.

If I can't get this working this computer must return to XP.  I don't want to though (but my wife really wants this working!).

---

### Post by sowelie on 2009-01-21
Honestly, I think you should find a different coupon site.  Why can't you just print the coupon right off the website?  I'd be willing to bet their "coupon printing" software has some sort of spyware or malicious agenda.  There is no reason you can't just print a coupon through your browser.  I'm sure there are other coupon sites out there.  This is a pretty extreme reason to quit using Ubuntu.

---

### Post by seedlings on 2009-01-21
> **sowelie said:**
> Honestly, I think you should find a different coupon site.  Why can't you just print the coupon right off the website?  I'd be willing to bet their "coupon printing" software has some sort of spyware or malicious agenda.  There is no reason you can't just print a coupon through your browser.  I'm sure there are other coupon sites out there.  This is a pretty extreme reason to quit using Ubuntu.

Do you know some friendly coupon sites?

---

### Post by dark_harmonics on 2009-01-21
Their website states: Coupon printing is not supported on Linux or WebTV. 

Looks like you need XP. 

Ubuntu is awesome but it just doesnt support adware/spyware!

---

### Post by seedlings on 2009-01-21
> **dark_harmonics said:**
> Their website states: Coupon printing is not supported on Linux or WebTV. 

Looks like you need XP. 

Ubuntu is awesome but it just doesnt support adware/spyware!

Yes, but you guys are good.  There are tons of sites linux can go to that he isn't supposed to, according to the website.

Yes, it is an extreme reason.  I went to ubuntu so that I wouldn't have to spend money and time on virus and spyware monitoring and removal.  However, I'll lose more money in coupon savings.

---

### Post by mjheagle8 on 2009-01-21
and our community doesnt respond well to blackmail either. ;)

---

### Post by dark_harmonics on 2009-01-21
> **mjheagle8 said:**
> and our community doesnt respond well to blackmail either. ;)

The title annoyed me and at the same time made it absolutely irresistible to click on.

---

### Post by seedlings on 2009-01-21
I couldn't find the "tongue in cheek" smiley or the Capt'n Jack Sparrow accent.  If the title is offensive, let me apologise, and Mods can delete it.

I don't mind if you're upfront with me.  If you think it can work, and would like to help, that's cool.  If you're pretty sure it won't work, again, cool - just let me know.

If you would prefer not to help, I'm OK with that too.

---

### Post by Shazaam on 2009-01-21
They may support linux at a later date (just my guess). Look here...
[http://news.cnet.com/8301-1023_3-10145890-93.html](http://news.cnet.com/8301-1023_3-10145890-93.html)

---

### Post by sowelie on 2009-01-21
I would recommend googling coupons, I personally don't use coupon sites, although maybe I should!  Maybe go back to the old fashioned get them in the paper?  I honestly wish I could help but I don't know of any coupon sites.

---

### Post by stoogiebuncho on 2009-01-22
If it were me, I would not install anything from a website simply to print coupons.  It's almost sure to have some kind of adware/spyware wrapped up in it.

But, it's up to you.  I'd try it with Wine.  You say you're getting garbled text.  Do you have microsoft core fonts installed?  If not:

```
sudo apt-get install msttcorefonts
```

Or, simply click here: [msttcorefonts]("apt:msttcorefonts")

---

### Post by irunwithscissors on 2010-09-29
The software required for printing coupons keeps track of the number of times you print a particular coupon or how many times a coupon has been printed for a particular market. The printed coupons from companies like coupons.com, smartsource.com, target.com and the like are also difficult to copy. An on-the-ball cashier/retailer can spot copied coupons and will refuse to honor them, as they will not get credit for them from the manufacturer.

If you want to print coupons, create yourself a dual boot setup and use the windows side to do your coupon printing. For those not in the loop with printing your own coupons, many of the ones found online using sites like those above are better (products not normally found in the newspaper) or can be used in addition to the ones in the paper. While I realize that this has nothing to do with ubuntu specifically, it does provide more information about the OP's problem and some of the further questions raised.

As an aside, many don't realize that most retailers will allow you to double up on your coupons. If you have a store specific coupon, say for target, and a manufactures coupon, you can use them both at the same time.

---

### Post by buckeyered80 on 2010-11-21
Or you could try installing XP on Sun's VirtualBox and install the printer there. VirtualBox is really good if you want to run another OS inside of yours. I used to do a dual boot, but I got tired of rebooting. I think we should make it our goal to just continue to fight against the companies that won't support Linux and get everything we need on 1 OS. But anyway...Hope it works for you.

---

### Post by archolman on 2010-11-21
[stoogiebuncho]("http://ubuntuforums.org/member.php?u=490159") said:
> If it were me, I would not install anything from a website simply to  print coupons.  It's almost sure to have some kind of adware/spyware  wrapped up in it.

But, it's up to you.  I'd try it with Wine.  You say you're getting  garbled text.  Do you have microsoft core fonts installed?  If not:

     Code:
     sudo apt-get install msttcorefonts 
On running the code, I got this return:


> Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.
I know, it was 20 months ago. Just updating... :)

---

### Post by williamts99 on 2011-01-24
The only solution is to choose to dual-boot windows, or run it in a virtual machine.  This also works to print to a network(even PDF) printer.
OpenDNS blocks the coupons.com site as Adware(inject ads into sites?).

Also might want to check out the following site, they might have fixed some things, but they might have just gotten better at hiding it.

[http://www.benedelman.org/news/082807-1.html](http://www.benedelman.org/news/082807-1.html)

"    * Installing with deceptive filenames and registry entries that hinder users' efforts to fully remove Coupons' software. Details.
    * Failing to remove all Coupons.com components upon a user's specific request. Details.
    * Assigning each user an ID number, and placing this ID onto each printed coupon, without any meaningful disclosure. Details.
    * Allowing third-party web sites to retrieve users' ID numbers, in violation of Coupons.com's privacy policy. Details.
    * Allowing any person to check whether a given user has printed a given coupon, in violation of Coupons.com's privacy policy. Details.
"

---

### Post by walt.smith1960 on 2011-01-25
> **irunwithscissors said:**
> **The software required for printing coupons keeps track of the number of times you print a particular coupon or how many times a coupon has been printed for a particular market.** The printed coupons from companies like coupons.com, smartsource.com, target.com and the like are also difficult to copy. An on-the-ball cashier/retailer can spot copied coupons and will refuse to honor them, as they will not get credit for them from the manufacturer.
................


This is the reason and they do it via one or more keys set in the lovely Windows Registry. I don't think the Windows .pdf printers will work either.

---

### Post by williamts99 on 2011-01-25
> **walt.smith1960 said:**
> I don't think the Windows .pdf printers will work either.

Correct, Windows PDF printers won't work, but networked pdf printers do.

---

### Post by Elfy on 2011-01-25
closed - op's been gone for over a year.

---

