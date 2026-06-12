---
title: "No Option to Suspend"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by CrazzzyBudha on 2010-12-16
I am running an Acer Timeline X 4820T laptop. I used to have an option to Suspend or Hibernate my computer, but no longer. The power icon at the top right does not list either Suspend or Hibernate as options, although it used to. Pressing the power button on the laptop used to bring up similar options, again but no longer has suspend or hibernate. Also, in power management, for each action such as "what to do when the computer is idle" there used to be options for suspend and hibernate, but those are gone. Finally, I have the laptop set to suspend when the lid is closed, set that way prior to the disappearance. If I close the lid, when it is reopened there is an error message about "failed to suspend". 

Because the options used to exist, but now don't I assume this is somehow my fault with something I've done to the computer recently. I have recently updated the BIOS. There is an issue with this laptop where the battery indicator will not work until the BIOS is updated. The indicator now functions fine after BIOS upgrade. 

I also reformatted my hard drive, essentially I deleted partitions with other linux distros and expanded my ubuntu partition into their old space. I wouldn't think this would be the cause of the problem, but when I did that I lost GRUB and had to reinstall it. Perhaps because GRUB was installed first by the other distros, removing them caused GRUB to be lost and a similar thing could be happening with this? Just a shot in the dark. 

Any help would be appreciated. Thanks!

---

### Post by duanedesign on 2010-12-18
Does the power management subsystem think you can suspend? Try the following command and see if you get 'True' returned:

```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" --type=method_call --reply-timeout=6000 /org/freedesktop/UPower org.freedesktop.DBus.Properties.Get string:org.freedesktop.UPower string:CanSuspend
```

If this says "true" then the subsystem thinks you should be able to suspend and gnome-power-manager is just not displaying the option. If it says "false" then we need to work out why it thinks you can't

EDIT: is gnome-power-manager running: if True, is gnome-power-manager runing?

```
ps aux | grep gnome-power-manager | grep -v grep
```

---

### Post by CrazzzyBudha on 2010-12-18
Thanks for the response; I was really looking for a starting place. 

So the first command you suggest returned false
```
method return sender=:1.17 -> dest=:1.49 reply_serial=2
   variant       boolean false

```

Not knowing what I'm looking at, but it appears that gnome power management is working after running the second command:

[HTML]nick      1782  0.0  0.3 242736 11444 ?        Sl   16:16   0:00 gnome-power-manager
[/HTML]

Thanks for the help!

---

### Post by CrazzzyBudha on 2010-12-18
Thanks again for the help, I'm going to go ahead and call this solved unless anyone gives me reason not to. 

So, I tried suspending manually from the terminal and got this error: 

[HTML]Error org.freedesktop.UPower.GeneralError: No kernel support[/HTML]

A quick google of the error led me to Reddit [http://www.reddit.com/r/linux4noobs/comments/dqgee/ubuntu_1010_broke_suspendhibernate/](http://www.reddit.com/r/linux4noobs/comments/dqgee/ubuntu_1010_broke_suspendhibernate/)

where someone with a similar problem said "PM-Utils did the trick, although it seems kind of buggy."

I downloaded Pm-Utils from the software center, and now I have a suspend option, both in the upper right corner thing and for closing the laptop screen, though I still don't have a hibernate option which is not much of an issue for me. 

So, I don't know if this was the best solution to the problem, but the laptop suspends so unless there is a better option anyone knows of I'll go ahead and chalk this up as a win. Thanks!

---

