---
title: "Slow ethernet transfers on one computer"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by jeeves on 2008-02-02
Usually on my network I can transfer files between computers using **scp** at a rate of about 10MB/sec. However on one computer** I can't get much better than 2MB/sec.** Any idea what can be going wrong? I already tried the following:

[LIST=1]
[*]using a different NIC  in the slow computer
[*]trying a different ethernet cable from the switch to the slow computer
[/LIST]

The computer in question is a slow but energy efficient[ Asus Terminator]("http://www.superwarehouse.com/ASUS_Terminator_C3/TERMINATOR_C3/p/481934") with a VIA C3 800 MHz processor. The OS is Xubuntu Gutsy.

---

### Post by jeeves on 2008-02-04
I still don't have this solved, but I was able to get about 30% increase in speed by using the** arcfour **cipher instead of the default one for SSH.

 Still not even  half what I should be getting on my network, but an improvement.

---

### Post by netztier on 2008-02-04
> **jeeves said:**
> I still don't have this solved, but I was able to get about 30% increase in speed by using the** arcfour **cipher instead of the default one for SSH.

 Still not even  half what I should be getting on my network, but an improvement.

For the sake of comparison, do an FTP transfer or use **iPerf** from the universe repositories. Search the forums a bit for "iPerf", I posted many times about how to use it. These can give you an impression of what is possible with raw TCP.

There is reason to believe that the slow CPU of that computer is just not up to the encryption/decryption work that is involved when using SSH - you might also want to try the reputedly less CPU-intensive blowfish algorithm for another test - I managed to get a decent increase also with that one.

regards

Marc

---

