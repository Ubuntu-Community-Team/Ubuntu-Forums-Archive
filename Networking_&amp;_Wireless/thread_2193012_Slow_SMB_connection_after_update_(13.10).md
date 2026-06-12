---
title: "Slow SMB connection after update (13.10)"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by enpinion on 2013-12-10
Hi,

Recently, I upgrade my home server's OS 13.10 x64 from 13.04 (Desktop version) as a Web and NAS like server.
Right after upgrade, everything was just fine. SMB connection can makes avg 114MB, full-throttle on gigabit network.

But, the problem is after automatic system update, SMB speed getting really slow! It makes only 15MB/s maximum.
So I test the network speed with "iperf" between the server and a windows desktop but there was no problem with connection speed on my LAN.

I search the forum and Google, and I tried several things like,
 Clean system install, "TCP_NODELAY" trick in the "smb.conf", Jumbo Frame (MTU)... but those things can't fix my problem.

Is this a bug on some updated package or it there any file changes after system update?

Current my Ubuntu system is
Intel Xeon E3-1280 / MSI Z77A-G43 / 8GB DDR3 / and a dual lan card. 

All my network looks okay.

Thanks in advance.

ps. sorry for my English

---

### Post by enpinion on 2013-12-11
Okay self-solving the problem.

The latest kernel (3.11.0-14) was the problem. 3.11.0-12 is fine.

If you have any networking related problem, don't use 3.11.0-14 kernel. It looks have a problem with networking part.


Edit: How can I change this thread as SOLVED?

---

### Post by toxicbreakfast on 2013-12-12
Thank you very much, I had the same problem and this is the only place I could find the answer.  3.11.0-13 works fine too.

---

### Post by john132 on 2014-01-06
I'm seeing this same issue as well. It started with 3.11.0.14 as with OP. I just updated to 3.11.0-15 and it too has the problem. I was getting full gigabit speeds, now about 1/10th the speed. Booting back to 3.11-12 returns speed to normal. Tested via samba with shares on both SSD and spinning disks.

---

### Post by silentcreek on 2014-01-08
I'm having the same issue :-(  Until recently I was getting transfer rates of 80-90MB/s. But after recent updates I'm only getting 7-9MB/s. I first thought something was wrong with the ethernet connection (running at 100MBit instead of 1GBit). But that's not the case.  Is there a bug report for this issue somewhere so we can expect an update anytime soon?  Thanks,  Timo

---

### Post by XxOsurfer3xX on 2014-01-28
I'm having the same issue too, can't stream FullHD content over Samba, only NFS. Any word on a fix?

---

### Post by Felhazi_Andrei on 2014-02-03
Oh my god Thank you so very much. Downgraded the kernel and got arround 930 Mbps. You are a godsent my friend!

---

### Post by ccerghe1 on 2014-02-06
I also noticed that suddenly, my transfer speed over a wired network to a Samba share was down to 14 MB/s.
My issue now is that when booting in the older 3.11.0-13 kernel, my XFCE session just locks up and accepts no keyboard or mouse input.  So I'm afraid this won't be a good option for me.  The only bug report I found related to this was [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1259634 ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1259634")and it looks like it's fixed upstream, so I decided to bite the bullet and upgrade to Trusty Tahr (Alpha).

---

### Post by XxOsurfer3xX on 2014-02-15
Is it fixed in Trusty? I'm still having the same problems....

---

### Post by john132 on 2014-02-23
This seems to be fixed with kernel 3.11.0-17. I'm now getting full speed via smb in and out.

---

### Post by XxOsurfer3xX on 2014-02-24
Not for me, still having the same issue on 3.11.0-17... I'll do some more testing and report back.

---

### Post by XxOsurfer3xX on 2014-03-08
OK, so I have an update. My Ubuntu-Windows shares are working at full speed with the new kernel. The problem is between my NeoTV 550-Ubuntu, the slow samba shares persist... Anyone has any idea of what could be happening?

---

