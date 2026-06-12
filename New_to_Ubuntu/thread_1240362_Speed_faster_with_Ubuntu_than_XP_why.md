---
title: "Speed faster with Ubuntu than XP why?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by gasmansteve on 2009-08-14
Hi folks
Just tried a broadband speed check through `Giganews` web site on my laptop running XP found 2800kbps, tried it on my desktop with newly installed Ubuntu and found nearly 4000kbps and wondered why that is as I`ve never had that speed before?, guess its another thumbs up for Ubuntu :):)
Steve

---

### Post by NightwishFan on 2009-08-14
Perhaps Xp has networking configured incorrectly. If you use Xp often, I would make sure there is nothing wrong. However, I do not think there would be. More likely you just tested it at low traffic time.

---

### Post by zerhacke on 2009-08-14
Linux will always be faster than Windows.  It can do an infinite loop in five seconds.

---

### Post by LewRockwell on 2009-08-14
It should be noted that transfer speeds(both up and down) vary wildly depending on the second by second loading of the system(interwebs)

Yesterday I was downloading a file and saw speeds from 127kbps to 896kbps within a 60 second time-frame

.

---

### Post by sasho_zl on 2009-08-14
Maybe you have a firewall or antivirus program on your XP which is scanning the traffic and that way slowing it down.

---

### Post by Joeb454 on 2009-08-14
It also depends on the method you're using to connect to your network at home (And the speed of that network).

For example, it sounds as though you were connecting wirelessly on the laptop, and via wired connections on the desktop? That is likely to have an impact

---

### Post by zerhacke on 2009-08-14
> **Joeb454 said:**
> 
For example, it sounds as though you were connecting wirelessly on the laptop, and via wired connections on the desktop? That is likely to have an impact

I disagree.  He's not seeing a 50Mbps difference.  He went from 2 to 4 Mbps and Wireless B and G's bandwidth are both much greater than that.  The only difference he would see on a wireless connection is that LAN connections would be slower than wired.

---

### Post by juancarlospaco on 2009-08-14
**All Windows silently reserved for itself 20%-25% of Network bandwith.**

---

### Post by credobyte on 2009-08-14
> **zerhacke said:**
> Linux will always be faster than Windows.  It can do an infinite loop in five seconds.

Infinity is an abstraction - you can't reach it [IMG]http://www.mysmiley.net/imgs/smile/cool/cool0046.gif[/IMG]

---

### Post by scorp123 on 2009-08-14
> **NightwishFan said:**
> Perhaps Xp has networking configured incorrectly. That's a possibility. It's also possible that there was less traffic as other posters suggested.

But: Fact is that Microsoft's network stack SUCKS ... Their TCP/IP implementation is a badly copied rip-off from BSD and it is _SLOWER_ on the same hardware than with any other OS.

Example:

File transfer with the "barebones" FTP client program: "ftp". The program exists on Windows too (they copied that one over as well) and it's the absolute same basic client you'd find on Linux and BSD as well. At least with Windows XP the "ftp.exe" program was installed per default, so chances are you already have it.

Log into Windows and transfer a very large file, let's say a DVD *.iso image. Best thing would be if you have it on a FTP server inside your LAN.

Then boot into BSD or Linux and repeat this. Make sure you really use the "ftp" command line client.

Most likely result based on my experience: on a 100 Mbit LAN Windows will transfer at about 6 MB/s whereas BSD and Linux will easily transfer the file at around 10-11 MB/s which is very very close to the physically possible maximum rate of 12.5 MB/s on a 100 MBit Ethernet LAN.

100 Mbit = 100'000'000 bits per second. There are 8 bits in a Byte. Hence:
100 MBit = (100'000'000/8) = 12'500'000 = 12.5 MB/s


BTW, You can repeat the experiment with SSH. With the overhead from the SSH-encryption Linux and BSD still transfer at speeds of around 9-10 MB/s on a 100 Mbit LAN whereas Windows even with good SSH/SCP clients such as "FileZilla" won't get beyond 4-5 MB/s ... 

So ... You have to transfer large files over the network? Don't use Windows. You might end up waiting twice as long :D

---

### Post by zerhacke on 2009-08-14
> **credobyte said:**
> Infinity is an abstraction - you can't reach it [IMG]http://www.mysmiley.net/imgs/smile/cool/cool0046.gif[/IMG]

You haven't watched Revolution OS, have you?

---

### Post by wojox on 2009-08-14
Infinite loops never terminate because no condition can be met.

---

### Post by zerhacke on 2009-08-14
You guys really need to pick up a Linux joke book.

---

### Post by credobyte on 2009-08-14
> **zerhacke said:**
> You haven't watched Revolution OS, have you?

No, I haven't ( th, looks interesting .. will check it out tomorrow ;) ).

---

### Post by wojox on 2009-08-14
Great now you've peaked my interest. I'll have to download Revolution OS now. :lolflag:

---

### Post by scorp123 on 2009-08-14
> **wojox said:**
> Great now you've peaked my interest. I'll have to download Revolution OS now. :lolflag:

Very good movie. A slight bit old by now ... but still very good. Another one I really like a lot is this one:  **Codename: Linux**

It was done by German/French TV station "ARTE" many years ago and I know that "Codename: Linux" exists both in German and French; I don't know if there is an English version though. But the movie is excellent despite its age because it also shows a lot about "our culture", e.g. the will and desire to share code and knowledge, and so on. So if you can find that one too somewhere ... it's definitely worth watching.

---

