---
title: "acpid can't open socket: /var/run/acpid.socket:"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by meatychunks on 2009-01-16
Hi,

I'm unable to boot into mythbuntu 8.10 (2.6.27.7) at the moment.

I'll get the message: acpid can't open socket /var/run/acpid.socket: Read only File System

followed by a whole bunch of Read only File System messages relating to files in /var/log/...

I can boot into safe mode - the ACPI service seems to fly by with no problems.

I had had a go at compiling my own kernel, but that didn't go well - I booted ok, and then set the machine to wakeup five minutes later - and from that point onwards I've had the problem above. I've since removed the kernel using Synaptic, but now I'm stuck with this problem.

Any help very gratefully received.

---

### Post by compiledkernel on 2009-01-16
A variety of possibilities. 

1. bad harddrive or hardware. 

2. Bad install

3. Your kernel compile went horridly awry. 

Recommendation - Reinstall.

---

### Post by meatychunks on 2009-01-18
OK thanks.

I've now re-installed mythbuntu.
Restored mysql database, re-configured everything. All good.

Thought I'd have a go at trying to configure the machine to wake it self up for recordings (which was what led to the attempt at building my own kernel previously).

Using the guide here - [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm) - I keyed into my terminal:
```
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm
sudo shutdown -h now
```

As expected nothing much happened - the machine didn't wake up. So I switched back on, only to be welcomed with the message in my first post.

Please tell me that my attempt at building a kernel has not permanently damaged my hardware(!) to the extent that any future attempt, regardless of how many times I re-install my OS, will result in this problem, requiring yet another mythbuntu re-installation.

Until now, this Mythbuntu installation has been running trouble-free for four months.

Again, any help very gratefully received.

---

### Post by meatychunks on 2009-01-22
Bump

---

