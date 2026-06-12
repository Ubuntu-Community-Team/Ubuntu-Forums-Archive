---
title: "Feeling Like Giving Up On Ubuntu After Only A Few Hours!"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-10
Sorry for spamming today, but I think I've become overwhelmed with Ubuntu in the few short hours I've been dealing with it. Maybe I'm trying to tackle too much all at once. The scanner doesn't work, the printer doesn't work, it worked before on my XP machine only days ago, and now I'm asking myself, is this really worth it?

Regarding my scanner (CanoScan LIDE 100), I tried some steps I found here on the forum, and on the web, shown here:

[http://ubuntuforums.org/showpost.php?p=10080046&postcount=20](http://ubuntuforums.org/showpost.php?p=10080046&postcount=20)

[http://ubuntuforums.org/showpost.php?p=10526638&postcount=31](http://ubuntuforums.org/showpost.php?p=10526638&postcount=31)

[http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick?commented=0](http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick?commented=0)

None worked. :( I'm probably missing a step, but I don't know.

Regarding the printer (HP DeskJet D1600), so far I haven't had luck either, I posted about it here (sorry if this is double posting! x__x):

[http://ubuntuforums.org/showthread.php?t=1721556](http://ubuntuforums.org/showthread.php?t=1721556)

I tried using the CUPS page, I added the printer, but all the printer did was blink its light, said it was processing, but did nothing. In CUPS it even said "completed" under the jobs.

So...yeah. *sheepish* I'm wondering if Ubuntu will be worth it or if I should just stick with Windows 7. I don't wanna seem like a quitter though. I know that one can't learn the ways of an OS overnight, it's just somewhat frustrating though. Anyway, sorry, and I'm uber-thankful for any help sent my way. :)

---

### Post by earthpigg on 2011-04-10
dual boot, play with the printer/scanner under ubuntu in your spare time and when bored. unless windows is substantially broken for you, it isn't worth losing sleep to make the printer/scanner work on ubuntu.

maybe eventually decide to remove windows, maybe not. not the end of the world either way. :)

it took me about 6 months to be fully comfy enough to remove windows.

---

### Post by mikewhatever on 2011-04-10
Looks like you've been overwhelmed by printers and not by Unity.:p

---

### Post by rosencrantz on 2011-04-10
Hi unknowngal,
according to the Sane project page your scanner should be fully supported with genesys.
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)
So, I'd think you'd best follow the instructions from your second forum discussion link.
I don't think you can go wrong with the apt-get instructions, but there are some pitfalls in editing 40-libsane.rules. Did you get the correct value for idProduct? It's 1904 for the Lide 100
Also, you might want to add
# Canon LiDE 100
usb 0x04a9 0x1904
to /etc/sane.d/genesys.conf, if it isn't listed.
(source: [http://ubuntuforums.org/showthread.php?t=1033181&page=2](http://ubuntuforums.org/showthread.php?t=1033181&page=2))

I'll move my printer comments to your other thread. Let's keep this thread scanner related to avoid confusion ;-)

---

### Post by HermanAB on 2011-04-10
Howdy,

The Canon LiDE100 scanner will most probably NOT work.  (I have one too).

Yes, it is supposed to work and it probably will eventually work in another year or two, but at the moment, it doesn't.  So, give it to someone you don't like and buy another one.

Installing a HP printer should be as simple as plugging it in.  That should bring up a wizard and a few seconds later it should work.  If it doesn't then there is something wrong.

---

### Post by unknowngal on 2011-04-10
> **rosencrantz said:**
> Hi unknowngal,
according to the Sane project page your scanner should be fully supported with genesys.
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)
So, I'd think you'd best follow the instructions from your second forum discussion link.
I don't think you can go wrong with the apt-get instructions, but there are some pitfalls in editing 40-libsane.rules. Did you get the correct value for idProduct? It's 1904 for the Lide 100
Also, you might want to add
# Canon LiDE 100
usb 0x04a9 0x1904
to /etc/sane.d/genesys.conf, if it isn't listed.
(source: [http://ubuntuforums.org/showthread.php?t=1033181&page=2](http://ubuntuforums.org/showthread.php?t=1033181&page=2))

I'll move my printer comments to your other thread. Let's keep this thread scanner related to avoid confusion ;-)

I followed the instructions from the second link, and I made sure it said 1904 for the Lide, and still nothing. It starts to make a scanning sound and then it comes up with an error message: "Failed to scan, unable to start scan".

I checked /etc/sane/d/genesys.conf, and it does show up. 

# Canon LiDE 100
usb 0x04a9 0x1904

So I dunno what could be wrong. :T

And okay, I'll check the other thread. :)

---

### Post by rosencrantz on 2011-04-10
What software are you using, Xsane, simple-scan...? Can you start the program from a terminal and post the output?

@HermanAB: That's an advice for die-hards and not for swing voters. If we don't get it to work I'd suggest running Windows on VirtualBox and scanning from there. Less cumbersome that rebooting every time you need something scanned in Gimp.

---

### Post by gmmcnair on 2011-04-10
):P

No major technical advice here, but just step back, take a breather, and enjoy what works right out of the starting gate. You may have some hitches here and there, but Ubuntu really IS very slick, very stable, and a wonderful OS once you get your sea legs. The other hardware will come in time (or you will find stuff that works better)

I switched from Win XP to 8.04 LTS, and eventually to 10.04 LTS, and each version just gets better and better. The first few days I had some jangled nerves, but things do settle down. I no longer have a Windows computer at home, and I am blissfully happy without XP or Vista, and only grudgingly use Win 7 at work because it's a necessary evil to run some specific software.

Just give yourself time and space to breathe; everything will work out the way it's supposed to.

---

### Post by unknowngal on 2011-04-10
> **rosencrantz said:**
> What software are you using, Xsane, simple-scan...? Can you start the program from a terminal and post the output?

@HermanAB: That's an advice for die-hards and not for swing voters. If we don't get it to work I'd suggest running Windows on VirtualBox and scanning from there. Less cumbersome that rebooting every time you need something scanned in Gimp.

I'm using Simple Scan. *nods* What should I put into the terminal in order to get the output? :o

---

### Post by unknowngal on 2011-04-10
> **gmmcnair said:**
> ):P

No major technical advice here, but just step back, take a breather, and enjoy what works right out of the starting gate. You may have some hitches here and there, but Ubuntu really IS very slick, very stable, and a wonderful OS once you get your sea legs. The other hardware will come in time (or you will find stuff that works better)

I switched from Win XP to 8.04 LTS, and eventually to 10.04 LTS, and each version just gets better and better. The first few days I had some jangled nerves, but things do settle down. I no longer have a Windows computer at home, and I am blissfully happy without XP or Vista, and only grudgingly use Win 7 at work because it's a necessary evil to run some specific software.

Just give yourself time and space to breathe; everything will work out the way it's supposed to.

Thank you very much for your message. :) I'll try and enjoy the ride then. XD *And* take a breather when necessary as well. *nods* :)

---

### Post by unknowngal on 2011-04-10
Okay, wow...this is going to sound very weird, but this ties in with my other post regarding my printer problem:

[http://ubuntuforums.org/showthread.php?t=1721556](http://ubuntuforums.org/showthread.php?t=1721556)

So I installed that software I mentioned in the last post. The printer ended up working. BUT...it's as if the software killed two birds with one stone! What I mean is, it also fixed the scanner! On a whim, wanting to try the scanner again to see if maybe something had changed, I went to Applications, then Graphics, and I found a new scanning program there: XSane Image scanning program. I was hesitant to try it, but I did anyway, and it worked! Then I tried scanning with Simple Scan, and that worked too! I have no clue how it happened...did that program install XSane? Does XSane control both printers and scanners? Is it a USB thing? Whatever it is, it fixed my problem! Awesome. XD Thank you again,rosencrantz!!! And everyone here at the forums who've been so helpful and just plain friendly. :D

---

### Post by el_koraco on 2011-04-10
Now all you have to do is wait for something else to go wrong so you can get frustrated again and fix it :D

---

### Post by rudihawk on 2011-04-10
Glad you got it fixed man!

---

### Post by Tigersmind on 2011-04-10
**> Whatever it is, it fixed my problem!**


Man I love it when this happens!

"How did you fix it?"
"I don't know and I don't care!" :lolflag:

---

### Post by rudihawk on 2011-04-10
> **Tigersmind said:**
> ****


Man I love it when this happens!

"How did you fix it?"
"I don't know and I don't care!" :lolflag:

True, but still - it would be nice why it didn't work and why what one did fixed it!

---

### Post by supergirlkara on 2011-04-10
Don't worry everyone feels this way when they first jump in to Ubuntu. There is always some piece of hardware that doesn't want to cooperate. There will always be something. May I also suggest VirtualBox to run a winxp environment. If you don't feel like dual booting. Don't worry in time you will figure out why it's not working in Ubuntu, nothing is impossible with Linux. Don't give up my friend. Windows XP is the most hackable operating system on the planet!

---

