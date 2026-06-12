---
title: "won't accept password"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by PegM_4 on 2010-02-12
I made the mistake of making my password too long when I installed Ubuntu.  Didn't realize I would have to enter it every time it went into standby.  This morning, I changed it.  Now, after a reboot, it won't accept the new or old password.  Is there anything I can do besides a clean re-install?

Peg](*,)

---

### Post by nothingspecial on 2010-02-12
Yes.

Restart and press escape when you see grub loading

Boot into a root recovery shell

Type ```
passwd username
```

change your password.

---

### Post by PegM_4 on 2010-02-13
> **nothingspecial said:**
> Yes.

Restart and press escape when you see grub loading

Boot into a root recovery shell

Type ```
passwd username
```

change your password.

When I press escape as soon as I see the word GRUB, I get a menu that shows the following:

Utuntu, Linux 2.6.31-19-generic
Utuntu, Linux 2.6.31-19 generic (recovery mode)
Utuntu, Linux 2.6.31-14 generic
Utuntu, Linux 2.6.31-14 generic (recovery mode
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda3)

I don't have Vista on this machine.  I presume the Vista choice is because I left the restoration drive in place.

I tried the second choice and it brought me to a blue screen with a menu:

resume....Resume normal boot
clean.....Try to make free space
dpkg......Repair broken packages
grub......Update grub bootloader
netroot...Drop to root shell prompt with networking
root......Drop to root shell prompt

Not sure where to go or if this was even where I was supposed to be.

---

### Post by nothingspecial on 2010-02-13
root......Drop to root shell prompt

---

### Post by Jefferythewind on 2010-02-13
Hi,  I have the same problem, I installed ubuntu on my friends computer and I made a password that both of us would use until it was all set up, and then he could change the password to something else.  But I forgot what the new password is! It was so stupid, I almost did a fresh install the other day, but If i could change the password like this that would be great.  I tried to press esc when grub started but it went directly to the boot choices.

---

### Post by mhgsys on 2010-02-13
@Jefferythewind

In the boot choice menu; (grub menu) 

Select; recovery mode

You will see these options > 
resume....Resume normal boot
clean.....Try to make free space
dpkg......Repair broken packages
grub......Update grub bootloader
netroot...Drop to root shell prompt with networking
root......Drop to root shell prompt

Select; root......Drop to root shell prompt.

once there type
```
passwd username
``` (where username is the username you want to change the password for)

---

### Post by Iowan on 2010-02-13
Same basic information...
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by PegM_4 on 2010-02-13
OK, I did as suggested and it looked like it worked.  Then I re-booted.  I wasn't able to get out of the screen where I changed the password so had to do a hard re-boot.  Is that how it was supposed to go.  When it rebooted, it goes to my desktop then a window pops up saying:  

**Enter password for default keyring to unlock**  The application 'NetworkManager Applet' (/usr/bin/nmapplet) wants access to the default keyring, but it is locked Password:_________

In the password blank, I tried the new password, the old password, the password I created that I had to put in for something that I'm not sure what it was, but it was required every once in a while.  None of them seem to work.  I can, however, click 'deny' and a window comes up asking for my Wireless Network password.  I type it in and the 'default keyring' window pops up again.  I again click on 'deny' and it goes away and I can get online.  I can use my laptop programs, but presume I will eventually have a problem as I assume the missing password will stop my access to something.  Does this make any sense to anyone?

---

### Post by nothingspecial on 2010-02-13
It should be your original (very long) password

---

### Post by PegM_4 on 2010-02-13
> **nothingspecial said:**
> It should be your original (very long) password

Tried it and it didn't accept it.  I'm about to reinstall.  I just installed it last week, so it isn't like there is a lot there to back up or anything and I'm retired with lots of free time.  Don't like having it doing strange things.  I think I really like Ubuntu, but will set my password this time and leave it alone.  :)

---

### Post by Jefferythewind on 2010-02-14
mhgsys,

  Thanks for the help, and thats to everyone else.  I will try to get in there to root on my friend's computer to see how it goes, and then post the results.

---

### Post by Jefferythewind on 2010-02-21
ok, i found it.  I'm sorry I guess I didn't realize that you had to go into recovery mode, it is easy enough.  I actually found another work around that works also:

In the grub menu, you press "e" to edit the boot information for the Ubuntu Kernel.  There is a line that ends with ```
ro splash screen
``` or something like that, and you can change that to ```
rw init=/bin/bash
``` and that gets you into the root command prompt.  The way outlined above, using the "recovery mode" is much more straight forward though.

  This brings up a question.  Anyone that has my computer can just do the same thing that I just did to reset the password, and then they would have admin privileges.  Is the system still safe then?  

  This technique was very helpful for me to recover a lot of work that I would have lost because I was stupid, but does it also leave ubuntu a little vulnerable?

---

### Post by JKyleOKC on 2010-02-21
> **Jefferythewind said:**
> This technique was very helpful for me to recover a lot of work that I would have lost because I was stupid, but does it also leave ubuntu a little vulnerable?The sad truth is that ANY system is vulnerable to anyone who has physical access to it. It's possible to disable the recovery options for the grub menu (at least it is with the original grub; I don't know about grub2) but that makes it extremely difficult to recover from bad situations such as the password snafu that started this thread.

The only way to keep a system absolutely invulnerable is to keep it in a locked safe to which nobody, including you, knows the combination. It's not very useful in that state, but invulnerability has its price...

---

### Post by Jefferythewind on 2010-02-21
Thats a great point.

---

