---
title: "Copying from CDROM"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by vyas.subbu on 2010-11-17
Hi,

I am very new to linux.
I have just installed ubuntu server edition. I need to install Nagios the infrastructure monitoring software. I downloaded it, and  copied to DVD. 

But when I try to copy it on Ubuntu. I just could not make it work.

I did CD /dev ls -l cd*
And found CDROM is pointing to sr0.

I then did sudo mount /mount/sr0 and I could listen to cdrom being accessed, but it failed. with lot of lines

end_request: I/O  error, edv sr0, sector 13824

last line says mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab.

Can someone help?

---

### Post by ironic.demise on 2010-11-17
> **vyas.subbu said:**
> Hi,
 
I am very new to linux.
I have just installed ubuntu server edition. I need to install Nagios the infrastructure monitoring software. I downloaded it, and copied to DVD. 
 
But when I try to copy it on Ubuntu. I just could not make it work.
 
I did CD /dev ls -l cd*
And found CDROM is pointing to sr0.
 
I then did sudo mount /mount/sr0 and I could listen to cdrom being accessed, but it failed. with lot of lines
 
end_request: I/O error, edv sr0, sector 13824
 
last line says mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab.
 
Can someone help?
Try 
```
mkdir ~/Desktop/CD
mount /dev/sr0 ~/Desktop/CD
```
 
try sudo?

---

### Post by vyas.subbu on 2010-11-17
Thank you very much. 
I did give an error but also mounted it. I could see the files now.

Thanks for your help again.

---

### Post by ironic.demise on 2010-11-17
> **vyas.subbu said:**
> Thank you very much. 
I did give an error but also mounted it. I could see the files now.

Thanks for your help again.

HAHA! Seriously?
Wow... Honestly, I didn't expect to be able to help, I'm still a bit of a newbie myself see.

Anyway, really glad to be of assistance, mark the thread as solved for other people and come back if you need anything else ;)

---

