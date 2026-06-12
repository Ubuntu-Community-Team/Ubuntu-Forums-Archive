---
title: "Fresh reinstall"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-08-31
Hey guys,

I'm wanting to delete Ubuntu and do a reinstall. But I was hoping I could get some help with the exact steps I need to do.

I have Ubuntu dual booted with Windows, and I use grub. I also want to make the Windows partition a few gb's bigger in this process since I made it too small when I did my first dual boot.

So how exactly would I go about this? Would I:

1: Get on Windows, fire up Partition Magic. Then use Partition Magic to format my Ubuntu partition.

2: Then use fixmbr to fix grub.

3: Then use partition magic to resize my Windows partition to make it bigger by a few gb's.

4: Then download Ubuntu, burn it to a disc, then reinstall the OS?

Does that sound about right, or am I totally wrong on this? Any help will be greatly appreciated. Thank you.

---

### Post by keplerspeed on 2009-08-31
More simply:

1) download ubuntu - burn it to disk
2) boot up into live cd, and go to system>admin>partition editor
3) resize partitions at will. GParted it an amazing and easy!
4) once your happy just install.

All done!

---

### Post by colau on 2009-08-31
> **h8uthemost said:**
> Hey guys,

I'm wanting to delete Ubuntu and do a reinstall. But I was hoping I could get some help with the exact steps I need to do.

I have Ubuntu dual booted with Windows, and I use grub. I also want to make the Windows partition a few gb's bigger in this process since I made it too small when I did my first dual boot.

So how exactly would I go about this? Would I:

1: Get on Windows, fire up Partition Magic. Then use Partition Magic to format my Ubuntu partition.

2: Then use fixmbr to fix grub.

3: Then use partition magic to resize my Windows partition to make it bigger by a few gb's.

4: Then download Ubuntu, burn it to a disc, then reinstall the OS?

Does that sound about right, or am I totally wrong on this? Any help will be greatly appreciated. Thank you.

You can also use unetbootin to install from pendrive.

---

### Post by h8uthemost on 2009-08-31
Hmmm...that does sound a lot simpler. Thank you keplerspeed.

I have a couple questions about that though.

Using Gparted from the LiveCD will let me resize my Windows partition? Or I'm guessing just by shrinking my Ubuntu partition would do it.

Also, I still have Ubuntu installed, so all I do is install Ubuntu again on my Ubuntu partition from LiveCD? Or do I format this Ubuntu partition before installing Ubuntu?

---

### Post by delukard on 2009-08-31
i'm interested in this answer also.(exept i don't want to resize)
sorry if i hijacked this tread, is just that i have the same question
:)

---

### Post by zvacet on 2009-08-31
First shrink Ubuntu partition to have space to expand your Windows partition.After giving more space to Windows during installation **format** Ubuntu partition.Then you can do fresh install on top of existing partition.

---

### Post by Niko Johnson on 2009-08-31
> **h8uthemost said:**
> Hmmm...that does sound a lot simpler. Thank you keplerspeed.

I have a couple questions about that though.

Using Gparted from the LiveCD will let me resize my Windows partition? Or I'm guessing just by shrinking my Ubuntu partition would do it.

Also, I still have Ubuntu installed, so all I do is install Ubuntu again on my Ubuntu partition from LiveCD? Or do I format this Ubuntu partition before installing Ubuntu?

 You have the right idea... you dont have to format your Ubuntu partition right now because as you already know you have the option to do so in the installation process. but when it comes to your windows partition it is safer and in my opinion more stable to do it with Ubuntu installed instead of off a live cd. you may come across problems with the live cd and when it comes to partitioning a disk we should always take possible problems into consideration, beacuse there is no back button : ).

---

### Post by h8uthemost on 2009-08-31
So Niko, do recommend resizing the Windows partition from Windows with Partition Magic?

Thank you for all the help guys.

---

### Post by Grifulkin on 2009-08-31
Instead of resizing the Windows partition, you can leave it unallocated and when you go to do partitions via live cd, you can click on manual and then use the unallocated space to do your / and swap.  The best part is you can use any filesystem you want so ext4 if you want the newest.  I changed it up and went with Reifers when I did mine today, finally got around to doing a real dual boot.  Only took me a year.

---

