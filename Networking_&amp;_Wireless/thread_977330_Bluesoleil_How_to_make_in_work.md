---
title: "Bluesoleil: How to make in work"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by ravi.xolve on 2008-11-10
Since Ubuntu 8.10 has broken Bluetooth I thought for the time bieng I will use Bluesoleil. I installed it and also installed the required dependencies from [http://update.eeepc.asus.com/p701/pool/](http://update.eeepc.asus.com/p701/pool/)

However when I start from /opt/bluesoleil/bluesoleil_link.sh I get the error 

[2244812850 - 3061709712] BsolClient.cc:153: assertion failed

How to make Bluesoleil work in Ubuntu??

---

### Post by nickoe on 2009-02-26
Have you found a solotion? I have the same problem.

---

### Post by ravi.xolve on 2009-03-02
As you can see nothing here, means I have not found the solution. This is really very sad. Most of the times this has happened with me that I post the solutions to the problems I send, not only here but in other forums too, because they are so much different or difficult or no one takes interest.

e.g. My problems with samba are still not solved.

---

### Post by ravi.xolve on 2009-03-02
I think this assertion is is to check that the software runs only on the licensed computer.

---

### Post by aditya2507 on 2009-07-05
This is actually a C/C++ (maybe header files) issue. I still have not got a way to make it run.

---

### Post by orion940 on 2009-08-13
Im getting the same thing in 9.04.  Anyone get past this?

O.

---

### Post by DouglasCaixeta on 2009-08-26
Same problem here

---

### Post by ARhere on 2009-09-17
Confirmed with 9.04 - remix addition.

Since it is paid for software written for Ubuntu Linux, has anyone asked them?

-AR

---

### Post by chucky500 on 2010-07-31
Any news on this?  I installed the Bluesoleil version for Ubuntu v8.04 (the closest version they had), and it installed successfully.  However, when I plug in the bluetooth dongle into the USB port, I see four btusb unknown symbol messages for hci_* symbols (this from the SystemLogViewer).  This same dongle works with BlueSoleil on WinXP just fine, but I'd prefer to work on a Unix derivative.

I'm about ready to give up on Ubuntu.  It seems to have been a hassle and a half over the last year and a half.  Is Linux Mint better?  Where to go?  Or can the problems be solved on Ubuntu and save the install investment, etc.?

:(:(

---

### Post by ravi.xolve on 2010-08-01
Better use Blueman. its a great app.

---

### Post by chucky500 on 2010-08-02
Yep, Blueman is where I was headed next.  Looks like then I wouldn't have to use BlueSoleil, correct?

After having researched the Bluetooth scene in Ubuntu, it appears that things got broken after v8.04 (which is why BlueSoleil supports v8.04, not 8.10, I would guess).  Ubuntu v9.10 apparently has Bluetooth working again (or at least BlueSoleil supports it).  I also notice that the download for BlueSoleil for Ubuntu v8.04 is much larger than for v9.10.

Linux Mint also appears to be broken Bluetooth-wise in the same way.

---

