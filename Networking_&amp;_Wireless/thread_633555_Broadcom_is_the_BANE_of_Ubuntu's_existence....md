---
title: "Broadcom is the BANE of Ubuntu's existence..."
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by Mazza558 on 2007-12-06
Thanks to Broadcom, I have to rely on the most incredibly buggy software package ever written = fwcutter. the "fw" probably stands for "forget working" rather than "firmware", because there's no hope of ever getting a stable wireless connection with my Inspiron 1501 with the bcm4311 drivers. Forget about ndiswrapper, which also fails completely(nasty-dismay-wrapper). I envy anyone who manages to get wireless to work with this laptop...

...and all this, just because one company does not want to free their drivers. I'm lucky to get maybe a minute of a connection with my network, and Firefox then gives me the dreaded "Looking up..." of Death. GAH! What REALLY annoyed me was downloading a massive file, getting to 98%, and then getting kicked off the network! Why, Broadcom, WHY?!?

Does anyone else HATE Broadcom for giving us nights of anguish and fury, nearly throwing stuff at our screens in sheer agony?

I sincerely wish I hadn't bought this laptop now...  I will very soon have to return to Vista, even though the only reason I bought this laptop was to run Ubuntu exclusively on it...

I case you hadn't guessed, I'm very ](*,) angry ](*,) and ](*,) :mad: frustrated!

In the mean-time, anyone else with this laptop, can you let me know what guide works with no problems for you, and what doesn't work?

---

### Post by SunnyRabbiera on 2007-12-06
Next time go with linksys, at least you can get a source code with them

---

### Post by voteforpedro36 on 2007-12-06
...after that rant, saying "Mine works" sounds kinda retarded, doesn't it?

What card do you have? I'm using 43xx if I remember right, and it's working fine.

---

### Post by Mazza558 on 2007-12-06
> **voteforpedro36 said:**
> ...after that rant, saying "Mine works" sounds kinda retarded, doesn't it?

What card do you have? I'm using 43xx if I remember right, and it's working fine.

bcm4311 (rev 1). Disconnects abound, using the default firmware from the restricted drivers manager. I don't know the exact model of the card, though it's built in to this laptop.

---

### Post by Kingsley on 2007-12-06
You bought the laptop to exclusively run Ubuntu, but you didn't research the hardware thoroughly? :confused:

---

### Post by Mazza558 on 2007-12-06
> **Kingsley said:**
> You bought the laptop to exclusively run Ubuntu, but you didn't research the hardware thoroughly? :confused:

It *should* work, according to ubuntu1501.blogpot.com, and it does work. The problem is fwcutter itself, which doesn't seem to be capable of keeping a connection going for long.

---

### Post by maniacmusician on 2007-12-06
I do feel for you, I had a broadcom card for a long time, but mine worked at decent speeds with ndsiwrapper, and not so decent speeds with fwcutter, But I'm also slightly dismayed, like Kingsley, that you knew you were going to run Ubuntu on it and still went with a laptop that had a Broadcom card. Several times a week, I see posts about Broadcom cards refusing to work or working in a very limited way, and this tipped me off to never buy a Broadcom card instead.

When buying a laptop to use Linux on, the first thing that I look for is Intel wireless, because that's the best way for me to get reliable wireless, and that's the highest priority for a laptop.

---

### Post by Mazza558 on 2007-12-06
> **maniacmusician said:**
> I do feel for you, I had a broadcom card for a long time, but mine worked at decent speeds with ndsiwrapper, and not so decent speeds with fwcutter, But I'm also slightly dismayed, like Kingsley, that you knew you were going to run Ubuntu on it and still went with a laptop that had a Broadcom card. Several times a week, I see posts about Broadcom cards refusing to work or working in a very limited way, and this tipped me off to never buy a Broadcom card instead.

When buying a laptop to use Linux on, the first thing that I look for is Intel wireless, because that's the best way for me to get reliable wireless, and that's the highest priority for a laptop.

The problem is, My desktop has a wireless card that uses a broadcom chipset, and it has NO problems whatsoever. On my laptop, the wireless sometimes works so well that I forget all about the disconnections... until they happen. Right now, it's working absolutely wonderfully. I'm pretty sure I'll lose connection in the next few minutes, though.

---

### Post by FuturePilot on 2007-12-06
Yep, I know what you mean. I don't have a Broadcom wireless card, but I do have a bluetooth dongle. And guess what. It's a Broadcom chipset. Although it works(just barely), I don't get the performance out of it that I get in Windows.](*,)

---

### Post by gumbi18 on 2007-12-06
My  BCM 4318 works ok with fwcutter. Connecting to  a wireless network is a  complete pain it sometimes takes up to ten minutes of "connect to other wireless" and entering the details for the network. Once it's connected it only very rarely drops out. My speeds are ok as well.

---

### Post by -grubby on 2007-12-06
why not just sell it to someone and buy a Linux compatible one?

---

### Post by LookTJ on 2007-12-06
> **nathangrubb said:**
> why not just sell it to someone and buy a Linux compatible one?
Second this suggestion.

I recommend replacing the Broadcom pci card with a Intel pci card, but do your research before buying.

Thankfully(my sister and I have the same model of a Dell laptop, I600M.) My sister's a broadcom, and I have an intel Pro Wireless 2200, which came with my laptop. :)

---

### Post by Lord_Dicranius on 2007-12-06
> **gumbi18 said:**
> My  BCM 4318 works ok with fwcutter. Connecting to  a wireless network is a  complete pain it sometimes takes up to ten minutes of "connect to other wireless" and entering the details for the network. Once it's connected it only very rarely drops out. My speeds are ok as well.
Same card, same situation, but I'm steering clear of Broadcom when I'm in the market again for a new laptop.

---

### Post by voteforpedro36 on 2007-12-06
Hmm it's weird that people that use the same firmware have such varying results. I don't keep up with driver issues, but what does Broadcom say about releasing a first-party driver?

---

### Post by crimesaucer on 2007-12-06
I had problems with my BCM43XX and fwcutter on xubuntu 6.10 and 7.04...


Then when I moved to Archlinux, I also had some of the same troubles so I tired out ndiswrapper.


It works perfectly now with a stronger signal that doesn't get dropped at all.


Here is some info you might want to check out:

[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/)

---

### Post by icechen1 on 2007-12-06
I use ndiswrapper to make wireless ''work''(1 boot out of 100 boots don't work),it is hard to set up,atleast it is as good as in windows xp(good connection).WE should all e-mail them for linux support.

---

### Post by crimesaucer on 2007-12-06
> **gumbi18 said:**
> My  BCM 4318 works ok with fwcutter. Connecting to  a wireless network is a  complete pain it sometimes takes up to ten minutes of "connect to other wireless" and entering the details for the network. Once it's connected it only very rarely drops out. My speeds are ok as well.

I had that problem with fwcutter and BCM4318XX using wifi-radar, wicd, and even network manager... and if it actually allowed a connection, the signal was weak and would drop and then be difficult to reconnect.


Once I got rid of fwcutter and the wl_apsta.o driver, and installed the ndiswrapper and the exact driver specified on the [COLOR="SeaGreen"]driver page[/COLOR]: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)


... following the specified instructions below, everything works perfectly:


*instructions from the ndiswrapper page*: 

"...To identify the driver that you need from List, first identify the card you have with lspci and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card by running:

```
lspci -n
```

... and locating the entry corresponding to the first column of lspci output. The PCI ID is third column or fourth in some distributions and of the form 104c:8400. Now you need to get the Windows driver for this chipset. In the List [COLOR="SeaGreen"](linked above)[/COLOR], find out an entry for the same PCI ID, and download the driver corresponding to it. Unpack the Windows driver with unzip/cabextract/unshield tools, and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). If there are multiple INF/SYS files, you may look in the List if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files (For example, TI drivers use BIN firmware) files are all in one directory..." -from this page: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by kevdog on 2007-12-06
Seriously --- you all know better

Broadcom works best with ndiswrapper, not bcm43xx -- period!

Should have gone with Atheros!

---

### Post by Fonon on 2007-12-06
I don't have that problem (Have a Dynex Wireless G Card), but i hear you, and I feel sorry for you.  Next time try to see if you can get a card that works well with Ubuntu.

---

### Post by Sp4cedOut on 2007-12-06
if you're having problems with fwcutter, try ndiswrapper.  My Broadcom card works great with that.

---

### Post by phrostbyte on 2007-12-06
Broadcom support is still hit in miss in Linux. Ndiswrapper still works however. Can someone please find some e-mails of executives at Broadcom so we can b*tch at them for not helping?

---

### Post by dasunst3r on 2007-12-06
I remember buying my first laptop.  I specced it up with Centrino.  Little did I know that I would be saying that anything with the Centrino sticker will guarantee a quite painless Linux experience with respect to networking.  Indeed, I know a few friends with Broadcom cards, and I curse out Broadcom every time I work on their machines.

Broadcom is not just the bane of Ubuntu -- it's the bane of Linux!

---

### Post by Dimitriid on 2007-12-07
First of all, wireless will always be a liability. A security liability, a stability liability, you will never have perfect signal strength, adequate signal, stable working routers, etc.

With that out of the way, how much was your laptop? 800? You are struggling endlessly with 1 piece of hardware that represents maybe 5% of the pricetag or less: Just buy a decent, Linux friendly usb adapter.

---

### Post by bailout on 2007-12-07
It could be worse. You could have a ralink chip that has had open drivers for 2 years and still doesn't work properly under ubuntu.

---

### Post by inversekinetix on 2007-12-07
The bane of ubuntu is the fanboi-ism and hating riddling these forums.   So very unproffessional.

---

### Post by Dimitriid on 2007-12-07
Well the forums are unprofessional: nobody here is getting paid hence not doing it as a profession a.k.a. job.

---

### Post by Griff on 2007-12-07
> **Mazza558 said:**
> blah blah bcm4311 blah blah
I've had a couple different laptops and they've all had broadcom chipsets.  My new baby, a hptx1205us, also has the bcm4311 chipset.  It has been the easiest and most functional (zero issues) of all the wireless chipsets I've had to work with.  Before you sacrifice yourself to vista, try the below link and scroll down to 'Broadcom BCM4311'.  Ignore the fact that it says 'presario'.  I did.  Nothing they do is laptop specific.  If all goes well (like it did for me) you'll be fine in less than 10 minutes.  Download the windows drivers directly from your laptop makers website.

Walkthrough: [http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A](http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A)

Good luck,
Griff

edit: and this does use ndiswrapper, which if you were using fwcutter would explain a lot of your frustrations

---

### Post by 23meg on 2007-12-07
[QUOTE=Dimitriid]Just buy a decent, Linux friendly usb adapter.[/QUOTE]

Suggestion: Edimax EW7318UG - Costs about $20, works without configuration in Gutsy, no signal loss, no dropping. There's Linux compatibility info on the box, and it even ships with Linux drivers on a CD, which aren't needed, since support is in mainline kernel now.

---

### Post by siralphred on 2007-12-07
from my experience with broadcom this is the best solution [http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless](http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless)  take a look at it.

---

### Post by adam.tropics on 2007-12-07
Just replace it....you are not alone btw, [read this one.]("http://ubuntuforums.org/showthread.php?t=598372")

---

### Post by blueturtl on 2007-12-07
I fought long and hard with the Broadcom adapter in my wife's laptop, then realized there was an easy way out: **replace the damn thing!** I took the laptop apart, stole the internal wlan card, sold it on an auction and purhcased a Linux certified PCMCIA adapter. Now everything just works. Unless money is really hard for you to come by, save yourself the trouble. :)

---

### Post by eye208 on 2007-12-07
> **Mazza558 said:**
> Broadcom is the BANE of Ubuntu's existence...
Since Linux is not going away any time soon, it will ultimately become the bane of Broadcom. I wouldn't touch Broadcom with a 10ft pole even if they turned around 180 degrees and released an open source driver tomorrow. This has been going on for too long already. They've been blacklisted by me and all my Linux-using friends.

I'm sorry for all the newcomers who chose their hardware without planning ahead. Avoiding Broadcom isn't hard, but it should be done *before* making the switch to Linux.

---

### Post by mips on 2007-12-07
Just buy a new card, they are really not expensive and sell the old one.

---

### Post by misfitpierce on 2007-12-07
Works fine with 4318 BC card. Try using windows driver with ndiswrapper then if its giving you problems.

---

### Post by ScarySquirrel on 2008-03-04
I agree, Broadcom wireless cards leave linux noobs in some dire straits.  
A while back, I got my wireless card working, but afterward, I had to reinstall ubuntu, and haven't gotten it working since, despite following the instructions several links and posts.
I tried the [HOWTO: Broadcom 43xx based wireless cards the EASY way.]("http://ubuntuforums.org/showthread.php?t=405990")
and several instructions on how to install and use ndiswrapper with the command line.
My cousin has the same problem with his wireless card on his Kubuntu system, and will soon switch back to Windows XP because of it.  
There must be some way to fix this thorny problem, some way to take the difficulty out of all this.

---

### Post by K.Mandla on 2008-03-04
Moved to Networking and Wireless.

---

### Post by uberlube on 2008-03-04
For anyone that reads this and is still trying to get their chip working, read my howto. Its not as hard as everyone thinks.

---

