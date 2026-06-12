---
title: "How do I get past Windows to load Ubuntu?"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by maxwinter2001 on 2010-01-12
Hi:
   
  (Please bear with me through the first 2 paragraphs.  I will get to my Ubuntu question.)
   
  My laptop recently caught the Rogue Internet Security 2010 malware bug.   While trying to get rid of it I rebooted a couple of times.  The second time I could not log in.   The bug had taken away my ability to do so.  I have no money and could not take the machine to be wiped and the software (Windows 2000 Professional, Office 2003), so I decided to wipe the drive myself by installing a Windows XP disc I had.  ¾ of the way through it got to the product key question, and for some reason insists that the key I have is invalid, (maybe because it’s been used before on another computer?  I don’t know).  
   
  Since, as mentioned above, I am broke, I got to looking up free OS’s and ran across Ubuntu.  It sounded ideal so I downloaded it on a friend’s computer, copied it to a disc, and inserted the disc into my laptop.  Even though my laptop is set to boot from the CD drive first, (I have verified and reinforced this twice), every time I turn it on the part of Windows XP that got loaded takes over and takes me to the product key box.  
   
  My question:  How do I stop Windows from taking over and get Ubuntu to load?

---

### Post by SteveHillier on 2010-01-12
It would strike me, particularly as you use the phrase copied Ubuntu to CD, that you have not made your CD bootable.

You should have downloaded the .iso file from the website.
Then you need to burn that .iso image to the CD using the 'burn image to CD' option in your CD software.  I know how to do this is Nero but other s/ware will have similar functions.

Once you have got a bootable CD then make sure that your BIOS setup searches for boot records from CD before HDD.  How you do this will vary depending on which BIOS your machine is running.

Post back with more information if you need more help.

---

### Post by 73ckn797 on 2010-01-12
Sounds like you do not have a bootable LiveCD as mentioned already. If you need to burn an iso image and do not have Nero you can check out "CDBurnerXP", a free program, which should allow you to burn the downloaded iso file to make the bootable LiveCD. This is assuming you have access to a Windows computer.

---

### Post by fcrowder on 2010-01-12
also if you have a newer computer you should be able to press f12 perhaps a diff. F key to go to a drive boot screen which will ask you what drive you want to boot from. "Pressing ESC key while the bios splash screen will allow you to see the Bios booting"
you should be able to sel. CD drive and then it will ether boot or give you a OS message saying not bootable insert bootable cd. which means that the cd was not setup correctly. I have also had good luck with calling the number they tell you to call to activate the windows and tell them that this is a new computer and that your old one died and they will give you a new key, maybe....

---

### Post by maxwinter2001 on 2010-01-12
Thank you for the suggestion.  However, when I go to [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) to download Ubuntu it does not give me a choice of types of downloads.  It just has the one "Download now" button.  So how do I find this "iso" file to download?

Also, when I did download it and copy it to CD I DID choose the "burn files" option.  I am using, on my friend's computer, Windows 7 - are you familiar with it?.  As soon as you point to D: drive with a blank CD in it the system asks "How do you want to use this disc?"  The options given are: (1) "Like a USB flash drive:  Save, edit and delete files on the disc anytime."  and (2) "With a CD/DVD player: Burn files in groups and individual files can't be edited or removed after burning."  As I said, I chose option 2.

---

### Post by pathfindermwd on 2010-01-12
You may have already been to this page:  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  this will tell you how to create your live cd.  There is also a free cd burning software there just in case yours doesn't burn an iso file.

Make sure that you can boot it from your friends computer before taking it home.

Ubuntu is great, you won't be disappointed, but there will be some learning involved.  Start here to begin learning:  [https://help.ubuntu.com/9.10/](https://help.ubuntu.com/9.10/)

---

### Post by maxwinter2001 on 2010-01-12
Okay, I see a couple more folks have joined the discussion while I was writing my reply to the first person.  No, I don't have Nero, (never heard of it), and as mentioned in my original post, the laptop with the problem HAS been set to boot from the CD drive first.  However, now that I know about this "iso" version deal I guess that's why it hasn't been working.  So, once again, how do I get the "iso" file?

---

### Post by raymondh on 2010-01-12
> **maxwinter2001 said:**
> Thank you for the suggestion.  However, when I go to [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) to download Ubuntu it does not give me a choice of types of downloads.  It just has the one "Download now" button.  So how do I find this "iso" file to download?

[COLOR="Navy"]That will link you to the 'iso' file.[/COLOR]



[COLOR="Navy"]Raymond[/COLOR]

---

### Post by maxwinter2001 on 2010-01-12
Okay, thanks to all.  I will try the sites pathfindermwd mentioned and see if I can do it right this time.  Once again, thank you all for your input.

---

### Post by SteveHillier on 2010-01-12
> **maxwinter2001 said:**
> I DID choose the "burn files" option. 

This is not the same as burning an **_image_** to CD.

Check the file you downloaded.  Was the file extension .iso.  It probably was.

---

### Post by admiralspark on 2010-01-12
Now Windows with a virus is something I have too much experience with ;-). That's one reason why I use linux.

Well, here's a few things to consider:
1)<SHOULD BE FREE, BUT TIME CONSUMING> Windows...unlike many people here, I don't hate it myself. However, their customer support is notorious for causing undue stress and generally being a major waste of your time. You can try calling them or, if you find that you like Ubuntu (many more like it than don't) keep linux. It's free, it does everything (but problem-free gaming) that windows does, and it'll be faster.

Note: do they still deal with XP keys since even Vista's a part of the past?

2) <FREE> Another option is to get/create a BartPE disk. According to their site [here]("http://www.nu2.nu/pebuilder/"), you must use a Windows XP disk with at least SP1 (you either already have that or you need to slipstream a copy). This CD will allow you to boot from the CD drive into a broken windows install, then use anti-virus/anti-malware to take care of your problems. It's a lifesaver. Unfortunately, it sounds like you've wiped the system already, and if so:

3) <FREE> Burn another copy of Ubuntu to a CD, either with the Nero trial (which for me never expired, weird though that is), CDBurnerXP, or ISOBurn. Burn on the _SLOWEST_ setting, usually something like 10x but varying wildly depending on the CD drive. My first Ubuntu CD was created with CDBurnerXP, though it took a few tries since I forgot to slow it down. 

When you go to boot, usually hitting ESC, F12 or another key will allow you to access your BIOS's boot menu, which lists the few ways you can boot. Select the CD drive, and try with the Ubuntu CD. Even if it was a bad burn, it will still boot to the Ubuntu LiveCD menu (and freeze). 

Let us know how it's progressing, and good luck!

---

### Post by maxwinter2001 on 2010-01-12
*Originally Posted by SteveHillier* 				
*Check the file you downloaded.  Was the file extension .iso.  It probably was.*

I checked and you're right, it does appear to be an .iso file.  But what I copied to disc must not be.

---

### Post by pathfindermwd on 2010-01-12
> **maxwinter2001 said:**
> Okay, thanks to all.  I will try the sites pathfindermwd mentioned and see if I can do it right this time.  Once again, thank you all for your input.


Also, if your computer can boot from usb and you have a 2 gig USB thumbdrive, I would really recommend the USB persistent version.  It's much faster than CD, and it can save data too.

Read up on it at this link:  [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by 73ckn797 on 2010-01-12
> **maxwinter2001 said:**
> *Originally Posted by SteveHillier*                 
*Check the file you downloaded.  Was the file extension .iso.  It probably was.*

I checked and you're right, it does appear to be an .iso file.  But what I copied to disc must not be.

If you copied what you downloaded then that was all that you did. The downloads from Ubuntu are all iso files. "ISO" files require a different way to burn to disk to work as the Ubuntu LiveCD does. Just making a copy is no different that copying any other data.

The CDBurnerXP I mentioned should burn the iso properly so that you will have a bootable disk from the iso file.

---

### Post by maxwinter2001 on 2010-01-12
Pathfinder:  Thanks again.  It's installing now.  (And no, my old laptop won't boot from a USB port, although it has two).

73ckn797:  Yeah, I got that.  Fortunately my friend's computer (with Windows 7) DID have an option for Burning disc image, which is why it's now loading.  

Thanks again to all.

---

### Post by 73ckn797 on 2010-01-12
> **maxwinter2001 said:**
> Pathfinder:  Thanks again.  It's installing now.  (And no, my old laptop won't boot from a USB port, although it has two).

73ckn797:  Yeah, I got that.  Fortunately my friend's computer (with Windows 7) DID have an option for Burning disc image, which is why it's now loading.  

Thanks again to all.

Let us know how things work out.

---

### Post by pathfindermwd on 2010-01-12
> **maxwinter2001 said:**
> Pathfinder:  Thanks again.  It's installing now.  (And no, my old laptop won't boot from a USB port, although it has two).

73ckn797:  Yeah, I got that.  Fortunately my friend's computer (with Windows 7) DID have an option for Burning disc image, which is why it's now loading.  

Thanks again to all.
No, problem, Hope everything goes smoothly.  If so, Enjoy!

---

### Post by ssulaco on 2010-01-12
> **maxwinter2001 said:**
> 
 I have no money and could not take the machine to be wiped and the software (Windows 2000 Professional, Office 2003), so I decided to wipe the drive myself by installing a Windows XP disc I had.  ¾ of the way through it got to the product key question, and for some reason insists that the key I have is invalid, (maybe because it’s been used before on another computer?  I don’t know).  
maxwinter,welcome to the world of Ubuntu,yes.....no product keys to worry about...ever,have fun with your free OS
Ubuntu is one of many flavors of Linux,you picked the best one IMO

---

### Post by 73ckn797 on 2010-01-12
> **ssulaco said:**
> Ubuntu is one of many flavors of Linux,you picked the best one IMO

I tried many different Linux distros but Ubuntu was the easiest to "load and go", "out of the box" experiences I had/have.

---

### Post by SteveHillier on 2010-01-13
Glad we were able to help you through so that you can join the enlightened world of Linux users.
Not always easy but always rewarding.

---

### Post by fcrowder on 2010-01-16
now it's up to him to get everything working.. sometimes a bit hard.. but as stated.. it's worth it.

---

