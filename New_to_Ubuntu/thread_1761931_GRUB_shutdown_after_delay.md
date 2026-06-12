---
title: "GRUB shutdown after delay"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by .:PiXi²:. on 2011-05-18
Hi,

Is there a way to make GRUB shutdown the computer if there where no keys pressed? Just like having a default shutdown entry selected. So when the computer boots, it shuts down automatically after a few seconds if the user doesn't select another entry to boot from.

Thanks in advance!

---

### Post by Rubi1200 on 2011-05-20
Hi,

first a question; why would you want to do this since it is GRUB's job to boot the computer? If you don't want it to boot, don't turn it on.

So, as far as I know this is not a direct option in GRUB2, available on versions of Ubuntu after 9.10.

In legacy-GRUB it was possible to edit the menu.lst and add an entry that would appear on the menu.

You can always press "c" at the menu to drop to a prompt and then do either:
grub>halt (to shutdown)
grub>reboot (self-explanatory)

Anyway, I hope this helps answer the question or at least bump the thread up so someone else can take a look and offer a solution.

---

### Post by .:PiXi²:. on 2011-05-20
Thanks Rubi1200 for your response. The reason why I want this, is because my laptop has the inconvenient habit of booting itself when it's in my backpack. This happens with the slightest pressure and has some nasty consequences, like having an overheated laptop with a dead battery.
I want to prevent this by making sure the laptop shuts down after it starts up when I'm not aware of it.

---

### Post by drs305 on 2011-05-21
It was an interesting question, so I played around a bit.

You can do it by creating a *menuentry* which contains the 'halt' command. You would make that *menuentry* the default, making sure you set the timeout long enough for you to select another one.

The menuentry would be:
> menuentry "AUTO SHUTDOWN" {
halt
}
Add this to 40_custom after the existing lines, save the file, and update Grub. The file should already be executable. If you would rather it appear at the top of the menu, save the file as 09_custom and make it executable, or simply rename 40_custom once you have saved it.

Of course, the above is too simple. So here is an idea for some eye candy for the warning. 

The original menu appears and selects the "AUTO SHUTDOWN" entry after the default timeout. 

The screen then changes to red and displays the highlighted menuentry "WARNING: AUTO SHUTDOWN in 10 seconds."

Here's how:
[LIST]
[*]Open /boot/grub/grub.cfg as root. Save the file as /boot/grub/halt.cfg.
[*]Remove everything below approximately line 63:
> ### END /etc/grub.d/00_header ### 
[*]Remove the 'recordfail' section to ensure it always executes, and edit the timeout to the desired timeout.
> 
[COLOR="Red"][s]if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else[/s][/COLOR]
  set timeout=**10**
[COLOR="Red"][s]fi[/s][/COLOR]

[*]Make the screen stand out with a colored background (red). Change 'black' (transparent) to 'red'.
> 
  set menu_color_normal=white/**red**
  set menu_color_highlight=black/light-gray

[*]Add a menuentry with a nice warning title.
> menuentry "WARNING: AUTO SHUTDOWN in 10 seconds." {
halt
}
[*]Edit 40_custom and change the menuentry to:
> menuentry "AUTO SHUTDOWN" {
configfile /boot/grub/halt.cfg
}
[*]Save both files and update grub.
[/LIST]

Of course, you should never see the eye candy screen since you would have selected another entry. But if you happen to be distracted, this will give you a few "OMG" moments to panic and try to remember how to stop it from shutting down before it does so.  ;-)

Note: Press the ESC key to back out of the menu.

---

### Post by .:PiXi²:. on 2011-06-09
Thanks drs305 for your excellent answer, this is exactly what I was looking for.

There is only one problem left, once the halt command gets executed, the computer doesn't shut down. I've also tried "halt --no-apm", without success. If I execute halt from the GRUB command line, the computer also fails to shut down.

I've found several topics about this problem, but none of them offers a solution.
Are there more options for the halt command than only "--no-apm"?
Or are there other commands to shut down the computer?
Any suggestions are welcome.

---

### Post by drs305 on 2011-06-09
I took a look at "help halt" in Grub 2 but the only option was the "-n" or "--no-apm" options. The only thing I can suggest is that you research your BIOS power options - perhaps there is a setting which will allow 'halt' to work.  

You could also try it from a normal terminal after booting, just to know if it's a GRUB issue or a system-wide one.

If I can find anything else I'll report back.

---

