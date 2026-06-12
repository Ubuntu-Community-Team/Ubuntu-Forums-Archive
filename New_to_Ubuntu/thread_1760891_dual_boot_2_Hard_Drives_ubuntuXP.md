---
title: "dual boot 2 Hard Drives ubuntu/XP"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Godeszila on 2011-05-17
Hi,
thanks in advance for the help, and please give me all instructions in your best "for dummy's":redface: version.

I  have 2 SATA hard drives.  Drive 0 has Windows XP, and is labeled Drive  H: (I have no Idea why:confused:, but I understand that now I cannot change it to  C)

Drive 1 has Ubuntu.

Both Drives/OSs boot if I go into the bios  and indicate which drive I wish to use. I don't want to use the bios.  How can I make this a dual boot system?

I found the boot options  in windows and got the boot screen to give me a choice between XP and  Ubuntu, but when I select Ubuntu it boots XP anyway:mad:.

This is what my boot.ini currently looks like-
< 

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(1)disk(1)rdisk(1)partition(1)\root="Ubuntu" /noexecute=optin /fastdetect 
  
>

I did a lot of web research and then tried my best #-o .... I didn't find much on dual boot using two drives.

thanks again for the help.

---

### Post by josh11 on 2011-05-17
Well..

I had Windows XP on my PC.

I then downloaded Ubuntu from the site: [http://www.ubuntu.com](http://www.ubuntu.com)

I burnt it to a disc

I then put it in my machine

It then detected windows XP and asked me if I wanted to overwrite it or install alongside it.

Choose alongside and there you have a dual boot system. When you restart you should get a screen asking what OS you would like to use once you have installed Ubuntu (or counterpart).

Need any more help? thanks.

---

### Post by Godeszila on 2011-05-17
yes, I need more help, I want my ubuntu on a seprate hard dirve from windows, not on the same hard drive. thanks.

---

### Post by josh11 on 2011-05-17
Ah. I don't see the problem :o

Two separate hard drives?

---

### Post by Godeszila on 2011-05-17
yes, two small hard drives... not enough room for both os's on one drive

---

### Post by josh11 on 2011-05-17
So it's like you installed both but one is corrupted because the small size?

---

### Post by Godeszila on 2011-05-17
i took out my windows harddrive, and put a diffrent harddrive into the pc, I then installed linux. then I put my hard drive with windows back into my pc on sata0 and put my hard drive with linux into the sata1.

---

### Post by Godeszila on 2011-05-17
> **Godeszila said:**
> 
I  have 2 SATA hard drives.  Drive 0 has Windows XP, and is labeled Drive  H: (I have no Idea why:confused:, but I understand that now I cannot change it to  C)

Drive 1 has Ubuntu.

[COLOR=Red]Both Drives/OSs boot if I go into the bios  and indicate which drive I wish to use. I don't want to use the bios.  How can I make this a dual boot system[/COLOR]?

I found the boot options  in windows and got the boot screen to give me a choice between XP and  Ubuntu, but when I select Ubuntu it boots XP anyway:mad:.

This is what my boot.ini currently looks like-
< 

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(1)disk(1)rdisk(1)partition(1)\root="Ubuntu" /noexecute=optin /fastdetect 
  
>

I want to not have to use the bios

---

### Post by josh11 on 2011-05-17
I think I get you now.. you have 2 hard drives.. 

One with XP

One with a variant of Linux

You want to know how to switch between the two on start up?

---

### Post by Godeszila on 2011-05-17
yes, thats it. Do you know how?

---

### Post by noidian on 2011-05-17
Hi,

you might want to check out this thread
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)


Kalyana SV

---

### Post by josh11 on 2011-05-17
I am afraid ATM I do not..

My Uncle is a PC technician, he will know, so I will ask him later when he returns from work and post the response.

BTW, what size of HD do you have?

---

### Post by Godeszila on 2011-05-17
> **noidian said:**
> Hi,

you might want to check out this thread
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)


Kalyana SV


Thank you soooo much, It worked!

---

### Post by Godeszila on 2011-05-17
> **josh11 said:**
> I am afraid ATM I do not..

My Uncle is a PC technician, he will know, so I will ask him later when he returns from work and post the response.

BTW, what size of HD do you have?
  
Thank you josh for trying to help, but I have found my answer. :KS

---

### Post by josh11 on 2011-05-17
No problem :D

What size of HD you have? Like 4 GB or sth?

---

### Post by noidian on 2011-05-17
Your welcome..Have fun.

---

