---
title: "Juanty and Karmic CDROM held by /root"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Timbot2000 on 2010-01-07
Hi All

One big problem with Ubuntu, or with my install, is that the CD/DVD media are all held by the root in dev/scd0. This causes problems for example, when I insert an audio CD, and the player auto-opens, nothing plays or is displayed in the playlist, and If I attempt to select and open Audio CD I get the error "Cannot convert to folder as it is not local". 
Similar on other box trying to play a DVD, autorun movie player opens, but cannot play as it it does not have permissions to actually use the drive.  (it can however amnually play individual files within the DVD if browsed from desktop).
Not to pile on, but reasonably free access to the freaking media drives is a pretty basic design aspect, and right now my CD/DVD drives are basically useless in the normal login mode. 
Questions
1) How do I verify the permissions on these drives
2) How do I change the permissions on dev/scd0 so it will mount from other than /root
3) How do I log on as /root (I know the admin password

---

### Post by benfindlay on 2010-01-07
> **Timbot2000 said:**
> Not to pile on, but reasonably free access to the freaking media drives is a pretty basic design aspect, and right now my CD/DVD drives are basically useless in the normal login mode.
I don't know what the problem is, but this is NOT normal behaviour for ubuntu. What else have you installed/done to the system since you did your fresh install?

---

### Post by unmole on 2010-01-07
> **Timbot2000 said:**
> Hi All

One big problem with Ubuntu, or with my install, is that the CD/DVD media are all held by the root in dev/scd0. This causes problems for example, when I insert an audio CD, and the player auto-opens, nothing plays or is displayed in the playlist, and If I attempt to select and open Audio CD I get the error "Cannot convert to folder as it is not local". 
Similar on other box trying to play a DVD, autorun movie player opens, but cannot play as it it does not have permissions to actually use the drive.  (it can however amnually play individual files within the DVD if browsed from desktop).
Not to pile on, but reasonably free access to the freaking media drives is a pretty basic design aspect, and right now my CD/DVD drives are basically useless in the normal login mode. 
Questions
1) How do I verify the permissions on these drives
2) How do I change the permissions on dev/scd0 so it will mount from other than /root
3) How do I log on as /root (I know the admin password

NEVER ever login as the root. If you need root access to folders see [this]("http://www.psychocats.net/ubuntucat/rootlauncher/").

---

### Post by adam814 on 2010-01-07
On my system CD media auto-mounts under /media.

Could you post your /etc/fstab?

You don't need to login as root, just type sudo -s in a shell and you have a root shell.

---

### Post by Timbot2000 on 2010-01-07
> **adam814 said:**
> On my system CD media auto-mounts under /media.

Could you post your /etc/fstab?

You don't need to login as root, just type sudo -s in a shell and you have a root shell.


I get "Bash: etc/fstab Permission Denied"

It is definitely a permissions problem, and I know there is a solution, I just do not know the solution. If permissions can be denied, they can also be given.

---

### Post by Timbot2000 on 2010-01-07
> **unmole said:**
> NEVER ever login as the root. If you need root access to folders see [this]("http://www.psychocats.net/ubuntucat/rootlauncher/").
Thank you for the link. I will make use of it. However, I also need to know what to do once I have access.

---

### Post by Timbot2000 on 2010-01-07
> **benfindlay said:**
> I don't know what the problem is, but this is NOT normal behaviour for ubuntu. What else have you installed/done to the system since you did your fresh install?
Glad to know it is not normal, but it is nonetheless happening on both my boxes, Jaunty and Karmic. It is a permissions issue, and so is fixable, permissions cannot be denied if permissions cannot also be given.

---

### Post by benfindlay on 2010-01-07
To display your fstab in terminal, you need to type ```
cat /etc/fstab
```
Without cat, I get the exact same error as you, so I wouldn't judge that as further evidence of permissions problems. It looks like there is something more complicated going wrong than simple permissions. Have you installed anything not from the repositories, or done any significant work in the command line lately?

---

### Post by Timbot2000 on 2010-01-07
> **benfindlay said:**
> To display your fstab in terminal, you need to type ```
cat /etc/fstab
```Without cat, I get the exact same error as you, so I wouldn't judge that as further evidence of permissions problems. It looks like there is something more complicated going wrong than simple permissions. Have you installed anything not from the repositories, or done any significant work in the command line lately?


Corrected input: received "No such file or directory"

I would add I just mounted and used a data disk easily and successfully. I only seem to have problems with Audio and Video players not being able to read the directory

---

### Post by doas777 on 2010-01-07
ok; then try
```
sudo cat /etc/fstab
```

here is the cdrom line from mine:
[PHP]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/PHP]

the 'user' parameter is what I think you are missing.  I believe that it allows user mounts/unmounts and file access.

---

### Post by adam814 on 2010-01-07
+1

My /etc/fstab matches doas777's except that my raw device is /dev/sr0.  I had to check whether mine was set to auto or noauto.  If you don't have user in the line only root can mount it, which seems to be the problem you're having.

---

