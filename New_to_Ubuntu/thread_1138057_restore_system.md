---
title: "restore system"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by amirncomputing on 2009-04-26
hi i disselect the io services from system->admin->services and i dont have mouse and keyboard rightnow for login i dont know what shoud i do please help me

---

### Post by cariboo on 2009-04-26
You could try starting in recovery mode and starting dbus.

Press esc at the grub menu and select recovery mode, once at the menu drop to a root prompt and start dbus.

```
/etc/init.d/dbus start
```

once the service has started you should be able to continue on to your desktop by typing exit at the prompt then selecting resume.

---

### Post by amirncomputing on 2009-04-27
hi sir
i cant understand well because i am new in ubuntu
please explain more how can go from recovery mode to dbus and what command need for /etc/...

---

### Post by nothingspecial on 2009-04-27
Restart your computer. At the very begining it will say something like "grub loading press Esc for menu".

Press escape. It will give you the option to boot into a failsafe terminal (something like that). Type exactly this

```
/etc/init.d/dbus start
```

Then type 

```
exit
```

Hopefully you will be able to continue as normal from there.

---

### Post by amirncomputing on 2009-04-28
hi before boot i press esc but appeare :
[FONT=Times New Roman][SIZE=3]Kernel 2.6.27-7-generic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Kernel 2.6.27-7-generic(recovery mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Memtest86+[/SIZE][/FONT]
nothings else 
and also i wrote /etc/init.d/dbus start  in command line ubuntu  but it did'nt work 
what should i do?

---

### Post by sahabcse on 2009-04-28
In the system boot time press +ESC then select Kernel 2.6.27-7-generic(recovery mode). After that it will boot to the recovery mode. there you run the command 
/etc/init.d/dbus start

---

### Post by amirncomputing on 2009-04-29
hi i do that but it work just on recovery mode after restart the system doen'nt work agian what should i do? when i select communication dbus in system->admin->services but no select and no work
thanks everybody to help me

---

