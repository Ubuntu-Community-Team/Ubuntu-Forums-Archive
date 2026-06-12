---
title: "Borked UNR installation; now stuck"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by northerndoctor on 2009-08-26
OK, I've got myself in a right pickle with this lot. :oops: Obviously, I am a newbie.
 
I've got a new Asus Eee PC 1005ha and I was hoping to run Windows XP/Netbook Remix on it as a dual boot. 
 
Initially, I ran UNR 9.04 off a USB stick and it seemed OK (ish) - bit hinky but I ploughed on and used the option in Ubuntu to install it to the hard drive. It created a separate 4gb partition to do it as part of the process. It then wouldn't boot without the USB stick in which all seemed wrong. I then, belatedly, checked the Md5sum and it was borked. Doh! So I had installed a corrupt copy of UNR. I used wubi through all this.
 
I'm struggling to retrieve the situation. Is my best bet to simply start again with the Asus - reinstall Windows XP and try again? I will have to go out and buy an external optical drive... but it's possibly a case of 'when in a hole: stop digging'. 
 
I have downloaded another copy of UNR and the md5sum checks out. From Windows I uninstalled Ubuntu (possibly an error) but now when I opt for Netbook Remix at the boot up I get:
>  
"Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll"

 
Windows boots up fine but I'm totally unable to get Ubuntu up and running. I suspect it must be possible to tidy up the 4gb partition and install UNR without recourse to a total stripdown of the Asus but despite trawling the forums I could do with a steer in the right direction. Cheers.

---

### Post by nothingspecial on 2009-08-26
I would make the 4gb partition about 10gig or more and install ubuntu on that from a usb stick using [[COLOR="Magenta"]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/")

---

### Post by northerndoctor on 2009-08-26
Ta very much. Will try immediately - I had totally forgotten I used unetbootin the first time I created a bootable USB stick. Will try that route again.

---

### Post by northerndoctor on 2009-08-26
Ok - tried that but no joy. Made bootable USB stick using unetbootin. Click on Netbook remix option at boot up and immediately get exactly same message as above with the missing file. Crikey.

---

### Post by nothingspecial on 2009-08-26
Are you still using wubi (with which I have zero experience) or did you install ubuntu to your hard drive - the resized 4 now 10 gig partition?

I will also admit I have no experience with windows but I do dual boot.

---

### Post by northerndoctor on 2009-08-26
Initially no joy and I think there was a problem with a file that disappeared from the boot helper when I uninstalled Ubuntu. I just managed to get wubi to function again by using unetbootin to get 9.04 on USB again. It has re-installed the CD boot helper again. It has just booted up 9.04 (not netbook remix) off the USB stick.
 
Phew! I seem to be off and running again. Thanks very much for the pointers - you folks offering your help are legends.

---

### Post by nothingspecial on 2009-08-26
From what I have read (and by no means take this as anything more than uninformed opinion), it seems that for all it`s qualities, wubi is a poor choice if you wish to get the most from ubuntu.

I would again recommend installing it to your hard drive as a dual boot system.

I don`t mind being corrected :)

---

### Post by stooshbunutu on 2009-11-03
> **nothingspecial said:**
> From what I have read (and by no means take this as anything more than uninformed opinion), it seems that for all it`s qualities, wubi is a poor choice if you wish to get the most from ubuntu.

I would again recommend installing it to your hard drive as a dual boot system.

I don`t mind being corrected :)

Far from correcting I'll agree with you.

The Wubi installer seems to be a very nice way to introduce change-o-phobes of computer noobs to Ubuntu without damaging their precious "safe" Windo$e installation. However, dual-booting is so easy for anyone with braincells and a vague understanding of what a partition is, then this should definitely be it's only real application.

---

