---
title: "desktop will not load 9.04"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by libihero on 2009-04-21
i was trying to change my graphics driver, and i was following the directions in [here]("http://ubuntuforums.org/showthread.php?t=1131492").  after i did sudo killall gdm, my desktop crashed, and i restarted my computer.  after rebooting, the screen goes black with random colors after the ubuntu logo....
is there anyway to undo the changes i made so i can get back on my desktop??  this sorta sucks since i got finals to study for haha

---

### Post by swoll1980 on 2009-04-21
go into the recue console 

```
cd /etc/X11
```
```
ls
```
this will display a list of files. Look for xorg.conf backups. If you see one do.
mv /etc/X11/name_of_backup_file /etc/X11/xorg.conf
This will replace the xorg file with the backup. Note the capital X in X11. Hopefully this will fix your problem.

---

### Post by libihero on 2009-04-21
ok i tried using the suggested backup file and that didnt work.... does the "failsafe" one work?

---

### Post by swoll1980 on 2009-04-21
It could. go ahead and try it

---

### Post by libihero on 2009-04-21
didnt work :( 
it all started when i did "killall gdm".... is there anyway to reverse wat i did?

---

### Post by defaria on 2009-04-21
> **libihero said:**
> ok i tried using the suggested backup file and that didnt work.... does the "failsafe" one work?

9.04, ati drivers right? These are all messed up at the moment. I suggest you stay with the open source drivers for now. One way to get your login back is to use Ctrl-Alt f1-f7 (I tend to use f4) and login to a terminal shell then completely remove the fglrfx drivers as well as ati and radeon drivers then reinstall the later two. This should get you back to the open source drivers. If you have further problems you may need to uninstall compiz and compiz-core. You should reboot as I believe the proprietary drivers hook into the kernel.

The following worked for me: [fglrx does not support xserver 1.6]("https://bugs.launchpad.net/ubuntu/jaunty/+source/fglrx-installer/+bug/313027"). The trick is using Ctrl-Alt f1-f7 to get a non GUI console since your GUI is dead. Then, of course, knowing the proper commands to use to get things back.

Good luck and report back.

---

### Post by libihero on 2009-04-21
when do i press control-alt-f4?

---

### Post by libihero on 2009-04-21
i tried it in recovery mode.... and it still didnt work
i feel like slamming my computer against a wall. 
i just need to get to my desktop i dont care how simple it is lol

---

### Post by alphacrucis2 on 2009-04-21
> **defaria said:**
> 9.04, ati drivers right? These are all messed up at the moment. I suggest you stay with the open source drivers for now. One way to get your login back is to use Ctrl-Alt f1-f7 (I tend to use f4) and login to a terminal shell then completely remove the fglrfx drivers as well as ati and radeon drivers then reinstall the later two. This should get you back to the open source drivers. If you have further problems you may need to uninstall compiz and compiz-core. You should reboot as I believe the proprietary drivers hook into the kernel.

The following worked for me: [fglrx does not support xserver 1.6]("https://bugs.launchpad.net/ubuntu/jaunty/+source/fglrx-installer/+bug/313027"). The trick is using Ctrl-Alt f1-f7 to get a non GUI console since your GUI is dead. Then, of course, knowing the proper commands to use to get things back.

Good luck and report back.

The latest version of fglrx does support xserver 1.6. I am running it. A problem is that the latest version of fglrx dumps support for a lot of the older ATI cards (even some that are still being sold in some laptops) The same situation exists for the Windows drivers (Catalyst 9.4) - way to go ATI. ATI released the specs for all the cards dumped, so that the opensource drivers can be tweaked to fully support them but that will take time for the devs to implement. If the OP has one of the older cards that have been dumped, then with jaunty, he has no choice but to run the opensource driver which may not have all the bells and whistles for his card. In another thread I explained how he can purge the proprietary driver from the recovery prompt so the opensource driver can be used but he says that didn't work. Didn't get much feedback though to try and diagnose the problem.

---

### Post by libihero on 2009-04-21
is there any way i can just go back to 8.10.. would that fix the problem?

---

### Post by libihero on 2009-04-22
bump... :( what more feedback did u need??

---

### Post by libihero on 2009-04-22
i also got this error when loading...
modprobe: FATAL: could not load /lib/modules/2.6....-generic/modules.dep: no such file or directory
i put ... because it was just numbers and i had to type fast
could that be the problem?

---

### Post by Mehtras on 2009-04-22
Hey,

Did you try to use the live CD to enter your desktop? It might be the easiest way to access your files..

Just to be sure you could backup your files and reinstall Ubuntu (either 9.4 or 8.10)

---

### Post by libihero on 2009-04-22
k thanks, i'll do that if no solution comes up

---

### Post by Mortus Pryde on 2009-04-22
Hmmmm... Looks like I will have to either patch myself up with the Open Source drivers for now, or maybe give Hardy a spin, though I must say I do like the performance boost otherwise from Intrepid to Jaunty.

I was able to get 9 frames a second out of OpenLife running at low settings on the Open Source drivers without any tweaking, so at least it was marginally usable. Sadly any tweaking at all dropped my frame rates down to 1.5. :( Still no where near the 20 to 25 frames I am used to under XP with the same machine.

Think I will wait for the full release and reinstall fresh again. Have no data on the machine other than Linux its self. ;)

---

### Post by defaria on 2009-04-23
> **libihero said:**
> when do i press control-alt-f4?

Whenever you want! But seriously, after booting up and when you get to the part that you can't go on, do Ctrl-Alt-f4 (or actually any of Ctrl-Alt-f1 through f6 should work). You should see a prompt for a command login. BTW Ctrl-Alt-f7 get's you back to your GUI session.

You can, in your IDE console (Ctrl-Alt-f4) find and kill your X server (ps -ef | grep X) and you should be sent back to the GUI login prompt. Again, Ctrl-Alt-f4 should get you back to your IDE console login.

---

### Post by defaria on 2009-04-23
> **alphacrucis2 said:**
> The latest version of fglrx does support xserver 1.6. I am running it.

Define support! What I experienced is 1) it doesn't support multiple monitors. That kills it for me. Plus 2) I experienced window manager aborts and 3) lots of CPU consumption. 

> If the OP has one of the older cards that have been dumped, then with jaunty, he has no choice but to run the opensource driver which may not have all the bells and whistles for his card.

That's where I'm at. My card is an ATI-Radeon 3200 HD which I thought was fairly new - perhaps too new - but who knows...

---

### Post by Hemmer on 2009-04-23
I had the same problem with my ATI radeon 200M which I solved by purging the fglrx driver as suggested earlier in the thread. Full instructions can be found here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

