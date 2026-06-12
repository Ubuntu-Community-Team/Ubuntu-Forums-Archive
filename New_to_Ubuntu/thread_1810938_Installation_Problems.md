---
title: "Installation Problems"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by silver52961 on 2011-07-23
I keep trying to install ubuntu onto my recently inherited netbook. it is an aspire one netbook. So I want to improve upon it by installing ubuntu.

So i tried installing Wubi, and I kept trying to install Netbook ubuntu. I kept getting an ISO error. 

So I then tried to download the iso. It worked, and I loaded it onto a virtual drive and tried installing, but that led to me sitting on the welcome screen (I didnt go through a log in screen), and my mouse was just a loading symbol so I couldnt do anything so after about 10 minutes I shut down.

I then put the ISO on a cd, and since my netbook does not have a cd drive, I had to use an external cd drive, and the computer could not boot linux from it. So then I did the option that stated that I could not boot from cd. And that just led me to the same exact problem as if I tried to boot it the iso from the virtual drive. 

And now, on startup I have 3 separate ubuntus to choose, and windows 7.

So what I was thinking, should I wipe my whole :C drive and do a clean install of ubuntu from a usb? 

Sorry if this doesnt make sense, I am just very frustrated right now.

---

### Post by e79 on 2011-07-24
Here is what I'd do; download Ubuntu live CD, make a [bootable usb]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and try the netbook (see if it can boot from it) and if so, see if everything is alright (graphic, wireless etc).

If it does work and you dont mind wiping Windows 7 do a full install choosing the option 'wipe and use the entire hard drive'.

Make sure to backup any important files to an external USB (per example) if there is anything to.

Hope this helps

---

### Post by gigenieks on 2011-07-24
Hello :)

[Click here -> Googl Ubuntu]("http://www.googlubuntu.com/") -  Ubuntu and Kubuntu search engine based on google - is your best friend now. :D

> 
to **improve** upon it by installing ubuntu

What you mean with "improve it"?

> 
it is an aspire one netbook

Hmm.. _Exactly_ which model? (there are many Aspire One netbooks as far as I know)

> 
I then **put** the ISO on a cd

With "put" you ment --> **Burned As Image?**



First we should figure out some things:

[LIST=1]
[*]Did you check [[COLOR="DarkOliveGreen"]**md5sum**[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
>  of .iso
The program md5sum is designed to verify data integrity..
In terms of integrity, an MD5 hash comparison detects changes in files that would cause errors. 

[*]I recommend to use one of the methods descriped [[COLOR="DarkSlateBlue"]**here (Burning Iso How To)**[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto")
Worked for me. :)
[*]Did you check (if could)[CD Integrity]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")?
[/LIST]

You said:
> 
So then I did the option that stated that I could not boot from cd.

I don't understand that sentence at all! Can you rephrase what happened there? ;)

> 
And now, on startup I have 3 separate ubuntus to choose, and windows 7.

:shock: [COLOR="DarkRed"]**Please post picture of that!**[/COLOR] Would help a lot to understand what have you done there.

Lastly:
> 
So what I was thinking, should I wipe my whole :C drive and do a clean install of ubuntu from a usb? 

If I were you, I would check **md5sum** of .iso you downloaded and burned in CD. Then I would check **CD Integrity** (if that is possible). If md5sum match with .iso and Ubuntu Hashes then I would burn again that iso using according method [[COLOR="Sienna"]**from here**[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto").

As for "wipe whole C:" that probably is the best thing to do ("I have 3 separate ubuntus to choose, and windows 7." :D)

If you **can't** install Ubuntu via CD. _Then_ try installing it from USB. --> [[COLOR="DarkRed"]**read this!**[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")


Some links that could be helpful for you:
[LIST]
[*][User Documentation]("https://help.ubuntu.com/community")
[*][Community Documentation - Installation]("https://help.ubuntu.com/community/Installation")
[*][Quick Guide: Installing Ubuntu from a USB memory stick]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick")
[/LIST]

Hope it help You.

---

### Post by amjjawad on 2011-07-24
> **e79 said:**
> Here is what I'd do; download Ubuntu live CD, make a [bootable usb]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and try the netbook (see if it can boot from it) and if so, see if everything is alright (graphic, wireless etc).

If it does work and you dont mind wiping Windows 7 do a full install choosing the option 'wipe and use the entire hard drive'.

Make sure to backup any important files to an external USB (per example) if there is anything to.

Hope this helps

Adding to the above:

1- I second "Backup".
2- If you want to keep Win7 which I guess it's Starter Version, then make sure to remove Wubi from Control Panel (Programs and Features).
3- Download Ubuntu - preferably 10.04.3 - from [www.ubuntu.com](www.ubuntu.com) and follow the instructions over there of HOWTO Create LiveCD/USB.
4- Please **[check md5sum]("https://help.ubuntu.com/community/UbuntuHashes")** for your downloaded iso.
5- Make sure you select the correct BOOTING DEVICE from BIOS. Note there are Booting Device and HDD Boot Priority.
6- Before you install, TRY Ubuntu from the Live Session and see if ALL your hardware work fine.
7- Sit back and Enjoy your life with Linux ;)

---

### Post by silver52961 on 2011-07-24
Ok I included the picture of the multiple ubuntu startup options.

And thank you for your input guys, I am going to boot from a USB after a backup and wipe my :C drive.

---

### Post by amjjawad on 2011-07-24
> **silver52961 said:**
> Ok I included the picture of the multiple ubuntu startup options.

And thank you for your input guys, I am going to boot from a USB after a backup and wipe my :C drive.

Good luck and let us know if you need any help :)

By the way, that's not even GRUB2. You'll see GRUB2 after you install Ubuntu. It's just a Wubi Installation.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

