---
title: "Whew, wifi is impossible for a noob"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by MoLeak on 2005-10-14
I have an Airlink card that works just fine in Windows but I can't seem to get any understanding how to do wifi here.  Any way to make wifi work?  Does anyone know?

-MoLeak

---

### Post by StuXP on 2005-10-15
Hi - I sympathise.

It just goes to show that Linux has a long way to go until it is a real contender against Windows.

If it's any consolation, the wifi on my laptop worked more or less straight away with the previous version Ubuntu, which impressed me.  Of course, it's broken now that I have installed Breezy Badger and neither of my network adapters appear to be detected.  My networking is stuck on 'lo'.

Will just have to wait for a solution. :( 

Stu

---

### Post by StuXP on 2005-10-15
Me again,

Well, wouldn't you know it... after all my complaining, I had another look to see if I had missed some settings and got the wifi working in a couple of minutes!

I went to System...Administration... Networking and then activated the wifi adapter eth0, added the network name, wep key etc then it all fired up.

Stu

---

### Post by MoLeak on 2005-10-15
Thanx Stu.  That was a very heart warming story. :)

However, I co-sign your earlier post but I'll press on to finally understand this pig.

-MoLeak

---

### Post by bionnaki on 2005-10-15
ndiswrapper worked for me.

---

### Post by MoLeak on 2005-10-15
[QUOTE=bionnaki]ndiswrapper worked for me.[/QUOTE]

If you could point me to a step by step or walk me through installing with Ndiswrapper, maybe I can get this working finally.

-MoLeak

---

### Post by bluefrog on 2005-10-15
setup ndiswrapper in breezy

[http://ubuntuforums.org/showthread.php?t=76710](http://ubuntuforums.org/showthread.php?t=76710)

---

### Post by MoLeak on 2005-10-15
I'm good until I get here:
"sudo modprobe ndiswrapper"

Then I get a Fatal: Error inserting ndiswrapper...Operation not permitted.

-MoLeak

---

### Post by az on 2005-10-15
You can get that error if you installed the wrong .inf file.

---

### Post by brentoboy on 2005-10-15
lookup your card on ndiswrapper.sourceforge.net

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

they list recommended drivers for lots of chipsets.  The driver that ships from the manufacturer is not always the recommended driver.  You look for your card on the list, it will tell you where 

download whatever they recommend and try that inf/sys instead of the one that came with the board.

---

### Post by MoLeak on 2005-10-15
Wow.  Now I see how to handle this.  Ask all my questions on the weekend! Cool.  I'll see what sourceforge has.

-MoLeak

---

### Post by MoLeak on 2005-10-15
Well, so much for that.  I have an Airlink plus awlc3025  cardbus card and nothing over there for that one.  Oh well, stopped again.

-MoLeak

---

