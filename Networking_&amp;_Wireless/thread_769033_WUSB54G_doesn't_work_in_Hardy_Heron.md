---
title: "WUSB54G doesn't work in Hardy Heron?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by wontstoptalking on 2008-04-26
Hi!

I'm new to Hardy Heron, but not really new to Ubuntu or Linux. I've been a Windows person for a long time, you see.

Anyway, I'm making use of that weird huge partitions that Acer computers seem to come with (for some reason, all Acer computers have the hard drives split into to partitions, each of the same size. My 300 Gig hard drive on my desktop is split into two 150s.) by installing Hardy Heron on it. Or should I say, I *did* make use of it because I have it installed already. My problem is that my WUSB54G V.4 USB wireless card isn't working properly in Hardy Heron. I did not have Ubuntu installed on this computer before, so I'm not sure if it worked with 7.10. In the top right corner, next to the date, is the little network button. It does see my network, so it must recognize the USB device, correct? It sees my network, and my neighbor's, too. So I click on mine, and when it asks for the encryption code (I'm using WEP) I choose WEP 64/128 HEX, type it in (I've done it so many times I'm sure I have it right; I do it with the "show key" box checked) and then it shows the two balls with the little thing flying around them. The one on the bottom left turns green, but the top right stays dark and unlit, and it stays like that for about 3 minutes, and then the box pops up telling my to put in the WEP code. It just does that endless cycle.

Is there a way to actually get it to work? I'm kinda new to Linux, and the command line is still scary to me. I mean, I understand it, but I don't understand 100% of it. I just need to know how I can get Ubuntu to connect to my WEP encrypted network.

Please help! Hardy Heron looks amazing, and I want to be able to take advantage of all of its wonderful features!

---

### Post by webbie180 on 2008-04-29
Mine doesnt work either after I upgraded to Hardy.....Linsys WUSB54G.  At a loss too, using windows to post this.  Anyone can help?
Can see my network but cant connect.

---

### Post by necromonger on 2008-04-29
mine does not work either. wusb54g ver.4

---

### Post by wesmo on 2008-04-29
try [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?action=fullsearch&context=180&value=linksys&titlesearch=Titles](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?action=fullsearch&context=180&value=linksys&titlesearch=Titles)

hope it helps :)

If your using ndiswrapper make sure you are using a 32 bit windows driver on i386 hardy and a 64 bit driver on amd64.

---

### Post by webbie180 on 2008-04-29
Is there a way around this without ndiswrapper?

I'm using version 2.2

---

### Post by webbie180 on 2008-04-29
[http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045")

I followed the instructions in the 1st post and it worked for me in hardy too.

---

### Post by DirtDawg on 2008-06-01
EDIT: I had two threads open and responded to the wrong one! Wotta boob. Sorry :D

---

### Post by herschen on 2008-07-23
I followed the instructions above and have a similar problem. I unclick roaming mode, choose the proper wireless network ssid and then it connects. The wireless network box is checked. When I close this window, I can't connect to the Internet and when I reopen the Network windows, wireless is again unchecked. What the deal? Anyone, please...I don't like sounding needy and impatient (even though I am).

---

