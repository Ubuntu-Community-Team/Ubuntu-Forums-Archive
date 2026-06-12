---
title: "Testing a Scanner"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by expatCM on 2009-01-15
My scanner has stopped working.  Or perhaps it still works and Ubuntu has stopped working with it.  The problem is that I do not know which.

The scanner (HP Scanjet 3970) did work with 8.04 and then I did a fresh install of 8.10 and got lots of grief.  The problems are random start delay of the scan, scan results that deliver a good scan only 1 of 50 times.  The rest of the time there is normally tiled windows over the bottom part of the page.  The top part is often good … apart from a pink tinge on the margins.

I use both xsane and gscan2pdf, both are up to date and both give similar problems.

So ..  something is not right but it could be something cute in 8.10 or it could be a component failure on the pcb.  The question is which.

My inclination would be to take it to another PC and test it there but the headache I have is that all the other PCs I have are also running 8.10.  Finding a Windows machine to test on is not such a good idea since people get the idea that I may do something exotic and break their machine.

Can anyone think of a way of working out if this is a hardware problem or an o/s challenge?  I had considered downloading knoppix and booting the system with that and testing but I am not sure that knoppix would be a good test since I think it has a common base with Debian / Ubuntu (and so replicate the problem)?

---

### Post by lkraemer on 2009-01-16
Here is a quick solution to test your HP 3970 with a LiveCD.

Google for this ISO:
PCLinuxOS N1PTT-TR5.ISO

Download and burn the ISO  (It is just a Beta Version for testing)

Boot from the LiveCDR to Beta PCLinuxOS Beta

Click on the BLUE Configure ICON in the lower left Toolbar.
Select Configure Hardware, then Configure Scanner.
It should find your scanner if it is attached to a USB port,
or select it manually.

Then locate the Xsane program and play with your scanner,
Xsane is in the Graphics Menu.

It works good, as I have played with this same setup testing a 
used HP3970.  If you get lots of color lines in some of the
scan and it seems to get better the more you scan it could be
that your power supply isn't good enough.  Mine did not have a power
supply and I borrowed one to test the scanner.  Now I have ordered
a 12VDC 3.3 Amp from www.allelectronics.com  for $15.95 + shipping.

lkraemer

---

### Post by expatCM on 2009-01-17
I found your comments about the power adapter to be very interesting.  I had to change the power adapter a couple of years ago ....  I wonder if it should be tested with another ....

The PCLinuxOS beta 2 is generally not available on torrent.  There are downloads offered but they are apparently to run with virtual machines which is not going to help me out.

So I downloaded Mandriva ..  and that will not completely load for some reason, it loads a full screen terminal and tries to do something with a log file ...  I will experiment more with the boot options.

If that is not successful I will either download the 2007 version of PCLinuxOS or look for something else ....

I will post back when I have tested the scanner ...... later ........

---

### Post by lkraemer on 2009-01-17
Yes, that Beta version of PCLinuxOS is just a Beta version,
and it isn't readily available, but it is still at this one 
site.

http://riksun.riken.go.jp/pub/pub/Linux/pclinuxos/live-cd/english/preview/

Go there, download the ISO and burn a LiveCD as DISK AT ONCE (DAO)
at 4x or 8x and use it to test.  It does work good with the scanner.

And on the Possible Power Supply issue....... 
If you are seeing Red, Green, Blue, bars on the left side of a color scan,
and they seem to disappear as the scan goes across the page, that is the
type of thing I was seeing.  I just got my new 12VDC 3.33 Amp Power
Supply yesterday and it works perfectly with the HP 3970.

www.allelectronics.com   Part Number PS-1233  $15.75 + $7.00 Shipping

Oh, and I found a BUG in 8.04 LTS with xsane and 300 DPI scanning.
http://ubuntuforums.org/showthread.php?t=1041790

lkraemer

---

### Post by expatCM on 2009-01-18
Thank you for the link to PCLinuxOS...  I have downloaded and tried it out.

On the machine I connect to the scanner it will not load, I guess this is why it is a beta ... no idea why not, there was an error message when working through all the options and trying to boot to safemode about no suitable media.  I tested the CD on a different machine and it loaded without issue .....  so something about AMD or Gigabyte I guess...

I then decided to boot from the Ubuntu CD to see what happened.  Interesting thing was that xsane scanned without delay or general errors (no windows tiling).  There was still a pink / purple margin.  That could be a hardware problem or it could also be driver related.

I then rebooted to my normal system.  Xsane for the first time scanned on demand and gave a good preview.  The actual scan however was back to the normal errors.

So really not too conclusive.

My next step is going to be to move the scanner over to the machine where PCLinuxOS will boot and see what happens there ....

---

### Post by expatCM on 2009-01-18
It looks like a hardware failure...  I just moved the scanner to a machine running PCLinuxOS off the live CD.  The xsane preview was good as before but also as before the main scan showed a tiled window at the bottom part of the scan.  Interesting though there is no pink / purple border here.

I want to run one final test which is replacing the power supply ...  If that fails then it has to be a component on the pcb.  Not too hard but above my head....

---

