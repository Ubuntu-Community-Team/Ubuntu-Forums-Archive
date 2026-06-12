---
title: "How can I remotely connect to my ubuntu on windows"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by lolzwut on 2010-01-04
Hi, I just installed Ubuntu dual booted with Windows Vista via wubi-installer. It's version 9. I was wondering if it was possible to remotely connect to my linux partition from windows via PuTTy or some other remote connection software, I don't need a Graphical connection just a shell would be fine. Is it possible if it's dual-booted? Also if I need to install SSH can you tell me how? Thanks.

---

### Post by =not4prophet= on 2010-01-04
if you are dual booting your system then only one os is available at a time (whichever system you have booted).  If you are looking to gain access to the files saved on in ubuntu from windows, you will need to use a file system for which there is a windows driver, such as one of the versions of EXT.

---

### Post by lolzwut on 2010-01-04
So you're saying that I can't remotely connect to my other partition because it's off?

---

### Post by adelphos on 2010-01-04
An operating system needs to be booted in order to receive/host a remote connection. You cannot have the Ubuntu and Windows partitions booted at the same time. You can, however, mount the Ubuntu filesystem and manipulate files, as described above.

---

### Post by lolzwut on 2010-01-04
Ok, thanks for the help guys.

---

### Post by K.J. on 2010-01-04
I think there might be some miscommunication here. Do you need to actually access the operating system or just the files on the partition? Ubuntu can very easily access a Windows partition (and even write to it) provided it was unmounted cleanly.

Vice-versa is a bit more difficult. Check out [http://www.fs-driver.org/](http://www.fs-driver.org/) for accessing your Ubuntu drive in Windows. Although, I highly recommend using a shared FAT32 partition (as long as most of your files are under 4 GB a piece).

---

### Post by lolzwut on 2010-01-04
I want to access the OS. But not graphically just command line. I don't want to access the files. If you're familiar with the program "PuTTy" you'll understand what I mean. I just want to remotely connect to a CLI.

---

### Post by Methuselah on 2010-01-04
OK.
In that case, to connect to Ubuntu it would have to be running rather than windows.

If you had ubuntu installed in a virtual machine running in windows you could configure it so ubuntu runs 'inside' windows.

Note that this option will be slower and ubuntu will not have direct access to your hardware just the 'fake' hardware emulated by Virtual Box.

VirtualBox
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Stormspace on 2010-01-04
> **Methuselah said:**
> OK.
In that case, to connect to Ubuntu it would have to be running rather than windows.

If you had ubuntu installed in a virtual machine running in windows you could configure it so ubuntu runs 'inside' windows.

Note that this option will be slower and ubuntu will not have direct access to your hardware just the 'fake' hardware emulated by Virtual Box.

VirtualBox
[http://www.virtualbox.org/](http://www.virtualbox.org/)

You will also need to redirect the SSH port to the virtual machine using the Virtualbox utilities.

---

