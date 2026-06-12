---
title: "Mount on startup Network Hardrive"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by gwu777 on 2008-05-11
Hi there, I have a network hardrive, Maxtor Shared Storage II, up til now, I am mounting it in termnial using:

sudo mount -t cifs //192.168.1.4/folder1 -o username=user,password=pass /home/user/maxtor

This way I have it in my home folder to access it for my documents.

It is all working fine, how can I do to have this same share mounted automatically by the system if I restart?

---

### Post by .rdg on 2008-05-11
> **gwu777 said:**
> Hi there, I have a network hardrive, Maxtor Shared Storage II, up til now, I am mounting it in termnial using:

sudo mount -t cifs //192.168.1.4/folder1 -o username=user,password=pass /home/user/maxtor

This way I have it in my home folder to access it for my documents.

It is all working fine, how can I do to have this same share mounted automatically by the system if I restart?

The simplest way would be adding the following line to /etc/fstab:

//192.168.1.4/folder1 /home/user/maxtor  cifs defaults,username=user,password=pass 0 1

If that doesn't work, just try mounting that share with a script, for example file /etc/init.d/maxtor-share:
#!/bin/bash
mount -t cifs //192.168.1.4/folder1 -o username=user,password=pass /home/user/maxtor
# end of file

One note to the mount above - no need for sudo, as it would be run by root on system start. That script would have to be executable, so in terminal write:

sudo chmod 775 /etc/init.d/maxtor-share

So it can be actually run. Finally, you would have to make it run on system start:

ln -s /etc/init.d/maxtor-share /etc/init.d/rc5.d/S100-maxtor-share

That should do it.

---

### Post by gwu777 on 2008-05-11
Thank you very much for the line of code, I have modified the fstab and it works perfectly. I haven't tried the script, I am not sure I would have been able to make it work, my knowledge is quite limited yet with ubuntu, but I am learning little by little, thank you very much.

---

### Post by .rdg on 2008-05-11
Not a problem - no need for scripting when it "Just works" with a simple fstab entry. Enjoy you Ubuntu ;)

---

### Post by gwu777 on 2008-06-21
Hi there, I thought I would keep updating this post as it relates to it... I manage to mount my network drive without problems, but I do not seem to have write access to it? I have done
```
sudo mount -t cifs //192.168.1.4/folder1 -o username=user,password=pass /home/user/maxtor

``` I don't know how I could get write access, if anyone as any idea it would be much appreciated...

---

### Post by gwu777 on 2008-07-05
Please, I am sure some of you can help me, How do I get write access on my network share?

---

