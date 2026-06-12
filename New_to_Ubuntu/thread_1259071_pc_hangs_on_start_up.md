---
title: "pc hangs on start up"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by demeter on 2009-09-05
hi there, I have installed jaunty on a test PC two days ago and everything seems to be working fine. I was able to install the Office 2007 on it and works fine. however when I started it up this morning, it hanged and stayed on the post boot screen, " starting up" and just stayed there... what could be the problem with this? I restarted the system (pressing the reset button) and still the same. The PC that Im using was an old PC that I got from a friend. I couldnt identify the mobo since it has no identifier on it, except that is was made in korea, had a 16 mb asus video card, 10 Gig HD, 512 SDRAM, running on an intel celeron Pentium III 700 MHZ... could this be an installation problem or a hardware one? Thanks....

---

### Post by gunksta on 2009-09-05
I have seen Ubuntu do this a couple of times in my house. Do you, by chance have something in one of the USB slots OTHER than a mouse or keyboard. I have seen WACOM tablets AND USB Keys "freeze" Ubuntu from booting. When I unplugged them and restarted everything worked correctly.

It took me forever to figure out tht the WACOM tablet would *sometimes* prevent my girlfriend's desktop from booting. Not all the time, just part of the time.

I have not been able to figure out why this happens, but I did find a simple "solution".

I hope this helps.

---

### Post by PGScooter on 2009-09-05
same happened to me when a printer was plugged in

---

### Post by demeter on 2009-09-05
thanks for the quick reply....did a visual check inside the PC  and I found out that the sound card had its screw missing and  wasnt inserted properly into its slot. so I fitted it properly and restarted the system...it went through the boot message but it said something like device unknown...ignoring....then would hang again...so i took out the sound card, restarted again and it worked...Im replying to this post right now on this PC...will try to insert the sound card again and see if it works...and by the way, how can I add new hardware on jaunty? in case this sound card still works....thanks again.... 

additional woe:
cant play video on websites, getting this msg:
CNTRLS=undefined, ID=undefined
PLIST=http://l.yming.com/m/ver/271015/player-2009-08-24-1330/blank:xml?&pt=xml
SERVER=undefined
BITRATE=undefined
PLPATH=undefined
CACHEPATH=undefined
undefined:undefined
NC_MSG=NetConnection.Connect.Success
NS_MSG=NetStream.Play.Stop
PLAYSTATE=stopped
TIME=2.068/2.068
BUFFER=undefined/undefined

thanks again

---

### Post by JC Cheloven on 2009-09-05
So you installed office 2007 ? How ? Not on wine, I guess...

As for the sound card: 
Did it worked with ubuntu before? 
Which model is it? If a sound blaster (for example), chances are that it will work out of the box (unless it's broken).

---

### Post by demeter on 2009-09-06
yup, installed the office with wine, is there another way to go around with it? just started with linux 2 days ago and still has a lot learn with this OS, anyway, the sound card is somewhat loose when I checked so I do think it wasnt detected when I installed the jaunty, and havent tried the audio too when I first ran, its kinda old, a PCI one, the prints on the board are somewhat erased but there's a chip that has creative printed on it and on the back that says " Eureka PCI 64"....thanks...

---

