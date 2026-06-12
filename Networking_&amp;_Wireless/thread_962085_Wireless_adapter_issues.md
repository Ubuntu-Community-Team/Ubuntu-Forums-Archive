---
title: "Wireless adapter issues"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by Craige4107 on 2008-10-28
I recently installed 8.04 on a Toshiba Satellite Laptop. I am dual booting with Vista 32. I have an AMD Turion 64 processor. My wireless network card is a Realtek RTL8187B. Ubuntu hardwires without issue. My NIC is a Realtek as well. When I check in the Network Manager, no wireless network is detected. When I try to install manually, I get a beep when I try to enter the ESSID, and it will not accept any keyboard strokes. The information regarding wireless networking is daunting. I have tried a few commands, usually met with, "Command not found". I am not a programmer, but I am far from a novice either. Networking is my weak point however. My question, what is the "typically" issue with wireless networks when Ubuntu is installed initially. Any help would be much appreciated.

1shw -C network
1spci
ndiswrapper -1

Just some of the commands that came back with "Command not found".

1wlist scan: Unable to scan, if I remember correctly

Thanks again.

---

### Post by Nallison on 2008-10-28
Check out Johnny Cuervo's blog ... if you are 8.04 he's got the solution [http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/](http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/) 

however, I have been playing with 8.10 and the 2.6.27 kernel has support for the RTL8187B out of the box .... it has been a little flaky for me.

---

### Post by Craige4107 on 2008-10-28
Thanks Nallison.

I've just recently installed 8.04.  Since it doesn't support my wireless card, would it make more sense to just intall 8.10 before I get very far with Linux?  If so, will Killbox take care of uninstalling 8.04?  Thanks again.

---

### Post by Nallison on 2008-10-28
I don't know much about killbox, sorry.  However, I ran 8.04 for 6 months using Johnny Cuervo's driver patch and had absolutely no issues.  Make sure you read all the read.me(s). 

I am having some funky problems with the out of the box support for the RTL8187B.  I upgraded to the current release candidate two days ago, and sometimes my NIC just drops its ip config for no good reason.   I have been scrubbing the logs and spinning through the forums trying to figure this one out.  

Personally, I would go with the patch in the short term and then keep an eye out for 8.10 in the next few weeks.  The official release date is 10/30.

---

### Post by Craige4107 on 2008-10-31
> **Nallison said:**
> I don't know much about killbox, sorry.  However, I ran 8.04 for 6 months using Johnny Cuervo's driver patch and had absolutely no issues.  Make sure you read all the read.me(s). 

I am having some funky problems with the out of the box support for the RTL8187B.  I upgraded to the current release candidate two days ago, and sometimes my NIC just drops its ip config for no good reason.   I have been scrubbing the logs and spinning through the forums trying to figure this one out.  

Personally, I would go with the patch in the short term and then keep an eye out for 8.10 in the next few weeks.  The official release date is 10/30.


Wish I would've took your advice Nallison.  I tried upgrading to 8.10, three times now, I might add.  Nothing but serious issues.  At this point 8.04 is hung at boot up because 8.10 would not finish.  Looks like I'll be dumping it again and trying Open Suse.  I don't want to give up on Linux yet, but this is ridiculous.  Cheers.

---

### Post by knix on 2008-10-31
If what you show in your post is what you ran, you probably have a keymap problem.
Apparently, "i"s an "l"s are showing up as "1"s.
Unless you possibly misread someone's directions
or that's not what you really ran.

good luck.

---

