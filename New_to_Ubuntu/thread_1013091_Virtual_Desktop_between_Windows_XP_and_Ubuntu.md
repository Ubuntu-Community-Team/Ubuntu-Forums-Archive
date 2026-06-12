---
title: "Virtual Desktop between Windows XP and Ubuntu"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-12-16
I have to computers where one the "main" computer that is used for everything, then there is an other computer that is used as backup and burning out CD/DVD since the "main" computer don't do this.

My question is if it's possible to create a virtual desktop between a ubuntu desktop and a windows XP desktop that make it possible to control the computer from the windows computer and be able to burn a CD without having to do anything at the ubuntu computer?

---

### Post by albandy on 2008-12-16
There are a lot of possibilities:
1.- Remote gdm login: enabling gdm remote login in ubuntu and installing an X client (like x-mins) in the windows computer.
2.- Use VNC
3.- By command line using ssh
...

---

### Post by Locke_99GS on 2008-12-16
You can use VNC from either to the other, or you can tunnel X from the linux machine to windows/cygwin.

Another option would be to purchase an inexpensive KVM, to have two machines sharing a keyboard, monitor, and mouse that you can switch between easily.

---

### Post by Hospadar on 2008-12-16
You might want to look into [synergy]("https://help.ubuntu.com/community/SynergyHowto"), which sort of gives you the feel of having a double monitor machine where one monitor is XP and the other linux.  It shares your mouse, keyboard, and clipboard between the two.  This is the kind of set up you might want to have if you frequently use stuff on both machines.

Probably for you, a better choice would be rdp, it's a protocol you can set up on windows and then remotely log in to windows from your linux machine.  It's much better suited to occasional use than synergy, which involves a tighter coupling of machines.
You'll need to set up your windows machine to accept rdp connections, you'll have to google how to do that, then you can use rdesktop (command line tool) from ubuntu to log into your windows machine.\
EDIT:
my bad, I thought you were trying to control your xp machine with ubuntu.

To control your linux machine, I think the best way is with putty, ssh, and xming.
Install the "ssh" package on your linux machine, putty and xming on your windows machine, then use putty to connect to the windows machine and you can open up graphical applications through putty (with xming running, in putty you have to "forward X connections")

---

