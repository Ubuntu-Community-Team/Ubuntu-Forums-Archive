---
title: "Suspend/Hibernate Issues in Ubuntu 8.10 with Lenovo IdeaPad Y530"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by danzber on 2009-03-29
I know this is a frequently discussed topic, but I have not been able to find a solution to the suspend/hibernate issues when running Ubuntu 8.10 on a Lenovo IdeaPad Y530 with an NVidia GeForce 9300M graphics card.  I have followed the steps posted here:

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

But this did not resolve the issue.  When I suspend, the screen goes black with a blinking cursor in the upper left corner, but the laptop does not "sleep".  If anyone can help with this, I would really appreciate it.  It's kind of annoying not being able to suspend and having to shut down every time.

---

### Post by 123456789123456789123456 on 2009-03-29
Try to identify the motherboard model in the laptop.  Search for a driver compatable with that motherboard BIOS.  Also, make sure that in the BIOS that you have its ability to suspend turned on through advanced power management.  Some motherboards though capable of doing this, do not have the ability turned on.

---

### Post by danzber on 2009-03-30
Thanks for the help...

I didn't see any suspend settings in my BIOS setup.  Where can I download BIOS drivers for Ubuntu?  My laptop uses AMI EFI BIOS v. 10CN38WW (220).

Again, I appreciate any help.

---

### Post by oOarthurOo on 2009-03-30
In a terminal type "sudo s2ram -f"

Does it suspend?

---

### Post by danzber on 2009-03-30
I guess I don't have s2ram installed....command not found.

---

### Post by oOarthurOo on 2009-03-30
Not your fault. Ubuntu has changed thing since I last used it.

[https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238](https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238)

---

### Post by danzber on 2009-03-30
Just an update...I tried using s2both, and I basically got the same result when suspending (after a few status/progress messages, it got to a point where a cursor was just blinking and the laptop remained on, using full power).  However, after a forced shutdown (holding the power button), when booting up, it took me right into the saved/suspended state.  So s2both was able to successfully save the state, it just didn't suspend the power usage, etc.

Thanks for the prompt replies.  Any more help with this is appreciated, as always.

---

### Post by oOarthurOo on 2009-03-30
Been trying to read up on the issue since finding out ... with some dismay, I might add ... that ubuntu has displaced one method with another, without much documentation. That I've been able to find anyway.

Well... let's try this the new way then, and grope about in the dark until we figure it out.

Check out /var/log/pm-suspend.log

If you paste the output of 'cat /var/log/pm-suspend.log' we might have something useful to go on with.

---

### Post by danzber on 2009-03-30
Here is what was in /var/log/pm-suspend.log:

Initial commandline parameters: 
Mon Mar 30 01:11:43 EDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Mon Mar 30 01:11:48 EDT 2009: performing suspend

---

### Post by oOarthurOo on 2009-03-30
Yeah... that was about what I expected. pm-suspend gives pretty useless log info.

---

### Post by bernie9998 on 2009-03-31
I believe I have the same exact laptop and am encountering the same suspend issues.  I believe its an issue with the ACPI drivers in the kernel.

I provided a description of the behavior in this post a few days ago:
[http://ubuntuforums.org/showthread.php?t=1106927](http://ubuntuforums.org/showthread.php?t=1106927)

---

### Post by bernie9998 on 2009-03-31
Hmm. . . you said you were able to restore from hibernate after forcing it off?

Give this a try:
edit the file /etc/pm/config.d/00sleep_module
and add the following line to it:
```

HIBERNATE_MODE="shutdown"

```

When I made this modification, I was able to get the laptop to shutdown properly during a suspend rather than leaving it in a unresponsive state.  I had trouble restoring the image afterwards, but that could have been from another unrelated issue.

---

### Post by danzber on 2009-03-31
Thanks for the help/suggestions.  I tried modifying /etc/pm/config.d/00sleep_module as you suggested, but the issue remains.  I can still restore the suspended state after a forced shut down, but I still have the unresponsive state issue when it attempts to sleep/hibernate.

---

### Post by bernie9998 on 2009-03-31
I forgot to mention that that configuration parameter is for the pm-hibernate command, not the s2both command that you tried earlier.

Give it one more try, executing pm-hibernate instead of s2both.

---

### Post by danzber on 2009-03-31
I tried pm-hibernate, and I got some error messages when it was shutting down, and then it ended up in an unresponsive state with a blank screen (it was still powered on).  After a forced shutdown, it booted normally, and did not revert to the saved state.  Thanks for the idea, though.

---

### Post by RomanSB on 2009-03-31
I have been having the same problem

---

### Post by tmy123 on 2009-04-01
For hibernate use _tuxonice_. Suspend isn't working now.

---

### Post by bernie9998 on 2009-04-01
I was just able to get the system hibernate command (pm-hibernate) to work by configuring it to use the tunxonice module.

To do configure it, add this line to your /etc/pm/config.d/00sleep_module file:
```

SLEEP_MODULE="tuxonice"

```

This should enable the pm-hibernate command to use the same module that the s2disk and s2both uses.

As I have stated before, hibernate would not shutdown my machine, leaving it in an unresponsive state.  However, adding this additional line forced the machine to shutdown:

```

HIBERNATE_MODE="shutdown"

```

With the two lines in the config together, hibernate works for me with the system's pm-hibernate command.

---

### Post by danzber on 2009-04-01
Thanks bernie...I tried your suggestion (modifying the 00sleep_module file), but I guess I obviously don't have tuxonice installed, because after the modification, the pm-hibernate command no longer did anything.  Is there an easy way to install tuxonice?  I haven't researched it much, to be honest, but from what I've seen, it looks like you have to reinstall or recompile the kernel, or something along that line.

---

### Post by ramjet_1953 on 2009-04-01
You may want to have a read of this:

[https://help.ubuntu.com/community/Suspend2Kernel](https://help.ubuntu.com/community/Suspend2Kernel)

Regards,
Roger :cool:

---

### Post by bernie9998 on 2009-04-02
Try adding uswsusp instead of tuxonice, so the complete line looks like this:
```

SLEEP_MODULE="uswsusp"

```

What package did you install to get the s2ram/disk/both commands?
Did you use the uswsusp package?  If so, that would be why it wasn't working for you.

The package tuxonice-userui has the same commands.  I used them on my laptop simply because I believe they are newer.

Let me know if it works with the uswsusp module.

---

### Post by danzber on 2009-04-02
I do have the uswsusp package installed, and I have tried using that module.  I get the same result; it doesn't properly shut down, but after a forced shut down, it will reboot to the suspended state.  Can I use the tuxonice-userui without installing tuxonice?  I took a look at the wiki page that was posted and, as I suspected, installing tuxonice involves messing with the kernel, etc.

---

### Post by bernie9998 on 2009-04-02
Do you have the other line in the config file as well?

On my laptop, I had the same issue-- it would go into an unresponsive state and had to be powered off manually.  It was the HIBERNATE_MODE line that fixed that particular issue for me.

The entire file should look like this (plus any comments already there):
```

SLEEP_MODULE="uswsusp"
HIBERNATE_MODE="shutdown"

```Make sure both lines are there and there are no typos.  For me, I wasn't able to get the machine to turn off automatically either until I added the hibernate shutdown line.

---

### Post by bernie9998 on 2009-04-02
If that still won't work, you can try to use the tuxonice modules.  No kernel modification should be necessary-- it has been enabled into the default kernel by default for a while now I believe.

All you need to do is remove the uswsusp package and install the tuxonice-userui module instead:
```

sudo apt-get remove uswsusp
sudo apt-get install tuxonice-userui

```

The tuxonice-userui package should provide the same s2ram/s2disk/d2both commands as the other package.

After you change, then modify the SLEEP_MODULE line accordingly:
```

SLEEP_MODULE="tuxonice"

```

---

### Post by danzber on 2009-04-02
Yes, I had the other line in there as well.  I removed uswsusp and installed tuxonice-userui, and modified the sleep module line accordingly.  However, after doing this, pm-hibernate had no effect; nothing would happen when running it.  I tried s2both and s2disk, and I am getting the same result as before (no proper shut down, reboots to suspended state after forced).

---

### Post by bernie9998 on 2009-04-02
What ubuntu release are you using?

I happen to be using the latest (or fairly recent) build of the upcoming Jaunty Jackalope 9.04.  Perhaps some of these improvements I'm using is new to this release.

---

### Post by danzber on 2009-04-02
I'm using 8.10.

---

### Post by bernie9998 on 2009-04-02
I would have thought that these improvements were already implemented in the 8.10, but I could be mistaken.

Lets see if we can implement the shutdown mode manually.  First, execute these commands:
```

sudo su -
echo shutdown > /sys/power/disk
exit

```

This should configure the kernel to perform a normal shutdown during hibernate instead of the default, which is apparently not working.

Then retry hibernate:
```

pm-hibernate

```

---

### Post by danzber on 2009-04-03
I tried manually implementing the shutdown mode, as suggested, but it still doesn't work; I get the same results.

Thanks for continuing to help me out, by the way.

---

### Post by bernie9998 on 2009-04-03
If it still isn't working, then it sounds like you need the newer kernel.  I have version 2.6.28-9 on my laptop with Jaunty.

I don't think you can easily upgrade it without upgrading to the new distro, but I believe you can install this kernel manually to see if this resolves your issue.

If you're running 64bit (amd64), the kernel package can be found here:
[http://launchpadlibrarian.net/23759442/linux-image-2.6.28-9-generic_2.6.28-9.31_amd64.deb](http://launchpadlibrarian.net/23759442/linux-image-2.6.28-9-generic_2.6.28-9.31_amd64.deb)

If you're running 32 bit (i386), the package can be obtained here:
[http://launchpadlibrarian.net/23758428/linux-image-2.6.28-9-generic_2.6.28-9.31_i386.deb](http://launchpadlibrarian.net/23758428/linux-image-2.6.28-9-generic_2.6.28-9.31_i386.deb)

Download the proper package for your system and install with this command:
```

sudo dpkg -i linux-image-2.6.28-9-generic_2.6.28-9.31_i386.deb

```

This command is assuming you downloaded the package to your home directory and you are using 32 bit ubuntu.  If you downloaded it into a different directory, cd into the appropriate directory accordingly.  Also, if you are using 64 bit, change the package name for the appropriate architecture.

Once this is done, you can reboot and the new kernel should be used automatically.  Once running with the new kernel, go ahead and see if hibernate works.

If you end up having trouble with the new kernel, you can always boot back into the old one.  While the machine is booting, you should see the grub boot menu appear (you may have to hit escape to get it).  The third entry on the menu should be the old kernel (the first two are both related to the new kernel).  Once back into the old kernel, remove the new kernel with the command:
```

sudo dpkg -r linux-image-2.6.28-9-generic

```


I hope this works.  If it still fails, I'm sure we'll have better success with Jaunty when it comes out in a few days.

---

### Post by danzber on 2009-04-03
Cool, thanks for the suggestion, but I'm actually downloading Jaunty right now.  I gave in and decided to just try upgrading.  Hopefully I'll have better luck with it.  I'll let you know.  Thanks again!

---

### Post by danzber on 2009-04-04
I upgraded to Jaunty, but I haven't had a chance to play with it yet.  I did try suspending using the default installation settings, but the problem remains.  I'll try all the configurations discussed in this thread, but I won't be able to try for 4-5 days, since I am out of town.  I'll let you know how it goes then...sorry.

---

### Post by bernie9998 on 2009-04-05
No problem.  I would try the HIBERNATE_MODE config parameter first.  The tuxonice/uswsusp package may not even be required-- I recall I was able to get the laptop to turnoff properly with the shutdown parameter before even trying tuxonice.

Good luck with it!

---

### Post by danzber on 2009-04-10
Hello all...so I'm back, and have experimented with Jaunty.  As was suggested, I first tried just inserting the HIBERNATE_MODE parameter in the sleep_module first.  As was predicted, the laptop did shut off properly, but when I restarted it, it booted normally (as if the laptop was completely shut down); i.e., it did not boot into the suspended state.  So I tried playing with the sleep_module, using pm_hibernate with both uswsusp and tuxonice.  However, I got the same result each time; the laptop would shut down properly, but when restarted, it would boot normally and not into the saved state.  I also tried just running s2both (uswsusp), and in that case, I got the same result I was getting with Intrepid; the laptop would not shut down (I had to force the shutdown), but the when rebooting, it would then successfully boot into the suspended state.  It seems I can only get one phase working at a time, and not the best of both worlds.  If anyone has any other ideas or suggestions, I'd really appreciate any help.  Thanks!

---

### Post by bernie9998 on 2009-04-10
Well, looks like we got one part of hibernate working.  It sounds like you need the shutdown method set while using the uswsusp modules.

We can try this manually first to test this out.  Enter in these commands which I mentioned in the thread earlier:
```

sudo su -
echo shutdown > /sys/power/disk
exit

```

Once that is done, try suspending with the s2disk command as before.

If that works, then we can go ahead and set pm-hibernate to use the s2both commands by configuring the SLEEP_MODULE accordingly (either tuxonice or uswsusp, depending on which one you installed).

---

### Post by danzber on 2009-04-11
It didn't work...I still get the same results.  But at least I can restore the suspended state after the forced shutdown; it's better than nothing.  Thanks again for all the help.  If you have any other ideas, I'm all ears.

---

### Post by bernie9998 on 2009-04-11
Sounds odd that your laptop behaves differently than mine.  I wonder what bios version you have.  I think you can find it from the bios setup screen when you push F2 at boot.

---

### Post by danzber on 2009-04-11
Yeah, it is strange.  I had posted my BIOS version earlier in the thread, here it is....

AMI EFI BIOS v. 10CN38WW (220).

---

### Post by tmy123 on 2009-04-14
Past your /var/log/hibernate.log

---

### Post by danzber on 2009-06-18
I know it's been a long time since I posted to this thread, but FYI, after a clean installation of Jaunty, I configured the sleep_module to use tuxonice with the shutdown mode, and hibernate now works fine.  I still can't suspend though.  Oh well.  Thanks again everybody.

---

### Post by linuxgeoff on 2009-10-26
I have Toshiba m200.

With 8.04, suspend and hibernate both worked a dream.  After double upgrade to Jauny at the weekend, I cannot get suspend to work.  same issue:  blank screen with blinking underscore cursor in top left.  Fans going at full tilt; everything powered up. Only soln is ctl-alt-del x2 to force a shutdown.

---

### Post by gjhein on 2010-05-05
Lenovo-Ideapad-Y530, lucid32 upgrade and lucid64 new install:

Hibernate generally works but resume takes longer than fresh boot, as much as 2x. 

Suspend runs up to shutoff (screen lit, fan and hhd running), power-off required.

System board not recognized by system code, perhaps someone should speak to Lenovo.

---

### Post by zhanxw on 2011-04-09
I have found a solution here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587457/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587457/comments/6)

It works on my Ubuntu 11.04 Nauty, and I assume it works for older version of Ubuntu.:KS

---

