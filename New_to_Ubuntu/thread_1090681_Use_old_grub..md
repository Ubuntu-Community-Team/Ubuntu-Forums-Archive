---
title: "Use old grub."
date: 2009-03-08
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-03-08
I have just installed a second version of Ubuntu on my system. Iknow have a triple boot with Linpus linux, Ubuntu & another Ubuntu. My original grub for the first & main Ubuntu is on sda3, the new grubfor my second version of Ubuntu is on sda5 how do I return to using the grub from sda3 ??

---

### Post by kansasnoob on 2009-03-08
> **celticbhoy said:**
> I have just installed a second version of Ubuntu on my system. Iknow have a triple boot with Linpus linux, Ubuntu & another Ubuntu. My original grub for the first & main Ubuntu is on sda3, the new grubfor my second version of Ubuntu is on sda5 how do I return to using the grub from sda3 ??

Well in GRUB numbering begins with 0 (zero), so sda3 = (hd0,2). That is Hard drive #1, partition #3.

So you would have to boot any Ubuntu Live CD (choose run without changes at boot), then go to terminal and run the command:

```
sudo grub
```

Which will drop you into a grub prompt like this:

>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 


then run the command:

```
root (hd0,2)
```

then run the command:

```
setup (hd0)
```

then finally run the command:

```
quit
```

Then restart and remove the Live CD.

You should know that you will then have to manually "add" any "new" operating systems to the menu list in that original GRUB!

---

### Post by celticbhoy on 2009-03-08
cheers mate will give it a try

---

### Post by celticbhoy on 2009-03-08
Worked a treat.

---

