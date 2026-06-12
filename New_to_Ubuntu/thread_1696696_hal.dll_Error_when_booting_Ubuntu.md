---
title: "hal.dll Error when booting Ubuntu"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Indev on 2011-02-27
Hey Everyone,

Pretty new to Ubuntu so bear with me. I was working in my Windows (XP) and was 'cleaning' stuff out. Later, when I tried accessing Ubuntu I was receiving an error saying that the hal.dll file was missing or corrupt. The odd part is that I can still boot to Windows, which I'm using now. I looked in my system32 folder and found that my hal.dll file is there. I restored Windows to see if that would work but nothing. Help?

---

### Post by Habeouscorpus on 2011-02-27
If every thing still works, don't play with it. I learned my lesson a while ago. (Sounds horrible, but it's true.)

---

### Post by Hedgehog1 on 2011-02-27
The Hardware Abstraction Layer (hal.dll) is missing on the Ubuntu side?

Sounds like you are (or were) running WINE on the Ubuntu side of the PC, and you were a little too aggressive with your Ubuntu side of the cleanup.

Reinstall the PC applications in WINE (or properly removing WINE if you are not using it anymore), that should do it.

:KS

***H.A.L. 9000: :I'm sorry Dave, I can't do that..."***

---

### Post by Indev on 2011-02-27
> **Hedgehog1 said:**
> The Hardware Abstraction Layer (hal.dll) is missing on the Ubuntu side?

Sounds like you are (or were) running WINE on the Ubuntu side of the PC, and you were a little too aggressive with your Ubuntu side of the cleanup.

Reinstall the PC applications in WINE (or properly removing WINE if you are not using it anymore), that should do it.

:KS

***H.A.L. 9000: :I'm sorry Dave, I can't do that..."***

I wasn't using WINE in Ubuntu. I was just deleting old files from Windows (that's what I meant by 'cleaning.') Anything I could do?

---

### Post by Hedgehog1 on 2011-02-27
Please help me understand. Your post said:

> **Indev said:**
> 
*when I tried accessing **Ubuntu** I was receiving an error saying that the hal.dll file was missing or corrupt*

Is the missing hal.dll message happening when you are running XP? Or when you are running Ubuntu?

---

### Post by TechWiz2100 on 2011-02-27
Ubuntu doesn't use .dll files afaik so it has to be something else... besides I dun think HAL is a boot requirement for anything. I could be wrong though

---

### Post by Indev on 2011-02-27
> **Hedgehog1 said:**
> Please help me understand. Your post said:



Is the missing hal.dll message happening when you are running XP? Or when you are running Ubuntu?

The error message occurs when I start my computer, I select Ubuntu from the, I'm guessing windows bootloader. When I select XP it runs just fine.

---

### Post by Hedgehog1 on 2011-02-27
> **Indev said:**
> The error message occurs when I start my computer, I select Ubuntu from the, I'm guessing windows bootloader. When I select XP it runs just fine.

OK - so it is happening on the Ubuntu side.

If you were using windows dll's stored on the Windows partition, but ***calling them ***from the Ubuntu side, and then removed them on the Windows side doing clean up; you would get an error on the Ubuntu side.

You would not see the error on the XP side, it wasn't using them any more.  But something in Ubuntu is (or is trying to).  Either you were using windows drivers in Ubuntu, or you were using them in WINE.

Do you have WINE installed? if so, I would look there first.  If you don't have WINE installed, then I suspect it is a driver that has (now) stopped working.

---

### Post by wep940 on 2011-02-27
I think it's far more likely the user has a WUBI install - and hence a .dll file.

---

### Post by psusi on 2011-02-27
Ubuntu does not know or care about hal.dll.  Can you be more specific about the exact message you get, and when?  Unless you are booting windows, there should be no mention of this file.

---

### Post by Rubi1200 on 2011-02-28
Hi Indev,
you need to confirm for us whether this is a Wubi install.

There are rare cases when a Wubi install complains about missing hal.dll on the Ubuntu side rather than the Windows install. This can happen sometimes if you installed Wubi to a drive other than C.

You also need to tell us which version of Wubi you are running.

The other thing to check is whether you have the wubildr and wubildr.mbr files at the root of the C drive. If not, copying them over to the C drive should make the error go away.

---

### Post by Indev on 2011-02-28
> **psusi said:**
> Ubuntu does not know or care about hal.dll.  Can you be more specific about the exact message you get, and when?  Unless you are booting windows, there should be no mention of this file.

This is the message I get:

"Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file."

I wasn't using WINE so I guess the driver part could be the issue. I had used WUBI to install Ubuntu before but that was like month ago. I used WUBI for Ubuntu 10.4 and I have the partition in another drive (Windows in my default C: and put Ubuntu in D:). With what Rubi1200 is saying this may be the problem. 

I was thinking, when I select Ubuntu I'm not using GRUB but, what I think is, Windows own dualboot system thing (not really sure what to call it). Perhaps when Windows is trying to run Ubuntu it tries to use the hal.dll file but since Ubuntu does not care for it then the error can occur.

---

### Post by vivek.pandey on 2011-02-28
check out these links
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
[http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm](http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm)
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

---

### Post by Rubi1200 on 2011-02-28
@Indev: did you check for the files I asked about on the C drive?

@neo_aryan: I appreciate that you want to help, but the OP has a Wubi install. This is a specific, and, as I said before, uncommon problem that sometimes happens with Wubi installs on the Ubuntu side NOT the Windows side.

---

### Post by psusi on 2011-02-28
> **Indev said:**
> 
"Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file."


That is definitely Windows trying to boot, not Ubuntu.

---

### Post by TechWiz2100 on 2011-02-28
> **psusi said:**
> That is definitely Windows trying to boot, not Ubuntu.

I'm not too familiar with Wubi installs but is there any chance that Wubi tosses some windows files into Ubuntu to facilitate booting ubuntu from BCD or that other bootloader XP used?

---

### Post by Indev on 2011-02-28
> **Rubi1200 said:**
> @Indev: did you check for the files I asked about on the C drive?

@neo_aryan: I appreciate that you want to help, but the OP has a Wubi install. This is a specific, and, as I said before, uncommon problem that sometimes happens with Wubi installs on the Ubuntu side NOT the Windows side.

The two files you asked about are not in the C: drive. They are only in my D: drive (the one Ubuntu is in). Where exactly do you want me to copy the files to?

P.S. Thanks to everyone giving input.

---

### Post by bcbc on 2011-02-28
Rubi1200 is right. If you deleted C:\wubildr.mbr then you'll get that hal.dll error. Copy it and wubildr from D:\ubuntu\winboot\ to C:\

---

### Post by psusi on 2011-02-28
> **bcbc said:**
> Rubi1200 is right. If you deleted C:\wubildr.mbr then you'll get that hal.dll error. Copy it and wubildr from D:\ubuntu\winboot\ to C:\

One would think that if wubildr.mbr is missing, then that it what it would say is missing, not hal.dll, but I suppose this is Microsoft we're talking about here.

---

### Post by Indev on 2011-02-28
Alright. Copied the wubilbr files over to my C:\ drive and Ubuntu worked! Was able to go straight the Ubuntu no prob. THANKS EVERYONE!

---

### Post by Rubi1200 on 2011-02-28
Excellent! And, you are more than welcome for the help :-) Thanks, too, to bcbc for the input about this little known Wubi issue.

Please mark this thread Solved using the Thread Tools near the top of the page.

Thanks.

---

### Post by reefis on 2011-03-03
had this exact same problem last night, except i didn't have the message at first. after installing a new update which was  a "new install", every time I booted and picked ubuntu (using Wubi) it automatically rebooted without any message. I ****** around with something in system settings pressing F2, something called OS install mode i think which reduced something to 256 mb. it loaded and so i decided to delete wubildr.mbr and THEN I got the hal.dll message. Something was messed up before and you might encounter a similiar problem in the future as I've always had boot problems using wubi. Think i'm going to reformat and get rid of windows alltogether. my windows doesn't even boot.

---

### Post by wep940 on 2011-03-06
I know this thread is now marked as solved, but for others who may read this in the future, see this guide for Wubi.  Part way down it talks about the hal.dll error.
 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

