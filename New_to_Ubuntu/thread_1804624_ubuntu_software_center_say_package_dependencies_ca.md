---
title: "ubuntu software center say package dependencies cannot be resolved ?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by mj360 on 2011-07-14
i read up on how to fix this, i tried sudo apt-get-f install i tried restarting my pc,
oh and when i when i tried to install something on the ubuntu software center now to say.

items cannot be installed or removed until the package catalog is repaired. do you want to repair it now? 

so i hit repair it does noting but keep saying the same thing. anyone know how to fix this ?

---

### Post by wildmanne39 on 2011-07-15
> **mj360 said:**
> i read up on how to fix this, i tried sudo apt-get-f install i tried restarting my pc,
oh and when i when i tried to install something on the ubuntu software center now to say.

items cannot be installed or removed until the package catalog is repaired. do you want to repair it now? 

so i hit repair it does noting but keep saying the same thing. anyone know how to fix this ?Hi, try 
```
sudo apt-get update
```
If you get errors post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by sikander3786 on 2011-07-15
For fixing any broken packages, after running the command mentioned in teh above post, run these commands one-by-one and post the complete outputs please:

```
sudo dpkg --configure -a
sudo apt-get install -f
```

We need to see the outputs.

---

### Post by mj360 on 2011-07-15
thanks for y'all help. just to be sure i understand. you what me to put in

sudo apt-get update first ? and then put

sudo [dpkg]("http://en.wikipedia.org/wiki/Dpkg") --configure -a sudo apt-get install -f
right ?

---

### Post by sikander3786 on 2011-07-15
Yeah, all of these one-by-one, after the previous command finishes its job.

```
sudo apt-get update
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

---

### Post by raja.genupula on 2011-07-15
hey 

 execute the commands as he has given
one by one

---

### Post by mj360 on 2011-07-15
i tried it and it still say package dependencies cannot be resolved ?

---

### Post by wildmanne39 on 2011-07-15
> **mj360 said:**
> i tried it and it still say package dependencies cannot be resolved ?Hi, did it tell you what package has unmet dependencies?

---

### Post by sikander3786 on 2011-07-16
> **mj360 said:**
> i tried it and it still say package dependencies cannot be resolved ?
Unless we see the outputs, we can do nothing.

---

### Post by mj360 on 2011-07-16
well when i tried this it say

0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded. ?

---

### Post by amjjawad on 2011-07-16
> **mj360 said:**
> well when i tried this it say

0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded. ?

From Terminal, run this command:

```
sudo apt-get clean

```
then

```
sudo apt-get update
```

After you run sudo apt-get update, post the output here and wrap up the text with CODE tags or highlight the output and click on "#".

---

### Post by sikander3786 on 2011-07-17
> **mj360 said:**
> well when i tried this it say

0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded. ?
Considering the outptut, I can't spot any errors in there. It is possible though that you are having dependency problems with some specific package that whenever you try to install it, there is an error. If this is the case, go to Terminal and run:

```
sudo apt-get install <package-name>
```

---

### Post by crunchy_chicken on 2012-01-13
had some issues with this as well and this is what i get for errors after running sudo apt-get clean and sudo apt-get udate.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Sources
  404  Not Found [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Sources
  404  Not Found [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Sources
  404  Not Found [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Sources
  404  Not Found [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main i386 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe i386 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.181 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

here is what i did to fix it:
Try
  sudo apt-get update   to update your package list. Then
  sudo apt-get autoclean   to clean up any partial packages. Then
  sudo apt-get clean   to clean up the apt cache.
  sudo apt-get autoremove 
after running autoremove, it told me what package was broken and told me to use

sudo apt-get -f install

now everything is working. soooo...hope this helps anyone else who runs into this

---

