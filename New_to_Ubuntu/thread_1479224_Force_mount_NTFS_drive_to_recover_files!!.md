---
title: "Force mount NTFS drive to recover files?!?!"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by onthefence on 2010-05-10
Hey guys,

I am helping a friend recover files from his windows computer that just crashed(registry problem, hard drive is ok, but won't boot into windows, BSD on windows load), so typing this from a live session on the machine in question, IBM ThinkPad T43.

Unfortunately, the hard drive is not mounting because it did not shut down cleanly (which we can confirm). So I tried:

sudo mount -t ntfs-3g /dev/sda1/media/IBM_PRELOAD -o force

But, this didn't seem to do anything. 

Any other commands or tips to get this drive to mount? We are just trying to get some files that were not backed up. Don't worry Ive already given him the backup lecture. 

Not looking like we can save this windows installation, so will wipe most likely once the data is retrieved. At which point he will get the Ubuntu lecture :)

Thanks!

---

### Post by dca on 2010-05-10
[I]sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows[/I] 

..after that does it respond with needing a 'force' switch because of improper shutdown?

---

### Post by onthefence on 2010-05-10
Yes precisely...
> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g force 0 0


---

### Post by ajgreeny on 2010-05-10
> sudo mount -t ntfs-3g /dev/sda1/media/IBM_PRELOAD -o force
I think you are simply missing the space between the device name (/dev/sda1) and the mount point (/media/IBM_PRELOAD).

Also check that you have actually pre-made the mount folder /media/IBM_PRELOAD, exactly as you wrote it, ie all UPPER CASE, because if not the command will fail.

---

### Post by onthefence on 2010-05-10
haha ajgreeny, I think you nailed it. I never said I was perfect. (Although the upper case was correct)

However, through a series of reboots and accessing the hidden IBM recovery partition, it seemed to clear up the problem, because this time I ran the live CD, and it mounted without any problems.

Go figure. 

Thanks for the help. This forum is the best.

---

