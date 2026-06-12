---
title: "Can't read DVD"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by mijdrawoh on 2011-08-31
11.04. Using the data function of Brasero, I burned some photos on a DVD-RW and got an error message that some files might be corrupted. In trying to check if there were problems with the burned images, I discovered that I had no way of reading the disk. I've obviously done something wrong, but I haven't been able to find what it is in my research. Can someone help?

---

### Post by seawolf167 on 2011-08-31
Ensure that you are burning on a sufficiently slow speed - if you try to burn the disc too fast it'll cause corruption if the buffer cannot keep up with the writing. I usually suggest when people burn LiveCDs to burn on the slowest setting possible.

---

### Post by Rex Bouwense on 2011-08-31
+1
Since the DVD is an RW, it doesn't cost anything to burn it again.  I have had the occasional problem with Brasero, but nothing permanent that restarting it didn't fix.

---

### Post by mijdrawoh on 2011-08-31
I burned the disk at the same speed I used to burn the ISO. My problem is finding a way to read the DVD.  Should it come up automatically when I insert the disk? Do I have to install something from Synaptic? I tried the ISO disk I used to install 11.04 and it was read without a problem, so I'm at a loss.

---

### Post by seawolf167 on 2011-08-31
Can you see it under the Places menu? Can you see it under the directory /mnt/cdrom?

---

### Post by Rex Bouwense on 2011-08-31
Does the OS recognize the DVD player with the DVD inserted?    When you try to open the DVD what error message are you getting?

---

### Post by mijdrawoh on 2011-08-31
Thanks for your responses. The DVD doesn't show up in Places or /mnt. It doesn't automatically mount, so I can't open it and there is no error message. If I put in the 11.04 ISO, it shows up in Places. If I put in a blank, a screen comes up asking what I want to do to the disk. The disk is there and is recognized, and spins up, but nothing indicates that 11.04 sees it.

---

### Post by eldette on 2011-10-13
> **mijdrawoh said:**
> Thanks for your responses. The DVD doesn't show up in Places or /mnt. It doesn't automatically mount, so I can't open it and there is no error message. If I put in the 11.04 ISO, it shows up in Places. If I put in a blank, a screen comes up asking what I want to do to the disk. The disk is there and is recognized, and spins up, but nothing indicates that 11.04 sees it.

I have a similar problem. I'm running Kubuntu Natty and my dvd doesn't show up in "Places". When I insert a blank dvd-r, I get the new media notification, it appears as "blank dvd-r", but there's nothing I can do with it... I tried:
```
sudo mount /media/cdrom0/ -o unhide
```and I got this:
```
mount: can't find /media/cdrom0/ in /etc/fstab or /etc/mtab
```I'm not a very advanced user and I haven't managed to find much help on this yet... I'd really appreciate it if anyone could give me a hand here...

Update: I upgraded to Kubuntu 11.10 and the problem doesn't exist anymore. :)

---

### Post by soap1 on 2011-11-26
make sure you have the libdvdcss2 package installed.  Here is a useful link
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

