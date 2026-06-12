---
title: "my flash drive has this weird name"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by lolzwut on 2010-06-21
Hi,

I just bought a new flash drive (SanDisk 8 GB) and put some files from my /home directory onto it. After that I umounted it and took it out. I put it back in and look what it was named:


[IMG]http://i48.tinypic.com/24xjcax.png[/IMG]



what is that? I wouldn't have a problem with it but I can't access it through the
command line now. Look what it says: How can I fix this?


[IMG]http://i49.tinypic.com/2r2ri9w.png[/IMG]

---

### Post by tacotime on 2010-06-21
> **lolzwut said:**
> Hi,

I just bought a new flash drive (SanDisk 8 GB) and put some files from my /home directory onto it. After that I umounted it and took it out. I put it back in and look what it was named:


[IMG]http://i48.tinypic.com/24xjcax.png[/IMG]



what is that? I wouldn't have a problem with it but I can't access it through the
command line now. Look what it says: How can I fix this?


[IMG]http://i49.tinypic.com/2r2ri9w.png[/IMG]

just try remaining it, and instead of unmounting hit safely remove.

---

### Post by lolzwut on 2010-06-21
when i right click it it doesn't have a rename option. And I can't rename it in the shell because I don't know how to even specify it. That isn't even a real character I don't think..

---

### Post by ronnielsen1 on 2010-06-21
[IMG]http://i49.tinypic.com/2r2ri9w.png[/IMG]


Assuming copy and paste doesn't work, try gparted to repartition or rename

---

### Post by JoshuaaXD on 2010-06-21
You should just take everything on it save it all to a folder on your desktop then right click the drive format it and restart the computer for good measure.

---

### Post by tacotime on 2010-06-21
> **JoshuaaXD said:**
> You should just take everything on it save it all to a folder on your desktop then right click the drive format it and restart the computer for good measure.

yeah that's what i'd do then...

---

### Post by lolzwut on 2010-06-21
> **JoshuaaXD said:**
> You should just take everything on it save it all to a folder on your desktop then right click the drive format it and restart the computer for good measure.

That fixed it thanks! Hey just for the future do you know how to access directories with spaces in them through the terminal? I named it "New Volume" and it can't access it through the shell. I can just format again and rename it but I've had problems with that before is there a way?

---

### Post by tacotime on 2010-06-21
> **lolzwut said:**
> That fixed it thanks! Hey just for the future do you know how to access directories with spaces in them through the terminal? I named it "New Volume" and it can't access it through the shell. I can just format again and rename it but I've had problems with that before is there a way?

To navigate to it 


cd /media/New Volume 


should do the trick

---

### Post by sandyd on 2010-06-21
> **lolzwut said:**
> That fixed it thanks! Hey just for the future do you know how to access directories with spaces in them through the terminal? I named it "New Volume" and it can't access it through the shell. I can just format again and rename it but I've had problems with that before is there a way?
surround it in double quotes,
so ```
cd "New Volume"
```

---

### Post by lolzwut on 2010-06-21
THANKS! I can't thank you guys enough. I'm so happy, have a nice day. ):P

---

### Post by JoshuaaXD on 2010-06-21
Why are you opening it through terminal wouldn't right clicking or double clicking suffice? I had a problem with Ubuntu 10.04 LTS where it suddenly decided to stop mounting all of my storage devices, I think it is a bug, but I'm not sure. I downgraded back to 9.10 because of that.

---

### Post by tacotime on 2010-06-21
> **lolzwut said:**
> THANKS! I can't thank you guys enough. I'm so happy, have a nice day. ):P

No prob- that's what we're here for :lolflag: 

bai ):P

Also can you mark this thread as solved? That'd be awesome

---

