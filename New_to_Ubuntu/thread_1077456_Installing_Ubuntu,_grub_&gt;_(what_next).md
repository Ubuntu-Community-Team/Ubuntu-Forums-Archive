---
title: "Installing Ubuntu, grub &gt; (what next)"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by c.moll on 2009-02-22
Hi there,

I installed Ubuntu in Windows for CD-Rom. No problem.
On rebooting, the 'please select the operating system to start' screen appears, leaving me the option to start either Windows XP or Ubuntu.

On choosing Ubuntu, pressing 'enter', grub4dos appears.
I face the next line:

grub >

Now, what do I do next?

Thanks for any guidance,

Chris

---

### Post by spiderbatdad on 2009-02-22
not sure what you did. Where you doing a wubi install? Or where you trying to install two separate operating systems. It looks like grub is missing info on your setup.
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)
```
grub> root (hd0)
grub> setup (hd0)
grub> quit
```

It may be easier for you to try the installation again by booting from the live cd...not booting into windows, if you are interested in a dual-boot.

---

### Post by spiderbatdad on 2009-02-22
another link [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2009-02-22
Did you do a Wubi install, i.e. installing Ubuntu inside of Windows? In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by c.moll on 2009-02-22
Thanks to all for a prompt reaction.

Before taking any action, for your understanding this is what I did.

- Ubuntu 8.10 CD-Rom in the drive;
- 3 options appear;
- I opted for:'install inside windows'.

Please confirm your suggestions.

Thanks,

Chris

---

### Post by caljohnsmith on 2009-02-22
> **c.moll said:**
> 
Before taking any action, for your understanding this is what I did.

- Ubuntu 8.10 CD-Rom in the drive;
- 3 options appear;
- I opted for:'install inside windows'.

Yes, you definitely did a Wubi install then. So do you want Ubuntu installed inside Windows, or do you want Ubuntu to have its own partition? How about booting the Live CD again, but this time choose "try Ubuntu without making changes," and when you get to the Ubuntu desktop, follow the directions in my previous post to download and use the Boot Info Script. We can work from there if you want.

---

### Post by c.moll on 2009-02-22
Many thanks for this.

No, I don't want a partition.
I'll work on this and let you know.

Thanks for your guidance sofar.

Best,

Chris

---

