---
title: "boot up problem"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by broekskw on 2008-12-16
funning thing that just started today, have ubuntu 8.04 and winxp on a dual boot dell, it's been going good for the last month or so but just this afternoon when i boot into ubuntu( main and swap partition on drive c and other on a external usb drive) after the ubuntu screen comes on it turns off my external usb drive power switch and then it fails to boot up because it can't access the files needed to boot up,at the end i have a window command line to input a command?? not sure what to input to get it to restart??:confused:

any help, all i have done is do updates when it tell me that there is updates to install

---

### Post by broekskw on 2008-12-16
here is the error message that i get

"checking file system 1179
fsck 1.40.8 (13 mar-2008)
stopping ntp server ntpd
fsck.ext3: unable to resolve
uuid=cfdb7e5c-4ebo-407c-bbb5-1d46df8a2354
fsck died with exit status 9

then some more messages before it tells me to "control-d to restart "

so i then turn on the usb h/drive and then do a  control d then system then boots up ok

so how come my usb h/drives shuts off when ubuntu is looking for the files on that h/drive to boot (when it starts to boot i can hear the h/drive spin then shut off):confused:

---

### Post by broekskw on 2008-12-17
o here is the rest of the error 

"file system check failed
a log is being saved in /var/log/fsck/checkfs
if that location is writable
please repair the file system manually
a maintenance shell will now start
control-d will terminate this shell & resume system boot
bash: no job control in this shell
bash: groups: command not found
bash: lseepipe: command not found
bash: command: command not found
bash: the: command not found
bash: dircolors: command not found
bash: command: command not found
bash: the: command not found
root@vandenbroeks-desktop:`#

thats it, so what do i have to do, manually fix this

if i reset my usb h/drive then hit the control d keys it loads up great,but this happens all the time i try to boot up in ubuntu

did not delete any files that i know of
help help do not want to do a reinstall:confused:

---

### Post by broekskw on 2008-12-17
ok i must not be the only one out there that has this problem
anyone have a sugestion as to what is causing this to happen and how to fix

thanks

---

