---
title: "HELP! iPod READ ONLY"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Archie69 on 2011-02-22
Hey,

I was hoping someone could help me. I have been using ubuntu for a while now and haven't had much issue. However, after about a year of being able to transfer music to and from my iPod to Rhythmbox I ran into an issue and had to restore my iPod back to factory settings. Long story short, Rhythmbox recognizes my iPod but will not allow me to transfer music or Podcasts to it.

I've tried using Amarock, no dice. I've tried using gtkpod, no luck. Rhythmbox was always fine but for whatever reason will not work now. Any ideas? I really want to get this thing to work. Any help would be great. 

I have a 120gb classic iPod (black)

---

### Post by mxFlush on 2011-02-22
I think maybe your ipod had a different firmware that Rhythmbox recognized and when you reset to factory it changed firmware.

---

### Post by Archie69 on 2011-02-22
Does that mean I can no longer get it back to being able to work with Rhythmbox?

---

### Post by Archie69 on 2011-02-22
Any ideas on how to fix this?

---

### Post by Archie69 on 2011-02-23
Other than gtkpod & Amarock what can I use to get this iPod not to be "read only"? I worked last week. Thats whats so annoying

---

### Post by Archie69 on 2011-02-27
So I was reading up on other posts and got this. To fix it i was supposed to write:

cat /etc/mtab

so this way I can find the dev. heres what I got:


marco@marco-laptop:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/marco/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=marco 0 0
/dev/sdb2 /media/ad9d8d8d-5968-32d8-9d75-14dd0dac72c1 hfsplus rw,nosuid,nodev,uhelper=udisks 0 0

I then type: dosfsk /dev/sdb2 -a
 
and nothing. Am I missing something?

---

