---
title: "ZEW1602: Please Help"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by Jeremiah Griffin on 2007-01-18
I have asked this before, but in the mass of posts that the thread attracted, it didn't seem to be heard: can someone please, **please** help me get my Zonet ZEW1602 wireless card to work? I've lived my life deprived of Linux because of my hardware :-(

---

### Post by sadalmelik57 on 2007-02-19
I also own a Zonet ZEW1602 wireless adapter that I am trying to get to work with ubuntu.  Fortunately I have a linux genius in our Linux Users Group.  Unfortunately we didn't get the chance to finish working on this by the end of the February meeting, but I'll give you what little I know and you'll just have to allow for the fact I'm a newbie.

ZEW1602 is based on the Marvell 88w8335 chipset.  By using Google he determined I needed the file 3CRGPC_10075_08_18_2005.exe which is available from this site:
[http://www.3com.com/products/en_US/searchbyfile.jsp?fileid=6&fname=&sort=dwntype&prodcat=13&pgnum=111](http://www.3com.com/products/en_US/searchbyfile.jsp?fileid=6&fname=&sort=dwntype&prodcat=13&pgnum=111)

He installed this file using wine by coding:
wine 3CRGPC_10075_08_18_2005.exe.

 Then he extracted the driver from there and installed it using ndiswrapper by coding:
sudo ndiswrapper -i mrv8335x.inf

now when I type lscpi I get output that includes:
00:0c:0 Ethernet Controller: Marvell Technology Group Ltd 88w8335 [Libertas] 802.11 b/g wireless (rev 03)

When I open the Windows Wireless Drivers it shows:
 mrv8335x  hardware present yes
(previous attempts to install the drivers supplied by Zonet showed no hardware present and lspci did not previously list the device).

This is the good news.  Now on to the part we didn't complete.   
When I open up Networking the wireless option does not appear.  When I type iwconfig I get "no wireless extensions."  When I type sudo dhclient I get no offers.

The next meeting isn't for a month.  Maybe somebody here can help us get to the next step.

---

### Post by sadalmelik57 on 2007-02-20
If someone could give a newbie a bit of help I'd be grateful.  If Ubuntu sees the wireless adapter card and ndiswrapper  shows the driver and shows the device is working, why doesn't "wireless adapter" show up in Networking?  How can I trouble shoot this?  Please?

---

### Post by horemans on 2007-03-09
I just installed anothre marvel Card in Mepis (99 percent Ubuntu) and it worked.

What I do notice is that the zonet download show another inf file...

netmw125.inf

try the ndsiwrapper procedure with the appropriate files.. get them from Zonet's site!

if I recall correctly... and I am a beginner!!!
download, and save the driver files .inf in a directory from ZONET
using a terminal window, navigate to that directory

make sure you are root (su or sudo)
ndiswrapper -l                 ( will list cards)
ndiswrapper -i netmw125.inf

ndiswrapper -l        ( should show hardware installed)

Note: I had to remove another driver, that showed hardware installed, but did not work) with 
ndiswrapper -e  driverbad.inf ( put in the driver name)
as soon as I figured out I neeeded to remove the offending driver, I ws in busines!

try this for a complete description: (clearest I have seen)
[http://www.mepis.org/docs/en/index.php/Using_Ndiswrapper](http://www.mepis.org/docs/en/index.php/Using_Ndiswrapper)

hope it works for you

---

### Post by TechZilla on 2008-04-22
i purchased a Zonet zew1630 and it is MUCH better then the zew1602.  the 30 has a Ralink chipset which is actually fully GPL linux compatible, which is why i thought the 02 was also.. damn was i wrong, (nasty marvel chipset)  thanks for posting bout this guys.

---

