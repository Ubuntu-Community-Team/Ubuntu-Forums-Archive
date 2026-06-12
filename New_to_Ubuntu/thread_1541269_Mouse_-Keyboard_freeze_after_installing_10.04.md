---
title: "Mouse -Keyboard freeze after installing 10.04"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by dnunet on 2010-07-28
I have a Compaq Pressario SR5250IL. I have 160 GB HDD, 2 GB RAM.
I have WinXP in part 1(30GB), Personal in Part 2(35GB).
I installed Ubuntu 10.04 ( from CD received from you only)
in the balance as 
12GB as root(/), 
3GB as Swap, 
Balance as /home.
It installed fine.
When I restart, Grub2 loads.  On selecting Ubuntu, booting fine.
When I select any application, the mouse- keyboard freeze. 
I have to power-off to come out.
Win XP boots, works fine.
What has gone wrong, what do I do to correct it ?
(P.S. I had the same problem running it as Live CD.)

---

### Post by dnunet on 2010-07-30
Any help.... still waiting

---

### Post by jtarin on 2010-07-30
Are you booting from a Grub menu? Try booting with kernelname (recovery mode)line.

---

### Post by jtarin on 2010-07-30
OK..I looked around and it seems your graphics chipset is problematic....people have tried differnt drivers (modules) with some partial success.The i915 and the i810 modules being two.If you can get to the desktop and before you do anything else try to drop to another screen.
There are 6 other terminal screens available by pressing Ctrl+Alt+(F1 thru F6). Go to one and issue the command after login....```
lspci
```look for your graphics chipset and make a note.
Next issue the command ```
lsmod
``` and see if you can locate either of the modules I have listed above.

---

### Post by dnunet on 2010-07-31
> **jtarin said:**
> OK..I looked around and it seems your graphics chipset is problematic....people have tried differnt drivers (modules) with some partial success.The i915 and the i810 modules being two.If you can get to the desktop and before you do anything else try to drop to another screen.
There are 6 other terminal screens available by pressing Ctrl+Alt+(F1 thru F6). Go to one and issue the command after login....```
lspci
```look for your graphics chipset and make a note.
Next issue the command ```
lsmod
``` and see if you can locate either of the modules I have listed above.

Thanks... Will try...Though the screen freezes after 2 clicks of mouse.
I have WinXP in Part 1, Is there a way to use it for the above?
Thanks again..

---

### Post by jtarin on 2010-07-31
Reboot and when you get to the Ubuntu login screen (not Grub) at the bottom you will see a panel.Click "Sessions">xterm. This will allow you to go straight to a terminal and proceed.When finished issue the command exit or reboot and login in normally next time. These commands will not repair your install as of yet. We need to gather some info first.

---

### Post by dnunet on 2010-07-31
> **jtarin said:**
> Reboot and when you get to the Ubuntu login screen (not Grub) at the bottom you will see a panel.Click "Sessions">xterm. This will allow you to go straight to a terminal and proceed.When finished issue the command exit or reboot and login in normally next time. These commands will not repair your install as of yet. We need to gather some info first.

Managed to get to terminal via Recovery mode...:D
The out puts are
[LIST]
[*]lspci - shows Intel 82945G/G2 Integrated Graphics controller (rev02)
[*]lsmod shows  i915 in a few places not i810
[/LIST]
Will this help in resolving the issue...
Look fwd to your further advice
Thanks

---

### Post by gandaran on 2010-07-31
hi.
I have seen some reports about this problem in Compaq Pressario laptops here on the forum before, but I don't know if there was a fix what I can tell is that some Toshiba netbooks with Intel graghics had exactly the same problem and the fix was to update the BIOS, this is just an idea but maybe this could work for you too, check if a BIOS update is available for the laptop and try it.

---

### Post by jtarin on 2010-07-31
Lets try to remove the module i915 and replace with i810. 
Issue the command```
 modprobe -r i915
```this will remove the i915 module. Now issue the command ```
modprobe i810
```this will load the i810 module. To confirm, issue the command ```
lsmod
``` Reboot and see if there are changes.Issue the command ```
lsmod
```once more to confirm i810 loaded on boot.
Has this helped?

---

### Post by dnunet on 2010-07-31
> **jtarin said:**
> Lets try to remove the module i915 and replace with i810. 
Issue the command```
 modprobe -r i915
```this will remove the i915 module. Now issue the command ```
modprobe i810
```this will load the i810 module. To confirm, issue the command ```
lsmod
``` Reboot and see if there are changes.Issue the command ```
lsmod
```once more to confirm i810 loaded on boot.
Has this helped?

I got into terminal by pressing ctrl-alt-F1.
Got my dnmint Desktop command line
Input modprobe -r i915
Shows FATAL : i915 is in use
Tried modprobe i810
Shows 'cannot insert i810 or some thing like that.
What mext?
P.S. 1. Thanks for your patience..
     2. How do I go to loading Ubuntu thru command line. When I type 'boot' it says 'No such command'

---

### Post by jtarin on 2010-08-01
Just log off of your current user session, and then press Ctrl+Alt+F1.
then just do "sudo modprobe -r i915" then "sudo modprobe i810.
to go back to the login screen press Alt+F7
The "X" graphical envoronment can not be running.

---

### Post by dnunet on 2010-08-01
> **jtarin said:**
> Just log off of your current user session, and then press Ctrl+Alt+F1.
then just do "sudo modprobe -r i915" then "sudo modprobe i810.
to go back to the login screen press Alt+F7
The "X" graphical envoronment can not be running.

Pardon me for being a bit dense
How do I log off..
1.As I boot in 'Lo graphic mode, go to terminal it asks me to login. It does not take any other command....
2. If I go to normal boot as I make a couple of strokes, mouse-keyboard freeze...
Catch 22.... it looks like.. to me
Pls help

---

### Post by jtarin on 2010-08-01
Pardon me my mistake...Normal boot....no mouse..._At the login screen_ press Ctrl+Alt+F1.
then just do "sudo modprobe -r i915" then "sudo modprobe i810.
to go back to the login screen press Alt+F7
The "X" graphical envoronment can not be running when you remove module.

---

### Post by dnunet on 2010-08-01
> **jtarin said:**
> Pardon me my mistake...Normal boot....no mouse..._At the login screen_ press Ctrl+Alt+F1.
then just do "sudo modprobe -r i915" then "sudo modprobe i810.
to go back to the login screen press Alt+F7
The "X" graphical envoronment can not be running when you remove module.
Just tried that. It goes to dnmint-desktop$ login only.
It does not accept plain sudo modprobe command.
On logging in then on modprobe it says Fatal: i915 is in use..
I am stuck... Sorry

---

### Post by orethrius on 2010-08-01
> **dnunet said:**
> Just tried that. It goes to dnmint-desktop$ login only.
It does not accept plain sudo modprobe command.
On logging in then on modprobe it says Fatal: i915 is in use..
I am stuck... Sorry

Then something is very, *very* wrong here.

Either:
A.  The **sudo** password doesn't work, or
B.  X can't be killed off.

What you *should* be able to do from that CLI is
**sudo -i** (that's a lower-case I), which then allows you to enter your root password for root access.

From there, you'd kill off X11 and GDM for good measure (**killall -9 X; killall -9 gdm**), *then* follow jtarin's directions, being sure to **exit** the root account when you're done.  Then you'd issue **sudo gdm**, which *should* reinitialize the GDM login screen.

After all that, you'd need to edit your boot modules to blacklist i915 in favor of i810; though I don't recall that procedure offhand... yet. ;)

---

### Post by jtarin on 2010-08-01
OK try to boot the recovery mode kernel and select root terminal or something such from the selection menu. Then go through the commands.

---

### Post by jtarin on 2010-08-01
OK try to boot the recovery mode kernel and select root terminal (worded as something such (not network)) from the selection menu. Then go through the commands.

---

