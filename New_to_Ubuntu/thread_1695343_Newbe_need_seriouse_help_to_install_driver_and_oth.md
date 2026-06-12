---
title: "Newbe need seriouse help to install driver and other stuff"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by RealBigSwede on 2011-02-25
Hello all.
OK so I "broker down" and installed Ubuntu But I'm total new to this and need Help Like hell. 
1. The Ubuntu do not recognize my monitor, ASUS 26inch Now I have only 800x600
2. I found the driver for my Ge-force GTX 460 
3. I don't understand how to install driver on any of my PC's one Quad amd and one Table PC (Fujitsu ST5010)

So please try to help me and remember I need step by step instruction.

Then I have to say I'm impress how well the "OS" is installing and the future I have discover so far, My Hat off to all you hard working guys/girls Thank You! For 10 years ago I tried Linux and gave up after 2 days I went back to Windows. I bought the win7 for 8 month ago but My Table I crashed and when I installed winXP it keep telling me that my window was Illegal and I got so P.O. and start looking for Linux and saw Ubuntu installed it on my Table to see and was impressed. and now I like to run it on my main computer. BUT I need help.
Thanks in advanced,
Yours RealBigSwede

---

### Post by josephmills on 2011-02-25
> **RealBigSwede said:**
> Hello all.
OK so I "broker down" and installed Ubuntu But I'm total new to this and need Help Like hell. 
1. The Ubuntu do not recognize my monitor, ASUS 26inch Now I have only 800x600
2. I found the driver for my Ge-force GTX 460 
3. I don't understand how to install driver on any of my PC's one Quad amd and one Table PC (Fujitsu ST5010)

So please try to help me and remember I need step by step instruction.

Then I have to say I'm impress how well the "OS" is installing and the future I have discover so far, My Hat off to all you hard working guys/girls Thank You! For 10 years ago I tried Linux and gave up after 2 days I went back to Windows. I bought the win7 for 8 month ago but My Table I crashed and when I installed winXP it keep telling me that my window was Illegal and I got so P.O. and start looking for Linux and saw Ubuntu installed it on my Table to see and was impressed. and now I like to run it on my main computer. BUT I need help.
Thanks in advanced,
Yours RealBigSwede
 If you go to system>addmin>additional drivers     it will help lyou find all of you proprietary driver. That should take care of the gtx460. 
as far as you monitor. Here is a link [http://ubuntuforums.org/showthread.php?t=1396101](http://ubuntuforums.org/showthread.php?t=1396101)
I hope this helps in some way.

---

### Post by RealBigSwede on 2011-02-25
Thanks Joseph! You :guitar:

---

### Post by Hakunka-Matata on 2011-02-25
Welcome to the forums RealBigSwede;

What release Ubuntu did you install?,  10.10, Desktop, 32bit?

---

### Post by RealBigSwede on 2011-02-25
> **Hakunka-Matata said:**
> Welcome to the forums RealBigSwede;

What release Ubuntu did you install?,  10.10, Desktop, 32bit?
10,10, 64bit

AMD quad 790 (3Ghz, OC to 3.4Ghz)
Gigabyte GA-MA790X-UD4P
4 gigs ddr2 Gskil
2 DVD dl
3 TB hard disk
GeForce GTX460
26 Inch Asus VK266
Lian-Li 1200 Server Box
Koolance Water-cooled
Logitech DiVo Wire3less Keyboard
MS Wireless Mouse

---

### Post by RealBigSwede on 2011-02-25
Thanks all It worked Now I trying ti install my Network Printer a Lexmark X4530 If some one have some Idea how to do it would be wonderful.
again Thanks for your help so far! :biggrin:

---

### Post by Hakunka-Matata on 2011-02-25
System > Administration > Printing

click on add, and go from there.  There may be a driver from cups that will just work.  If not, go from there

---

### Post by RealBigSwede on 2011-02-25
It can't find my printer and the driver I found on Lexmark site do not work..... :(
and the list for Lexmark do not have any listing for 3500-4500 printer

---

### Post by Hakunka-Matata on 2011-02-26
I searched for a linux driver for your Lexmark X4530 and found nothing.  I found many people who have the same problem with the same printer.  Sorry............

---

### Post by josephmills on 2011-02-26
> **RealBigSwede said:**
> It can't find my printer and the driver I found on Lexmark site do not work..... :(
and the list for Lexmark do not have any listing for 3500-4500 printer

ok so the lexmark printers have been giving the linux kernel some problems for a while now. these are some of the things that you can do to fix that.
1) go on craigslist and trade it for an hp printer they work "out of the box"(most of them)
2) run it though wine via CUPS
3) run it though virtual box via windoz
4) try to find a printer driver that is a lexmark and just try it some times they will work. make sure that the driver has all the same features as yours does well hope that this helps out.

---

### Post by RealBigSwede on 2011-02-27
well thanks for your help all of you!!

---

### Post by Hakunka-Matata on 2011-02-27
> [SIZE="2"][SIZE="3"][COLOR="Red"]ok so the lexmark printers have been giving the linux kernel some problems for a while now[/COLOR][/SIZE][/SIZE]. these are some of the things that you can do to fix that.
1) go on craigslist and trade it for an hp printer they work "out of the box"(most of them)
2) run it though wine via CUPS
3) run it though virtual box via windoz
4) try to find a printer driver that is a lexmark and just try it some times they will work. make sure that the driver has all the same features as yours does well hope that this helps out.
josephmills is offline Report Post   	Reply With Quote

@josephmills, I agree with you partially.  However I have a lexmark C4 color laserjet printer which works great with Ubuntu, there is a .ppd driver file for it, and that's all that's needed.  Unfortunately, I've searched high & low for .ppd driver file for the OPs X4530 and find nothing........

---

### Post by RealBigSwede on 2011-02-27
WHERE CAN Find supported printer I can buy that Ubuntu will support.... like I betting on a Kodak just now.. ( max $5.00) hehe

---

### Post by Hakunka-Matata on 2011-02-27
The big question here is: do you want a LaserJet printer or InkJet printer?[LIST]
[*]LaserJet printers are more expensive to purchase, but much less expensive on cost/page metric.
[*]InkJet printers are Much Less expensive to purchase, but much MORE expensive on cost/page metric.
[*]LaserJet Toner cartridges are quite expensive, say $80, (and there are four total, magenta, cyan, blue?, black) but they last MUCH MUCH longer than InkJet cartridges.
[*]LaserJet printed documents are superior quality (IMHO) compared to InkJet documents, but DO NOT Print photos well.
[/LIST]

Once you decide that, just find a printer you like but check to MAKE sure it supports Linux before purchasing.

Or so I would approach the situation...........

---

### Post by evPaseo on 2011-02-27
A good resource for linux printer compatibility information is [http://www.openprinting.org/printers](http://www.openprinting.org/printers).

---

### Post by josephmills on 2011-02-27
> **RealBigSwede said:**
> WHERE CAN Find supported printer I can buy that Ubuntu will support.... like I betting on a Kodak just now.. ( max $5.00) hehe   

Here I hope that this helps with the paperweight I mean printer 
[http://westmd.craigslist.org/search/sss?query=printer+&srchType=A&minAsk=&maxAsk=10+](http://westmd.craigslist.org/search/sss?query=printer+&srchType=A&minAsk=&maxAsk=10+)

---

### Post by Talon2 on 2011-02-27
> **josephmills said:**
> 
1) go on craigslist and trade it for an hp printer they work "out of the box"(most of them)


I've been using Brother printers for the last few years.  They work very well under Linux.  I'm not aware of any Brother printers that aren't supported.

---

### Post by RealBigSwede on 2011-02-28
> **evPaseo said:**
> A good resource for linux printer compatibility information is [http://www.openprinting.org/printers](http://www.openprinting.org/printers).:guitar: Great Thanks

---

