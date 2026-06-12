---
title: "boot.ini and grub setting"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by samizdatstudio on 2011-05-04
i installed  jolicloud 1.2 in my D drive,then i formate my c drive xp windows, and recovery the c:drive by ghost ,now my pc only can go insside jolicloud directly ,
it cant choose or priority go inside windows now ,what can i do to make it go inside windows? i see xp boot.ini is no menu choose for wither windows and jolicloud os

do i need what kind of setting to make it works?
need set both window boot.ini and jolicloud grub?
i see the grub folder there are no menu.lst file,
i need do the change on grub.cfg firstly to make me go inside window?
please help...thanks x 100!!

---

### Post by spikoley on 2011-05-06
You didn't state which version of Ubuntu you are running.  It sounds like you are using a version that uses Grub2, so I will give you things to try for Grub2.

Try updating grub to see if it fixes the issue.  Reboot after running the following command.

```
sudo update-grub
```

Grub2 uses /etc/default/grub to update the grub.cfg.  Use the command below to update grub.  After making changes to grub always run the update command above.

```
gksudo gedit /etc/default/grub
```

More on [Grub2]("https://help.ubuntu.com/community/Grub2").

---

### Post by samizdatstudio on 2011-05-07
since i use jolicloud 1.2, i no way to check what version ubuntu its use,also grub version.actually  i install the startup manager,it screen still cant show in gurb boot,after i force click esc buttom, the menu show out,
the jolicloud os force no show the boot screen and go jolicloud directly.
it solved now,thanks your help.

my fujitsu u810 works on default jolicloud os 1.2 and can use windows xp tablet too.
seem most tablet function on ubuntu system work fine  when using,
happy now

---

