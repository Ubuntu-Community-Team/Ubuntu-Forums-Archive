---
title: "GRUB error 21 after Jaunty install"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Jacdeb6009 on 2009-05-02
Hi there, I have a most annoying problems after installing Jaunty.

Previously I was running Hardy and XP from my notebook's internal drive and Intrepid from an external USB drive.

With this I could boot Hardy or XP when the external drive was disconnected and Intrepid with the external drive connected (although Hardy and XP appeared on the GRUB boot menu of the external drive, I could never get these to boot with the external drive connected).

This afternoon I deleted Intrepid, re-partitioned the external drive and installed Jaunty.  Jaunty boots perfectly with the external drive connected (Hardy and XP still won't).  However on disconnecting the external drive and trying to boot Hardy (my working system) I get a GRUB error 21.  The only way to boot the machine now is either with a LiveCD or by connecting the external drive and running Jaunty.

This is a problem as Hardy is what I use for work and it has all the relevant package installed and set up.  Jaunty was supposed to be a test system until I am sure that everything works and then I would move it over to the internal drive.

While I can access the internal drive (/home is in a separate partition) I cannot get it to boot.  I have tried using the SuperGRUB Live CD, but I am not able to figure out how to get my old set up back. 

I suspect that somehow the original MBR has been overwritten... How do I get it back??

I really need to have Hardy working again.  Any advice would be appreciated.

Thanks!!

---

### Post by caljohnsmith on 2009-05-02
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by 123456789123456789123456 on 2009-05-02
you could try super grub disk, to repair GRUB.  How ever the problem you listed may have something to do with hardware issues.  For instance, if for some reason, in BIOS you have it set to boot from external/removable media, and GRUB was written to the external drive.  It would not necessarily read the internal disk.  Check BIOS settings, make sure that boot from that device is like third option or something, any way, make sure internal disk is set to boot from before any others, except maybe cd drive.

But I suspect you are correct, I think that 9.04 may have overwritten the GRUB stage 1 in the internal disks MBR.  I believe that running the commands from the super grub disk, should create a new one, identifying the OS's on the disk, and fix the listings.
If the GRUB is working properly, if you have it set to boot from internal drive, GRUB should list the external drive OS also, and you should be able to choose which partition you want to start from.

---

### Post by Jacdeb6009 on 2009-05-03
Hi there guys,

Thanks, actually I managed to solve the problem some hours after posting the original, but since my internet connection in the hotel "crapped out" I couldn't post it.

The solution is relatively simple.  In the installation process I missed the option where you can select the location for the boot loader to be installed (silly me).  The default is to install it on drive 0.  This was OK, except that with the external hard drive removed, the boot loader is pointed to a device that does not exist... error 21...

Solution was simple.  Boot a LiveCD (with the external drive disconnected), fire up terminal and run GRUB.

Change the grub root back to the original device (in my case hd0,5) , setup grub root again on hd0 and that's it.

Re-boot and all is well...

Silly mistake, simple fix (took a bit of looking though...)

Thanks again,

---

### Post by trinidadflores on 2009-05-04
> **Jacdeb6009 said:**
> Hi there guys,

Thanks, actually I managed to solve the problem some hours after posting the original, but since my internet connection in the hotel "crapped out" I couldn't post it.

The solution is relatively simple.  In the installation process I missed the option where you can select the location for the boot loader to be installed (silly me).  The default is to install it on drive 0.  This was OK, except that with the external hard drive removed, the boot loader is pointed to a device that does not exist... error 21...

Solution was simple.  Boot a LiveCD (with the external drive disconnected), fire up terminal and run GRUB.

Change the grub root back to the original device (in my case hd0,5) , setup grub root again on hd0 and that's it.

Re-boot and all is well...

Silly mistake, simple fix (took a bit of looking though...)

Thanks again,

I had the same problem on my computer before and here was the fix that i used.  Same as your but with the actaul code.

 Re: Installing Grub from LiveCD after some MBR problems.. help
There's no need to re-install, all you need to do is boot your Live CD and open a GRUB shell and re-install GRUB to the MBR in the USB drive.
Probably something like:
```
sudo grub
```



```
find /boot/grub/stage1
```



(you use the answer you get from the above command for the input in the next command)

```
root (hd1,0)
```


Where: the results of the second command indicate that (hd1,0) is the correct disk and partition where /boot/grub/stage1 was found.

```
setup (hd1,0)
```

```
setup (hd1)
```

```
quit
```

---

