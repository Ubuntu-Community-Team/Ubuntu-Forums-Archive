---
title: "Error while trying to burn Ubuntu install Cd in 10.04"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by lupulin on 2010-11-21
Hey all, having problems with my CD burner. Seems like the ubuntu install disk is bad luck for me. I bought a new computer and all I want to do is get ubuntu istalled on it. I'm trying to burn a CD and it keeps telling me "an unknown error occurred". anyone have any tips? I can paste the brasero-session.log but it's very long. Any help would be appreciated.

[edit: I also installed GnomeBaker and it gave me an error. Both programs are giving me errors regardless of what I'm trying to burn.]

---

### Post by carl4926 on 2010-11-21
You can always use patebin: [http://pastebin.com/](http://pastebin.com/)
For the error log

Assume you are burning the image? not trying to write the .iso as data, though actually you should be able to accomplish both without trouble.

Does it burn anything? You know, does it get part way and quit or does it just not get anything done?

---

### Post by beew on 2010-11-21
Forget about burning CDs and trouble shooting your burners.

If you have a usb drive laying around just make a live usb. Lots faster (both in terms of making one and actually using one) and you don't have to worry about quirks or bugs in CD burners or CD drives. 
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

Since you said it is a new computer you should have no problem booting from a usb, just make sure to set the boot piriority in the BIOS to put usb device first.

Oh, you should check that your iso is not corrupt.

---

### Post by lupulin on 2010-11-21
It does not burn anything. Works for about 30 seconds and then ejects the disk. 

Let me try that pastebin thing...

Uh, I think I missed something on paste bin. My error log should be here: [http://pastebin.com/BDpPrBQq](http://pastebin.com/BDpPrBQq)

---

### Post by carl4926 on 2010-11-22
Might be this177. BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
Can you use the USB method as suggest by @beew?

Or try a different CD. Good quality?

---

### Post by lupulin on 2010-11-22
I don't have a USB drive or any other CD's but I can probably get some. It sounds like the usb method is easier, so I'll try to get one tomorrow and just keep it around as my ubuntu install method.

---

### Post by amjjawad on 2010-11-22
The Write on CD/DVD Function in Optical Drivers has a time-frame. After few years, the drive will stop writing to CDs/DVDs and will be used as Read-Only drive. After that, it will stop completely.
I didn't study that or read it, I know this from personal experience.

However, let's assume there's nothing wrong with the write ability and it's brand new drive. You have few options:

1- Use USB instead.
2- Use K3b (you could get it from Synaptic).
3- Follow the instructions on Ubuntu's website (how to burn to CD).

---

### Post by lupulin on 2010-11-22
> **amjjawad said:**
> The Write on CD/DVD Function in Optical Drivers has a time-frame. After few years, the drive will stop writing to CDs/DVDs and will be used as Read-Only drive. After that, it will stop completely.
I didn't study that or read it, I know this from personal experience.

However, let's assume there's nothing wrong with the write ability and it's brand new drive. You have few options:

1- Use USB instead.
2- Use K3b (you could get it from Synaptic).
3- Follow the instructions on Ubuntu's website (how to burn to CD).

Ah that would probably explain it. This cd burner is from 2004 or so. Hence the new computer. 

I swear once I get the new computer running, I am going Office Space on this thing. It's given me so much trouble in the past couple of months...

---

### Post by amjjawad on 2010-11-22
> **lupulin said:**
> Ah that would probably explain it. This cd burner is from 2004 or so. Hence the new computer. 

I swear once I get the new computer running, I am going Office Space on this thing. It's given me so much trouble in the past couple of months...

My CD/DVD burner is 5 years old and I'm burning CDs/DVDs on daily basis so it started to not detecting the new/blank CDs/DVDs unless I restart (sometimes) or keep replacing blank CDs. Before, I remember one driver stopped writing completely so had to use it for read-only.
However, this might NOT be the case even though the chance is high. One way to find out is to try to use the suggested methods by me and other guys here and hope it would help.

Your new PC has an OS or not? if it has any OS, use it to burn the CD :)

---

### Post by mastablasta on 2010-11-22
> **amjjawad said:**
> The Write on CD/DVD Function in Optical Drivers has a time-frame. After few years, the drive will stop writing to CDs/DVDs and will be used as Read-Only drive. After that, it will stop completely.
I didn't study that or read it, I know this from personal experience.

 
i call BS on this as i have CD write driver since 1999 (give or take a year) and it works perfectly. as do all other drives. most of them are older than 5 years except for two  which are 1 and 3 years old.

---

### Post by amjjawad on 2010-11-22
> **mastablasta said:**
> i call BS on this as i have CD write driver since 1999 (give or take a year) and it works perfectly. as do all other drives. most of them are older than 5 years except for two  which are 1 and 3 years old.

As I explained earlier, that was from personal experience **NOT** from books, etc. That was my plain own opinion and I explained it clearly and wrote that it could **NOT** be the case, **_it's a possibility_**.

It doesn't mean I'm wrong or you're right and vice versa. As everyone knows, the same brand, same device (say Optical Drive) could work for someone but not for the other. It's common sense.

:)

---

