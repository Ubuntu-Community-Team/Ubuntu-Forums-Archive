---
title: "Power Matters"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by windfarm on 2009-06-03
Hi all,
When I shut down Ubuntu (9.04) my PC does not switch off and the hibernate function doesn't work either. Would this be related to the message that flashes up at start-up that says the BIOS date (1997) is earlier than the cut-off (2000) so ACPI will not work?

If that's the case I don't understand why Ubuntu thinks my BIOS date is 1997, because the BIOS info that appears right after I press the power-on button seems to say that the BIOS dates from Dec 13, 2001.

All suggestions welcome.

---

### Post by porchrat on 2009-06-03
> **windfarm said:**
> Hi all,
When I shut down Ubuntu (9.04) my PC does not switch off and the hibernate function doesn't work either. Would this be related to the message that flashes up at start-up that says the BIOS date (1997) is earlier than the cut-off (2000) so ACPI will not work?

If that's the case I don't understand why Ubuntu thinks my BIOS date is 1997, because the BIOS info that appears right after I press the power-on button seems to say that the BIOS dates from Dec 13, 2001.

All suggestions welcome.

Flash the BIOS with a newer version, normally solves my ACPI problems. There isn't really any other way to solve it.

---

### Post by windfarm on 2009-06-03
I did look for a BIOS update, but that's another problem. My motherboard is a Matsonic MS8308D/E and I looked on their website, but they don't seem to be in the motherboard business anymore. I looked on a few other sites but couldn't find anything that had a BIOS for this board.

---

### Post by porchrat on 2009-06-04
> **windfarm said:**
> I did look for a BIOS update, but that's another problem. My motherboard is a Matsonic MS8308D/E and I looked on their website, but they don't seem to be in the motherboard business anymore. I looked on a few other sites but couldn't find anything that had a BIOS for this board.

I looked around and I see what you mean there is nothing out there for that motherboard. I do see though that there was definitely a BIOS released for that board that grants ACPI support.

Honestly I have never encountered a situation where a motherboard manufacturer no longer exists and there is no one hosting the BIOS. Perhaps post on forums asking if anyone has a copy of a newer BIOS that they would be prepared to send to you.

Problem with that is that you may be dealing with someone that doesn't really know what they are talking about and next thing you know you force the flashing of a new BIOS that isn't intended for your motherboard and end up bricking the machine.

My advice to you is just to live with ACPI issues it isn't worth the risk.

EDIT: I have just realised that I didn't really answer your first questions. Yes, the no ACPI issue is the reason that your machine doesn't turn off and doesn't hibernate. Both of those are ACPI functions.

You can stop some of the error messages from coming up at least. If you edit the /boot/grub/menu.lst file and add "noacpi" to the end of the line containing your kernel information it should stop some errors from being displayed. It won't solve the problem though.

To do that first make a backup in case you break something:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then edit the file:
```
gksudo gedit /boot/grub/menu.lst
```

When the file comes up in the text editor navigate to the line with your linux kernel information on it (this line should end with the words "quiet splash") and add the word "noacpi" to the end of that line and save and exit. That will let Ubuntu know that it shouldn't bother looking for ACPI and should stop the error messages.

BTW if you do break something then you can boot into Ubuntu with the liveCD and then reload the backup copy backby typing:
```
sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

Has this machine ever run Windows and if so did ACPI function correctly under Windows? If so this BIOS could just be badly designed with regard to the Linux-specific DSDT tables, which again is something that you can't solve without a BIOS update, but then at least you know that you have an ACPI-supporting BIOS version and that there is even less hope :( .

---

### Post by windfarm on 2009-06-06
Thanks for the advice, I will look some more for a BIOS update on other forums. But I still don't understand why the O/S thinks the BIOS is pre-2000, when it displays the date 13/12/2001 and this is supported by the motherboard's User's Manual which is also dated 2001. I purchased it in March 2002.

I converted the machine from Windows XP about 2 months ago, so I'm very new to Ubuntu. All the power features worked fine under Windows

There is something else that comes at the end of the ACPI error message - something about ACPI = force required ..... Does this mean I can force it to turn on ACPI? How would I do that and is it safe to do so?

Thanks again.

---

### Post by plucky on 2009-06-06
> **windfarm said:**
> Thanks for the advice, I will look some more for a BIOS update on other forums. But I still don't understand why the O/S thinks the BIOS is pre-2000, when it displays the date 13/12/2001 and this is supported by the motherboard's User's Manual which is also dated 2001. I purchased it in March 2002.

I converted the machine from Windows XP about 2 months ago, so I'm very new to Ubuntu. All the power features worked fine under Windows

There is something else that comes at the end of the ACPI error message - something about ACPI = force required ..... Does this mean I can force it to turn on ACPI? How would I do that and is it safe to do so?

Thanks again.

Do as porchrat said and edit your menu.lst file and in the kernel line add acpi=force so it looks like ```
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro [color=blue]acpi=force[/color] splash quiet
initrd		/boot/initrd.img-2.6.24-24-generic
quiet
```

and then you might have to update initramfs with ```
sudo update-initramfs -u -k all
``` to stop the acpi/bios error message.

Good Luck

---

### Post by windfarm on 2009-07-19
> **plucky said:**
> Do as porchrat said and edit your menu.lst file and in the kernel line add acpi=force so it looks like ```
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro [COLOR=blue]acpi=force[/COLOR] splash quiet
initrd        /boot/initrd.img-2.6.24-24-generic
quiet
```and then you might have to update initramfs with ```
sudo update-initramfs -u -k all
``` to stop the acpi/bios error message.

Good Luck

I only just got around to trying the acpi=force suggestion, but pleased to say that it worked; the machine now switches itself off at shut down. Thanks for the help.

The only thing that confused me slightly was that the menu.lst file has five kernel lines under different titles as follows:
title        Ubuntu 9.04, kernel 2.6.28-13-generic
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
title        Ubuntu 9.04, kernel 2.6.28-11-generic
title        Ubuntu 9.04, kernel 2.6.28-11-generic
title        Ubuntu 9.04, memtest86+

I only edited the kernel line under the first title, which worked, but should I add acpi=force to the other kernel lines as well?

---

### Post by Whiffle on 2009-07-19
Actually the proper place to put it is here, on the kopt line.  That way anytime your kernel gets upgraded, it will maintain the change.  The way you have it now you'll have to edit your menu.lst file every time the kernel gets upgraded

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=477e9a22-a94e-451d-bf4e-11cd6de39cdf ro [COLOR="Red"]acpi=force[/COLOR]

```

---

### Post by windfarm on 2009-07-21
Thanks, Whiffle. I have edited the kopt line as you suggested. All seems ok.

---

