---
title: "How to remove Lubuntu?"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by beew on 2010-10-28
I installed Maverick in an old machine. I then decided to see if there is significant performance gain if I installed Lubuntu instead. So I created a dual boot with Lubuntu 10.04  in another partition for testing. Now I want to remove Lubuntu and give the whole hard disk back to Maverick

If I just delete Lubuntu with gparted (using a live usb) I think I would run into problems because I need to restore grub2 to maverick. I read about it briefly but forget how to do it (haven't done  that before)

Please tell me what the proper procedure is. Thanks.

---

### Post by TeoBigusGeekus on 2010-10-28
While in Maverick, use gparted to format the lubuntu partitions expand the maverick ones. Don't interrupt gparted at any cost.
After that, open terminal and give
```
grub
```
then 
```
grub install /dev/sda
```
Replace /dev/sda with the appropriate partition - i.e. where do you want grub to be installed.
Finally
```
sudo update-grub
```

---

### Post by beew on 2010-10-28
Thanks. Will try that when I get home.

---

### Post by amjjawad on 2010-10-28
Hello my friend :)

Did you install Lubuntu's boot loader in the MBR?

---

### Post by beew on 2010-10-28
Hi,

I think so. I carved out a small partition for it with gparted and then install Lubuntu in that partition, choosing manual installation so I could create a /root and /home partitions( I was preparing for a possibility that I might keep Lubuntu instead of Maverick. But it turned out I could get the same performance gain by simply switching between compiz and openbox and removing pulseaudio in Maverick)

On the boot screen the Lubuntu option appears on top and system would automatically boot into it if I do nothing. So it seems that Lubuntu's bootloader was installed.

---

### Post by amjjawad on 2010-10-28
> **beew said:**
> Hi,

I think so. I carved out a small partition for it with gparted and then install Lubuntu in that partition, choosing manual installation so I could create a /root and /home partitions( I was preparing for a possibility that I might keep Lubuntu instead of Maverick. But it turned out I could get the same performance gain by simply switching between compiz and openbox and removing pulseaudio in Maverick)

On the boot screen the Lubuntu option appears on top and system would automatically boot into it if I do nothing. So it seems that Lubuntu's bootloader was installed.

If you didn't choose where to install the boot loader so yes, most likely it was installed in the MBR.

Hope you'll be able to fix it as per the steps mentioned above :)

---

### Post by beew on 2010-10-30
> **TeoBigusGeekus said:**
> While in Maverick, use gparted to format the lubuntu partitions expand the maverick ones. Don't interrupt gparted at any cost.
After that, open terminal and give
```
grub
```then 
```
grub install /dev/sda
```Replace /dev/sda with the appropriate partition - i.e. where do you want grub to be installed.
Finally
```
sudo update-grub
```


I just deleted Lubuntu. When I typed "grub", it said package not installed. So I installed it and tried again and after typing grub I got a prompt that looks like grub> When I entered "grub install /dev/sda1" it said "command not found". I entered just "install /dev/sda1" and still the same.

Now I am going to reboot and will find out whether it works or not.

---

### Post by TeoBigusGeekus on 2010-10-30
My mistake, sorry... It should be
```
sudo grub-install /dev/sda
```

Even if you can't boot, you can easily do it with a live cd.

---

### Post by beew on 2010-10-30
Ok, bad news. It doesn't work. I rebooted and get a black screen with the line "error: no such partition" 
and the prompt > grub rescue>Someone please rescue me. :(

---

### Post by TeoBigusGeekus on 2010-10-30
Again
```
sudo grub-install /dev/sda
```
where /dev/sda is the hd you want to install grub to.

---

### Post by beew on 2010-10-30
> **TeoBigusGeekus said:**
> My mistake, sorry... It should be
```
sudo grub-install /dev/sda
```Even if you can't boot, you can easily do it with a live cd.

I booted into a live usb and entered this command and get 

/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)

I opened the partition from "Places" in the live usb so I think it is mounted. I open gparted and under the partition /dev/sda there is the option "unmount" so it seems to be mounted.

---

### Post by beew on 2010-10-30
> **TeoBigusGeekus said:**
> Again
```
sudo grub-install /dev/sda
```where /dev/sda is the hd you want to install grub to.


Enter this in "grub rescue" screen or the terminal in  live usb?

---

### Post by TeoBigusGeekus on 2010-10-30
Try in grub rescue.

---

### Post by beew on 2010-10-30
I entered the command in the "grub rescue" prompt and it said  "unknown command 'sudo'". So I just entered "grub-install /dev/sda" and it said "unknown command 'grub-install'"

---

### Post by TeoBigusGeekus on 2010-10-30
Try [this]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") then.

---

### Post by beew on 2010-10-30
The link works. But instead of the usual boot screen showing the Linux headers I get a "grub loading" message before entering the Ubuntu splash screen (the purple screen with the title "Ubuntu 10.10" and 4 orange/white dots.)

Is this the way it works usually? I thought reinstalling grub is more straight forward.

Thanks man. I am so lucky that you are close at hand. :)

---

### Post by TeoBigusGeekus on 2010-10-30
> **beew said:**
> Thanks man. I am so lucky that you are close at hand. :)

Don't thank me. It is I that should apologize for getting you into that mess. :)


Can you post the contents of /etc/default/grub?

---

### Post by beew on 2010-10-30
> **TeoBigusGeekus said:**
> 
Can you post the contents of /etc/default/grub?

Here it is 

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by TeoBigusGeekus on 2010-10-30
Comment out the hidden timeout option, ie.

```
#GRUB_HIDDEN_TIMEOUT=0
```

save, open terminal and give
```
sudo update-grub
```

---

### Post by beew on 2010-10-30
> **TeoBigusGeekus said:**
> Comment out the hidden timeout option, ie.

```
#GRUB_HIDDEN_TIMEOUT=0
```save, open terminal and give
```
sudo update-grub
```

Nothing changes. Still can't see the Linux-headers.

---

### Post by TeoBigusGeekus on 2010-10-30
Change this
```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```
to
```
GRUB_HIDDEN_TIMEOUT_QUIET=false
```
as well. Don't forget to update grub again.
Reboot and post back with the results.

---

### Post by beew on 2010-10-30
This time even the purple Ubuntu splash screen disappears. :)

---

### Post by TeoBigusGeekus on 2010-10-30
Ok, get it back to true. 8-[
Just testing you... :P
Sorry man, I still use grub legacy.
In order not to torment you any more with experimentations, go to [this]("http://ubuntuforums.org/showthread.php?t=1195275") page and hopefully you'll find an answer.
Post back if you do find a solution.

---

### Post by beew on 2010-10-30
> **TeoBigusGeekus said:**
> Ok, get it back to true. 8-[
Just testing you... :P
Sorry man, I still use grub legacy.
In order not to torment you any more with experimentations, go to [this]("http://ubuntuforums.org/showthread.php?t=1195275") page and hopefully you'll find an answer.
Post back if you do find a solution.

Don't worry about it man. I will look at the link, I am sure there is a way somehow. Thanks for the time and the patience. :)

---

### Post by TeoBigusGeekus on 2010-10-30
> **beew said:**
> Don't worry about it man. I will look at the link, I am sure there is a way somehow. Thanks for the time and the patience. :)

Good luck.

---

