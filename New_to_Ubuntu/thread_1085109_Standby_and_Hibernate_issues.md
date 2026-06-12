---
title: "Standby and Hibernate issues"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Donkeykwon on 2009-03-02
Hi all,  I just installed Xubuntu this weekend to wade into the world of linux.  I'm having issues with both the standby and hibernate modes.  I need standby since this computer is going to be my non-wifi (huge distraction) class notes computer and I need the ability to standby while I'm between classes.

Problem

Every time I try to boot up from standby mode, either:
1) the screen is just a series of vertical stripes (akin to the calibration print of some printers) when I move my mouse, a small box (again striped vertical lines) moves in a sea of vertical lines, or 
2) the hard drive starts spinning, things seem as if they will start without anything being displayed on the screen and then reverts back to standby mode.

3) When I try to hibernate, an error message pops up and my computer just shuts down.  Hibernation isn't as important as standby is for me right now.

My System

- Dell Inspiron 4150, Pentium IV 1.7Ghz, 256Mb Ram.  
- Xubuntu release 8.10, xfce 4.4.2

Thanks in advance for any help and advice thrown my way.

---

### Post by chrisod on 2009-03-02
I've got a Dell Inspiron 600m and for whatever reason sleep mode only works if invoked from the command line. If I use the GUI it won't come back and I'll have to power off and reboot. So you might try this.

```
sudo /etc/acpi/sleep.sh sleep
```

Also, I thought I read somewhere once that a lack of swap space can cause problems with standby and hibernation, so you might want to make sure that swap is at least as large as your RAM.

Edit: Didn't notice that this was Xbuntu - I'm on Ubuntu 8.04. My wife's laptop is Xbuntu and I haven't got standby working on it either. However, since she uses it as a desktop I haven't really worried about it.

---

### Post by Jose Catre-Vandis on 2009-03-02
I was somewhat surprised to see my ancient laptop go into and come out of standby, using a CLI xubuntu install with openbox on top. I used the following command to take it down on the command line:
```
sudo /usr/sbin/pm-suspend
```

Hibernate works too:
```
sudo /usr/sbin/pm-hibernate
```

If you want to put these into scripts, you will have to give user access to the commands. Edit your sudoers as follows:
```
sudo visudo
```
Scroll to bottom and add the following:
```
yourusername ALL  = NOPASSWD: /usr/sbin/pm-suspend
yourusername ALL  = NOPASSWD: /usr/sbin/pm-hibernate
```
and save out.

You still have to use the sudo in the command for this to work, but you don't have to enter a password.

To avoid the above, make sure you have gksudo installed, then use a command like:
```
gksudo /usr/sbin/pm-suspend
```
you should get a dialog for a password.

This all works for me, so maybe it will help you out?

---

### Post by Donkeykwon on 2009-03-05
Thanks for the tips guys, but I'm still having the same issues booting up from standby.  Has anyone else had standby bootup issues with Xubuntu?  I just hope that whatever is wrong will be fixed in the next iteration in April.  Besides the standby thing, I'm loving Xubuntu.

---

