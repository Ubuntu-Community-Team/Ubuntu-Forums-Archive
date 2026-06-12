---
title: "I/O error, dev sr1, sector 765768"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Milind on 2009-03-02
I'm a WinXP SP2 user and have recently installed Ubuntu 8.10 as a dual boot option on my computer. The first few days went fine but then I started getting the following messages while booting into Ubuntu :

> sr 3:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sr 3:0:0:0: [sr1] Sense Key : Medium Error [current] 
sr 3:0:0:0: [sr1] Add. Sense: L-EC uncorrectable error
end_request: I/O error, dev sr1, sector 765768
Buffer I/O error on device sr1, logical block 191442

 
This block repeated multiple times. On trying Ubuntu recovery mode the boot process went through such blocks many times before finally booting. As a noob I couldn't work out what was happening nor could I find any solution here, so I reinstalled Ubuntu. End result - same ! Fine for two days and now the same problem. Any advice would be appreciated. (Please bear in mind that I'm an Ubuntu newbie!)

---

### Post by diablo75 on 2009-03-02
How many CD/DVD drives do you have?

---

### Post by Milind on 2009-03-02
> **diablo75 said:**
> How many CD/DVD drives do you have?

Two - one CD-RW, and one DVD-RW.
As a further piece of information, I have now discovered that this problem seems to occur when there is any CD in the drive(s) at the time of booting. Booting seems to proceed without a problem when there is no CD inserted.

---

### Post by diablo75 on 2009-03-02
It sounds like you've found a work-around to the problem.  I'm curious if you were to put a CD into the other drive if the problem comes back.

---

### Post by cragdor on 2010-08-18
Hi,

I also get this with a CD left in the drive at boot. Though my error message is slightly different but i think that is because it is a AudioCD.

[11444.743960] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11444.743967] sr 0:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[11444.743973] sr 0:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[11444.743980] sr 0:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[11444.743991] end_request: I/O error, dev sr1, sector 0

On the plus it seems this error isn't limited to Ubuntu, Gentoo forums have topics on it too.

Craig

---

