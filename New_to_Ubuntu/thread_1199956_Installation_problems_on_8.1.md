---
title: "Installation problems on 8.1"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Grizlybare on 2009-06-29
This should tell you how new I am.  I have tried to install ubuntu 9 times.  Each time while downloading update packages the download stalls and locks the system.  I have waited for several hours but it does not continue.  I reboot and repaired broken packages.  I have almost completed the updates when it always stops.  I have had mozilla firefox not load after updates, been unable to load the window(that time I was at the black & white command line setup), used sudo dpkg many times, grub command line, etc.

Right now I am on the 10th try.  I will not give up, but it is making things difficult.  The screen has locked up again.  

I am running on an asus board, amd64 dual core, 250gb HD, 4gb ram, loading version 8.1.  Should I stop loading the updates and run without?  Even then the system eventually locks up.

Sometimes after I rebooted I would get msgs that crashes occured, and have to go to pkg mgr and make repairs per instructions.  The system would continue to install then lock again.  

I have followed all the directions I can find.  Any suggestions?  Questions?

Thank You.

---

### Post by Celauran on 2009-06-29
Depends what you mean by 'the screen has locked up'. Is it just the download that has stalled, or are applications crashing? If it's the former, try using a different mirror (System -> Administration -> Software Sources -> Download from: ). If it's the latter, please provide more specifics.

Have you tried running the machine without doing any updates? Does this work?

---

### Post by TeoBigusGeekus on 2009-06-29
Have you made a check on the installation cd?
...and come to think of it, why use 8.10 and not 9.04?

---

### Post by Grizlybare on 2009-06-29
The screen stops totally. Right now it is stopped on Downloading pkg files at file 67 and nothing on the page works, the clock has stopped, but the cursor moves.

Yes I have tried running 8.1 without installing any updates but it still locks up.  Sometimes the cursor stops also when this happens.

---

### Post by Grizlybare on 2009-06-29
I use 8.1 because it was given to me and I have to start somewhere.  I have checked the cd and all is well.  I even made a new cd and check sum was fine.

---

### Post by Grizlybare on 2009-06-29
This install is on a new 250gb hd.  I followed all the directions for preparing disk, then ran ubuntu which installed fine.  But like I said... it also locks up, sometimes after 2-3 hours or longer, and sometimes right away.

---

### Post by ibizatunes on 2009-06-29
why dont you download a new copy of 9.04 from ubuntu.com - 9.04 is alot faster the 8.10
Make sure you cd drive is set to boot from cd

---

### Post by scrooge_74 on 2009-06-29
I prefer myself to go with 8.04 for install of new machines.

Did you check the servers?

But if the PC is locking itself even when not downloading you could have other issues there.  How about heat?

check the log files maybe you will get an idea of what is locking it up

---

### Post by Grizlybare on 2009-06-29
I'll try the 9.04.  Should I use the 32 or 64?  I tried both with 8.1.

---

### Post by Grizlybare on 2009-06-29
Servers?  as in download?  Not the heat.  Log files?  Will have to find and check. Right now the Ubuntu computer is locked up.. I did not want to reboot till I had some other options from the forum.

---

### Post by scrooge_74 on 2009-06-29
Is your system a 32 bit or 64 bit? That will depend which CD you need.

Sometimes PCs lock up because of heat issues, like a clogged fan or heat sink.

in /var/log you will find the logs of the system

---

### Post by Grizlybare on 2009-06-29
Rebooted.  Download of updates completed, but - installation stopped.

Examining /etc/kernel/postinst.d.
run-parts: executing /etc.kernel.postinst.d/nvidia-common

Setting up language-pack-base (1:8.10+20061107) ...
Generating locales...
en_AU.UTF-8
en_BW.UTF-8
en_CA.UTF-8
en_DK.UTF      ->This is where it has stopped.

Should I reboot and continue again or try to install 9.04??

---

### Post by TeoBigusGeekus on 2009-06-29
Boot up with 9.04 (live cd) and see how it goes.

---

### Post by Grizlybare on 2009-06-29
It is a 64 but I am installing 32 because instructions said this one had the least problems.  haha  I also tried the 64 but with the same results.

---

### Post by scrooge_74 on 2009-06-29
More the reason I use the LTS versions for the extra support and stability

---

