---
title: "only root can play sounds"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by earthpigg on 2010-02-28
```
mike@mike-laptop:~$ sudo su
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@mike-laptop:/home/mike# aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
root@mike-laptop:/home/mike# exit
exit
mike@mike-laptop:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
mike@mike-laptop:~$ 

```

first one plays the sound fine, second one does not.

i have no idea how i managed this. this is typically caused by permissions, so i went nuts with /etc/group....

```
mike@mike-laptop:~$ cat /etc/group
root:x:0:root
daemon:x:1:root,mike
bin:x:2:root,mike
sys:x:3:root,mike
adm:x:4:mike,root
tty:x:5:root,mike
disk:x:6:root,mike
lp:x:7:root,mike
mail:x:8:root,mike
news:x:9:root,mike
uucp:x:10:root,mike
man:x:12:root,mike
proxy:x:13:root,mike
kmem:x:15:root,mike
dialout:x:20:mike,root
fax:x:21:mike,root
voice:x:22:root,mike
cdrom:x:24:mike,root
floppy:x:25:root,mike
tape:x:26:mike,root
sudo:x:27:mike,root
audio:x:29:pulse,mike,root
dip:x:30:mike,root
www-data:x:33:root,mike
backup:x:34:root,mike
operator:x:37:root,mike
list:x:38:root,mike
irc:x:39:root,mike
src:x:40:root,mike
gnats:x:41:root,mike
shadow:x:42:root,mike
utmp:x:43:root,mike
video:x:44:root,mike
sasl:x:45:root,mike
plugdev:x:46:mike,root
staff:x:50:root,mike
games:x:60:root,mike
users:x:100:root,mike
libuuid:x:101:root,mike
crontab:x:102:root,mike
syslog:x:103:root,mike
fuse:x:104:root,miket
mlocate:x:105:root,mike
ssh:x:106:root,mike
lpadmin:x:107:mike,root
sambashare:x:108:mike,root
admin:x:109:mike,root
messagebus:x:110:root,mike
avahi:x:111:root,mike
netdev:x:112:mike,root
haldaemon:x:113:root,mike
gdm:x:114:root,mike
pulse:x:115:root,mike
pulse-access:x:116:root,mike
nogroup:x:65534:
mike:x:1000:mike
ssl-cert:x:117:root,mike
avahi-autoipd:x:118:root,mike
couchdb:x:119:root,mike
saned:x:120:root,mike
Slmodemd:x:121:root,mikemike@mike-laptop:~$ 

```



any other suggestions?

---

### Post by earthpigg on 2010-02-28
update:

removing the pulse dotfiles temporarily fixes it:

rm -r ~/.pulse

...until the next reboot. sooo sound works, but i have to run that when i login. i have no idea why it is generating faulty dotfiles. alsamixer isn't muted, nor is it in the gui.

---

