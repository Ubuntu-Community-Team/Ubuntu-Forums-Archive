---
title: "Which wireless network cards would you recommend for ubuntu"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by seancarlgrech on 2008-10-02
Could anyone please recommend some network cards for ubuntu?

---

### Post by seancarlgrech on 2008-10-03
which cards are the most ideal for ubuntu?

---

### Post by mbratch on 2008-10-03
Did you check the forum sticky note, near the top of the forum: "Supported wireless cards list"

---

### Post by seancarlgrech on 2008-10-04
hi, thanks for your interest

yes I already saw that, what i need isn't just "supported card" but the best cards for ubuntu, the most recommended

---

### Post by Kevbert on 2008-10-04
My preference are Broadcom cards.  The have been problems reported for most makes of card, but I would personally steer clear of Atheros cards as they seem to be almost impossible to configure and get running.
I have a (Belkin) Broadcom BCM4306, (Pluscom) Realtek RT2561T and an Intel Pro Wireless Lan 2100 3B.
The Belkin adapters may be based on a number of different chipsets, yet can have the same model number.  The Pluscom, I found was a little unreliable (regarding signal strength and noise).  The Intel adapter (built into Acer laptop) I ended up downloading the driver from the Intel website.
Sorry that I haven't suggested a specific card, but it seems you pay your money and take your choice.  I you look hard enough on the forums you'll see most cards seem to have posts relating to problems installing, configuring and running.

---

### Post by seancarlgrech on 2008-10-04
thanks
yes thats true...
but people keep on asking me what is the most ideal card which sort of "always" works without problems... but this seems to be quite hard to find...

---

### Post by kevdog on 2008-10-04
Ill take issue with what was said earlier.  If you can find an Atheros based card that is supported by the madwifi driver(you are looking for particular chipsets with the Atheros family), the wireless card will truly be plugin -- it works.  All broadcom cards either need the builtin bcm43xx driver or ndiswrapper.  With atheros cards its possible to run your card in monitor mode or turn your computer into an access point.  This is useful if you are wanting to do any packet monitoring using aircrack or such tools.  Supposedly with the bcm43xx driver a subset of the monitoring mode features are available, however honestly I have really never seen broadcom cards/monitor mode discussed in these forums.

On the positive side, my broadcom/ndiswrapper combination is extremely fast.  I have done any scientific comparisons, however I do believe it to be a touch faster than the Atheros card.  This is just a subjective feeling however.

---

### Post by seancarlgrech on 2008-10-04
aha infact i got a friend who also managed to sort it out with a broadcom wireless card and is quite satisfied,
but from what he said it's a bit compliacted to install

((( this could be of some good help for anyone who has a broadcom card [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)  )))

i'm searching for a card which is relatively simple to install, so that new users can install it without needing any help... but my hope is fading with the minutes as all cards seem to have some complications..

---

### Post by Kevbert on 2008-10-04
> **seancarlgrech said:**
> thanks
yes thats true...
but people keep on asking me what is the most ideal card which sort of "always" works without problems... but this seems to be quite hard to find...

This would be a good idea for a poll...

---

### Post by seancarlgrech on 2008-10-04
> This would be a good idea for a poll...

i fully agree...

---

### Post by seancarlgrech on 2008-10-04
the only problem is that the poll's maximum is of ten... 
so we have to conclude; WHICH ARE THE BEST 10 first:

1.	ADDON_ADD-GWP110
2.	AR5006EG
3.	Acx111
4.	Airlink101_AWLL3026
5.	AirportExtreme
6.	BT_Voyager_1055
7.	Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)
8.	Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)
9.	Belkin_F5D8010
10.	Broadcom_BCM4306
11.	Broadcom_BCM4311_rev_01_(ndiswrapper)
12.	Broadcom_BCM43xx_(all,_ndiswrapper/firmware)
13.	BuffaloWLIL11GUSB
14.	CiscoCB21AG
15.	CompaqW200
16.	D-Link_WUA-1340
17.	D-Link_WUA-2340
18.	DWA-111
19.	DWA-552
20.	DWL-122
21.	DWL-520vE1
22.	DWL-G111
23.	DWL-G122_(Rev_B)
24.	DWL-G122_(Rev_C1)
25.	DWL-G650+
26.	EdimaxEW7128G
27.	F5D7000
28.	F5D7010
29.	Fritz!WLAN_USB_Stick
30.	IntersilPrism25Wavelan
31.	LinksysWPC54GS-UK
32.	LinksysWUSB11
33.	LinksysWUSB54GC
34.	LinksysWUSB54GP
35.	Linksys_WMP54GX
36.	Linksys_WUSB11v4_(ndiswrapper)
37.	Linksys_WUSB54GS_v1_&_v2
38.	Linksys_WUSB54Gv4
39.	NetgearMA111
40.	NetgearWG111
41.	NetgearWG511andNdiswrapper
42.	Netgear_WG311_v3
43.	Netgear_WG511_v3_Made_in_China
44.	Pentagram_Hornet_USB_Lite
45.	RTL8180L
46.	RealtekRTL8187b
47.	TP-Link_TL-WN620G_(ndiswrapper)
48.	TRENDnet_TEW-421PC_H/W:B1_(ndiswrapper)
49.	TRENDnet_TEW-424UB_(ndiswrapper)
50.	TRENDnet_TEW-424UB_3.0R_(ndiswrapper)
51.	Topcom_Skyracer_USB_4001g_(WLAN-USB-Stick)
52.	WG111T
53.	WG121
54.	WifiDocs/Driver/bcm43xx/Gutsy
55.	ipn2220




**_[COLOR="Red"]MOVED TOPIC TO A NEW THREAD;[/COLOR]_**
[http://ubuntuforums.org/showthread.php?p=5905347#post5905347](http://ubuntuforums.org/showthread.php?p=5905347#post5905347)

---

### Post by kevdog on 2008-10-04
Its not a particular card brand -- its the chipset.  Manufactures just rebrand chipsets after they construct and build the card.

Chipsets are
Atheros
Broadcom
Ra
Realtech
intel
(Others)

With some of the particular chipset versions, there are drivers built into the linux kernel -- if you ever compile a generic vanilla kernel you will know what I mean.  You can choose what particular chipset version drivers to include.  With drivers that are not included in the vanilla kernel, there are either 3rd party linux drivers, or you are forced to use the windows drivers (xp,98) in combination with ndiswrapper.

Really what you want to know are particular chipsets/chipset version numbers -- and then you want to know what particular Manufacture card (version) sells this chipset.  Please note that if you actually go to the store and look on the box -- say a linksys wireless card or netgear -- this information is not posted on the box.  What is posted is the manufacture version.  What you need to do is to correlate the manufacture version to the particular chipset version contained in the card.  Compiling this list is somewhat of a chore -- and as you can see, nobody has a complete list.  If you want to know what a small sample list would be -- I would take a look at this post that lists only Broadcom chipset numbers that work with ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Please note that this list is only for the Broadcom/ndiswrapper series, and does not include any other chipsets or alternative ways of using the particular cards (such as using the bcm43xx driver with broadcom cards).

Also just taking a big step back -- what do you want to accomplish with your wireless card?  If its just to be a wireless client -- any will work.  If you want to do some sophisticated things like act as an access point, packet sniff, aircrack etc, then you will need to obtain a particular kind of chipset that allows these functions.

---

### Post by seancarlgrech on 2008-10-04
all i really want to know is which cards are the most simple to install for new users

(it's not for me, mine is well functioning on my other pc upstairs, it's for people who are considering to switch to ubuntu and ask me [what is the most ideal card which sort of "always" works without problems])

---

### Post by kevdog on 2008-10-04
I believe if you read my previous post, that is quite difficult to answer.  Manufactures change chipset numbers, version, and still sell the different card under the same name except for likely a revision number.  Cards seem to change about every 6 months, with older well functioning cards being exchanged for newer ones.

---

### Post by Kevbert on 2008-10-04
It may be worth leaving out all USB sticks as they normally cause no end of problems.  What you could also do is lump most of the Broadcom based cards together (same for Atheros cards) as Kevdog suggests as the methods are the same for each chipset manufacturer.  Sorry if this causes any grief (it's not as straightforward as you think), hence the large number of wireless threads/posts on the forum.  I appreciate what you're trying to do, but wireless seems to be in a bit of a mess.
Here's a link for [[COLOR="Red"]Ralink based cards[/COLOR]]("http://ubuntuforums.org/showthread.php?t=564419")  and here's one for [[COLOR="Red"]Broadcom based cards[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560").

---

### Post by seancarlgrech on 2008-10-04
thanks, you were very helpfull :)
 
therefore we may conclude that for new users, usb would be the most simple?
is there any model i could recommend in particular?

---

### Post by Kevbert on 2008-10-04
> **seancarlgrech said:**
> thanks, you were very helpfull :)
 
therefore we may conclude that for new users, usb would be the most simple?
is there any model i could recommend in particular?

Sorry, USB is a pain in the ****. Not to be recommended for new users.

---

### Post by Phreaker on 2008-10-04
Linksys WUSB54

It works out of the box 

I have the WUSB54GR version and it runs on all linux/unix-like/windows

It uses the ralink chipset 

And it's recommend by the FSF

---

### Post by seancarlgrech on 2008-10-04
> Sorry, USB is a pain in the ****. Not to be recommended for new users.
 
i terribly misunderstood!! (honestly, I suspected so infact)
 
thanks a lot Phreaker!

---

### Post by Phreaker on 2008-10-04
No problem.
When buying wireless adapters just check what the chipset is and from that you can see if it's supported out of the box

---

### Post by Kevbert on 2008-10-05
Here's a [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=790822") that will help if you get any problems with the Linksys.

---

