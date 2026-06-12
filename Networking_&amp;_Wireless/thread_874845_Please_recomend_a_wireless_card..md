---
title: "Please recomend a wireless card."
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by whodatpat on 2008-07-30
I am a super nubie.  I have loaded Ubuntu Studio onto an older Dell Latitude Laptop.  My old Linksys wpc54g cards will not work, and i am sick of trying to make it.
I would like to buy a new card that is preferably stronger and able to pull in signal better than the old linksys one did with windows.  I would like one that works out of the box.  I am not afraid to drop some code in the terminal if needed, but thats about as deep as i can dig without step buy step instructions.  Your help is GREATLY appreciated.
BTW, so far I think this OS rocks, and this form in awesom.

---

### Post by Frederick J. Harris on 2008-07-30
I'm in about the same boat whodapat.  I'd like to just know which one to buy and just have it work, no fighting with it, no pasting commands in the Terminal, and what not.  I've been researching this issue for the past couple hours and can't believe how miserable it is.  For example, the Free Software Foundation mentions that some Belkin cards work pretty good with Linux.  These you can buy right off the shelf at Walmart or wherever.  So I look up some Belkin cards at Amazon.com and find all kinds of reviews, some saying that a card with this model number 'F5D7010' works good with Linux, then a few reviews down one finds out that on some of these cards Belkin uses the good Atheros chipset and on others the bad blasted miserable Broadcom chipsets!  And all on the same card with the same model number and everything!

I just looked up D-Link's DWL-G650 Wireless Cardbus Adapter, 802.11g, 108Mbps at Amazon.com and for this card there seems to be piles of reviews stating this card works 'out of the box' on Ubuntu.  Here's the link...

[http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6/ref=cm_cr_pr_pb_t](http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6/ref=cm_cr_pr_pb_t)

Maybe I'll get that one.  Its cheap too.  I'm even a programmer myself, but this isn't a battle I want to fight.

---

### Post by whodatpat on 2008-07-30
I just ordered it.  $23.31 including expedited shipping is cheap enough.  I will report back on my findings.  i see it is still of the older G variety as opposed to the newer N variety.  But cheap is the name of the game in this project.

---

### Post by Frederick J. Harris on 2008-07-30
Yes, please let me know how that works Whodatpat.  I still havn't taken the plunge yet.

---

### Post by generalludd on 2008-07-30
This isn't a super easy solution, but check out this list
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You can find out which cards require special action (such as using ndiswrapper to make use of windows-based *.inf driver files) and which ones make use of built-in Linux drivers.

---

### Post by Jordanwb on 2008-07-30
> **whodatpat said:**
> My old Linksys wpc54g cards will not work, and i am sick of trying to make it.

I was able to get my wpc54G working perfectly. You have to install nidswrapper, ndisgtk (graphical frontend for ndiswrapper), modprobe, and wifi-utils (not sure about spelling on that one).

Download the latest drivers for the card. Open NdisGTK (varies on DE). Click Install drivers, and install them. Click "Configure Network" and set the Wireless settings. I don't remember everything but I hope this helps.

---

### Post by whodatpat on 2008-07-31
> **Jordanwb said:**
> I was able to get my wpc54G working perfectly. You have to install nidswrapper, ndisgtk (graphical frontend for ndiswrapper), modprobe, and wifi-utils (not sure about spelling on that one).

Download the latest drivers for the card. Open NdisGTK (varies on DE). Click Install drivers, and install them. Click "Configure Network" and set the Wireless settings. I don't remember everything but I hope this helps.

What version was your card?  I know from my research that V5 can work with some extra effort like you described.  However i have also found in searching this forum that older ones like my V3, and V? do not.  That alphabet soup of installs is what I am trying to avoid.  Along with being a newbie and a bit ignorant when it comed to installing a bunch of software on top of software and setting up interdependencies to get stuff to work.

I am looking for a card that just plugs and plays.  The one i ordered is on the list.  What I was hoping for was someone who could say buy card XYZ and it will work right out of the box.  Hopefully the one I ordered will.  I will report back tothis post.

---

### Post by whodatpat on 2008-08-02
The D-Link's DWL-G650 showed up in the mail today.  Plugged it in, booted up, and went straight online to this forum to tell you it is just that easy.  We will see how the speed and signal strength is, but it works out of the box.  No CD, No Driver download.:guitar:

---

### Post by Frederick J. Harris on 2008-08-04
Great News Whodatpat!  I'm happy for you!  I probably ought to take my own advice!  When I recommended that as a result of my searches of buyer feedback at Amazon.com and you jumped and bought it I thought "Boy! I hope I didn't steer that poor feller wrong!"

This past weekend I really jumped in and finally took the plunge and attempted to get three different dual boot laptops working with Ub untu wireless.  The three were:

Compaq Evo N600c Win2000/Ubuntu 8.04
Ibm Thinkpad A30p Win 2000/Ubuntu 8.04; 1.2 ghz; 1 gig ram; 60 gig hd
HP DV8000 WinXP/Ubuntu 8.04 2 gig ram; AMD Turion 64 bit (32 bit OS)

The Compaq and Ibm setups I used a PCMCIA Linksys WPC54G card and ndiswrapper.  It worked.  Both connect wirelessly anywhere in my house.

The HP DV8000 with built in WiFi is another story.  Can't get it working.  I'm still trying to figure out why, and will probably have to ask for help at some point.  But I'm glad yours works!

---

