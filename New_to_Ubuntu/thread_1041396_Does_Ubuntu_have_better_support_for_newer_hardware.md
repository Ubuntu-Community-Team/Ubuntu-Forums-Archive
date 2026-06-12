---
title: "Does Ubuntu have better support for newer hardware?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by aireq on 2009-01-16
So I've been trying out Ubuntu for about a week, and have been having some problems

1) Getting my ATI 9800 setup was a bit of a pain, at least until I realized 

2)My lexmark printer has no support

3)My onboard NIC (Nvidia nForce2 board) runs at 3mbps, but if I boot up windows my connection tests to 20-30 mbps.

My computer is rather old (Athlon 1700), and I need to upgrade sometime soon anyway. But I'm wondering does Ubuntu/Linux have better support for newer hardware? It seems like it's use has increased in popularity over the past few years. I don't want to give up on it just yet. But printing and getting my full connection speed to my ISP are rather major issues for me.

If I built a new computer I could check the hardware on this site for compatability with Linux. The printer I don't have a lot of control over, and I could just get a new one. But the NIC issue last night really through me. I thought NICs are fairly generic? Maybe it's because it's an onboard card. I'll pickup a PCI card this weekend to try. But overall would I expect to have as many issues if I was running new hardware?

Eric

---

### Post by stchman on 2009-01-16
> **aireq said:**
> So I've been trying out Ubuntu for about a week, and have been having some problems

1) Getting my ATI 9800 setup was a bit of a pain, at least until I realized 

2)My lexmark printer has no support

3)My onboard NIC (Nvidia nForce2 board) runs at 3mbps, but if I boot up windows my connection tests to 20-30 mbps.

My computer is rather old (Athlon 1700), and I need to upgrade sometime soon anyway. But I'm wondering does Ubuntu/Linux have better support for newer hardware? It seems like it's use has increased in popularity over the past few years. I don't want to give up on it just yet. But printing and getting my full connection speed to my ISP are rather major issues for me.

If I built a new computer I could check the hardware on this site for compatability with Linux. The printer I don't have a lot of control over, and I could just get a new one. But the NIC issue last night really through me. I thought NICs are fairly generic? Maybe it's because it's an onboard card. I'll pickup a PCI card this weekend to try. But overall would I expect to have as many issues if I was running new hardware?

Eric

The ATI Radeon 9800 works OOB even with Compiz.

Lexmark printers suffer from poor driver support under Linux.  Blame Lexmark.

I have a PC with an nForce 2 chipset and the nForce2 ethernet runs fine.  I have a 10Mbps connection and I get around 9.8Mbps according to Speakeasy.

---

### Post by jerome1232 on 2009-01-16
> **aireq said:**
> 
2)My lexmark printer has no support


Yeah you can thank lexmark for that. I understand hp is very linux compatible. (All of my HP printers just worked after I plugged them in, didn't have to do a thing)

ATI also has (had) horrible support. Recently they've been bought out by amd and seem to be working to change that. They are working to release their linux drivers the same day the release their Windows drivers, going to implement crossfire for linux and etc... 

(I've even heard they want to start branding their packages with tux)

---

### Post by aireq on 2009-01-16
> **stchman said:**
> The ATI Radeon 9800 works OOB even with Compiz.

Lexmark printers suffer from poor driver support under Linux.  Blame Lexmark.

I have a PC with an nForce 2 chipset and the nForce2 ethernet runs fine.  I have a 10Mbps connection and I get around 9.8Mbps according to Speakeasy.

Do you do anything special to setup your Ethernet? Drivers? Special settings?

I got 30 (yes 30 no 3.0) mbps last night on my XP laptop from work, and 3mbps on my Ubuntu desktop.


Eric

---

### Post by LowSky on 2009-01-16
I'm sorry but what type of connection do you have that is supplying you with constant 30Mbps? Most cable companies don't even come close to that number.
The only connections that can handle those speeds are OC-1/OC-3 or T3 connection. All are high end business infastructure lines that only work at those speed from within the company network.  for a normal user 3Mbps is rather decent connection from point to point.

---

### Post by aireq on 2009-01-16
> **LowSky said:**
> I'm sorry but what type of connection do you have that is supplying you with constant 30Mbps? Most cable companies don't even come close to that number.
The only connections that can handle those speeds are OC-1/OC-3 or T3 connection. All are high end business infastructure lines that only work at those speed from within the company network.  for a normal user 3Mbps is rather decent connection from point to point.

Comcast cable. When the guy originally set it up a few weeks ago he went to speakeasy's site and it was around 20. Last night I got 34. I can try again when I get home tonight.


Eric

---

### Post by aireq on 2009-01-16
If I pick up a new network card is there a specfic brand/model that is generaly the most compatible with Ubuntu?

Eric

---

### Post by stchman on 2009-01-16
> **aireq said:**
> Do you do anything special to setup your Ethernet? Drivers? Special settings?

I got 30 (yes 30 no 3.0) mbps last night on my XP laptop from work, and 3mbps on my Ubuntu desktop.


Eric

No.  Maybe your work has a fatter pipe.  Is your Ubuntu desktop also at your work?

---

### Post by aireq on 2009-01-16
No both computers are at home. Why would I compare connection speeds between different computers on different connections?

---

### Post by aireq on 2009-01-16
I sorry I just reread my post . .when I said "XP laptop from work" I meant my work provided me with the laptop.

---

### Post by egalvan on 2009-01-16
One thought,

when comparing connection speeds, make sure you are using the same "apple" or "orange"

the speed can be measured in
"bits per second" or 
"bytes per second"

about a ten-to-one difference...


Microsoft (among others ) tend to use whatever will make them look "better" :)

which MAY account for the OP's original "Windows is ten times faster than Linux" observation...

Or maybe not...

anyway,
Use a site that measures actual download speeds, or download a file of a known size. (if downloading, then try to use a big-enough file that will take at least a minute, in order to smooth out Internet bobbles)

ErnestG

P.S.
at work, I can download a CD-size ISO (approx700MB) in fifteen minutes.

Talk about envy.

---

### Post by jerome1232 on 2009-01-16
I was thinking the same thing for example my internet connection is 6 megabits per second, or 6mbps, that comes out to 6144 kbps (6 * 1024, there's 1024 kilobits in a megabit) If you convert this to kilobytes (8 bits in a byte so 6144/8) then that's roughly 768 kilbytes per second or 768 KB/sec.

Do you see the difference? 6144 kbps vs 768 KB/sec. That's just the theoritcal max, you will actually get roughly ~10% below that.

My lan is all 100 mbps, that's 12 MB/sec, if I transfer files between computers I get roughly 9.8 MB/sec transfer speed (that would be 78.4 mbps, more than 20% below theoretical max speed).

I hope that makes the difference between bits and bytes clear. This was just to hopefully eliminate any confusion on that.

Most home connections max out at 12 mpbs down (That's 1.5 MB/sec). I have seen up to 16 mpbs, or 2 MB/sec down.

---edit--- Also if your connection is that high I believe flash has a problem with speed detection once you get above 20 mbps, I don't remember where I've heard that... and it may not be true.

---

### Post by aireq on 2009-01-16
Yes I know bandwidth and file size values can be confusing with KB vs kb. But seeing the needle peg at 20 on the speakeasy speed test multiple times is not.


Regardless of the units at 2AM (when there should be very little congestion) my Ubuntu desktop's upload speed reliably tested to be 1/3 of my upload speed. Where as my laptops download speed tested to be 3 times my upload speed. Upload was always around 10mpbs.


I'll try another test tonight when I get home.


Eric

---

### Post by Son of William on 2009-01-16
> **LowSky said:**
> I'm sorry but what type of connection do you have that is supplying you with constant 30Mbps? Most cable companies don't even come close to that number.
The only connections that can handle those speeds are OC-1/OC-3 or T3 connection. All are high end business infastructure lines that only work at those speed from within the company network.  for a normal user 3Mbps is rather decent connection from point to point.

Out of curiosity, I just ran the [speakeasy speed test ]("http://www.speakeasy.net/speedtest/")here at my home.  In Ubuntu 8.10 using Firefox I got 10992 kbps download.  I then rebooted into Vista and ran the test using Internet Explorer 7.  I got 10673 kbps download (statistically insignificant).


I have Comcast and I live in a suburb.  No T3 lines here.

---

### Post by aireq on 2009-01-16
Well I can't say much until I can get home and test it. I'll post some screen shots as well.


Eric

---

### Post by aireq on 2009-01-17
Here's screen shots. I cleared my firefox cache between each test just in case.

**XP Laptop**

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%201.jpg[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%202.jpg[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%203.jpg[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/XP%20Laptop%20test%204.jpg[/IMG]




**Ubuntu Desktop**

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%201.png[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%202.png[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%203.png[/IMG]

[IMG]http://dl.getdropbox.com/u/113068/ubuntu%204.png[/IMG]

---

