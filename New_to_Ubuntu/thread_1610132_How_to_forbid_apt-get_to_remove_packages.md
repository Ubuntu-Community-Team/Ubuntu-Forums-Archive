---
title: "How to forbid apt-get to remove packages?"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by Mariane on 2010-10-31
Hi, 

I am trying to install C turtle following the instructions here: 
[http://www.ros.org/wiki/cturtle/Installation/Ubuntu](http://www.ros.org/wiki/cturtle/Installation/Ubuntu)

I was told to install ros-cturtle-pr2all

This package depends upon several others, among which:
ros-cturtle-common and libvtk5-dev
It won't install without having these 2. 

But When I install ros-cturtle-common it automatically removes libvtk5-dev and when I install libvtk5-dev it automatically removes ros-cturtle-common. 

I use command-line apt-get:
sudo apt-get install <package name>
I tried:
sudo apt-get build-dep ros-cturtle-pr2all
but then it tells me it cannot find the package. 
-f and -m don't help

sudo apt-get --no-remove install ros-cturtle-common
(with libvtk5-dev installed) says: "E: Packages need to be removed but remove is disabled" and stops. 

It looks like I need some kind of cheat. If I could install one of these 2 packages and then hide it somewhere where apt-get won't see it while I install the other it might work. 

Mariane

---

### Post by Hippytaff on 2010-10-31
Do you thin aptitude will be more succesful? I don't know if this will help but it's worth a try

---

### Post by Mariane on 2010-10-31
I don't know how to use it and I'm struggling enough not to feel inclined to learn it right now...

---

### Post by Hippytaff on 2010-10-31
I think

```

sudo aptitude install {packagename}

```

---

### Post by Mariane on 2010-10-31
This installs one but removes the other. 

Mariane

---

### Post by Hippytaff on 2010-10-31
So same result then...I don't know then...seems odd

---

### Post by Mariane on 2010-11-10
Bump

---

