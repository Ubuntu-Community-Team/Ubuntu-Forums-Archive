---
title: "Firefox hogging CPU"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by zcacogp on 2009-07-24
Chaps, 

I'm running 9.04, with an ATI graphics card, on my desktop machine. This DID work fine until I ruined the install trying to update the kernel. Long story short, I managed to make it run again, and all seems to be well, with a couple of exceptions - one of which is firefox. 

When I run a decent number of tabs in firefox (10 or more), it runs like a dog. Slow to switch between tabs, slow to scroll. Other aspects of the machine seem fine. 

My xorg.conf file looks like this: 

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:5:0"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

If I type: 

```
glxinfo | grep 'direct'
```

I am told that ```
direct rendering: no (LIBGL_ALWAYS_INDIRECT set)
```. 

If I type: 

```
unset LIBGL_ALWAYS_INDIRECT
```

Then things are maybe fractionally better, but I am not convinced. 

Note: Before the changing kernel debacle things were fine, and this wasn't a problem. I am now back on the same kernel as before, with the same screen driver (I think), but this problem has arisen, so I know that it is possible for it to be better. 

All help welcomed - thanks. 


Oli. 

P.S. I mention the things about direct rendering and xorg.conf because reading on here seems to suggest that they are relevant, but this is just guesswork on my behalf.

ETA: Typing "top" tells me that the process hogging the CPU is firefox (on occasions managing to show a CPU usage of greater than 100% - not sure how this is possible).

---

### Post by Luke Carrier on 2009-07-24
I presume you have a multicore processor? If so, that's most likely how a process can consume more than 100% CPU.

As for the Firefox problem, have you tried running 'firefox' in a terminal and looking at the output for any potential issues? It is highly unlikely that a kernel upgrade would cause Firefox to misbehave...

---

### Post by Dougie187 on 2009-07-24
I am getting this same issue and haven't gotten any responsise to my thread. Though mine was mainly about how it stays active even after I close it with a usage of over 100% (the over 100% is because of multiple cores as previously mentioned).

Either way, I will be interested to see if anyone has an idea how to fix it. Since this even happens to me when I am using say, 2 or 3 tabs. It's noticable because firefox 'skips'. 

Also though, I am using FF 3.5, not sure if you are as well.

EDIT: Also, I ran it in a command line, and checked the log files, and there wasn't any useful information for me. Though I did this a while ago.
Here is my thread [http://ubuntuforums.org/showthread.php?t=1220964](http://ubuntuforums.org/showthread.php?t=1220964)

---

### Post by irv on 2009-07-24
My system is running good so I thought I would just run a test to see if I could bog down my firefox, but I couldn't. The most CPU % I could get with 12 tabs open was 35%, but most of the time it would run at 5 to 8%. Here is a screenshot:
[ATTACH]122250[/ATTACH]
This might give you something to shot for.
I am sorry I can't really help with the problem, but I hope someone has an answer.

---

### Post by zcacogp on 2009-07-24
Chaps, 

Thanks for the answers. 

Luke Carrier - yes, it is dual-core. I didn't realise that each core would run up to 100% - I thought that the %age was of the total capability. Thanks! :P

When you say "Run Firefox in the terminal", do you mean open the terminal and type "Firefox". If so, I've just tried it and it runs fine, and the terminal prompt doesn't say anything. 

On the kernel issue - I tried to upgrade to 2.6.30, but it conflicted with my screen driver and I had to uninstall the screen driver, downgrade the kernel and re-install the screen driver. I suspect it is in the uninstalling and re-installing of the screen driver that I have changed some setting. But, to confirm, I am back where I was in terms of screen driver installed and kernel being used. Or at least I should be, this problem notwithstanding .... 

Dougie, I'm using FF 3.0.12. Upgrading could be an option ... thanks. 

Irv, thanks for the screenshot. I know this can be better as it was better before! Good to have something to aim for. 


Oli.

---

### Post by SecretCode on 2009-07-24
Firefox slowdowns are often due to memory hogging (less so in Fx 3 than earlier versions but still a factor) or due to lots of items in the cache. Hogging the CPU is only a symptom. And it may not be anything to do with graphics.

Clear your cache and restart firefox - does this make any difference?

---

### Post by irv on 2009-07-24
> **SecretCode said:**
> Firefox slowdowns are often due to memory hogging (less so in Fx 3 than earlier versions but still a factor) or due to lots of items in the cache. Hogging the CPU is only a symptom. And it may not be anything to do with graphics.

Clear your cache and restart firefox - does this make any difference?

I remember now reading this somewhere so I googled it, and here is a link:
[http://markusthielmann.com/blog/firefox_slowdown]("http://markusthielmann.com/blog/firefox_slowdown")

---

### Post by LewRockwell on 2009-07-24
must have missed where OP stated Firefox version...

dougie is using FF 3.5 and having the problem(I've noticed FF3.5 bogging down as well)

irv is using 3.0.12 and not having a problem...


maybe we should all switch back to 3.0

.

---

### Post by Dougie187 on 2009-07-24
> **LewRockwell said:**
> must have missed where OP stated Firefox version...

dougie is using FF 3.5 and having the problem(I've noticed FF3.5 bogging down as well)

irv is using 3.0.12 and not having a problem...


maybe we should all switch back to 3.0

.

I don't know if I am still having the same problem with 3.5. Are you using the ubuntu repo 3.5? "Shiretoko"? or are you using a PPA one?

I am using Shiretoko, and I think my problem has something to do with the last update committed to the ubuntu repos, but again, I am unsure as I haven't read a lot of reports on this.

---

### Post by lovinglinux on 2009-07-25
Firefox uses a lot of CPU on some javascript sites and when playing flash videos. Additionally, some extensions I had installed in the past were leaking memory and causing lag, with Firefox using about 650 Mb of resident memory. Nevertheless, the CPU usage was normal on this situation.

Check the tutorial link in my sig. It might help.

---

### Post by zcacogp on 2009-07-26
Lovinglinux - that tutorial was a great help, thanks. I'm now on FF v3.5, having done some of the things suggested, and it seems quite a bit better. 

I do seem to recall that I had updated the version of FF on the last install on this machine, so we are moving more into line with how it used to be. 

(I guess all I now need to do is wait until V3.5 starts bogging down as well, as others on this thread are reporting!) 


Oli.

---

### Post by lovinglinux on 2009-07-26
> **zcacogp said:**
> Lovinglinux - that tutorial was a great help, thanks. I'm now on FF v3.5, having done some of the things suggested, and it seems quite a bit better. 

I do seem to recall that I had updated the version of FF on the last install on this machine, so we are moving more into line with how it used to be. 

(I guess all I now need to do is wait until V3.5 starts bogging down as well, as others on this thread are reporting!) 


Oli.

You are welcome.

Firefox requires some maintenance if you want to keep it running fast. The database optimization can help a lot. Also don't forget to backup your profile regularly, since it can save you a lot of trouble.

---

