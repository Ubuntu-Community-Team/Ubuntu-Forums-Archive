---
title: "Live USB won't boot - 11.04"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by B. Suttree on 2011-06-29
I'm trying to make a Live USB so I can install 11.04. Everything seems to go okay - I get no error messages. But I can't get the computer to boot from the USB. I've tried it in 2 different machines, both running 10.04. (I've changed the BIOS settings so that the machine should boot from the USB.) I've also checked the downloaded file with mdsum, reformatted the USB (in fat), and used both Startup Disk Creator and Unetbootin. It could be the USB, I guess, but I used it to install 10.04 last weekend. Any advice?

---

### Post by dFlyer on 2011-06-29
Are you getting any errors message at all?

---

### Post by B. Suttree on 2011-06-29
No - nary a one.

---

### Post by dFlyer on 2011-06-29
Here is another links with same problem

[http://ubuntuforums.org/showthread.php?t=1760931](http://ubuntuforums.org/showthread.php?t=1760931)

[http://www.thinkdigit.com/forum/open-source/140181-ubuntu-11-04-not-booting-live-usb-hp-laptop.html](http://www.thinkdigit.com/forum/open-source/140181-ubuntu-11-04-not-booting-live-usb-hp-laptop.html)

---

### Post by westie457 on 2011-06-29
> **B. Suttree said:**
> I'm trying to make a Live USB so I can install 11.04. Everything seems to go okay - I get no error messages. But I can't get the computer to boot from the USB. I've tried it in 2 different machines, both running 10.04. (I've changed the BIOS settings so that the machine should boot from the USB.) I've also checked the downloaded file with mdsum, reformatted the USB (in fat), and used both Startup Disk Creator and Unetbootin. It could be the USB, I guess, but I used it to install 10.04 last weekend. Any advice?

Hi while creating with 'Startup Disc Creator' after you have chosen the .ISO and selected which USB drive to install to then clicked on 'Make Startup Disk'. Do you get any prompts to enter your password?

---

### Post by B. Suttree on 2011-06-29
Yes - it asks for the password twice in short succession.

---

### Post by B. Suttree on 2011-06-29
I've just tried it with a different USB drive, and I get the same results. I'd be so grateful for any advice.

---

### Post by cbowman57 on 2011-06-29
You probably need to delete & recreate the partition table.

I'm guessing that you select USB from the bios startup menu and it flies straight to the HDD without even displaying anything from the USB?

---

### Post by B. Suttree on 2011-06-29
That's right - it goes straight to the HDD. Could you say more about the problem with the partition table? (Thanks for your help.)

---

### Post by cbowman57 on 2011-06-30
> **B. Suttree said:**
> That's right - it goes straight to the HDD. Could you say more about the problem with the partition table? (Thanks for your help.)

My next guess is that you normally use the USB flash drives with Windows, for some reason they write a partition table that causes a problem.  If you don't already have GParted installed you need to do that, if it's already installed, open it up and select your USB device, then in the menu under Device, you can create a partition table.  It should reset things and allow you to reformat and then your flash drive should be detected when you burn the iso to it.

Sometimes a picture helps so here you go.  

[ATTACH]196363[/ATTACH]

Let us know if you're successful.

---

### Post by amjjawad on 2011-06-30
I would double check the BIOS settings before anything else.

After that, make sure you're creating a "bootable" USB.

---

### Post by B. Suttree on 2011-06-30
> My next guess is that you normally use the USB flash drives with Windows, for some reason they write a partition table that causes a problem. If you don't already have GParted installed you need to do that, if it's already installed, open it up and select your USB device, then in the menu under Device, you can create a partition table. It should reset things and allow you to reformat and then your flash drive should be detected when you burn the iso to it.

I do have GParted installed, so I used it to create the new partition table. No dice - it still goes straight to the HDD.

> I would double check the BIOS settings before anything else.

After that, make sure you're creating a "bootable" USB.

The BIOS is definitely set to boot from the USB. (It identifies it as "Removable Dev.") 

I've tried both UNetboot[/QUOTE]in and Startup Disk Creator. Is there any way to use those without creating a bootable USB? If so, I could be overlooking something.

---

### Post by cbowman57 on 2011-06-30
> **B. Suttree said:**
> 
I've tried both UNetbootin and Startup Disk Creator. Is there any way to use those without creating a bootable USB? If so, I could be overlooking something.

Not that I know of. Hopefully someone can come up with the answer.

---

### Post by B. Suttree on 2011-06-30
Thanks for your help, cbowman.

---

### Post by amjjawad on 2011-06-30
> **B. Suttree said:**
> I do have GParted installed, so I used it to create the new partition table. No dice - it still goes straight to the HDD.



The BIOS is definitely set to boot from the USB. (It identifies it as "Removable Dev.") 

I've tried both UNetboot in and Startup Disk Creator. Is there any way to use those without creating a bootable USB? If so, I could be overlooking something.


Perhaps you are wrong. This is how some BIOS detect USB: [http://ubuntuforums.org/album.php?albumid=2145&pictureid=7191](http://ubuntuforums.org/album.php?albumid=2145&pictureid=7191)

---

### Post by B. Suttree on 2011-06-30
> [QUOTE]Perhaps you are wrong. This is how some BIOS detect USB: [http://ubuntuforums.org/album.php?al...pictureid=7191]("http://ubuntuforums.org/album.php?al...pictureid=7191")[/QUOTE]

You're right! The "Boot Device Priority" screen only listed a "Removable Device," but another menu on the BIOS's Boot menu, "Hard Disk Drives," listed my HDD and an option for "USB." So I made the USB the primary HDD, went back to the Boot Device Priority menu, and the USB was listed as an option. I guess it considered it to be the HDD. I set it as the first boot option, and it worked! Thanks for your help, amjjawad.

---

### Post by amjjawad on 2011-06-30
> **B. Suttree said:**
> You're right! The "Boot Device Priority" screen only listed a "Removable Device," but another menu on the BIOS's Boot menu, "Hard Disk Drives," listed my HDD and an option for "USB." So I made the USB the primary HDD, went back to the Boot Device Priority menu, and the USB was listed as an option. I guess it considered it to be the HDD. I set it as the first boot option, and it worked! Thanks for your help, amjjawad.

At your service ;)

Enjoy and have fun!

Edit: Was about to ask you to mark this thread as SOLVED if you don't have any other question but you beat me to it :)

---

### Post by cbowman57 on 2011-06-30
Glad to know you guys got it figured out. :)

---

