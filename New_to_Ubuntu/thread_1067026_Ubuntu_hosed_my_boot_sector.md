---
title: "Ubuntu hosed my boot sector"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by TomFulton53 on 2009-02-11
OK, well I have to admit the bloom is off the rose for me, Ubuntu-wise.

I have tried to install Ubuntu onto a USB thumb drive, with no luck so far.  A suggestion was made that I use the regular Install method, rather than use the 8.10 "Create a USB startup disk" item off the System Administration menu.  I was able to do that...I was careful to specify the USB drive, not my main drive.  It apparently was able to install Ubuntu onto the USB drive...but it apparently wrote something onto the boot sector of my main drive, so that it will no longer boot.  I can start Ubuntu (not from the thumb drive, **that ** part didn't work), and look at the main drive...so I can see that my data is there.  I haven't lost anything (yet), but I have to figure out if I can change the boot sector back to Windows XP.

Is there a way to do this?  I mean, I can bring the machine to a Linux shop, I suppose, to fix it...but I'd rather hear that there's a way of simply removing something that will make it bootable again.

Any suggestions?  Please?

The message I get when I attempt to boot is: "GRUB loading stage 1.5", then "GRUB loading, please wait", then "Error 21"

Thanks in advance.

---

### Post by halitech on 2009-02-11
sounds like it installed GRUB to the MBR as the default install will do unless selected otherwise. Check out SuperGrub Boot disk, it will allow you to restore your windows boot options or you can boot from your windows install cd, go to recovery mode and restore it with I believe fixmbr

---

### Post by MarblePanther on 2009-02-11
the link for supergrubdisk is in my sig.

burn it to cd and boot

---

### Post by ainsworth_t on 2009-02-11
If you have a Windows XP install CD you can try to run the recovery console from it and run the DOS command "fixmbr" to write a new master boot record. If that doesn't work, look into the "fixboot" command. 

If those options don't work, there is an XP install option called the "Repair Installation" that basically re-installs XP but keeps your data and installed applications.

Hope this helps.

---

### Post by marco123 on 2009-02-11
If you use Vista use the recovery disc/installation media that came with your PC or download recovery disc here - [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Then go to command prompt on the disc and type bootrec /fixmbr then bootrec /fixboot

The Windows bootloader is now restored.

EDIT:  Oops didn't read the OP fully: same applies for XP only use /fixmbr then /fixboot without the "bootrec"

---

### Post by TomFulton53 on 2009-02-11
Thanks everyone!  I was able to use a Windows Recovery disk to fix the MBR...although I have to say, it was rather disconcerting to see the message that said, effectively: "There is some chance that running fixmbr will totally wipe out your partition and data".  I think I'm going to try Ubuntu on a machine that I don't mind trashing, until I get more familiar with it.

Thanks again...you saved my life.

---

