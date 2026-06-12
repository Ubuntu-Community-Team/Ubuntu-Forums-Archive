---
title: "Can I clone a Ubuntu system from one hard drive to another?"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by bwallum on 2010-04-21
Hi

I want to remove a system from a failing hard drive and put it on a new hard drive.

Is there a way of simply 'cloning' the system?

I appreciate that the two devices will have different UUIDs. What problems would this create, if any?

---

### Post by BillyBoa on 2010-04-21
Maybe is better to just clone your /home. Then make a fresh installation and use your old /home. Look here:
[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html")

---

### Post by pavel989 on 2010-04-21
dd is the command you want
```
dd if=/orig of=/newdrive
```

methinks theyre supposed to be sda's. im not sure. do research before u type that in. 

```
man dd 
```

should tell u more

---

### Post by Sef on 2010-04-21
Check out [Clonezilla]("http://clonezilla.org").

---

### Post by rcayea on 2010-04-21
I would like to chime in...

I recently used clonezilla. It worked great and the compression was decent (gzip). I didn't want to wait the amount of time it would have taken to use bzip2 to compress so my question is related to a previous suggestion. 

My 500GB HD using 188GB of space took 2.5 hours and it was only compressed down to about 160GB. Does anyone know how much bzip2 would compress 188GB to?

---

### Post by HarrisonNapper on 2010-04-21
> **bwallum said:**
> Hi

I want to remove a system from a failing hard drive and put it on a new hard drive.

Is there a way of simply 'cloning' the system?

I appreciate that the two devices will have different UUIDs. What problems would this create, if any?

An important part of this is what exactly you mean by "failing hard drive". I wouldn't assume there would be any issues in copying everything over as long as there's not anything on the new drive and it has the same filesystem. Then again, I don't know which applications expect the UUID, so as was mentioned, installing fresh and copying /home and /etc should be fine from a basic desktop end-user standpoint.

---

### Post by Sir Jasper on 2010-04-21
Hi,

If your new drive is larger than your old one the free version of HDClone should be ideal and I believe the new drive should work without any uuid adjustment.

My regards

---

### Post by bwallum on 2010-04-21
Thanks everybody! I have to say dd looks exciting. I'm off for a bit of trial and error...

---

