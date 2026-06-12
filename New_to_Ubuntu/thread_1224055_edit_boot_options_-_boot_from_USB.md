---
title: "edit boot options - boot from USB"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by sb56473 on 2009-07-26
I got Ubuntu 9.04 to boot from USB.  This is the best and easiest of all Linux flavors I have tried.  Kudos to Ubuntu.  Now for my question.  
I ran the "USB Startup Disk Creator" from Ubuntu 9.04.  It works great on my Vista machine.  But I want to edit the boot options.  I want to add the NOSWAP argument.
All the other threads say to edit the menu.lst in /boot/grub.  But there is no grub directory under /boot.  I've tried checking in terminal using sudo, and it's just not there.
I can't access the /root folder because I lack permissions.
I know that NOSWAP might make Ubuntu run slower, but I'm willing to take that risk.  I see a line about boot options at the Run Persistent/Install/ etc prompt, but can't see where it comes from.
So, how do I add a NOSWAP boot option when running 9.04 from USB?

---

### Post by ecmatter on 2009-07-27
I don't know how the bootable usb drives are set up, but you might take a look at fdisk to see if you have a linux swap partition:

```

fdisk -l

```A swap partition (if you have one) should be clearly marked.

If you don't have a swap partition listed, that doesn't mean that you're not using swap.  You could be using a swap file instead.

```

cat /proc/swaps

```will list all swap partitions and swap files

If you have any, you can disable them all with:

```

swapoff -a

```check the man page for swap off for more details

```

man swapoff

```And [THIS LINK]("https://help.ubuntu.com/community/SwapFaq") for further reading on swapon/swapoff.

---

### Post by sb56473 on 2009-07-27
Thanks for your quick and thorough response.  Maybe I'm on the wrong track here . . .
My concern is swapping with the hard drive of the machine, not space on the USB drive.  I was told that the O/S (in this case, Ubuntu) running on the USB would use free space on the Hard Disk (in my case, Vista) for swap.
If, however, Ubuntu running from the USB (not installed on the hard disk) won't use the hard disk for swap, then I don't need to change the boot options I have now.
Can you verify that it will or won't use the hard disk for swap?  Thanks again for any guidance you can give me.

---

### Post by Mighty_Joe on 2009-07-28
> **sb56473 said:**
>  I was told that the O/S (in this case, Ubuntu) running on the USB would use free space on the Hard Disk (in my case, Vista) for swap.


Find whoever told you this and hit them with a stick.  Ubuntu only uses dedicated swap partitions or files.  It will not use a non-Linux partition.  
[c.f. SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by sb56473 on 2009-07-28
Thanks, Joe, I'll hit him with a memory stick !

---

