---
title: "AV in Ubuntu"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by I8NY on 2010-05-08
Okay i have looked and looked, and i just need some AntiVirus software for Ubuntu to scan *risky* downloaded files off the internet before putting them onto windows pc. I'm not worried about Ubuntu getting a virus i'm more worried about spreading a virus onto windows pcs.  I have tried Avira, no GUI sucks, AVG doesn't support 64bit, and Clam AV just seems outdated and slow.  So what AV should i try or is there any that will run in Wine to scan files?

---

### Post by MooPi on 2010-05-08
There is a program called clamscan in the repository. Install via synaptic or apt-get.
The program updates at boot and works out of the terminal. It might be called clamav

---

### Post by lavinog on 2010-05-08
You can scan files individually with [http://www.virustotal.com/](http://www.virustotal.com/)
it scans the file with a bunch of scanners (good for catching zero day attacks)

---

### Post by Rasa1111 on 2010-05-08
check out  clamTK, and/or Avast. 
they should be sufficient.
and simple.
both with GUI.

---

### Post by doas777 on 2010-05-08
the best one i've found thus far in terms of interface and whatnot is bitdefender. you have to register to get a license key, but it is free. here is a guide for installation: [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

### Post by I8NY on 2010-05-08
okay i tried Clam AV, it works and has a GUI so i'll use that to detect viruses in files.  It was easier to get installed than Avira, thanks for your help!

PS: any good free video editors similar adobe premiere elements?

---

### Post by jerenept on 2010-05-08
[http://www.osalt.com]("http://www.osalt.com")
That should help.

---

### Post by ccw127 on 2010-05-08
Here is my issue with clamav... The windows version finds two threats in a scan of a directory(better than AVG btw, it only found one of the them); but when I boot into ubuntu and scan with clamav (clamscan), the same directory, it says all files were clean...

I've been trying to ask around, but so far, no one knows why.

---

### Post by Kafubie on 2010-05-08
Called KlamAV

---

### Post by ccw127 on 2010-05-08
update on my quest (hope no one things I hijacked this thread...)..

Finished installing Avast as a test for some alternative to clamAV...

Downloading updates failed twice; once due to lost connectivity (that's what it claimed) and once due to complete prog crash (seg fault).

I think avast is lost to me.... oh, and I didn't like that I had to register and request a key to use the 'free' version....

trying out AVG right now...

---

### Post by sixthwheel on 2010-05-08
> I'm not worried about Ubuntu getting a virus i'm more worried about spreading a virus onto windows pcs.

I came to Ubuntu mainly because I got tired of dealing with AV programs and such.
I admire your concern for others, however it should be their responsibility to keep themselves secure, if they choose to use Windows.

I can't help with your problem, because a virus is the last thing on my mind anymore.
Sorry.

---

