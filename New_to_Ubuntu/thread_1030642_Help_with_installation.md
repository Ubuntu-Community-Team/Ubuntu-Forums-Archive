---
title: "Help with installation"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by fireball1953 on 2009-01-04
I am new to the forums group. Looking for help. I am new to Linux. Have downloaded 8.10. Burned the ISO. Booted from the cd. Intention is to do a new install. I selected install at the first opportunity. I am installing on an HP Pavilion 533, 2ghz, 256mb, 20 gb hd. The partitioner thinks the hd is scsi. It is not it is IDE, western Digital WD200.

I can't figure out how to get the partitioner to recognize that it is IDE. How do I proceed? I am perfectly willing to try to find the info, just don't know where to start. Could someone tell me in simple terms how I find the info I need to install on this PC?

---

### Post by bodhi.zazen on 2009-01-04
Post moved to a support section (the Education thread is not a support thread)

I believe as of 6.10 Ubuntu recognizes all HD as scsi, you should be able to install, although 256 RAM is a bit low. You may need to use the alternate CD and make a 512 Mb swap partition.

---

### Post by halitech on 2009-01-04
as bodhi says, with the way the newer kernels work, it thinks every device is scsi so they will all show up as /dev/sdX

IE. Primary master would show as /dev/sda with the first partition showing as /dev/sda1
Secondary Master would show as /dev/sdb with first partition being /dev/sdb1, etc, etc

---

### Post by fireball1953 on 2009-01-04
Thanks for the replies. I will get the alternate cd.

---

### Post by fireball1953 on 2009-01-05
I downloaded the alternate cd and installed. Everything went OK up until booting up from the hd after install. I was asked to enter username and pwd which I did. All i get is the desktop background color and nothing else happens. Mouse pointer will move so I guess not hung up.

Can someone provide tips on what to do now?

---

### Post by bodhi.zazen on 2009-01-05
My guess is that you have insufficient RAM.

---

### Post by fireball1953 on 2009-01-05
Thanks for the reply bodhi. You mentioned that yesterday when you suggested the alternate cd. How do I set up the 512mb swap file?

---

### Post by bodhi.zazen on 2009-01-05
During the installation, at the partitioning part, you will need to manually set up your partitions, and make the swap partition 512 Mb.

The other option would be to boot with either the live CD or the live gparted CD and manually resize the partitions.

---

### Post by halitech on 2009-01-06
the other possibility is an issue with the video card. What kind of video card do you have?

---

### Post by fireball1953 on 2009-01-07
Is there a Linux program or utility that will probe the video adapter and tell me what it is. I'm almost sure that it is Intel Extreme Graphics, not sure of the numbers. I think 82865 maybe. I blew Windows away so I can't use it to tell me.

I really appreciate all assistance. I would really like to get comfortable with Linux. I'm no expert but have been working on computers since S100 bus and CPM. I just haven't figured out how to get the info. that makes since to me.

I would like to understand how to do in Linux what I know how to do in Dos/Windows.

Any advise would be greatly appreciated.

---

### Post by bodhi.zazen on 2009-01-08
You can list your hardware from the command line with

sudo lshw

you can format that to a html document with 

```
sudo lshw -html > hardware.html
```

You can then view the output with firefox if you prefer.

---

### Post by fireball1953 on 2009-01-08
Thank you for the reply sir.

---

### Post by fireball1953 on 2009-01-10
halitech, video card is integrated, Intel 82845G/GL [Brookdale-
G] GE Chipset Integrated Graphics Device. Also there is a 721mb swap partition. Thanks in advance for your assistance.

---

### Post by bodhi.zazen on 2009-01-11
I am not overly familiar with that card, but I think there is an issue with Ubuntu 8.10

Hopefully someone familiar with that card will pipe in, otherwise try google.

You may want to try Ubuntu 8.04

---

