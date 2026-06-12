---
title: "How to connect to shared foled on win10 pc automatically?"
date: 2020-05-20
forum: Networking &amp; Wireless
---

### Post by chrisnk on 2020-05-20
Hi!
Here is what I try to do on Lubuntu latest ver.:
When I open Caja and click to "Browse Network" then to the desired pc where are my folders shared on windows I have to log in.
Then everything is fine.

Here is how I do the command from terminal, but I wish to do that on boot time:
**sudo mount -t cifs -o username=xxx,password=xxx //192.168.0.100/temp //home/lubuntu/mnt/winshare/**

So, how can I achieve this on boot up time when Lubuntu is booting up but without to do the login etc. manually by me?
Maybe a better solution for me would be to mounting through schedule task manager like When.
But I again stumbled into a problem to enter the pass for sudo...

btw. I don't care about the security cos the pc is not on the Internet, and this is just for learning purpose.

Thank you.

---

### Post by webaake on 2020-05-20
A line in the file /etc/fstab is your answer.

Like so:```
//servername/sharename  /media/windowsshare  cifs  username=msusername,password=mspassword,iocharset=utf8,sec=ntlm  0  0
```

---

### Post by webaake on 2020-05-20
More info here:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by Morbius1 on 2020-05-20
>  **sudo mount -t cifs -o username=xxx,password=xxx //192.168.0.100/temp //home/lubuntu/mnt/winshare/**
In /etc/fstab that becomes:
```
//192.168.0.100/temp /home/lubuntu/mnt/winshare cifs username=xxx,password=xxx,uid=1000 0 0
```

Do not use sec=ntlm. If your Win10 machine is up to date it will have no idea what that means.

Notes:

Most Linux desktop systems mount things in fstab before the network stack is functional at boot resulting in the cifs mount being attempted before it's able to connect to anything. A way around this problem is a systemd automount. To do that:

[1] It's best to have a mount point outside your home directory or under /media so I would suggest something under /mnt:
```
sudo mkdir /mnt/winshare
```
[2] If your share is mounted unmount it. If you managed to mount it manually unmount that:
```
sudo umount /home/lubuntu/mnt/winshare
```
[3] Then the line in fstab would look like this:
```
//192.168.0.100/temp /mnt/winshare cifs username=xxx,password=xxx,uid=1000,noauto,x-systemd.automount 0 0
```
[4] Run the following commands to make systemd happy:
```
sudo systemctl daemon-reload
```
```
sudo systemctl restart remote-fs.target
```
Now go to /mnt/winshare to verify its contents.

A systemd automount mounts on contact ( when you access the mount point ) not at boot.

---

### Post by chrisnk on 2020-05-20
**_webaake_**:
Thank you so much for the nice link and explanation.

_**Morbius1**_:
Thank you very much for your very valuable writing and explanation.

You helped me a lot, your writing helped me to solve my problem.
It is working like a charm and I learned so much new.

Thank you very much!
My best regards.
Chris.

---

