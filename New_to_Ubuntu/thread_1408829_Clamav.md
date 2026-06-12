---
title: "Clamav"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by MaryO on 2010-02-16
Greetings,

I tried to find as much as I could; and even though I found a lot of useful information, I still have some questions.

First of all, I keep trying to install clamav 0.95.3 using Synaptic; and it seems to work (it shows 0.95.3 as installed), but if I shut Synaptic down and start it up, it shows 0.95.2 as being installed.  Why does this happen?  

Also, when I type freshclam, it returns the message:  

ERROR:  Can't open /var/log/clamav/freshclam/freshclam.log in append mode (check permissions!).
ERROR:  Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclamlog).

What does this mean?

Once you start a clamav scan, is there a way to stop it?

Thanks all.

---

### Post by MooPi on 2010-02-16
Freshclam needs super user privledge so request freshclam  ```
sudo freshclam
```.
 To stop the scan just hit ```
ctrl c
```

---

### Post by 2hot6ft2 on 2010-02-16
Freshclam just updates clamav I think it auto runs and keep clamav updated.
Clamav is a command line tool and has to be run with root privileges so you would use
```
sudo clamav
```
Since your not familiar with it you can use one or more of these for more info on using it
```
man clamav
info clamav
clamav -h
clamav -help
```
If you want the gui for it look in
Applications > System Tools > Virus Scanner
If it's not there it can be installed with
```
sudo apt-get install clamtk
```

---

### Post by MaryO on 2010-02-16
Thanks Moopi; that worked!

Is it reverting to 0.95.2 because 0.95.3 isn't in the repository, yet?

(I hope this question makes sense.  I'm really, really new to this.)

---

### Post by MaryO on 2010-02-16
Thanks, 2hot6ft2.  I'm going to look at this.

---

### Post by MooPi on 2010-02-16
I'm not certain how you're ending up with .95.2, because I'm showing .95.3. 
Try this ```
clamscan -V
``` and see which version shows.

---

### Post by 2hot6ft2 on 2010-02-16
You're welcome. You should only scan your home folder or other drives. Scanning the file system will give warnings on some files but they are ok, it's been in the forums already and I'm sure it will be again from time to time.

Here's mine
> ClamAV 0.95.3/10397/Tue Feb 16 13:38:01 2010
Must be a typo somewhere

EDIT: Other drives are in /media/

---

### Post by MaryO on 2010-02-17
When I typed clamscan -V, it said, "ClamAV 0.95.2..."


I opened Synaptic, reloaded, and removed ClamAV from my computer (mark for complete removal).  I reinstalled Clamav.  Synaptic showed that 0.95.3 was installed.


I opened Terminal and typed, "  [FONT=&quot]sudo apt-get install clamav".  clamscan -V shows [/FONT]0.95.2  on my computer as does Synaptic.


What's going on?

---

### Post by ikt on 2010-02-17
> **MaryO said:**
> When I typed clamscan -V, it said, "ClamAV 0.95.2..."


I opened Synaptic, reloaded, and removed ClamAV from my computer (mark for complete removal).  I reinstalled Clamav.  Synaptic showed that 0.95.3 was installed.


I opened Terminal and typed, "  [FONT=&quot]sudo apt-get install clamav".  clamscan -V shows [/FONT]0.95.2  on my computer as does Synaptic.


What's going on?

Installing through synaptic suggests 0.93, and after install 0.93 shows up.

> I opened Synaptic, reloaded, and removed ClamAV from my computer (mark for complete removal). I reinstalled Clamav. Synaptic showed that 0.95.3 was installed.


I opened Terminal and typed, " sudo apt-get install clamav". clamscan -V shows 0.95.2 on my computer as does Synaptic.

So synaptic shows 0.95 installed after you install it?

What version of ubuntu are you running?

---

### Post by MaryO on 2010-02-17
I'm running Ubuntu 9.10 Netbook Remix off of a flash drive.

---

### Post by kentechy on 2010-02-17
You should try the Free Bit Defender anti virus for Linux.  It works  great and you get a free license for a year.  After the year is up you  just get another free one.  Here is a link:
[http://tombuntu.com/index.php/2009/07/07/download-and-install-bitdefender-antivirus-on-ubuntu-with-1-year-free-license/](http://tombuntu.com/index.php/2009/07/07/download-and-install-bitdefender-antivirus-on-ubuntu-with-1-year-free-license/)

I even recently connected to another persons virus ridden laptop drive  and ran Bit Defender from my Linux machine and removed the viruses from  the XP laptop.  Hope you give it a try...  


> **MaryO said:**
> Greetings,

I tried to find as much as I could; and even though I found a lot of useful information, I still have some questions.

First of all, I keep trying to install clamav 0.95.3 using Synaptic; and it seems to work (it shows 0.95.3 as installed), but if I shut Synaptic down and start it up, it shows 0.95.2 as being installed.  Why does this happen?  

Also, when I type freshclam, it returns the message:  

ERROR:  Can't open /var/log/clamav/freshclam/freshclam.log in append mode (check permissions!).
ERROR:  Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclamlog).

What does this mean?



Once you start a clamav scan, is there a way to stop it?

Thanks all.

---

### Post by 2hot6ft2 on 2010-02-17
> **kentechy said:**
> You should try the Free Bit Defender anti virus for Linux.  It works  great and you get a free license for a year.  After the year is up you  just get another free one.
I'm pretty sure the key is only good for about 4 months then you have to get another key. I installed it less than a month ago and have 93 days left.

Avast is another good one free key with it too, don't recall ever having to update the key on it.

---

### Post by walt.smith1960 on 2010-02-18
> **2hot6ft2 said:**
> I'm pretty sure the key is only good for about 4 months then you have to get another key. I installed it less than a month ago and have 93 days left.

Avast is another good one free key with it too, don't recall ever having to update the key on it.

Avast for Windows key is good for 1 year. I presume the Linux version is the same.  I recall an AntiVirus comparison in some magazine or the other and Clam for Windows didn't do very well, it missed a lot of problems. Of course in Windows there are more problems to find ;).

---

