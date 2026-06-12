---
title: "Grub doesn't list Vista/Ubuntu"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by mercenary10 on 2008-12-22
I went through my ubuntu installation on my new laptop, and there was some error saying it couldn't install some kernel. I simply said continue, and there was another error saying the grub loader couldn't be installed. I clicked on "Continue without installing a loader" and when I booted up, I saw Grub. It only lists Ubuntu memtest, Windows Vista (loader), and Windows XP Embedded. If I boot into Vista, it takes me to the recovery menu, and if I boot into XP, it gives me a blue screen.

What should I do?

Thanks in advance.

---

### Post by jimmy the saint on 2008-12-22
try to do the install over again.  I would recommend making a small (100MB) partition and mounting it as /boot.  That tends to solve the problem for people who report similar problems.  

As a general rule, if the kernel can't be installed you shouldn't continue.  It's like buying a car even though the dealer said they coudn't find the engine for it.

---

### Post by mercenary10 on 2008-12-22
> **jimmy the saint said:**
> try to do the install over again.  I would recommend making a small (100MB) partition and mounting it as /boot.  That tends to solve the problem for people who report similar problems.  

As a general rule, if the kernel can't be installed you shouldn't continue.  It's like buying a car even though the dealer said they coudn't find the engine for it.

Ah.

Is there any way to simply remove ubuntu?

I can't boot into any OS right now.

---

### Post by Sef on 2008-12-22
Did you shrink the Vista partition with Ubuntu, Vista, or other partitioner?

---

### Post by mercenary10 on 2008-12-22
> **Sef said:**
> Did you shrink the Vista partition with Ubuntu, Vista, or other partitioner?

I just used the Guided partition option.

---

### Post by mercenary10 on 2008-12-22
When I went back and reinstalled ubuntu, and got to the Grub part, it said the only OS it detetced was Windows Vista/Longhorn (loader), and Microsoft Windows XP Embedded. 

=\

---

### Post by Sef on 2008-12-22
> I just used the Guided partition option.

Vista needs to be shrunk with its own partitoner.  I'm not sure if there is another way to fix your problem without having Vista on the whole partition, then reinstalling Ubuntu.  I will let someone else tell you, if that is possible, or if I have them I will do research, or you could do research on that.

---

### Post by caljohnsmith on 2008-12-22
If you want a "quick fix" in order to boot back into Vista, how about from your Ubuntu Live CD (install CD) open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
That will restore a Windows equivalent MBR to your internal drive so that you should be able to boot into Vista again. Let me know how that goes or if you run into problems.

---

### Post by mercenary10 on 2008-12-22
I don't see any Applications option on the CD. Is there any other way to get to a terminal?

How would I go about removing Grub? I currently have Vista installed, and don't have the vista discs because my laptop came installed with it. I tried do to "fixmbr" with the WinXP discs, but that didn't work, lol.

---

### Post by bryncoles on 2008-12-23
applications should be top left on the live CD. if its not then press alt-f2 and a run dialogue should appear. type 'terminal' into that, press return and the terminal should appear. then cut-and-paste caljohnsmith's command into the terminal and cross your fingers!

---

### Post by eder.apt-get on 2008-12-23
After that "restart" from the beginning, I recommend you go through some tips on setting up partitions. It´s very easy, which also means, it´s very easy to make mistakes. Check this page:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

---

### Post by mercenary10 on 2008-12-23
> **caljohnsmith said:**
> If you want a "quick fix" in order to boot back into Vista, how about from your Ubuntu Live CD (install CD) open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
That will restore a Windows equivalent MBR to your internal drive so that you should be able to boot into Vista again. Let me know how that goes or if you run into problems.

I had to redownload ubuntu (the latest 8.10 version) and this worked. I was able to boot into vista, thanks.

Now, however, I'm lost installing 8.10. I'm using a USB stick, and I get to this terminal-like thing that says "ubuntu@ubuntu", not sure what to do there. It doesn't go to the same menu as the other CD, where you would simply click "Install ubuntu".

---

### Post by Duck2006 on 2008-12-23
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

