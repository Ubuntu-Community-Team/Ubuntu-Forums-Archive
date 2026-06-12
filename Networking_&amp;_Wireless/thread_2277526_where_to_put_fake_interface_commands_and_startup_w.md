---
title: "where to put fake interface commands and startup? which  file?"
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by eyaln on 2015-05-09
Hi, 

I finally succeeded in creating fake interfaces, from command line
it goes like this:
sudo /sbin/modprobe dummy numdummies=5
sudo /sbin/ip link set name eth10 dev dummy0
sudo /sbin/ip link set name eth11 dev dummy1
sudo /sbin/ip link set name eth12 dev dummy2

ifconfig -a confirms that interfaces were created

my problem:
I need this to happen at startup, when the system is coming up
so I followed some guy's advice to put the following line in /etc/modules 
dummy numdummies=5 (interface name and parameters)
which was a good advice
only I'm not sure where to put the other lines:
/sbin/ip link set name eth10 dev dummy0
/sbin/ip link set name eth11 dev dummy1
/sbin/ip link set name eth12 dev dummy2

I tried creating a file named /etc/modprobe.d/dummy.conf and place these commands there
only it seemed that this file was never executed at startup...

any ideas?

thanks

---

### Post by kerry_s on 2015-05-09
did you make it executable ? (sudo chmod +x /etc/modprobe.d/dummy.conf)

---

### Post by eyaln on 2015-05-10
unfortunately,changing dummy.conf into executable (+x) didn't help

---

### Post by kerry_s on 2015-05-10
maybe try putting the commands in /etc/rc.local

---

### Post by eyaln on 2015-05-10
Hi,

I tried both:
[COLOR=#000000]/etc/modprobe.d/dummy.conf
[/COLOR][COLOR=#000000]/etc/modules-load.d/dummy.conf
both files with x permission

How can I know if these files were executed at startup?

BTW:
if I execute these files AFTER system has come up, it's working
so I know I'm pretty close...

[/COLOR]

---

### Post by eyaln on 2015-05-10
thanks, putting these commands in /etc/rc.local really helped, it's working,thanks!!

However, seems to me (and I may be wrong) that the idea of the people who designed the linux architecture
was to put these specific lines in /etc/modules and /etc/modprobe.d/dummy.conf
so if someone has some ideas as to how can I figure out if these files were executed during startup and what's wrong there
I'd really like to hear your ideas...

---

### Post by kerry_s on 2015-05-10
sorry was busy creating a windows 10 usb installer for my nephew. just upgraded his laptop to 8gb ram & a 60gb ssd drive. all so he can get better gaming. lol

i'm sure it's just a matter of putting the right command in /etc/modules. i've looked in mine, it's empty so there's no example of what format to use.
i'm using xubuntu 15.04 so there might be some miner differences compared to yours. for example looking on mine, i would have put the commands in  my session autostart or /etc/xdg/autostart.

---

### Post by tgalati4 on 2015-05-10
```
modinfo dummy
```

Shows only one parameter (numdummies), so that is the only parameter that you can include in either /etc/modules or in a configuration file.  The other commands are actually *ip*, which you would need to run in either rc.local or modify a networking script.  Because networking depends on timing of the other parts of the system, you would need to study the arrangement of the bootup scripts in /etc/rc5.d, /etc/init.d, and /etc/default.  

If you modify an existing script, you may break something or your changes will get wiped out during an update.

---

