---
title: "Sprint novatel wireless ovation broadband usb modem"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by gljay on 2007-05-16
I would like to get off M$ winders totally.  I am on the road most of the time and have the USB Novatel Wireless Broadband Modem from Sprint.  I have not found anything on sprints site nor on the novatel site that would allow me to install this on my Ubuntu 7.04 system.  Does anyone know anything to assist.   If not I am working to get them at Novatel to assist with a driver.](*,)

---

### Post by stephlivsey on 2008-01-21
Hi, I am a Linux newbie but just installed Ubuntu 7.04 on a PC.  I just purchased the new Sprint Novatel Ovation U727 that boasts compatibility with Linux.  Anyhow, after a LONG day...I finally got it working.  I followed Sprint's directions; however, there was one "error" that really threw me off for most of the day.  If you don't already have a working internet connection (why would you if you didn't have the card working yet???), use the terminal and WvDial.  I posted my edits to the Sprint manual here:  [http://lynndouglasmedia.com/ubuntu/Set-up-sprint.pdf]("http://lynndouglasmedia.com/ubuntu/Set-up-sprint.pdf")

Wireless Broadband USB is now working great!  I hope this helps others out there...

---

### Post by ludedude on 2008-01-25
> **stephlivsey said:**
> Hi, I am a Linux newbie but just installed Ubuntu 7.04 on a PC.  I just purchased the new Sprint Novatel Ovation U727 that boasts compatibility with Linux.  Anyhow, after a LONG day...I finally got it working.  I followed Sprint's directions; however, there was one "error" that really threw me off for most of the day.  If you don't already have a working internet connection (why would you if you didn't have the card working yet???), use the terminal and WvDial.  I posted my edits to the Sprint manual here:  [http://lynndouglasmedia.com/ubuntu/Set-up-sprint.pdf]("http://lynndouglasmedia.com/ubuntu/Set-up-sprint.pdf")

Wireless Broadband USB is now working great!  I hope this helps others out there...

Thanks, helped me ;) Do you have a working signal strength meter?

---

### Post by stephlivsey on 2008-01-27
I am glad that my information helped :)
No, I do not have a working signal strength meter.

I did; however, also find out that this set up works with my current broadband card from sprint as well (Sierra Aircard 595U).  I also realized that I have to go through the steps each time I want to connect (however, I do not have to set up the wvdialconf file each time):

So, now when I go to connect I plug in my card and do the following:
1.   sudo modprobe -r usbserial
 (enter password)
2.  sudo modprobe usbserial vendor=[vendorID listed on sheet] product=[ID listed on sheet]
3.  sudo dmesg|grep -i ttyUSB
4.  sudo wvdial
Then, after that I'm connected (but no strength meter)  It's faster than the first time because I don't have to edit the wvdialconf file each time, but it does take just a moment to go through the terminal commands.

I did try and download the KPPP program that Sprint recommended in their directions; however, I have found the terminal method of wvdial to be more reliable (works every time for me...KPPP seems to not recognize my modem and I still have to go through terminal to enter the first two commands above).

---

### Post by astrashe on 2008-01-27
I've been trying to get my Sprint Sierra Wireless AirCard 595U to work.

I've tried to use Sprint's instructions, and the ones that I've found here and in other places, but I can't make it work.  I always get the same error -- a NO CARRIER message from the modem after it dials.  

I've tried both KPPP and wvdial, but am mostly trying to use wvdial, because it seems to be easier.

I'm using Ubuntu 7.04.

Has anyone seen this NO CARRIER problem before?

---

### Post by stephlivsey on 2008-01-27
Have you made sure to include the "Carrier Check = no" in your wvdialconf file?  I haven't had this error, but when my file wasn't configured properly the first time, I did get a 'cannot connect to carrier' error message.

---

### Post by ludedude on 2008-01-29
Each time I want to connect I just have to open a terminal and type wvdial and wait for it to connect.....I do however get some errors/warnings I wonder if you get them too, and if they can be fixed..

```

WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial<Notice>: Don't know what to do!  Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Tue Jan 29 00:45:58 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 9762
WvDial<*1>: Using interface ppp0
```

and it seem to be disconnecting on me on it's own.....is there a time out setting??

---

### Post by stephlivsey on 2008-01-30
Hmmm....
I'm sorry but I don't know how to help on that one.  I run through each step everytim (load drivers, test drivers, then sudo wvdial) and I never get any errors.  The commands in terminal show that it initialized the modem, connected the the carrier and then I'm on; I haven't been dropped from my internet connection at all.

I had problems using the KPPP program, but not with using the terminal based wvdial.

---

### Post by ludedude on 2008-01-30
ha...I'm using kppp now ith now problems and/or dropped connections....go figure :P

---

### Post by stephlivsey on 2008-01-30
technology can be funny...
I'm glad it's working well now for you.

---

### Post by Pe Elle on 2008-03-18
:-D to make the module load persistanly use add your modprobe stuff into /etc/rc.local

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

That pdf has detailed instructions for this somewhere in the last couple of pages.

---

