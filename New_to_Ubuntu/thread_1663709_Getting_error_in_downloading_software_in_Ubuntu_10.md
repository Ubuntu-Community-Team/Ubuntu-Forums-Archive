---
title: "Getting error in downloading software in Ubuntu 10.10"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by sushilgupta on 2011-01-10
[IMG]http://www.freeimagehosting.net/uploads/35f8f09c67.png[/IMG]Hello everybody! I am a newbie of Open Source, and specially Ubuntu. I just installed ubuntu 10.10 on my Acer Aspire. After installing it, I tried to download softwares through "Ubuntu Software Center" present in the applications menu, but it doesn't opens. And I get some kind of error as shown in the image attached. Please help. Thanks in advance.

---

### Post by Bucky Ball on 2011-01-10
Can you do it manually?

Open a terminal (Applications >Accessories >Terminal) and type or paste this:

```
sudo apt-get update
```

If that works, run:

```
sudo apt-get upgrade
```

This last command will ONLY upgrade packages, NOT the OS.

---

### Post by sushilgupta on 2011-01-10
Again getting error  which is shown in the picture here in twitpic, [http://twitpic.com/3opgj7](http://twitpic.com/3opgj7) thanks for the help..

---

### Post by Bucky Ball on 2011-01-10
Try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```One command at a time. First command then hit enter, second command/enter.

Fix from post #4 here:

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by sushilgupta on 2011-01-10
> **Bucky Ball said:**
> Try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```One command at a time. First command then hit enter, second command/enter.

Fix from post #4 here:

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)


Thanks alot. This worked and now I am being able to update the software. ;)

---

### Post by Bucky Ball on 2011-01-10
Excellent! After running update one more time, run the 'sudo apt-get upgrade'. This will upgrade out-dated packages also. ;)

Enjoy the new OS, the learning curve, post back with new probs on a new thread, and please mark this one as 'solved' using 'thread tools'. :D

---

### Post by sushilgupta on 2011-01-10
Thanks.. ;)

Any suggestion for quick starting guide in Ubuntu like to customize and use some web developer application... etc!
Any links you would recommend?

Thanks again!

---

### Post by Bucky Ball on 2011-01-10
I use Kompzer myself. It is in the repositories (System >Admin >Synaptic Package Manager).

Filezilla for ftp to the server, also in repos. Just search there for them. ;)

There are plenty of guides about. Just Google: kompozer.

[http://kompozer.net/community.php](http://kompozer.net/community.php)

[http://www.charlescooke.me.uk/web/kz-ug-home.htm](http://www.charlescooke.me.uk/web/kz-ug-home.htm)

(Kompozer used to be called NVU)

Start a new thread on this topic if required. You will get a lot more help and more specific. ;)

---

