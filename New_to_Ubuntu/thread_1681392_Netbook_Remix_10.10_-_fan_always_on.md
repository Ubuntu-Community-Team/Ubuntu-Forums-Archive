---
title: "Netbook Remix 10.10 - fan always on"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by castalla on 2011-02-04
I installed Remix on a Packard Bell Dot-s.  I notice the fan is always running - fast at first then slower later.

I know there are fan problems with some netbooks - I have searched for some consistent advice on how to fix this, but without luck.

Given Remix is designed to be user-friendly, can someone suggest a relatively straight-forward procedure to fix this problem?

---

### Post by 3rdalbum on 2011-02-04
The fan should always be running; the Atom CPU puts out too much heat to cool passively inside a netbook chassis.

Fan control is handled by your computer's BIOS based on thermal sensors and CPU load; you could try making sure that your BIOS is up-to-date.

If you feel like the fan speed is excessive, check whether there is a "runaway" process that is keeping your CPU at 100%; if there is, then kill it.

---

### Post by castalla on 2011-02-04
Thanks.

Strange it seems to switch off and run appropriately in windows.

How would I check for a 'runaway'process as opposed to a normal process?

---

### Post by 3rdalbum on 2011-02-05
> **castalla said:**
> Thanks.

Strange it seems to switch off and run appropriately in windows.

How would I check for a 'runaway'process as opposed to a normal process?

Oh; when I say a runaway process, I might one that is using 100% CPU for no valid reason. You can look in System > Administration > System Monitor to see if your CPU is being used 100% and what might be pushing it that far. On an Atom CPU it will show 2 CPUs, you just have to look for at least one at 100%.

---

