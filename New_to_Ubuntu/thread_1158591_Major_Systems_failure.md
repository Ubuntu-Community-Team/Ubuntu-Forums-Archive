---
title: "Major Systems failure"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by tropdoug on 2009-05-13
There I was happily working away yesterday, when FUUT! the power went down. The electricity company decided to carry out maintenance and shut off mains power, however from the sound that came thru my speakers I reckon there was a fairly large spike. 

Problem No1 my power surge equipment did not catch it. 
Problem No 2 -- I cannot boot into my system

I have reloeaded the system entirely, as well as re written grub a couple of times, re formatted two partitons and all to no avail. 

I have even checked the BIOS setup to make sure that the Hard disk is first boot option which it is. 

I used the live CD menu to order a boot from first hard disk and this is what came up

**Error - isolinux diskerror.01, AX=0201, Drive 80**

I have no idea what that means other than guessing my BIOS has been trashed. 

Anyone got any ideas, or know how to fix it. 

Thanks

Douglas

---

### Post by whoop on 2009-05-13
It might be that the error message is totally useless because the biggest bet is you hardware is borked somewhere. Most likely BIOS or firmware.

[http://ubuntuforums.org/showthread.php?t=627443](http://ubuntuforums.org/showthread.php?t=627443)
[https://answers.launchpad.net/ubuntu/+question/17924](https://answers.launchpad.net/ubuntu/+question/17924)

---

### Post by lisati on 2009-05-13
It *is* possible that one of  BIOS has been scrambled just enough to make it difficult to read from disks. Does your system's BIOS have a "reset to default settings" option?

---

### Post by NHArticleTen on 2009-05-13
what happens when you disconnect your hard drive(s) and boot up clean using the Live CD?

---

### Post by NHArticleTen on 2009-05-13
I don't think your BIOS is damaged.  I'm more inclined to think it might be hard drive damage resulting from your power anomaly.  Remember, out of all your hardware components your hard drive is the most fragile.

Let's see how your system runs just using the Live CD.  Are you able to totally wipe the primary(master) hard drive with DBAN?  If DBAN doesn't work then you might try KillDisk.

Also, does your BIOS have MBR over-write protection?  Or it might call it BIOS level anti-virus or something like that.  It's possible that even though you feel you've totally reformatted the drive, the MBR may not be rewritten properly(or at all)...that's why I like DBAN, it zeros out even the MBR.

You can also work with your MBR using MBRTool if you feel comfortable doing so(usual backup warnings apply here).

Links:

[http://www.dban.org/](http://www.dban.org/)

[http://www.killdisk.com/](http://www.killdisk.com/)

[http://www.diydatarecovery.nl/mbrtool.htm](http://www.diydatarecovery.nl/mbrtool.htm)

Here is where having a spare hard drive around, or even a semi-retired machine, comes in handy when you need to experiment or learn about a new tool without sacrificing your primary unit.

Good luck and keep us posted on your progress!

---

### Post by tropdoug on 2009-05-14
Thanks for all the suggestions. I thought that the DBAN route sounded the best option and went down that one. Totally wiped both my harddisks. 

This morning installed 8.10 - al went well, and then I went to reboot. system went through it's checks finding the drives etc. then it stops at 

[B]verifying DMI pool data ............ 

Boot from CD

[/B]The CMOS is set to Hard drive first then CDROM. so whatever the DMI pool data is, seems to be where the issue lies. 

I am currenlty working off the live cd, there is no problem with this, which makes me think that if I can fix the boot problem there will not be a problem.

After posting this I am about to shut down, disconnect both drives and try to boot off the cd. I will add an edit to this when I have the result.

**UPDATE & SOLVED**

OK it appears that the DMI is "desktop management Interface" and for those who would like to know > DMI or DesktopManagement Interface is a layer of abstraction between system components and the software that manages them. The System Management BIOS (SMBIOS) is an extension of the Basic Input Output System (BIOS) that formulates and delivers this information to the operating system. The pool data is the information. In short, when the BIOS is "Verifying DMI pool data" it is verifying the table of data it sends to the 
operating system (Windows, etc.). If it isn't sucessful, it should return an error.

So the DMI pool data is the last thing the BIOS checks before accessing the MBR, and if there is an issue, it simply stops, or skips over the MBR and therefore goes to the next boot option being in my case the CDROM..

During all this I also noticed a one line flash past that stated "checking RAID configuration" Hmmmm weird I thought, because back in the dim dark days when I used the dinosaur program, Windoze the machine had been set up in a RAID config. But when I went to LINUX it was inactive (or so I thought) 

I went into BIOS, re set to the defaults, re booted  - same issue. I then tried again, but this time searched for anything to do with RAID and disabled all of it. -- rebooted and bingo here we are a working system again. 

So thats the fix for me anyway. maybe it can help others, and obviously even a small spike can scramble parts of the BIOS without harming anything else. SO I will now move up to a full UPS I think because my computer is my business, and my business is my income, and my income is life choices, and I love having life choices. 

Thank you to all for your assistance. 

I have a question -- is there any benefit in having RAID working in linux, and if so how do I set it up - I have two drives each 80gb

---

