---
title: "Computer will not power off and keeps re starting"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by neilms on 2010-08-02
I have just installed ubuntu on an old machine. When I try to shutdown, it will turn off and re start. I have tried shutting down at the command line using : shutdown -P now. Same problem occurs. I have managed to power it off once by going into the bios.

I have read that some people have problems with acpi and I think that this machine may need me to set acpi to off. 

Any ideas?

---

### Post by mbsullivan on 2010-08-02
> I have read that some people have problems with acpi and I think that this machine may need me to set acpi to off. 

Well, I'm not sure what the problem is. However, if you want to try turning off ACPI, I can tell you how to do that (at least under Grub, I'm not sure if it's changed recently for Grub2).

You're gonna want to add "acpi=off" to your boot list. Edit:

```
/boot/grub/menu.lst
```

As root, and find the line that starts with "# kopt=" (the default kernel options). Now add " acpi=off" to the end of that line. Save the file and run:

```
update-grub
```

From terminal. Now ACPI should be disabled from the next boot.

Mike

PS: You could also try disabling APIC, with " nolapic" at the same place. Often, the two are found in conjunction to fix issues.

---

### Post by jtarin on 2010-08-02
Try ```
shutdown -h now
```

---

