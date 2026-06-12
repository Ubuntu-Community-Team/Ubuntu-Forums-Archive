---
title: "Ubuntu 9.10"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by wstay on 2010-03-24
I tried Ubuntu 9.10 on Intel Pentium 2.66Ghz on a new motherboard Gigabyte S-series G31M-ES2L with 1Gb ram (call this system 1)and the system can behave strangely - like the system hangs, the usb mouse stop moving, the screen on the desktop can flicker and at one time the screen can start blinking, the firefox I am browsing can disappear all of a sudden, the synaptic package I am using to install a package can suddenly stop or disappear.
I bring the HardDisk with this Ubuntu 9.10 installed to another computer with Intel Pentium Dual-Core 3Ghz processor also on a new and the same model motherboard Gigabyte S-series G31M-ES2L also with 1Gb ram (call this system 2) and the system can function normally without any problem. 
Is it that Ubuntu 9.10 is not compatible with system 1 and should not not be installed and use on system 1.
Or may be it is some problem with my hardware on system 1.
I don't know. Can someone please advise.

---

### Post by -grubby on 2010-03-24
Oh wow, that's pretty severe; do you know how Windows behaved on System 1? If you don't, try using a live cd and doing those actions and see if they hang or error like that. If they don't, maybe you should reinstall Ubuntu on system 1.

---

### Post by Drenriza on 2010-03-24
How about trying to install a LTS version on your system instead of 9.10

---

### Post by -grubby on 2010-03-24
> **Drenriza said:**
> How about trying to install a LTS version on your system instead of 9.10

Long Term Support means it's supported longer with bug fixes, not necessarily more stable.

---

### Post by steve-shinn on 2010-03-24
Sounds like a hardware issue to me.
Try running the memtest (option available at boot up) for a couple of hours. Or alternatively, try the ram from system 1 in system 2 and vice versa

---

### Post by ukripper on 2010-03-24
> **wstay said:**
> I tried Ubuntu 9.10 on Intel Pentium 2.66Ghz on a new motherboard Gigabyte S-series G31M-ES2L with 1Gb ram (call this system 1)and the system can behave strangely - like the system hangs, the usb mouse stop moving, the screen on the desktop can flicker and at one time the screen can start blinking, the firefox I am browsing can disappear all of a sudden, the synaptic package I am using to install a package can suddenly stop or disappear.
I bring the HardDisk with this Ubuntu 9.10 installed to another computer with Intel Pentium Dual-Core 3Ghz processor also on a new and the same model motherboard Gigabyte S-series G31M-ES2L also with 1Gb ram (call this system 2) and the system can function normally without any problem. 
Is it that Ubuntu 9.10 is not compatible with system 1 and should not not be installed and use on system 1.
Or may be it is some problem with my hardware on system 1.
I don't know. Can someone please advise.

Try the live cd as grubby has suggested on system 1. 

If you see problem still than try another version of ubuntu live cd for e.g. ubuntu 9.04 live cd.

BTW, Are you using 32 bit or 64 bit ubuntu?

---

### Post by andy1964 on 2010-03-24
I thought 9.10 was LTS?

---

### Post by -grubby on 2010-03-24
> **andy1964 said:**
> I thought 9.10 was LTS?

No, but 10.04 will be.

---

### Post by wstay on 2010-03-24
My system 1 is 32bit I presume and my system 2 is 64bit.
I don't how to check for sure which bit it is.
When I download ubuntu 9.10 I thought it is a i586 version.
Someone pointed out to me ubuntu 9.10 is a i386 version.
I also suspect could be my ram because at one time the screen went blank and I restart my computer also blank screen. So I change the ram slot and it restarted ok. Until now every time it restarts ok.
The problem now is the system 1 is behaving strangely.
I don't know if ubuntu 9.10 is a stable release.
Can someone confirm whether it is or it is not.

---

### Post by ukripper on 2010-03-24
> **wstay said:**
> My system 1 is 32bit I presume and my system 2 is 64bit.
I don't how to check for sure which bit it is.


go to terminal and type this command:
```
grep flags /proc/cpuinfo
```

If output shows **lm** then it means your processor support 64 bit otherwise 32

---

### Post by -grubby on 2010-03-24
> **wstay said:**
> My system 1 is 32bit I presume and my system 2 is 64bit.
I don't how to check for sure which bit it is.


On each computer, open terminal, type the following command, and give us the result:

```

cat /proc/cpuinfo

```

> 
When I download ubuntu 9.10 I thought it is a i586 version.
Someone pointed out to me ubuntu 9.10 is a i386 version.


i386 means it's compiled to run on the 386 or higher. i586 means the Pentium or higher. Ubuntu won't run on either of them so it doesn't really matter.

> 
I also suspect could be my ram because at one time the screen went blank and I restart my computer also blank screen. So I change the ram slot and it restarted ok. Until now every time it restarts ok.


Try starting up the Ubuntu cd and selecting the "memtest" option. It'll take a long time so you might as well run it overnight or something. Tell us the results when it finishes

> 
The problem now is the system 1 is behaving strangely.
I don't know if ubuntu 9.10 is a stable release.
Can someone confirm whether it is or it is not.

9.10 has had it's final release, it's considered stable. The current testing release is 10.04.

---

### Post by 1991sudarshan on 2010-03-24
try the previous version 9.04 on your system and tell if you face any problem in the future!! linux is designed to work with older systems  and systems which are not of high end and latest hardware configurations!!!!!!!

---

### Post by s.fox on 2010-03-24
Hello,

> **andy1964 said:**
> I thought 9.10 was LTS?

The current LTS is 8.04.  It can be found [here]("http://releases.ubuntu.com/hardy/").

The next LTS is  10.04 and it will be released on  29th April.  

-Silver Fox

---

### Post by wstay on 2010-03-24
I am now running the ubuntu 9.10 Live cd on system 1.
Only just now the first time I booted and used the Live cd the first thing I notice is that the usb mouse hang but the wireless mouse can use. After about half an hour of using, the wireless mouse also hang and also the wireless keyboard hang. So I just pressed the restart button to reboot.
Now the second time this ubuntu 9.10 Live cd booted, the usb mouse and also the wireless mouse and keyboard seem to be functioning.
I better stop here for now just in case the mouse and keyboard hang.

---

### Post by wstay on 2010-03-24
I am still on and running ubuntu 9.10 Live cd on system 1.
I post:
ubuntu@ubuntu:~$ grep flags /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
ubuntu@ubuntu:~$ 

and aslo post:
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 2.66GHz
stepping	: 4
cpu MHz		: 2667.013
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 5334.02
clflush size	: 64
power management:

ubuntu@ubuntu:~$ 

From the postings, I don't see any 1m. So my system 1 is 32bit.
I will do the postings on my system 2 later.
For now, already about 1 hour it seems to be functioning normally on system 1.

---

### Post by wstay on 2010-03-24
I am now running ubuntu 9.10 Live cd on system 2.
I post:
ubuntu@ubuntu:~$ grep flags /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
ubuntu@ubuntu:~$ 

and also post:
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Pentium(R) D CPU 3.00GHz
stepping	: 4
cpu MHz		: 2400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
bogomips	: 5999.81
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Pentium(R) D CPU 3.00GHz
stepping	: 4
cpu MHz		: 2400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
bogomips	: 6000.14
clflush size	: 64
power management:

ubuntu@ubuntu:~$ 

So the lm confirms my system 2 is 64bit.
Can we say that all Dual-Core processors are 64bit?

If I can do a "memtest" option which as you say is going to take a long time, how am I going to sent the result over to you?
I have never done a mentest. So if there is a safe option to safe it to the hard-disk after the memtest is done, then may be I will try.

One more thing to ask.
How do I find out if my ubuntu 9.10 Live cd is 32bit or 64bit?
I think if I remember correctly, when I downloaded the ubuntu 9.10 Live cd, it is 32bit. How can I confirm or see that the cd I have now is 32bit.

---

### Post by -grubby on 2010-03-24
> **wstay said:**
> 
Can we say that all Dual-Core processors are 64bit?


Not quite, but in practice they are

[quote=wstay]
If I can do a "memtest" option which as you say is going to take a long time, how am I going to sent the result over to you?
I have never done a mentest. So if there is a safe option to safe it to the hard-disk after the memtest is done, then may be I will try.
[/quote]

To be honest, I've never done a memtest either, I'll try one in a virtual machine and tell you the results after it finishes.

EDIT: here's a screenshot of it in action. I'm going to run it as long as I can but it seems the "errors" column would list if there's any errors.

[img]http://i42.tinypic.com/27xnznn.png[/img]

[quote=wstay]
One more thing to ask.
How do I find out if my ubuntu 9.10 Live cd is 32bit or 64bit?
I think if I remember correctly, when I downloaded the ubuntu 9.10 Live cd, it is 32bit. How can I confirm or see that the cd I have now is 32bit.[/QUOTE]

Again, I don't know. I'll try to figure that out in a VM also.

---

### Post by wstay on 2010-03-24
This morning I started my computer with the ubuntu 9.10 live cd on system 1. Everything seems ok except my wireless mouse is not functioning. Could be battery in the wireless mouse run flat. After about 5 minutes now I got message saying: 'Your system encountered a serious kernel problem. Your system might become unstable now and might need to be restarted.'
I noticed a red coloured icon on the taskbar just after the computer had login on the desktop. I right click on it and it disappeared. Now it appears again after about 15 minutes and I point the mouse on it and it says 'Crash report detected'. So obviously something has crash but don't know what it is. I had click on send to send the message saying my system encountered a serious kernel problem to the developer. They should be able to figure out what and where the problem is.
Its already about half an hour into using system 1 with ubuntu 9.10 live cd and everything seems to be functioning.
I better submit this reply/post just in case or before any problem might appear.
Just when I submit this, my internet connection got disconnected.
I switched off the modem and switched on again and got connectted to the internet again.

---

### Post by oldsoundguy on 2010-03-24
use your disk and re run memtest .. only this time walk away for a while and let it run the complete series.  To ME, this sounds like a ram problem because errors keep shifting.

---

### Post by wstay on 2010-03-24
When doing a memtest, if it is a ram problem, what reading in particular do I look for. I did change the ram slot a few times when at that few times I could not boot my computer because when I booted my computer, it gave me a blank screen. Now it boots every time ok. May be it could also be a problem with the ram slots on the motherboard. Both the motherboard and the ram are new which I bought about 2 months ago.
I will do a memtest and let you know soon.

---

### Post by wstay on 2010-03-25
I started the memtest at about 12 noon time. 45 minutes into the memtest and it says "Pass complete, no errors, press Esc to exit" after I think it finishes at Test #4. But the memtest still continues and its at Test #7 now.
I press Esc to exit but it won't exit or reboot.
Is this an indication of problem of ram or ram slot on the motherboard?
Should I just continue with the memtest although it says "Pass complete, no errors, press Esc to exit"

---

### Post by wstay on 2010-03-25
I restart the memtest again and this time after about half an hour, it says "Pass complete, no errors, press Esc to exit" and it continues testing. I press Esc and this time I can exit and reboot my computer.
So, shall I restart the memtest and continue eventhough if it says "Pass complete, no errors, press Esc to exit".

---

### Post by wstay on 2010-03-26
I have one important question to ask.
Why on the same computer with a windows os on the same hard-disk on a separate
partition, the windows os would run normally except only on one occasion the
firefox I was browsing suddenly disappear from the screen. I formatted my ubuntu
9.10 partition and installed Mandriva One 2010 kde4 i586 in its place and find
that not long after using (about a 3 to 5 minutes) the usb and wireless mouse and
keyboard would always stop functioning. This would always happen even after
restarting the computer.
I feel that running the os from live cd is much faster than running it after
installing it onto the hard-disk. And running it from the live cd would not have
any problem except on one occasion after about 20 minutes of using the usb mouse stop functioning.
Any comments please.
I need an urgent answer so that I know what is happening to my computer.
I need to know the problem is with the os I downloaded or the cd I burnt the os onto, 
or these are hardware problem?

---

### Post by 3rdalbum on 2010-03-26
Take it from someone who knows: Faulty RAM can work fine across multiple memtest passes. You need to run it overnight; test that RAM for 10 hours.

A quick short-cut is to install the Phoronix Test Suite and run the memory speed benchmark; if your computer crashes during this benchmark (which only takes a few moments) then your memory is bad.

Bad RAM can cause all those symptoms that you describe.

The easiest way to check if you have bad RAM is to look at the sticks - if they say "Kingston", then they're faulty... ;-)   No seriously, my entire experience with faulty RAM is with Kingston; we're talking about multiple occasions.

---

### Post by wstay on 2010-03-28
My computer seems to to be back to normal after I use the ram from system 2 which is functioning normally and put it into system 1. The faulty ram from system 1 is a Mushkin Enhanced ram which I bought new. Now I can claim a replacement for it because it is under life warranty.
Thank you all for the help and support.
Any comment on the quality of this brand of faulty ram?

---

