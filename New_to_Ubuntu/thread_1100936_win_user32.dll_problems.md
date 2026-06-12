---
title: "win user32.dll problems"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by XSindy on 2009-03-19
trying to fix XP, first error was user32.dll missing and it constantly rebooted, tried safe mode and other mods couldn't boot
found user32.dll copied it to win/system32
rebooted, didn't work, downloaded another user32.dll copied it
and now the error is: The system dll user32.dll was relocated in memory etc

any ideas?

---

### Post by XSindy on 2009-03-19
"The relocation occured because DLL Dynamically Allocated Memory occupied an addres range reserved for Win system DLLs. The vendor supplying the DLL should %s %s"

---

### Post by cwsnyder on 2009-03-19
I know only that the user32.dll belongs in the C:\Windows\System32 directory.

---

### Post by mikechant on 2009-03-19
Have you tried:
a) Rolling back to the restore point before the system got screwed up using the system restore feature?
b) or using the Windows recovery disc or partition and selecting the 'repair' option?

Also, how did Windows get screwed up in the first place?

---

### Post by XSindy on 2009-03-19
typo I  copied it in system 32 xD

a) would try to do that, but can't boot it at all, and don't know a way to do it outside win
b)you mean the instalation disc? am trying to find it to try

I really don't know, a few days ago I remember it crashing down, since I'm used to it, I just swiched to ubuntu and continued whatever I was doing.
An hour ago I tried to boot but the system check was there, I let it do it's job and I can't boot it now :S

---

### Post by mikechant on 2009-03-20
> a) would try to do that, but can't boot it at all, and don't know a way to do it outside win

Yes, of course - I read that you couldn't boot at all, my mind must have gone blank when I suggested system restore - as far as I know you can't do this with an unbootable system.

> b)you mean the instalation disc? am trying to find it to try

Yes, I think your install disc should include the repair option.
Or there's the possibility you might be able to repair from your recovery partition on your hard drive if you can't find the disc.
If you don't know if you've got a recovery partition do 'fdisk -l' in a terminal in Ubuntu it will show up if it's there.

---

### Post by ivanvajar on 2009-03-20
It might happen that you lose your boot loader for Ubuntu after reparing Windows. If that happens:

1. Boot the Desktop/Live CD. (Use Ubuntu 8.04 or later)

2. Open a terminal (Applications -> Accessories -> Terminal)

3. Start grub as root with the following command :

> sudo grub

4. You will get a grub prompt (see below) which we will use to find the root partition and install grub to the MBR (hd0)

>                [ Minimal BASH-like line editing is supported.   For
               the   first   word,  TAB  lists  possible  command
               completions.  Anywhere else TAB lists the possible
               completions of a device/filename. ]

      grub>



Type the following and press enter:

>       find /boot/grub/stage1

      If you get "Error 15: File not found", try the following:

>       find /grub/stage1

      Using this information, set the root device (fill in X,Y with whatever the find command returned):

>       grub> root (hdX,Y)

      Install Grub:

>       grub> setup (hd0)

      Exit Grub:

>       grub> quit

5. Reboot (to hard drive). Grub should be installed and both Ubuntu and Windows should have been automatically detected.

6. If, after installing grub, Windows will not boot you may need to edit /boot/grub/menu.lst

    * Open a terminal and enter :

     >  sudo gedit /boot/grub/menu.lst

     Your Windows stanza should look something like this :

       title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
       rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
       makeactive
       chainloader +1

      Note: Put your Windows stanza after AUTOMAGIC KERNEL LIST in the menu.lst to avoid disapearing of Windows entry after kernel upgrades.

---

