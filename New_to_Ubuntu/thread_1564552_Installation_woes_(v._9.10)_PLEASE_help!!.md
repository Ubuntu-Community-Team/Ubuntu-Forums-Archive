---
title: "Installation woes (v. 9.10) PLEASE help!!"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Spottydog on 2010-08-30
Hi All: 
 
I posted here about my problems when I upgraded to Ubuntu v.10.04.  I am running a Dell Inspiron 6000 and have had great success with it for the past year or so, running Ubuntu version 8.4 I believe it was.  I went through some upgrades all the way up to 9.4 with no problems.  Last week I ok'd it to upgrade to v. 10 and my screen faded away to a white fog.  After several attempts to fix it, and having success running both 10.04 and 9.10 from a usb stick with no real screen problems, I decided to do a complete re-install of 9.10 from the usb stick.  It all seemed to go really well - I followed all the prompts and it all looked very promising.  When it came to the fnal part where it advised to remove the usb stick and restart, that's when I got the following message on my screen (after the re-start):
[FONT=Arial][/FONT] 
[FONT=Arial]Error: No such device fa-bffo-4053-ae99-8ac4c0bedf70.  Press any key to continue.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]It also advises that  it has loaded (or is loading, I can't remember as I'm not in front of the Dell at the moment, but at work) [/FONT][FONT=Arial]gnu grub versions 1.9,[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Does any of this mean anything to anyone?  Can it have anything to do with the fact that my hard drive is large (360 gig) ?  I seem to recall, from the foggy recesses of my tired brain, that I had to do some special partitioning iof the great big hdd when I first tried to install ubuntu, but the thing is, when I followed along with the prompts during the installation, it seemed to know what it was doing.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Can anyone suggest anything (I have tried to install this now about 3 times).  I am desperate to get it up and running again.  I can live with teh fact that I've lost everything on the hdd, but I can't live with the thought of using Microslop again :([/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]So, if you can help - I'd be MOST grateful![/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Thanks.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]SpottyDog[/FONT]

---

### Post by Windows Nerd on 2010-08-30
> **Spottydog said:**
> Hi All: 
 
I posted here about my problems when I upgraded to Ubuntu v.10.04.  I am running a Dell Inspiron 6000 and have had great success with it for the past year or so, running Ubuntu version 8.4 I believe it was.  I went through some upgrades all the way up to 9.4 with no problems.  Last week I ok'd it to upgrade to v. 10 and my screen faded away to a white fog.  After several attempts to fix it, and having success running both 10.04 and 9.10 from a usb stick with no real screen problems, I decided to do a complete re-install of 9.10 from the usb stick.  It all seemed to go really well - I followed all the prompts and it all looked very promising.  When it came to the fnal part where it advised to remove the usb stick and restart, that's when I got the following message on my screen (after the re-start):
[FONT=Arial][/FONT] 
[FONT=Arial]Error: No such device fa-bffo-4053-ae99-8ac4c0bedf70.  Press any key to continue.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]It also advises that  it has loaded (or is loading, I can't remember as I'm not in front of the Dell at the moment, but at work) [/FONT][FONT=Arial]gnu grub versions 1.9,[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Does any of this mean anything to anyone?  Can it have anything to do with the fact that my hard drive is large (360 gig) ?  I seem to recall, from the foggy recesses of my tired brain, that I had to do some special partitioning iof the great big hdd when I first tried to install ubuntu, but the thing is, when I followed along with the prompts during the installation, it seemed to know what it was doing.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Can anyone suggest anything (I have tried to install this now about 3 times).  I am desperate to get it up and running again.  I can live with teh fact that I've lost everything on the hdd, but I can't live with the thought of using Microslop again :([/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]So, if you can help - I'd be MOST grateful![/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Thanks.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]SpottyDog[/FONT]
Haha, *Microslop*, that's a good one.

Why are you trying to reinstall 9.10 when the latest version is 10.4? You know 10.4 works with your hardware, due to it working on the LiveUSB.

That error seems like it is complaining that it cannot find a hard drive (the number looks like a UUID, or Universally Unique Identifier of a hard drive).

It looks like a Grub 2 error. Ugh. *Edit:*I just saw that you mentioned that is specifies Grub 1.9 is loading. Can you actually get to the GRUB screen and boot Ubuntu or not?

Can you post the output of:
```
fdisk -l
```

When you installed the partitions, did you manually select partitions, or did you hit guided? 

Scott

---

### Post by Spottydog on 2010-08-30
hi there Nerd - thanks for the assistance.  

Firstly, i was trying to install 9.10, because when I tried both versions (9.10 and 10.4) from a USB stick, 10.4 did not recognize my modem "stick", whereas 9.10 did.  So that's what persuaded me to try and install the earlier version.

When I installed it, i just followed the suggestions - one of which (I believe) was to install on the whole hard drive (as opposed to leaving the non-functioning 10.4 on the drive).  I don't recall being prompted about much else.

I entered GNU grub just now.  Its listing:
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, linux 2.6.31-14-generic (recovery mode)
Memory Test (memtest86+)
Memorty Test (memtest 86+, SERIAL CONSOLE 115200)

i tried to run fdisk -1 from the c prompt, and the message I got was

GNU Grub version 1.98~beta4
(Minial bash-like line editing is supported. for the first word, TAB lists possible command ............. etc.
sh:grub> fdisk -1
error" unknown command 'fdisk'


Does any of this mean anything to anyone???

Thanks!
SD

---

### Post by Windows Nerd on 2010-08-31
> **Spottydog said:**
> hi there Nerd - thanks for the assistance.  

Firstly, i was trying to install 9.10, because when I tried both versions (9.10 and 10.4) from a USB stick, 10.4 did not recognize my modem "stick", whereas 9.10 did.  So that's what persuaded me to try and install the earlier version.

When I installed it, i just followed the suggestions - one of which (I believe) was to install on the whole hard drive (as opposed to leaving the non-functioning 10.4 on the drive).  I don't recall being prompted about much else.

I entered GNU grub just now.  Its listing:
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, linux 2.6.31-14-generic (recovery mode)
Memory Test (memtest86+)
Memorty Test (memtest 86+, SERIAL CONSOLE 115200)

i tried to run fdisk -1 from the c prompt, and the message I got was

GNU Grub version 1.98~beta4
(Minial bash-like line editing is supported. for the first word, TAB lists possible command ............. etc.
sh:grub> fdisk -1
error" unknown command 'fdisk'


Does any of this mean anything to anyone???

Thanks!
SD

So when you get to the listing at the GRUB menu, can you boot into the first option/line? (Press enter when GRUB loads).

If you can boot no problem, I wanted you to enter the command from a shell.

If GRUB cannot boot, boot a LiveCD/USB and then enter the command from there.

Scott

---

### Post by QIII on 2010-08-31
Spotty --

That's 

fdisk -l

(small "ell", not the numeral 1).

Give that a whirl.

---

### Post by Windows Nerd on 2010-08-31
> **QIII said:**
> Spotty --

That's 

fdisk -l

(small "ell", not the numeral 1).

Give that a whirl.

Thanks for pointing out that you can run that from a GRUB prompt, totally forgot...

---

