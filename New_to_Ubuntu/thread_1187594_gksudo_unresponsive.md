---
title: "gksudo unresponsive?"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by col_hapablap on 2009-06-14
Hello everyone,
Long time lurker, first time poster.  I installed Hardy Heron on a very old laptop I got for free from a friend.  The laptop was absolutely trashed and I've at least got it running.  The internal wired lan does not work hardware wise.  The software 'sees' it, but I can't do anything with it.  So I invested $20 in a WIRED lan card.  Now at least my router can see the laptop (DHCP even assigned!), but the laptop cannot see/ping the router.  I think this is because the ping command is defaulting to use eth0 rather than the new card on eth1.

SO... went into xterm and typed ifconfig eth0 down and got the default no permissions error because I'm not logged in as root.

_*HERE'S the REAL problem*_
I did an alt+f2, typed in gksudo xterm...  but the terminal never opens, gksudo goes straight into sleep mode when viewed in the system monitor.

Any ideas?  The gksudo xterm command was working and bringing up a terminal screen a week ago, now nothing...  :(

Thanks in advance to all the friendly and helpful people on these forums!  ;)

---

### Post by yeats on 2009-06-14
I use Applications > Accessories > Terminal by default...  From there you can do sudo commands for everything you need to do.

Edit: Oops - I see you're using Xubuntu, which I'm not as familiar with.  Is there no menu option for a terminal?

---

### Post by kerry_s on 2009-06-14
> **chrissharp123 said:**
> I use Applications > Accessories > Terminal by default...  From there you can do sudo commands for everything you need to do.

Edit: Oops - I see you're using Xubuntu, which I'm not as familiar with.  Is there no menu option for a terminal?

yes it should be there, it is on mine anyways, i don't use it though, i usually just "sudo su" in the regular terminal.

---

### Post by col_hapablap on 2009-06-14
Thanks for the quick responses!
There is terminal in the menu for xubuntu and I can get xterm to open from alt+f2 (sorry for the confusion), but gksudo xterm will not open.

Is there a way to run root commands in a terminal that's been opened in a basic user login/session?

Any ideas on why gksudo goes right to sleep and doesn't run?

ie - in a terminal and I type gksudo
pop run screen opens and I type "ifconfig eth0 down", click Run, nothing happens.

Or

in a terminal, and I type ifconfig eth0 down, and I get SIOCSIFFLAGS: Permission denied.

Thanks!

---

### Post by TheBuzzSaw on 2009-06-14
gksudo is for GNOME.

kdesudo is for KDE.

I'm not sure what you use in xfce. I doubt it is gksudo though.

---

### Post by kerry_s on 2009-06-15
> I'm not sure what you use in xfce. I doubt it is gksudo though. 

it is gksudo, xfce4 is gtk2 based just like gnome.

> ie - in a terminal and I type gksudo
pop run screen opens and I type "ifconfig eth0 down", click Run, nothing happens.

your running a terminal command in the run dialog you should check the run in terminal. use "sudo" the command is not a gui program.
you can for instance do this " **xterm -e sudo ifconfig eth0 down** " or just "sudo ifconfig eth0 up" but check the run in terminal

sudo = terminal commands
gksudo = gui based programs, example: gksudo xterm, gksudo thunar, gksudo mousepad. 

you can also make life easier and set some to "NOPASSWD" so you don't need to use a password, up to you, i have a few set to make life easier.

you might also want to "alias" some commands to save you typing.
example: alias up='sudo ifconfig eth0 up'
then all you would have to type is "up".

---

### Post by col_hapablap on 2009-06-16
Thanks for the words of wisdom, kerry.
Not sure why it's not working on mine, but I understand now that gksudo is for gui, sudo is for terminal.

So...  I do an alt+f2, type "xterm -e sudo ifconfig eth0 down", check the run in terminal checkbox...  Terminal comes up, computer thinks for a minute, then the terminal closes.  I open up a separate terminal and type in ifconfig to check status, and the darn eth0 is still there...

Is there a way I can get the xterm terminal screen to stay up?  I tried "xterm sudo" as well, but again, terminal comes up, computer thinks, terminal closes.

I wish I could post a screenshot, but networking is kind of the crux of the problem.

Any other ideas?  Can I simply login as root rather than as a user in the boot/login screen?

---

### Post by col_hapablap on 2009-06-16
Oh, guess what?  Through my unbelievable networking genius (dumb luck) I got eth0 down through the system networking gui app screen thing.  Hallelujah!  The laptop lives.  :)

Suggestions on how to get sudo / gksudo working so I can enter commands, open a root mousepad, etc, are quite welcome, but for now, the primary problem is solved.
Thanks to all!


Mwhahaha! :p

---

