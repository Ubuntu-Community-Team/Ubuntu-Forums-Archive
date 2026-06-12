---
title: "No system boot"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by expatCM on 2009-02-06
What I see today is a white underscore in the top left of the screen and nothing else.

If I boot the system from a CD I can mount / browse all the hard drives and open files on each.

I have reset the bios but this had no effect.  All devices appear to be correctly identified in the bios.

The system was working last night.  There are no beeps or error messages. 

How do I work out what is wrong here?   

If I were to run fsck from the CD, what is the syntax so that it checks all mounted volumes?  I can see that fsck -a  will automatically fix errors but will running from the CD not get in the way here?

The system is Ubuntu 8.10, fully updated.  Quite a fresh install, the system is used to play movies only and so very little beyond the default programs have been installed.  5 SATA hdd's, a SATA DVD.

---

### Post by Voland on 2009-02-06
Can you boot in rescue mode?

---

### Post by expatCM on 2009-02-06
Don't think so .........

I power on ....

I see the bios output.

The next thing I see is the white underscore .......

It sounds a bit like the primary hard drive is the problem but I can browse the volume without issue from the CD.  

I have the system set to auto login though so would I do not normally see the grub options.  I can edit to stop the auto login, do you happen to know what to change?

---

### Post by Voland on 2009-02-06
Boot from livecd, mount partition containing /boot and edit string starting with timeout	in /boot/grub/menu.lst

---

### Post by expatCM on 2009-02-06
I just changed the timeout to 30 and also commented out the hidden menu setting.

No change on reboot though.

The white underscore appears immediately after post has completed, it does not appear that grub is being accessed ......  (I have checked the bios hard drive boot order just to make sure that the right drive is selected).

---

### Post by caljohnsmith on 2009-02-06
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by newbee70 on 2009-02-06
> **expatCM said:**
> Don't think so .........

I power on ....

I see the bios output.

The next thing I see is the white underscore .......

It sounds a bit like the primary hard drive is the problem but I can browse the volume without issue from the CD.  

I have the system set to auto login though so would I do not normally see the grub options.  I can edit to stop the auto login, do you happen to know what to change?

Have you got a copy of the Ultimate Boot Disk so you can test your system?

if not here is the location.


[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

hope this helps you out.

---

### Post by hyper_ch on 2009-02-06
while in the live cd, open a terminal and run the following command post the output here:

```

sudo fdisk -l

```

---

### Post by longtom on 2009-02-06
> **newbee70 said:**
> Have you got a copy of the Ultimate Boot Disk so you can test your system?

if not here is the location.


[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

hope this helps you out.

Great link!  Thank you - was always on the lookout for something like that.

longtom

---

### Post by expatCM on 2009-02-06
Thanks for all the suggestions .......  I will follow through with these a bit later (time short now).

I think this could be the motherboard though .......  I just put a new hard drive in and did a fresh install ........   no issues or problems until I restart from the hard drive and then exactly the same thing happens.  

Since this is a new drive I know it is not likely to be the drive so that leaves the power supply and the motherboard.  

I will disconnect most of the hard drives later and test.  That should eliminate (or confirm) the power supply as the cause.  I will also test booting from another SATA port .........

---

### Post by expatCM on 2009-02-07
I have taken a different track today.  This has to be a fundamental hardware problem, most probably with the motherboard.

What I have done is to remove all drives (hard drives and DVD) leaving just one drive.  That drive has Ubuntu on it but it has not been run with this system.  I have tried this drive in two separate SATA ports.

I have also removed the CMOS battery and reset the jumper to clear the settings.  I have changed the SATA cable.  I have changed the memory.

After all of that the same problem appears.

So unless the PSU is doing something very cute this has to be a problem with the motherboard, the SATA interface at a guess.  That the Ubuntu Live CD will run on the system suggests that the PSU is probably fine.

To rma the motherboard appears to be the next step.

---

### Post by expatCM on 2009-02-07
caljohnsmith -- I just ran the script on my main machine to take a look at the output.  This appears to be a very comprehensive utility in collecting boot related information.  A very nice find :)

If more people know about this it will save a lot of frustration ...  it is a very easy way to get information together.

---

