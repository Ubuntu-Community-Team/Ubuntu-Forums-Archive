---
title: "Grub does not run default boot timer when shut down from a script"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by AndrewU on 2011-08-17
Hey All,
     I am fairly new to Ubuntu, and like it so far, but I have a weird problem.  I am trying to use Ubuntu (ntfsclone) to automatically reload a windows image to computer lab computers every night when people go home.  I have everything set up to run in automatic, but when I run a script to shut down Ubuntu automatically, the next time the system boots, the "boot to default OS" timer in Grub does not work, or even appear.  I have messed around trying to pinpoint where/why it fails to show up, and I think it is because the shut down is coming from a script...  I am at my wit's end trying to figure this one out, and could really use some help! 
 
Background:
    System is set up for dual boot, with Ubuntu as the default
    In windows, an automated task reboots the computer at 7:00pm
    After the reboot, Ubuntu starts automatically after the 10sec timeout, (This is where my timer is gone)
    Upon hitting run mode 2, (multi-user, /etc/rc2.d) I have a script that says "sudo shutdown -P +5".
    After 5 min, the computer shuts down.
    Upon hitting run mode 0, or 6, (halt or reboot, /etc/rc0.d or /etc/rc6.d) I have a script that runs ntfsclone 
             to re-image my windows partition.
    The next morning, the students boot up the computer, and select "windows XP", and enjoy a clean 
             computer.

Testing I have done so far:
     If I run "sudo shutdown -P +5" from the terminal, I get the timer on the next boot...  I do have to enter in 
             the root password at the prompt though, which I obviously don't have to do for the script.
     If I shut down/restart the computer with the controls in the upper right-hand corner of the screen, I get 
             the timer.
     Other shutdown options, -h, -r, etc give the same result

Help please!

---

### Post by drs305 on 2011-08-17
I am not sure what is happening but have one idea for you to investigate.

When Ubuntu boots Grub 2 places a 'recordfail' event in /boot/grub/grubenv. Once the system successfully boots, the 'recordfail' event is removed. 

When Grub 2 boots the next time, it looks at /boot/grub/grubenv to see if the 'recordfail' flag is still set. If it is, Grub 2 halts any automatic boot and waits for user input.

So perhaps the way your script is running is preventing Grub2 from removing the 'recordfail' after booting. You can check the contents of 'grubenv' with:```

sudo grub-editenv list
```

If you find a recordfail listing, you can add a command to your script at the appropriate time:
```

sudo grub-editenv create
```
which will create a 'clean' file.

I'll be away for a couple of days, so I'll give you a backup solution. 

If the menu is stopping because of a 'recordfail', you can disable the check by manually editing /boot/grub/grub.cfg. Find the recordfail section and change the -1 value to any positive integer. Mind that you are disabling a feature of G2 which would prevent continuous booting if a problem occurs.
> 
if [ "${recordfail}" = 1 ]; then
[s]  set timeout=-1[/s]
  set timeout=3
else
  set timeout=10
fi****

This isn't an ideal solution because you are overriding a G2 feature, and the edit will be removed any time update-grub is run. But it would at least tell you if it is the recordfail function which is causing problems.

---

