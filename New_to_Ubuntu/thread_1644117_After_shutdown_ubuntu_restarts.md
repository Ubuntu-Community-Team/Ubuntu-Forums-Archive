---
title: "After shutdown ubuntu restarts???"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by ledwardz on 2010-12-12
hi, I've had ubuntu 10.10 installed on my laptop for a while and never had any problems at all with it but now ive installed it on my parents computer after telling them how good it was and what do ya know..... it lets me down. 

when i shutdown the computer it restarts after around 10 seconds it simply doesn't want to turn off........ its driving me crazy i cnt figure out what is wrong with it.

and secondly printing on my kodak ESP-3 printer is a problem. Ive tried installing through wine and going into system- administartion ad printing. Neither work.

If anyone could help id appreciate it. Thanks, Lee.

---

### Post by sandyd on 2010-12-12
> **ledwardz said:**
> hi, I've had ubuntu 10.10 installed on my laptop for a while and never had any problems at all with it but now ive installed it on my parents computer after telling them how good it was and what do ya know..... it lets me down. 

when i shutdown the computer it restarts after around 10 seconds it simply doesn't want to turn off........ its driving me crazy i cnt figure out what is wrong with it.

and secondly printing on my kodak ESP-3 printer is a problem. Ive tried installing through wine and going into system- administartion ad printing. Neither work.

If anyone could help id appreciate it. Thanks, Lee.
1. Kodak ESP printers don't work with ubuntu.
2. try
```

sudo shutdown 0 -h
```

---

### Post by llamabr on 2010-12-12
Ya, you're never going to make that printer work.  It was not designed to be used with your computer.

How are you shutting down the computer?  Terminal?  Some little button?

---

### Post by ledwardz on 2010-12-13
hi, thanks for the reply. The computer somehow fixed itself and has been behaving since but its a shame about the printer. Is there no way i can run windows in virtual box and print via that otherwise its back to windows.

---

### Post by redbook4574 on 2010-12-13
> **ledwardz said:**
> hi, thanks for the reply. The computer somehow fixed itself and has been behaving since but its a shame about the printer. Is there no way i can run windows in virtual box and print via that otherwise its back to windows.

You could certainly try virtual box but my advice would be to dump the kodak and by a good value HP, Mostly they just work in linux, If not HPLIP soon sorts them out.

---

### Post by ledwardz on 2010-12-13
> **redbook4574 said:**
> You could certainly try virtual box but my advice would be to dump the kodak and by a good value HP, Mostly they just work in linux, If not HPLIP soon sorts them out.


 I will never buy another HP product in my life, i could have a massive rant but i will restrain myself. Ive tried virtual box but it is being a pain in the ****. so reluctantly it looks like its a new printer. I think if ubuntu could sort out a few things like windows compatibilty issues it would take off but until it comes main stream and more programs are designed for it people aren't going to be willing to make the jump and uninstall windows.

---

### Post by sandyd on 2010-12-13
> **ledwardz said:**
> hi, I've had ubuntu 10.10 installed on my laptop for a while and never had any problems at all with it but now ive installed it on my parents computer after telling them how good it was and what do ya know..... it lets me down. 

when i shutdown the computer it restarts after around 10 seconds it simply doesn't want to turn off........ its driving me crazy i cnt figure out what is wrong with it.

and secondly printing on my kodak ESP-3 printer is a problem. Ive tried installing through wine and going into system- administartion ad printing. Neither work.

If anyone could help id appreciate it. Thanks, Lee.
Actually, I take back my words. I was a bit distracted (watching Victorious) while saying no, as ALL kodak ESP printers have been non-working for a couple years now.

But with some further looking, if you want to print only in B&W -> [http://www.openprinting.org/printer/Kodak/Kodak-ESP3](http://www.openprinting.org/printer/Kodak/Kodak-ESP3)

The drivers are downloadable here -> [http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_15-1_i386.deb/download](http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_15-1_i386.deb/download)

p.s. if you don't like HP, try brother. you can find all the brother drivers on the site, just check that the drivers exist for the printer you are going to get.

---

### Post by sandyd on 2010-12-13
> **ledwardz said:**
> I will never buy another HP product in my life, i could have a massive rant but i will restrain myself. Ive tried virtual box but it is being a pain in the ****. so reluctantly it looks like its a new printer. I think if ubuntu could sort out a few things like **windows compatibilty issues **it would take off but until it comes main stream and more programs are designed for it people aren't going to be willing to make the jump and uninstall windows.
I know this is kind of frugal cause it goes both ways, but this non-support is kodak's support. They stated here -> [http://art.ubuntuforums.org/showthread.php?t=843710](http://art.ubuntuforums.org/showthread.php?t=843710)

that they are not going to support linux nomatter what.

But then again, I don't know many people who use Kodak printers, most of my coworkers swear by HP, even though the ink cartridges are so freaking small. We all end up printing to the main networked Xerox copier ;)

---

### Post by ledwardz on 2010-12-13
> **sandyd said:**
> I know this is kind of frugal cause it goes both ways, but this non-support is kodak's support. They stated here -> [http://art.ubuntuforums.org/showthread.php?t=843710](http://art.ubuntuforums.org/showthread.php?t=843710)

that they are not going to support linux nomatter what.

But then again, I don't know many people who use Kodak printers, most of my coworkers swear by HP, even though the ink cartridges are so freaking small. We all end up printing to the main networked Xerox copier ;)

ill have a go at installing the driver tomorrow (cba right now), i think its the one ive already tried but what the hell, one more attempt aint gunna hurt. Cheers for the reply and ive never had a hp printer but did have a laptop and computer by them. both of which were absolute rubbish. When the laptop broke down within a month they had a look and returned it in a worse state than i sent it. There customer service was pathetic and so i stick with Dell now. 

Also do you know any programs that work like Aero snap feature that windows 7 has? I have had a look on the forums but they are all for earlier versions of ubuntu or really complicated for a crappy beginner like me.

---

### Post by sandyd on 2010-12-13
> **ledwardz said:**
> ill have a go at installing the driver tomorrow (cba right now), i think its the one ive already tried but what the hell, one more attempt aint gunna hurt. Cheers for the reply and ive never had a hp printer but did have a laptop and computer by them. both of which were absolute rubbish. When the laptop broke down within a month they had a look and returned it in a worse state than i sent it. There customer service was pathetic and so i stick with Dell now. 

Also do you know any programs that work like Aero snap feature that windows 7 has? I have had a look on the forums but they are all for earlier versions of ubuntu or really complicated for a crappy beginner like me.
Aero Snap.
[http://ubuntuforums.org/showthread.php?t=1304261](http://ubuntuforums.org/showthread.php?t=1304261)

or... you could just install KDE, Aero Snap is enabled by default.

and Dell printers don't work (or rather, not many people have bothered). Dell printers are Rebranded Lexmark printers, and Lexmark supports a limited amount of printers.

At this stage, I would probably advise checking the openprinting database that I linked to earlier, and choose either canon or brother.

---

### Post by ledwardz on 2010-12-14
hmmm, ive copied code and set it but theres a problem as per usual. it wasn't to full size of screen, i altered the width to fill the screen but now the right one overlaps the left one when i snap it. I tried setting the y to -150 for the right hand side to c if tht would make any difference but no joy. Any ideas. I guess i could live with it the way it is or try Kubuntu, whats the difference between kubuntu and ubuntu? Also still need to try driver for printer but i can't get on the computer. seems like the whole family has taken a shine to ubuntu after all. :p Also thanks for the help once again.

---

### Post by sandyd on 2010-12-14
> **ledwardz said:**
> hmmm, ive copied code and set it but theres a problem as per usual. it wasn't to full size of screen, i altered the width to fill the screen but now the right one overlaps the left one when i snap it. I tried setting the y to -150 for the right hand side to c if tht would make any difference but no joy. Any ideas. I guess i could live with it the way it is or try Kubuntu, whats the difference between kubuntu and ubuntu? Also still need to try driver for printer but i can't get on the computer. seems like the whole family has taken a shine to ubuntu after all. :p Also thanks for the help once again.
no difference, really, its just a different desktop.

Unfortunatey, I cant give you a screenshot, because my KDE is not the KDE youll be using.

It probably requires a more powerful graphics card than one in gnome, but if you can do compiz fine in gnome, you should be able to run KDE.

Just disable the "blur" effect at Start -> System Settings -> Desktop Effects -> All Effects -> Blur.

Its still quite buggy and slows down things A LOT.

---

### Post by Billt Joe on 2010-12-24
Another way to get aero snap with compiz is to enable "grid" under window management. it can snap to left,right, lowerleft etc. The downside is that you can only use keyboard shortcuts and no click and drag. Also, there is no way I know of to get the original window size back. But it works flawless :)

---

### Post by ledwardz on 2011-01-10
thanks, that seems to work prety well also.

---

