---
title: "New SSD for Asus 900A - help installing 9.10"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by happysalsa on 2009-11-11
Well I have a new, never-used Asus 900A that had Linux. I now installed a Super-Talent 32 GB SSD and would like to install the new UNR 9.10. 
 
I downloaded the 9.10 ISO onto my Sandisk 16GB USB flash drive using my Windows XP desktop and am stuck as to where to go from there. I have tried to insert the flash drive into my Asus 900A and then turn "on".. I then hit the F2 button to go into the BIOS screen and set the "USB:SanDisk Cruzer" as the priority and only device to boot from, -but to no avail.
 
Dunno if the fact that this Sandisk Cruzer puts a couple of files on the USB stick?? One is the "U3" feature and the other is a "Document" folder? Is that a possible issue?
 
I don't know if I needed to put an "installer" on my USB drive.. and if so, which one? I'm not computer-illiterate but this is confusing me. I think some of the install advice on some sites is assuming that person has an OS on their netbook already, which I don't have.... just a completely new 32GB SSD...
 
Please help!! Trying to give the wife her gift with a little upgrade but I'm not looking like the hero!
 
Thanks in advance..
Sean

---

### Post by Jon Monreal on 2009-11-15
You can remove U3 using the [U3 removal software]("http://u3.com/support/default.aspx#CQ3") for Mac or Windows. Alternatively, you can try [u3_tool]("http://u3-tool.sourceforge.net/"), which runs under Linux.

At any rate, removing U3 will probably fix the problem because, as it is, your drive has multiple partitions, which is probably causing the problem.

---

### Post by Sven6210 on 2009-11-16
I also have the EeePC 900a however I did not need to change anything in the BIOS in order to install Ubuntu. Actually you only need to press the 'Esc' key when you get the Asus BIOS screen. A blue box appears and you can choose the booting device (SSD harddisk or USB memory stick unless connected)

If you can not see your USB stick try another one. I also had one stick that did not work for booting on the EeePC even though it works well for copying files (both, with Ubuntu and Windows XP).

Let me know if you have further questions e.g. getting the Ubuntu image on the stick. I can send you the tools I used if that helps you.

---

### Post by mikechant on 2009-11-16
> I downloaded the 9.10 ISO onto my Sandisk 16GB USB flash drive...

Do you mean that you just placed the file on the drive? What I mean is, if you look at the drive in windows, does it appear as whatever.iso in windows explorer?

If that's the case, then it won't work. You need to use a special 'imagewriter' program to write the iso onto the USB stick in the correct format.
The details are here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I'd recommend you do the U3 removal process first though.

---

