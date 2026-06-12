---
title: "How do I format or use a DVD-RW?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by TruthOrDare on 2010-05-01
I want to use some DVD rewritables to back up my data for moving to Lucid but Ubuntu refuses to work with my DVD-RWs.

I'm using GnomeBaker and I just get these errors:

When trying to burn:
```
:-[ PERFORM OPC failed with SK=5h/CANNOT WRITE - APPLICATION CODE MISMATCH]: Wrong medium type
/dev/sr0: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/CANNOT WRITE - APPLICATION CODE MISMATCH]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type
```


When trying to format:
```
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
* 4.7GB DVD-RW media in Sequential mode detected.
0.0%:-[ PERFORM OPC failed with SK=5h/CANNOT WRITE - APPLICATION CODE MISMATCH]: Wrong medium type
:-[ FORMAT UNIT failed with SK=5h/CANNOT WRITE - APPLICATION CODE MISMATCH]: Wrong medium type
```


To me, these errors look like Ubuntu just doesn't support -RW. :(

Brasero won't work either, it'll burn then error at the end.

---

### Post by wilee-nilee on 2010-05-01
Can you right click on the DVD then blank disc?

---

### Post by TruthOrDare on 2010-05-01
I've tried "blanking" but that just makes the discs undetectable.

One thing I've noticed in GnomeBaker is that in the Preferences there are CD-R, CD-RW, DVD-R and DVD-RAM tick boxes for writing options but no DVD-RW.

---

### Post by robert shearer on 2010-05-01
Yeah, the Gnome disk writing apps can be troublesome at times.

Just install K3b from synaptic (it will pull in a lot of other files and libraries that allow it to work under Gnome but it will **work**)

---

### Post by wilee-nilee on 2010-05-01
I am using Lucid, so the version of gnomebaker under tools has a dvd formatter, not sure about jaunty though, should though.

---

### Post by TruthOrDare on 2010-05-01
In the menu, GnomeBaker does have a "Format DVD+-RW" option but it doesn't work it seems.

---

### Post by robert shearer on 2010-05-01
> To me, these errors look like Ubuntu just doesn't support -RW

Does your dvd-burner support -RW  ?

---

### Post by TruthOrDare on 2010-05-01
I think I found the problem, it is my writer.

I found this notice for my writer: Please Note: 4X DVD-RW media is not compatible for recording with your drive, please use 1X or 2X compatible DVD-RW media only.

I'm using 4x DVD-RW media (although I tried burning at 2x).

---

### Post by Irihapeti on 2010-05-01
I use DVD-RWs a lot. I prefer to use cdrskin (in the repos) and work from the command line. I've set up a few scripts that I can call from a menu entry. A bit clunky, but it works well. Cdrskin is the only program I've found that will burn multi-session DVD-RWs.

I believe that cdrskin can be used as the back-end to K3b instead of cdrecord, but I'm not sure how you would set that up.

I've noticed that Brasero seems to prefer DVD+RWs. If I use a DVD-RW, I get an error message, although the disk appears to have burnt OK.

---

### Post by wilee-nilee on 2010-05-01
> **Irihapeti said:**
> I use DVD-RWs a lot. I prefer to use cdrskin (in the repos) and work from the command line. I've set up a few scripts that I can call from a menu entry. A bit clunky, but it works well. Cdrskin is the only program I've found that will burn multi-session DVD-RWs.

I believe that cdrskin can be used as the back-end to K3b instead of cdrecord, but I'm not sure how you would set that up.

I've noticed that Brasero seems to prefer DVD+RWs. If I use a DVD-RW, I get an error message, although the disk appears to have burnt OK.

I always get you have to manually remove DVD message.

---

### Post by Irihapeti on 2010-05-01
> **wilee-nilee said:**
> I always get you have to manually remove DVD message.

I've been getting that, too. CDs are OK, and Brasero handled DVD+RWs fine in Hardy.

Edit: it's already been reported as a bug: 519935. I've marked myself as affected.

---

### Post by spiky001 on 2010-05-01
>  					Originally Posted by **wilee-nilee** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9208277#post9208277") 				
 				I always get you have to manually remove DVD message

here as well

---

### Post by rnerwein on 2010-05-01
hi
first question: if you are using a double layer dvd - can your drive handle this ?
if yes you can also try in a terminal run: 
[COLOR=Blue]dvd+rw-format -force[/COLOR]  /dev/dvd   ( if you have more than 1 drive you have to use /dev/sr0, /dev/sr1 ... )

good luck
ciao

---

