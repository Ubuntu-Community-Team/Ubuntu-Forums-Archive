---
title: "Ubuntu Maverick. CD-DVD drive not recognized at all"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by odraude123 on 2010-11-09
I recently installed maverick meerkat and my cd dvd drive is not recognized by ubuntu or the computer. I am not allowed to boot from cd drive, its not even an option. i dont know what to do.

---

### Post by SuaSwe on 2010-11-09
Can you see the drive in the BIOS/when selecting boot options? If not (and correct me if I'm wrong, everyone!), the issue isn't with Maverick as the BIOS is not dependent on the installed OS.

---

### Post by odraude123 on 2010-11-13
No I cant see it, how can I make it appear

---

### Post by chamira on 2010-11-15
The CD drive may have been disconnected? Did you open up your PC for any reason during the upgrade? Does it power up at all - can you open/close the drive?

If the CD drive is attached and powered up correctly you should be able to see in the BIOS. If it is in the BIOS and you can't see it within Ubuntu then it may a driver issue.

---

### Post by odraude123 on 2010-11-16
No i did not open the computer, the drive opens and closes, im not sure how to see my bios though......  all i know is my cd drive is named atapi. anothrer thing. when i put the cd in and then try to boot off of it it doesnt appear as an option. because i had to install ubuntu through junk drive instead of cd.

---

### Post by odraude123 on 2010-11-18
here is what i get for 
$ sudo lshw -C disk                in case it helps
      

*-disk                  
                 description: ATA Disk
                 product: WDC WD1200BEVS-6
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXC208D12427
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000ee933

---

### Post by mastablasta on 2010-11-18
this is your hard disk.
 
i think ATAPI is driver for CD/DVD drive. i could be wrong...
 
when you turn on your computer there is some message on the screen. it is usually fast (dissapears fast) and it says how to enter bios or settings. different motherbaords (computers) have different way to access BIOS (it's the thing that control the devices on computer).
 
usually it's F3, F12 or delete key, but i've seen soem other combinations as well.
 
once you access the BIOS screen, you will see there which devices are on your computer. carefull with any changes in settings as you can destroy the hardware. just have a look and save withouth doing any change.
 
anyway you will see there if your drive is recognised. if not, but the drive works, it might be that the drive hasa faulty data cable.

---

### Post by chamira on 2010-11-18
During bootup, press Escape and enter the BIOS. 

Navigate to the 'Boot Configuration' setting and select 'CD-Rom' as the first choice and 'Hard-drive' as the next choce.

Next, navigate to the 'Hard-drives' tab and you can select the order in which the BIOS will look look for an OS - useful if you have multiple hard-drives with various versions of Ubuntu or Windoows.

Save & Exit.

You should be able to boot from CD-Rom after that.

---

### Post by odraude123 on 2010-11-21
See the problem is I can't read cds, is there a driver I can try to download that might work.

---

### Post by coffeecat on 2010-11-21
> **odraude123 said:**
> See the problem is I can't read cds, is there a driver I can try to download that might work.

People have been asking you if you can see the CD drive in the BIOS. You haven't said whether you can or not. There is no point looking for a driver if the BIOS does not recognise the CD drive. If the BIOS can't see the CD drive no operating system ever will. Have you looked in the BIOS?

---

### Post by joshuamrobertson on 2011-02-05
I find that i'm having a very similar problem but i do see my drive in the bios so i know thats not the issue

---

