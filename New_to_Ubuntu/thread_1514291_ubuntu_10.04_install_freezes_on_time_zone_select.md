---
title: "ubuntu 10.04 install freezes on time zone select"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by bobthewalrus on 2010-06-20
Hey, complete newbie to Ubuntu here, so thanks in advance for any help. My HP laptop running Vista stopped booting up a few days ago, so I spent all last night trying to restore it. That didn't work, so now I'm fed up with Windows and wanted to try Ubuntu. It's an AMD 64 bit machine, and it has all my old Windows crap on it that is inaccessible. So far I tried the Live CD and followed all the steps until the time zone selection screen, where after picking the correct time and pressing forward the installation hangs. I was able to run Ubuntu directly off of the CD but have not yet been able to install it. I tried the alternate installer but that immediately went to a "kernel panic" message. I've seen people with similar problems but nothing that really helped. What should I do?

---

### Post by MooPi on 2010-06-20
Put the Live install CD and boot. Use memtest to see if you have a ram module gone bad.

---

### Post by bobthewalrus on 2010-06-20
How do I do that? When I boot from the live cd it just goes straight to the install window where I can select to try or install.

---

### Post by bobthewalrus on 2010-06-20
bump, what to do?

---

### Post by tacotime on 2010-06-20
> **bobthewalrus said:**
> bump, what to do?

you may want to try an alternate installer...

---

### Post by bobthewalrus on 2010-06-21
By alternate installer do you mean the text based alternate installer or an older version or what?

---

### Post by wilee-nilee on 2010-06-21
> **bobthewalrus said:**
> How do I do that? When I boot from the live cd it just goes straight to the install window where I can select to try or install.

The memory test is on that screen in the list, also we probably can get your Vista back if it's not totally corrupted.

---

### Post by dim3000 on 2010-06-21
> **bobthewalrus said:**
> How do I do that? When I boot from the live cd it just goes straight to the install window where I can select to try or install.

Press any key when you see the logo during boot to access the menu.

---

### Post by wilee-nilee on 2010-06-21
> **dim3000 said:**
> Press any key when you see the logo during boot to access the menu.

Good call if its lucid the shift key is a good one just click it repeatedly as soon as you boot the cd.

---

### Post by bobthewalrus on 2010-06-21
Thanks for responding to my question.
 
Ok, I ran memtest for about two hours and it said it passed with no errors.  What next?

---

### Post by wilee-nilee on 2010-06-21
> **bobthewalrus said:**
> Thanks for responding to my question.
 
Ok, I ran memtest for about two hours and it said it passed with no errors.  What next?

How much ram does the computer have? Actually since you had vista 64 bit it must have at least 2 gigs. 

I wonder if the live cd is corrupted in some manner it shouldn't freeze up. You might try if you have another computer and the one your using will boot from a thumb using unetbootin to load it with a verified md5sum ISO.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Also on the screen you ran the test memory there is a cd verify as well.

---

### Post by bobthewalrus on 2010-06-21
I have 4GB of RAM. I used the scan disc for errors option on the same screen as install, memory test, etc., and it came up with no errors found.  I'm pretty sure I got a good burn on the CD.  I formatted one of my drives when I was trying to restore Windows, so might that have something to do with it?

---

### Post by wilee-nilee on 2010-06-21
> **bobthewalrus said:**
> I have 4GB of RAM. I used the scan disc for errors option on the same screen as install, memory test, etc., and it came up with no errors found.  I'm pretty sure I got a good burn on the CD.  I formatted one of my drives when I was trying to restore Windows, so might that have something to do with it?

Boot the live cd and download the script in my signature and put it on the desktop then run this command in the terminal, 
```
sudo bash ~/Desktop/boot_info_script*.sh 
```
then copy and paste the contents of the file in a response and highlight the text and click on the # in the reply panel. Just copy and paste the command you will see the same one in the link

The script will give us the lowdown of the whole setup.

---

### Post by wojox on 2010-06-21
Maybe make another copy. Use the slowest speed possible.

---

### Post by thetallestpaul on 2010-07-04
This also occurs using a USB drive (64 bit version of ubuntu for sure). I created the bootable usb using the ubuntu live usb creator. It has no trouble running the os, but it hangs on the timezone selection screen when booted directly to install or when launched from the desktop. The symptoms mirror those in the thread exactly.

If you ask me it's silly to even have such a selection screen upon install, setting the time should be the first thing anyone does... Ah well.

---

### Post by Denis.Gorbachev on 2011-05-15
I had this problem, too. In fact, it doesn't hang or freeze. It just copies at the *very low speed*. So try waiting for 10 minutes or so without clicking anywhere.

---

### Post by sagar mali on 2011-07-06
i have tried to install ubuntu 10.04 many a times ,but it freezes before installation steps initiates.....I even tried with ubuntu 11.04 too...this problem is for FULL INSTALLATION...while for installation under windows ,I need to run ubuntu in LOW GRAPHICS MODE..else it freezes at login window.

---

### Post by lastguy on 2011-10-17
as far as you use back space it hangs and stopped copy. so just use forward and change zone after installed. a minor yet very annoy bug stays in a few versions.
 
another minor and even annoy bug - resize dialog box too sensitive - is fixed in 11.04.
 
11.04 support intel new - named gen2 - built in graphics, while redhat/centos 5.x not support. I don't know why there is patch from redhat.
 
also, redhat 5.5 adds a strange bug fix that blocks MAC change. Another thing is there is trend - stupid trend started from fedora - hide terminal by default. Here 11.04 follows it and so it is #1 stupid progress in Linux world. May be it is before 11.04.

---

