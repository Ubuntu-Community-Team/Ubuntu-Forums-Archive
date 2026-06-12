---
title: "will my earlier os wont work ???"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by naved ..... on 2011-04-13
i heard that after installing ubuntu u cant access to ur older operating system i.e windows 
bcoz u modifys some of the setting .....is that true ....
????help me plz

---

### Post by Hippytaff on 2011-04-13
Have you installed alongside windows or just used the whole hard drive. If you use the whole hard drive you wipe windows, if you install alongside windows you have acces to windows and ubuntu.

---

### Post by alphacrucis2 on 2011-04-13
> **naved ..... said:**
> i heard that after installing ubuntu u cant access to ur older operating system i.e windows 
bcoz u modifys some of the setting .....is that true ....
????help me plz

It depends on how you install it. You can install it completely overwriting whetever was there before, or you can install it along with windows in dual boot mode. There is even an option of installing it under windows (wubi option) but I have never tried that. To do the dual boot install you need to make sure there is a enough free space to install Ubuntu, which usually requires shrinking the existing windows ntfs partiton to free up the required space. The latop I am running at present is set up like this. On boot up I select the OS I want to load (either Windows or Ubuntu) from the GRUB boot loader menu. You can access all your windows files from ubuntu but not the other way around as windows doesn't understand the EXT4 file system that ubuntu uses by default.

---

### Post by Hippytaff on 2011-04-13
I would advise against a Wubi install :-)

---

### Post by Mark Phelps on 2011-04-13
Word of advice in advance ... if you decide to go dual-boot (with Ubuntu in its own partition) and your PC is running Vista or Win7, do NOT use the Ubuntu installer, or any Linux utility, to shrink the Windows OS partition to make room for Ubuntu.  Vista and Win7 OS partitions are especially touchy and shrinking them with Linux utilities can lead to filesystem corruption -- rendering them unbootable.

Instead, use the Windows Disk Management utility to do the shrinkage -- but leave the new unallocated space blank.

Also, if you're running Win7, use the Backup feature to create and burn a Win7 Repair CD.  That will come in very handy later should you need to repair your Win7 boot loader.

---

### Post by 3rdalbum on 2011-04-13
> **naved ..... said:**
> i heard that after installing ubuntu u cant access to ur older operating system i.e windows 
bcoz u modifys some of the setting .....is that true ....
????help me plz

Not true. If you select the "Install side-by-side" option in the installer, Ubuntu will install alongside Windows and you'll be able to choose on each bootup which OS to boot into.

However, the opposite is true: If you reinstall Windows, you'll lose access to Ubuntu, because Windows modifies the MBR to prevent the computer booting to Ubuntu's bootloader. Fixable, but not nice.

Remember to make a backup of all your important files on Windows, just in case the partitioning step goes wrong (rare, but it happens) and you'll find it quicker to defragment Windows first from within Windows. And be careful - make sure you select the "Install side-by-side" option, do NOT opt to erase the whole disk.

---

### Post by naved ..... on 2011-04-13
is ubuntu is linux os ???
 and can i unistall ubuntu any time i want ??? if yes how ?

---

### Post by sanderd17 on 2011-04-13
Ubuntu is a "flavour" of GNU/Linux. Technically it's not Linux, but ubuntu uses the Linux kernel. You can do nothing with Linux alone (without apps).

You can uninstall it, but you will have to use a windows repair disk.

I have a feeling that Mark Phelps knows more about it. I haven't used windows in a long time, so I can't really help you.

---

### Post by alphacrucis2 on 2011-04-13
> **naved ..... said:**
> is ubuntu is linux os ???
 and can i unistall ubuntu any time i want ??? if yes how ?

Ubuntu is probably the most popular distribution of linux. It is based on another distribution called Debian Linux. There are many distributions that serve different purposes. Some other popular ones are Fedora, Red Hat Enterprise Linux, CentOS, SUSE and Mandriva. The [distrowatch]("http://distrowatch.com/") website gives information about them.

 To uninstall Ubuntu after installing in dual boot mode you need to

1. Replace Ubuntu's boot loader with the Windows MBR. To do that, use  either the Windows install or recovery CD. Google restore Windows MBR for details.

2, Boot into Windows and recover the Ubuntu space by deleting the Ubuntu partitions using the Windows disk management tool. You can then expand an adjacent ntfs partition and reallocate the space freed up.

---

### Post by naved ..... on 2011-04-13
i also heard that ubuntu terminal has all programming software like c, c++,java , perl , python , asp.net , etc inbuilt ????? ..so we dont need to install extra software for the same , like in windows we have to install different software for different programming lanuguage ...i m using ubuntu (linux) just for programming bcoz i m a programmer and i need to do a lot of  programming stuff !! plz also reply 4 this pzl help !!!

---

### Post by Hippytaff on 2011-04-13
THere are lots of free programming facilities/software. the terminal is a bit like command prompt it windows, but with far far more functionality.

---

### Post by alphacrucis2 on 2011-04-13
> **naved ..... said:**
> i also heard that ubuntu terminal has all programming software like c, c++,java , perl , python , asp.net , etc inbuilt ????? ..so we dont need to install extra software for the same , like in windows we have to install different software for different programming lanuguage ...i m using ubuntu (linux) just for programming bcoz i m a programmer and i need to do a lot of  programming stuff !! plz also reply 4 this pzl help !!! 

I'm not sure that all the compilers are installed by default. You can easily install them from the repos if they aren't. You would start by installing the package build-essential which gets you the basic dev programs. You can either install stuff using the Ubuntu software centre or the Synaptic package manager. If you like terminal commands you would install the build-essential package like this:

```
sudo apt-get install build-essential
```

This will download and install the programs associated with the build-essential package

---

