---
title: "Upgrade now no CD drive"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by jivabill on 2010-05-02
I installed 9.10 on my Dell C610 Laptop.  Then I foolishly decided to do the upgrade to 10.04LTS.  Bad idea.  I have never yet had an upgrade work right.

So now when I put a CD-R in the CD Drive it cycles 10 times and shuts down.  Can't read it. When I try to use K3b it, K3b, says there is no medium in the drive.

I have no idea what to do to fix this or if it is a common problem.  

Help would be appreciated.
thanks for reading.
bill

---

### Post by nhasian on 2010-05-02
thats odd.  can you try booting from the Ubuntu 10.04 liveCD?

---

### Post by jivabill on 2010-05-02
Hi Hasian, nice to meet you.  Thank you for your suggestion.  Unfortunately I don't have the 10.04 Live CD.  The way I got 10.04 was by the Upgrade Link at the top of the Update Manager screen while I was running updates to 9.10.

So I guess if I decide to go ahead with 10.04 I will have to download the Live Desktop CD.

If this was happening on a Windows machine I would know what to do: update the driver for the CD drive or replace it with a better driver.  I have no idea how that would be done in Linux.

Thanks again,
bill

---

### Post by nhasian on 2010-05-02
it doesnt matter if you are going to upgrade or not, my objective was to see if your cdrom works or not.  do you have any bootable cd rom you can try?

---

### Post by jfreak_ on 2010-05-02
@jivabill download the alternate iso and run

 sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0
 gksu "sh /cdrom/cdromupgrade"
This way you won't have to burn a cd

---

### Post by jivabill on 2010-05-02
Nhasian, I understand.  And yes the CD drive does work.  I was able to boot the system using the 9.10 Live CD, worked fine.

jfreak, thanks for the idea on the upgrade.  I'll keep that on file for future use.  I have the 10.04 LTS Live CD downloaded now and burning it to a CD is no problem, one of my machines has a very fancy burner drive.  And  I am going to need the Live CD later on.  Thanks for your input.

---

### Post by jivabill on 2010-05-05
After some experiments with CDs and CDRs and different write speeds during the burn, I think the problem has been that the Dell laptop's CD/DVD reader can not handle some of the more modern faster burning speeds.  That is it can't read a CD that was burned at say 48x.  But the same data burned at 8x can be read OK.

Then I found that IF I made sure the CD was mounted before trying to read it then I could get it to read.

However the only CDs that will just play when I put them in the drive are the ones written at 8x or below.

So that may be the answer.  Problem solved -- I think.
Thanks to all who helped with this I appreciate all the suggestions.  Got me to thinking and trying different burn speeds and found an answer for my problem.
bill

---

