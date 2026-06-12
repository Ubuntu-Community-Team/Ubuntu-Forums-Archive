---
title: "Dial Up Slower Than US Mail"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by xDaveManx on 2007-07-10
I recently "reinvigorated" an older Gateway Essential for my mother to learn on, and installed Ubuntu Feisty to it.  Here are the specs, just FYI:

500MHZ PIII
320 MB RAM
MX4000 Vid
Generic Sound
External Serial 56K Modem

Not exactly a speed demon, but good enough for a 60 year old to take her first computing steps on.

So here's the problem:  Dial up is ridiculously slow on this machine.  I am using wvdial and gnomeppp to connect using a serial hardware modem, and everything works just kosher, only the connection speed is crazy slow.  I am talking sub-14.4 slow, sometimes as slow as single digits.  It also seems faster in the couple of minutes after connecting, then the speed nosedives.  I don't think it is a problem with the phone lines, because I used to use the same lines for dial up when I lived there with no problems using Windows 98 and a WinModem.

Is there some sort of tweak I can try, or configuration file I may have missed that could be limiting the speed of her connection?  I understand that Ubuntu wasn't exactly built for dial up, but these speeds seem out of the ordinary.  I left everything stock in Gnome-PPP, incuding the connection speed.

---

### Post by Bartender on 2007-07-11
It would be interesting to try a newer machine at the same location.  I've been dinking with dial-up at our house and with a few neighbors the last few weeks.  My old PIII 450 MHz Linux test box takes about 2 minutes to open up the average webpage.  Jeez.  I brought the same serial external modem over to a friend's house, and their PII 400 MHz Win98 PC is also painfully slow.
My P4 3 GHz PC running W2K is fairly snappy with the serial external.  According to the little networking status icon in the systray I'm getting 44 kbps this morning, which was unheard of with the Intel 536 winmodem inside.  Unfortunately I don't have Linux loaded on the P4.  That would be a better comparison for your situation.  But I'd sure want to try a faster PC at your mom's house.
BTW, what's the external modem, and who's your ISP there?  I've got a USR Sportster.  The little switches on the back are set up s that #3, 5, and 8 are down, the others are up.  Don't even know for sure what most of these switches do, but that's how they were when I bought it (eBay) and tweaking with them didn't seem to help any.

---

### Post by xDaveManx on 2007-07-11
The modem is a [TRENDnet TFM-560x]("http://www.trendnet.com/Products/TFM-560X.htm"), and I am using Copper.net as an ISP, one of the only ones I could find that allowed a "raw" connection without having to use a proprietary dialer for Windows or Mac.

I have noticed that this ISP shares connection numbers with others (TurboUSA, namely) so the number I am dialing may be overloaded.  To be fair, I am using one of the only dial up numbers available in her rural area, and she is having to dial 10 digits to connect (no long distance fees, tho).  I am going to try some other numbers from around the area and see if they help.

I did try the modem here at my house before the move to hers, and it was painfully slow here too.  Right now, it is taking Google Mail around 1 to 2 minutes to load, and some web pages never do.

Maybe I am just jaded by my 5 Mb connection and I have forgotten what dial up is like.

I don't expect her to be zipping around the internet at ludicrous speed, but being able to check email without frustration would be nice.  I used to use AOL at her house on a Celeron 433, and it was quite zippy 7 years ago, so I can't figure why this connection is so slow.

---

### Post by Bartender on 2007-07-11
Try this site.  Wait for the list of servers to come up and pick the one closest to you.  What does it say for your d/l speed?

The test will probly take several minutes.

I'm not even sure it'll work on a Linux PC but it oughta

I just ran the test on a black US Robotics v.92 external I just picked up today.  Got 35 kbps d/l and it claims 85 kbps upload.  I don't know about that second number - 85 kbps shouldn't be possible on dial-up.  This is on our Windows PC, the newer one, not the old Linux test PC (sig).

Just for the heck of it, I tossed a PCLinuxOS LiveCD in (because it's easier to configure dial-up than Ubuntu/Kubuntu) and set up KPPP.  Dialed our crappy ISP (Juno) and ran the speed test.  Got 32 kbps d/l and 44 u/l.  I don't know if running off a LiveCD makes any difference or not, but the d/l number's pretty close to the performance in Windows.  As I said, I don't know what to think of that first upload number.

---

### Post by xDaveManx on 2007-07-11
Umm... what site?:-?

---

### Post by Bartender on 2007-07-12
Hi, Dave -
What a dope, I forgot to include the link
[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

You know what, forget speakeasy.  I did some more research this morning.  Fired up the old test PC, running Ub 7.04, and it wanted an Adobe Flash Player update to run the Speakeasy site properly.  Funny that an old version of PCLOS ran just fine, but 7.04 wanted updates.
I chose to use another one instead:

[http://pcpitstop.com/internet/Bandwidth.asp](http://pcpitstop.com/internet/Bandwidth.asp)

Ran this test at 0500 hours, when the lines are quieter.  The old test PC w/ the new US Robotics 5686E external scored 6 kbps on the PC Pitstop speed test.  For a subjective test I googled Ubuntu Forums and clicked on the link.  Almost 2 minutes later the webpage hadn't even started to come up.  I ran out of patience and turned off the old PC.  Swapped the USR external over to the P4 3GHz Windows PC, and ran PC Pitstop again.  Scored 37 kbps. 
The Ubuntu Forums webpage completely loads in about 10 sec.  

Yesterday, the PCLOS LiveCD running on the Windows PC scored almost as well on the Speakeasy d/l test as when running Windows, so I don't think it's Linux.
I've read that a dial-up connection will be the slowest link in a modern PC, but it seems the computer's ability to process that data also makes a big difference.

---

### Post by xDaveManx on 2007-07-13
Hmmm.  This is interesting and disappointing at the same time.  I'll take the laptop I intend to buy Sunday  over there sometime and see if I can get similar results to what you are experiencing.

I don't understand how the computer's ability to process incoming data could slow down your internet connection that significantly.  I mean, the computer plays DVD movies flawlessly, streams uncompressed audio from CDs, and transferred files in a flash from my cable internet here at my house with an old NIC card installed.  How would 56K be any different?

There has to be some sort of bug or setting that I have missed.  At least, I hope that is the case.

And if you are looking for a good lightweight speed test, use the automatic one at [http://www.testmy.net](http://www.testmy.net).  Works pretty good for me so far on my Cable connection, and it is supposed to scale itself to your bandwidth.

I am about to leave for mom's house to work on the FrankenBeast.  Wish me luck!

---

### Post by xDaveManx on 2007-07-13
Well, I changed dial up numbers on her computer to a closer hub.  Things did not improve dramatically, but the are better than they were.

She is getting download rates in the teens (Kbps).  While this is not blazingly fast, a patient person can get done what they need to get done.  I don't suspect she is going to be downloading DVD ISO's or hosting games of Unreal Tournament 2004 any time soon, anyway.  I upped the size of her cache so that it would be able to store more images from websites that she visits, because I noticed those we went to more than once loaded a heck of a lot faster.

I now suspect the problem is noisy phone lines, and I guess there isn't a whole lot that can be done about it.  I don't think the phone company would exactly jump on the problem if I called them.  What can you expect from dial up, anyway?  I hooked the same computer up here at my house before I took it to her and it seemed a little faster.  But not by much.

As long as I'm at it, does anyone know how to pass commands to a serial modem using a terminal in Ubuntu?  I'd like to get a report on the SNR on my line from the modem, but I don't know how.

---

### Post by Bartender on 2007-07-13
> **xDaveManx said:**
>  and transferred files in a flash from my cable internet here at my house with an old NIC card installed.  How would 56K be any different?
Dave, I know what you mean and I don't understand it.  I've lugged my old Linux PC to a broadband connection and watched it become a download hog.  
Your question about terminal commands is interesting - I hope someone answers!

---

