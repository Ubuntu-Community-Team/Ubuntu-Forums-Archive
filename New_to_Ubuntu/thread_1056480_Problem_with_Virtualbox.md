---
title: "Problem with Virtualbox"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by eilios on 2009-01-31
Hello, you may remember me as that intelligent newbie ;), I decided to try virtualbox and enjoyed running Ubuntu 8.10 with it, it was easy to install, and fun to use, I liked how it looked, except my resolution is stuck at 800x600 and I have no way of changing it, not through virtualbox, nor the preferences.

---

### Post by Simian Man on 2009-01-31
You have to install the Guest Additions inside the guest system.  It is easy to do and google should turn up a guide.

---

### Post by eilios on 2009-01-31
I've tried those, they don't seem to work with me. I have used the sudo commands they said, the guest addition works fine, the sudo command doesn't. I presume it is due to the fact I am using 8.10, but I am not 100% sure. Maybe I did something wrong?

---

### Post by albinootje on 2009-01-31
> **eilios said:**
> I've tried those, they don't seem to work with me. I have used the sudo commands they said, the guest addition works fine, the sudo command doesn't. I presume it is due to the fact I am using 8.10, but I am not 100% sure. Maybe I did something wrong?

You should mount the Guest Addition cdrom, and make sure that you have the package "build-essential" installed in your Ubuntu guest VM.

Here's an old, quick and (esp.) dirty howto :
[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

### Post by eilios on 2009-01-31
> **albinootje said:**
> You should mount the Guest Addition cdrom, and make sure that you have the package "build-essential" installed in your Ubuntu guest VM.

Here's an old, quick and (esp.) dirty howto :
[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)
I changed to the directory, and to my dismay nothing happened. So, I tried to use what it actually looks like - nothing.


Edit: I'll post a screenshot, maybe somebody can help me better with some info?

---

### Post by eilios on 2009-01-31
[http://img231.imageshack.us/img231/5001/helpaz1.png](http://img231.imageshack.us/img231/5001/helpaz1.png)

There's the image, it's where the CD is, and the name. What would the command be?

---

### Post by albinootje on 2009-01-31
> **eilios said:**
> 
There's the image, it's where the CD is, and the name. What would the command be?

Okay, type in the terminal :
```

cd /media/VBOX

```
press <tab>
and hit enter.
Then run :
```

sudo apt-get update
sudo apt-get install build-essential
sudo ./VboxLinux*

```

---

### Post by johnjohn2 on 2009-01-31
> **albinootje said:**
> Okay, type in the terminal :
```

cd /media/VBOX

```
press <tab>
and hit enter.
Then run :
```

sudo apt-get update
sudo apt-get install build-essential
sudo ./VboxLinux*

```

Worked for me. Thanks

---

### Post by eilios on 2009-01-31
> **albinootje said:**
> Okay, type in the terminal :
```

cd /media/VBOX

```press <tab>
and hit enter.
Then run :
```

sudo apt-get update
sudo apt-get install build-essential
sudo ./VboxLinux*

```
It says no such file or directory.

---

### Post by albinootje on 2009-01-31
> **eilios said:**
> It says no such file or directory.

Can you make a screenshot of that ?

---

### Post by eilios on 2009-01-31
[img]http://img218.imageshack.us/img218/2261/screenshotbr8.png[/img]

Here you go.

---

### Post by albinootje on 2009-01-31
> **eilios said:**
> Here you go.

Thanks.
Are you saying that after typing "cd /media/VBOX" and then hitting the <tab> key there's no name completion ?

Can you show the output of :
```

mount
ls /media

```

---

### Post by eilios on 2009-01-31
> **albinootje said:**
> Thanks.
Are you saying that after typing "cd /media/VBOX" and then hitting the <tab> key there's no name completion ?

Can you show the output of :
```

mount
ls /media

```
You solved the problem for me :)

It was being called "cdrom0", not VBoxlinux for some odd reason.

Your advice is working now.

---

