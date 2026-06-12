---
title: "Shutdown only logs out?"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Chrissd on 2011-04-16
Hi all,

Within Ubuntu, when I click shutdown in any GUI (shortcut in the panel top right or Ubuntu-> Shutdown -> Shutdown), it only logs out. If I use the command line to shutdown using -h, it will shutdown.

Anyone tell me how to fix this?

Thanks

---

### Post by oklokl on 2011-04-16
In my case
 Failure

Please note ->Do not Run

[COLOR=Red]gksu halt [/COLOR]--help

Usage: [COLOR=Red]halt[/COLOR] [OPTION]...
Halt the system.

Options:
  -n, --no-sync               don't sync before reboot or halt
  -f, --force                 force reboot or halt, don't call shutdown(
  -p, --poweroff              switch off the power when called as halt
  -w, --wtmp-only             don't actually reboot or halt, just write wtmp
                                record
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

This command is intended to instruct the kernel to reboot or halt the system;
when run without the -f option, or when in a system runlevel other than 0 or 6,
it will actually execute /sbin/shutdown.


Report bugs to <upstart-devel@lists.ubuntu.com>

---

### Post by skytreader on 2011-04-16
Chrissd, does this happen all the time or only on a few instances?

When you click on the switch button (the one which gives you access to shut down/log-out/hibernate/etc options), how many options do you see?

To be clearer, in mine I see,

Lock Screen
----------------
Guest Session
Switch From me
----------------
<And then how many options do you see in this bottommost section?>

---

### Post by Chrissd on 2011-04-16
Every time, without fail. This is the amusing thing, I have four options.

Shutdown/Restart/Suspend/Hibernate

No log out. :lolflag:

---

### Post by skytreader on 2011-04-17
> **Chrissd said:**
> Every time, without fail. This is the amusing thing, I have four options.

Shutdown/Restart/Suspend/Hibernate

No log out. :lolflag:

Oh. I don't really have a solution to your problem; I asked as someone who *might* be experiencing the same thing.

In my case, you see, it happens rarely and I don't know how to make it happen. When it happens, Ubuntu starts with the sound muted (when I distinctly remember that I didn't mute it during my last session). Then, the said section will have only 3 options. I'm without "Suspend" and "Hibernate". Shutting down will only log me out and I can't mount any disks.

I asked about it here but got no replies then :(.

---

### Post by grvsaxena419 on 2011-04-17
> **Chrissd said:**
> Every time, without fail. This is the amusing thing, I have four options.

Shutdown/Restart/Suspend/Hibernate

No log out. :lolflag:

Can you find out what is the command associated with your options ?

---

### Post by Chrissd on 2011-04-19
> **grvsaxena419@gmail.com said:**
> Can you find out what is the command associated with your options ?

How would I do that?

---

### Post by Chrissd on 2011-05-03
Just upgraded to Natty and still have the same problem. :(

---

### Post by seanos on 2011-07-14
I also have this problem.  It's just emerged on this machine after an upgrade from Lucid to Maverick.

The only other things I've done since that are (at all) related:

[LIST]
[*]fixing the ugly low-res boot screen caused by the upgrade
[*]running Admin | Login Screen
[/LIST]
Mysterious.

I'm planning to upgrade to Natty shortly, but it doesn't sound likely that will have any effect.

---

### Post by pulpo88 on 2011-07-17
I have this same problem on a *fresh install* of Natty.

New laptop, installed from the 64-bit live image CD.

I do *not* have this problem on my old laptop, which has been steadily upgraded since Dapper or so...

---

### Post by docksteaderluke on 2011-08-16
Same problem here on Natty 11.04. It just started happening all of a sudden one day.

Any progress? Luckily it seems to only be the menu as restarting/shutting down from the command line still works correctly.

---

