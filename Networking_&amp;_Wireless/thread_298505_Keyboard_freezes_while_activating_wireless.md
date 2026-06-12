---
title: "Keyboard freezes while activating wireless"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Foster Reed on 2006-11-12
I'm having a problem getting online with newer versions of Ubuntu.  As soon as I activate my wireless card, the keyboard stops responding.  The keyboard works fine with everything else, but as soon as I click "activate" the keyboard locks up.  I am running the live disk of Edgy at the current time, but had the exact same problem with Breezy as well.  I had no problem with the keyboard or wireless with the same computer using 5.10 so it must be something with the newer versions.  I would like to make sure I can get the internet working before I install to the hard drive.  Thanks everyone.

---

### Post by FrodoB on 2006-11-12
What about with Dapper Drake 6.06? It is on long term support and is rather stable from what they say.

---

### Post by Foster Reed on 2006-11-12
Sorry, I reread my post and I typed incorrectly.  I didn't have any trouble with Breezy Badger.  I did have the exact same problem with Dapper Drake.  Now I'm having trouble with Edgy.  Sorry for the confusion--I got the names mixed up! Thanks.

---

### Post by FrodoB on 2006-11-12
Not knowing any better I would assume that you are using ndiswrapper, correct?

Maybe you need to use the version of ndiswrapper that came with the version of Ubuntu that worked for you.

The ndiswrapper site should have all of those older versions. 

Maybe someone can chime in with some better ideas.

---

### Post by Foster Reed on 2006-11-12
No, I'm not using ndiswrapper.  Breezy automatically detected my wireless card (Linksys WMP54-G).  All I had to do was enter my network name and switch to DHCP, and then click "activate" and it worked.  I assumed that if my card worked with 5.10, it would work with the newer 6.06 and 6.10--is my thinking flawed here?  Or, is it possible the problem is because I am running the "live" disk instead of installing it to my hard drive?  I would just install it dual boot with windows, but if I can't get networking to work properly, I can't do too much with my computer.

---

### Post by FrodoB on 2006-11-12
Well one would have hoped that.  Maybe if you post the details on the card such as model and version along with the output from lspci, iwconfig, and dmesg, someone can chime in and assist you. It sounds like it is going to work.

There are a lot of listing for your card and as you can see there are many different models out there:

[http://www.ubuntuforums.org/search.php?searchid=9744077](http://www.ubuntuforums.org/search.php?searchid=9744077)

So there is a good change that this is going to work. But it would be nice to see it work in live CD mode before installing.

---

### Post by raydekok on 2007-02-10
i have this problem to and i can't get it. for a few days i have installed dapper on my second system. this is a hp d330. i use a wireless linksys (wmp54G) card for the insternet. this card wil work out of the box but when i get a connection my wireless keyboard stops working. i can't type anything. the keybord is working because i use a kvm switch, when i press Ctrl+NUM2 i go to my other system (feisty) and there is my internet wired. keyboard works fine here.

the problem with the keyboard only begins when i turn on my wireless internet.

---

