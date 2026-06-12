---
title: "ubuntu boot logo messed"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by libihero on 2009-04-26
i tried editing the startup manager to make it higher resolution, and it messed up the colors (made it negative).  i switched it back, but the colors are still messed up....

---

### Post by cariboo on 2009-04-26
When you make changes to usplash, the splash screen, you should run in an Applications-->Accessories-->Terminal:

```
sudo update-initramfs
```

---

### Post by libihero on 2009-04-27
i cant figure out what to do from there

---

### Post by y_garti on 2009-04-27
enter to applications and add/remove
install the program StartUp-Manager
after the installation enter to system -> administration -> StartUp-Manager
in the display resolution chose the desire res and chose close (enjoy)

---

### Post by libihero on 2009-04-28
ya that's what i did in the first place, and it ended up giving me a "negative" of the splash screen when its loading

---

### Post by y_garti on 2009-04-29
1 try to select a lower resolution
2 if it still doesn't work do a p/s of all the tabs so we can look and see if you select a bad configuration

---

### Post by libihero on 2009-04-29
here is what it looks like now...

---

### Post by y_garti on 2009-04-30
well its look fine
i want to be sure i get what you are trying to say 
is that you have a problem with grub (that you see a negative picture)
if so i recommend a full back up of your system and try this

Booting from ubuntu live CD and open the terminal.

[LIST=1]
[*]Open terminal by going to Application>Accessories>Terminal
[*]As usual you need to gain root access. Via live CD we know that we can do SUDO to gain temporarily access to root but we have a lot of command need root access so i prefer you change the root password so that we can use SU command to gain permenent root access. To change root password type SUDO passwd root.  then set your root password.  (Remember, this do not change your root password in your existing linux distro)
[*]Then we began to the repairing part.  First use su command to gain root access. Then make a new directory by typing mkdir repair/ im using directory name .
[*]Next is we have to mount the default linux partition to your new directory by using mount /dev/hda7 /repair. (hda7 is the partiton which you have your ubuntu distro installed)
[*]After that, we need to mount dev directory into /repair/dev by commiting this command. mount -o bind /dev /repair/dev
[*]After you finish doing all the above command successfully, then we may proceed by chrooting to the directory.
[*]Type chroot /repair
[*]Then type grub-install dev/hda to install a new GRUB bootloader.
[*]Then restart by typing shutdown -r now
[/LIST]

---

### Post by libihero on 2009-05-07
it doesnt let me get past the point with mount /dev/sda1 /repair (i even tried mount /dev/sda1/repair).  with mount /dev/sda1, it gives me :mount: mount point /repair does not exist
with mount /dev/sda1/repair, it gives me:
mount: can't find /dev/sda1/repair in /etc/fstab or /etc/mtab

---

### Post by libihero on 2009-05-10
bump...

---

### Post by libihero on 2009-05-11
bump

---

### Post by Don1500 on 2009-05-11
CD /
then do the commands

---

### Post by libihero on 2009-05-14
ok i did everything and on the last step, this is what happened:

```
root@ubuntu:/# grub-install dev/sda
Format of install_device not recognized.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
```

what do i do from there??

---

### Post by libihero on 2009-05-15
bump...

---

### Post by y_garti on 2009-05-16
i am sorry man but i don't know

---

### Post by libihero on 2009-05-18
anyone else?? :( bump...

---

### Post by mrplow887 on 2011-06-03
you specify "dev/sda" in your grub-install prompt. 

so you need to specify the absolute path to your device.  
```
/dev/sda
```
Notice the / at the beginning.  

```
grub-install /dev/sda
```
is what you want to do :)

or specify the grub-style device, this should be "hd0"

---

### Post by JohnBonne on 2011-06-03
Try themes. You may have a black and white theme. I know it sounds obvious, but I am about to make it an adage. The basic things apply; even if you can write complex codes you still have to have the device plugged in.

 "When the toaster don't pop up check the plug first."

Hope this helps,

John

---

