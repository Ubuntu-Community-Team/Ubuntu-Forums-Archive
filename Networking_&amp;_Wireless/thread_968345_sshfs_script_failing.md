---
title: "sshfs script failing"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2008-11-02
I have a script that mounts all my computers media to my mythbuntu box at boot.  The problem is, it isn't mounting the drives.  It works fine once the computer is booted up, however.

I made a script to check where the source of the problem is:
```
echo 'Script begins' > /home/gregory/status.txt
echo 'Error Report:' >> /home/gregory/status.txt
sshfs steve@10.0.0.2:/home/steve/Music /var/lib/mythtv/music/steve 2>> /home/gregory/status.txt
sshfs steve@10.0.0.2:/home/steve/Videos /var/lib/mythtv/videos/steve 2>> /home/gregory/status.txt
sshfs kyle@10.0.0.3:/home/kyle/Videos /var/lib/mythtv/videos/kyle 2>> /home/gregory/status.txt
sshfs kyle@10.0.0.3:/home/kyle/Music /var/lib/mythtv/music/kyle 2>> /home/gregory/status.txt
echo 'Is SSHD Running?:' >> /home/gregory/status.txt
ps -ef | grep sshd >> /home/gregory/status.txt
echo 'Mounted drives:' >> /home/gregory/status.txt
mount >> /home/gregory/status.txt
echo ''
echo 'Script Completed!' >> /home/gregory/status.txt
date +%r >> /home/gregory/status.txt

```

I have since determined the problem is within networking not starting soon enough.  Here is output from the script:

```
Script begins
Error Report:
read: Connection reset by peer
Is SSHD Running?:
root      4821     1  0 14:13 ?        00:00:00 /usr/sbin/sshd
Mounted drives:
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
Script Completed!
02:13:14 PM

```

SSH gets a connection reset by peer. What can I do about this?  Can I make it so networking starts sooner than my script?

---

### Post by cariboo on 2008-11-02
How are you starting your script? if you are using rc.d, you can always give it a higher number than networking to get it to start after networking has started.

Jim

---

### Post by Hawk__0 on 2008-11-02
this is how I set it up, I stuck it in the /etc/init.d directory, and ran this on it:
sudo update-rc.d mount.sh defaults

---

### Post by Hawk__0 on 2008-11-04
bump

---

### Post by Hawk__0 on 2008-11-05
bump

---

