---
title: "Aironet 4800"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by krnkstrgngstr on 2013-11-30
First of all.. Hi.. Thanks for the service..

I have an old Aironet 4800 11Mbps networkncard I want to use and I was looking for a driver online
and this is what I ended up finding 
html [http://www.gsp.com/cgi-bin/man.cgi?topic=an](http://www.gsp.com/cgi-bin/man.cgi?topic=an)
O.K.  I have questions about everything that page says... so I found a slightly less useful page at
 [http://cateee.net/lkddb/web-lkddb/AIRO_CS](http://cateee.net/lkddb/web-lkddb/AIRO_CS).
which confused me even more, so I came here...
 I am a reforming Microsoft junkie (swore it off when XP is dead - April) and I have played around with alotta
Linux varients but play is about as far as it got, I have no knowledge whatsoever of the OS
 but yesterday I decided to try and dedicate myself to using Ubuntu (almost) exclusivly and trying to
become familiar enough to not be tempted to get another MS machine,, 
So this being my second full day, I have not really had many problems except I cant get WINE to install PokerStars
which is horrible amd I am sure there will be a thread concerning that here sooner or later..
But right now I just wanna ask if all the stuff on the page of the url above url is nessasery, and if so, 
I am deefinatly in need of figuring out where to type what because 
I refered to a FreeBSD help page 
[http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=loader.conf](http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=loader.conf)
so now I know some of the words, but none of the actual how to do it..
and as far as that goes it might as well be in Japanese I would understand it as well..

I need alot of guidence.. RTFM is not a problem, I am going back to that immediatly
but now I have introduced myself and I am sure all the smart people will be absoutly sick of me within a week..

I am gonna try some stuff...  I willl be back soon..

Thanks, L8r..

Mike

---

### Post by krnkstrgngstr on 2013-11-30
[IMG]http://www.cisco.com/en/US/i/templates/blank.gif[/IMG]Cisco's  Linux driver supports version 2.2.xx and 2.4.xx of the Linux kernel. To  determine your kernel version, [COLOR=#ff0000]**type uname -a and press Enter**[/COLOR]. The name  of your computer and the Linux kernel version are displayed. For  example, in Linux montecito 2.2.16-22#1 Wed Aug 8 164906 EDDT 2001 i686  unknown, montecito represents your computer's name, and 2.2.16-22 is the  kernel version. 

It's simple stuff like this.. Whre do I type stuff, and how do I get there, and do I type everything to the same place (command prompt?) or there are seperate places for different things..  
Just trying to clarify my problem...

---

### Post by steeldriver on 2013-11-30
What actual chipset is it? That usually matters more than the model number - I have some experience with an Aironet 350 on an old Thinkpad.

In general you type stuff in a terminal - in the regular Ubuntu desktop you can either go to the 'Dash' and search for it by name (i.e. start typing t e r m i ...) or hit the keyboard shortcut Ctl-Alt-t

To find the PCI ID you can type

```
lspci -vnn | grep '\[02.0\]'
```

The important bit is the number at the end in square brackets like [14b9:a504] - that will give us a starting point as to what's possible. You can also get useful info from lshw

```
sudo lshw -C network -sanitize
```

Be aware that those old 802.11a/b cards may not support WPA2 (the 350 for sure doesn't) so if that's a requirement then best not to fight with it, USB/CardBus adapters are so cheap nowadays - that's the route I went.

---

### Post by mörgæs on 2013-11-30
Hi, welcome to the fora.

You don't have to focus on such old (=obsolete) kernels as 2.2 and 2.4. According to your second link the latest kernel (found in Lubuntu 13.10) supports the card, so it might work without modifications. 

As mentioned above routers with strong encryption might not connect. Do you know if your encryption is WPA or WEP?

---

### Post by krnkstrgngstr on 2013-12-03
ubuntu-12.04.2 - Dell Inspiron 6000

Well it's not so much card preferance, it was just the neatest looking thing in a box of crap..
I am more interested in learning to use Ubuntu do things other than:
Logging in, Opening FireFox, Closing Firefox, Shutting Down Computer, and opening misc folders...
I am pretty good at all of those things but everything else can use improvement..
So, I drug out a box, picked out the neat anteanna card and jotted down the numbers stuck it in the hole..
Actually it was second.. the first one was a Linksys and a window popped up and i installed the driver and got blue screens, 
definatly not beginner level material, so back in the box it went...
The Aironet didnt offer a driver, so It seemed like a good start to learn to do something useful..
I googled it and picked out a few URL's to read (the ones I posted)
I wanted to type the things it said to, so I used my well honed talent of opening misc. folders and clicking misc. things
results were unsucessful...  I call it the Burn and Learn technique.. 
I did learn that there are lots of hidden things... decided that they are probobly hidden because people like me shouldnt be messing with them.. 
I will be back to that when I wanna learn how many random clicks it takes to render the OS useless..
I practiced opening Firefox again.. success..
Then I saw the URL to here..  Posted.. 
I came here because it sounded like smart people that know where to type stuff might tell me,
Probobly much more efficent than Burn and Learn, and I could roll with pretty much anything I find that needs typed in..
Then went to cisco to find that the card is not forgotton completly.. but almost.. Dead links to driver..
I found the driver at a third party site that has drivers for obsolete stuff and got it.. I think I extracted it 4 or 5 times.. 
Finally found where they went and clicked them.. I am pretty sure that did nothing, and as far as I can tell the card still dont work..

Learning new things is hard...  I am betting less than 25 random clicks in hidden files to render the OS useless, I can learn that pretty quick...  

I am grading my day as an F- due to lack of effort and wandering off subject..

---

### Post by krnkstrgngstr on 2013-12-03
Cool.. I can type things and see what happens next.. 
I have a the closest thing to a intelligent question I can ask.. 
Where can I learn what lspci, -vnn, grep,  as well as everything else ya said to type actually means?
I wanna read up on the basics and try out a few things...
It may be awhile before I come back, 
I have a tendency to take things way too far, once I have a little bit of an idea where to start..
I am gonna go find a kindergarden level page on this subject and see if I can comprehend some of this stuff little kids have mastered..

---

### Post by mörgæs on 2013-12-03
This thread should make for a beginning:
[http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

Did you try Lubuntu 13.10?

---

### Post by chili555 on 2013-12-03
You can read what lspci and most other things do by reading the manual. Please open a terminal and run:```
man lspci
```> DESCRIPTION
       lspci  is  a  utility for displaying information about PCI buses in the
       system and devices connected to them.

       By default, it shows a brief list of devices. Use the options described
       below  to  request  either a more verbose output or output intended for
       parsing by other programs.

etc., etc.Use the arrow keys to scroll back and forth to see the options and further details. 

The first thing I'd do with the ancient and creaky Aironet is insert it and check the logs to see if the driver airo_cs loaded automagically:```
lsmod | grep airo
```*Standing by while you read *man lsmod** 

If it did load, see if a wireless interface was created:```
iwconfig
```If not, post some diagnostics for our review:```
dmesg | grep airo
lspcmcia ident

```Then I would probably recycle it. I doubt that it is capable of WPA or WPA2 and so is quite insecure.

I would rather troubleshoot the Linksys, actually!

---

