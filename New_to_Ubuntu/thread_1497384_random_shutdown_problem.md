---
title: "random shutdown problem"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by diversionist on 2010-05-30
Hi!

I have Ubuntu 10.04 running on an old Acer Aspire 5610.

Every now and then it randomly shuts down without an apparent reason. It doesn't go through the shutdown procedure, it just goes "clack" and the computer is off. I'm running the notebook with the powersupply right now, I removed the battery.

  dmesg tells me:
```
[   36.822474] ACPI: EC: GPE storm detected, transactions will use polling mode
[   44.984035] eth0: no IPv6 routers present
[  106.461091] CE: hpet increasing min_delta_ns to 15000 nsec
[  239.691804] CE: hpet increasing min_delta_ns to 22500 nsec
[  314.096068] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
[  314.096101] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.Z000] (Node f70128b8), AE_TIME
[  314.096178] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.WMBA] (Node f7012ae0), AE_TIME

```How do I fix that?

Any help would be really appreciated since I just switched to Ubuntu and I'm really happy, but this issue would be a major dealbreaker.

Thanks!
div

---

### Post by dv3500ea on 2010-05-30
I have a similar problem with my HP DV3500EA laptop and I think it is a hardware fault. It is not to do with  Ubuntu as it just turns off (as if the batery had run out). 

Lots of places suggest that this is an overheating problem and to try cleaning the laptop or using coolant. For me, I don't think it is an overheating problem as its only an issue when I am on battery power (I am thinking there is some problem with the battery).

I'm afraid I don't have a solution but I'm sure its not to do with Ubuntu as, for me, it first started when I was (on one of the rare occaisions) using Windows Vista.

---

### Post by GingerAlex on 2010-05-31
Similar problem on an Acer 5610Z - since upgrading to 10.04 from 8.04. 

I think the problem is that the upgrade installed ACPI, which I'd not used before. I got rid of the random shutdown issue by editting grub the grub menu, to add the 'acpi=off' option to all the kernel entries. (there are other threads on how to do this). 

This has however led to other problems, such as slow graphics, no Compiz, shutdowns not completing and no power management. So it's still a work in progress for me; I'm currently seeing if there is a package or setting that allows ACPI to work so I don't have to disable it completely. 

Not the greatest upgrade I've ever experienced!

---

### Post by genis200 on 2010-05-31
This happens if one of the following occurs...
Your RAM is faulty, or
Your computer is attempting to get more ram, because it is using it all on the application that you are using.
Ubuntu includes the memory test application on the GRUB menu, it'd be a good idea to run that.

---

### Post by diversionist on 2010-05-31
thanks a lot, everyone!

I read somewhere that I should check if I have the latest BIOS running - I did not, so I flashed it yesterday and no problems since! I hope it'll stay like that :)

I didn't think it was due to overheating since it doesn't shut off on XP...

@GingerAlex: if you don't have BIOS v3.50 running, you should definitely try updating!

---

### Post by GingerAlex on 2010-06-06
Hello - 

I can confirm that patching the BIOS fixed the random shutdown issue using ACPI, so I was able to get rid of the 'noacpi' options which fixed the various other issues I had.

(Ubuntu 10.04 Laptop Acer 5610Z, Bios patched to v3.50, was originally v3.24)

In summary - upgrade installed ACPI, ACPI didn't like old BIOS, not using ACPI caused all sorts of other problems, ACPI did like new BIOS so upgrading BIOS fixed it. Not a hardware issue as such because Windows was OK all this time.

Thanks for the remedy Diversionist and thanks for the suggestion genis200.

cheers,
Alex

---

