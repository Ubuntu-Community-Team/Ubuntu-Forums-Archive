---
title: "ubuntu 8.10 upgradation error."
date: 2009-08-18
forum: New to Ubuntu
---

### Post by pinku80 on 2009-08-18
Hi,
After I upgraded ubuntu 8.10 and installing the updates I am unable to log in to my system. This is the following problem I'm having.
 
[FONT=Times New Roman][SIZE=3]Boot from (hd0,9) ext3 9557a59a- ff9f -451b -95cd –b51fcd5c99dc[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Starting up…[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Loading, please wait…[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]usplash: Setting mode 1152×864 failed[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]usplash: Using mode 1024×768[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Gave up waiting for root device. Common problems:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-[/SIZE]         [SIZE=3]Boot args (cat/proc/cmdline)[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]   -Check root delay= (did the system wait long enough?)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]   -Check root= (did the system wait for the right device?)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]-   Missing modules (cat/proc/modules; ls/dev)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ALERT! /dev/disk/by-uuid/9557a59a- ff9f -451b -95cd –b51fcd5c99dc does not exist. Dropping to a shell![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]BusyBox v1.10.2 (ubuntu1:1.10.2-2ubuntu7) built-in shell(ash)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Enter ‘help’ for a list of built-in commands.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3](initramfs)[/SIZE][/FONT]
 
 
Please help me out with the problem.

---

### Post by ptn107 on 2009-08-18
Verify that 9557a59a-ff9f-451b-95cd-b51fcd5c99dc exists:
```
ls -l /dev/disk/by-uuid/
```

You should see 9557a59a-ff9f-451b-95cd-b51fcd5c99dc listed.  If not then you need to change /boot/grub/menu.lst to point to an existent root partition.

---

### Post by pinku80 on 2009-08-18
> **ptn107 said:**
> Verify that 9557a59a-ff9f-451b-95cd-b51fcd5c99dc exists:
```
ls -l /dev/disk/by-uuid/
```
 
You should see 9557a59a-ff9f-451b-95cd-b51fcd5c99dc listed. If not then you need to change /boot/grub/menu.lst to point to an existent root partition.
 
 
Thanks for the reply, but I would like to know how I would change that?
 
Also I would like to know how to get the data back from the ubuntu drive, incase I can't login?

---

