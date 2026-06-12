---
title: "connecting dependencies"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by phanipalagummi on 2009-01-27
I have a splashy_0.3.10-1_i386.deb file on my desktop which when i installed i got a dependency problem saying
Error: Dependency is not satisfiable: libdirectfb-1.0-0

i tried doing even this sudo apt-get install libdirectfb-1.0-0 but i find no use

how do i connect this dependency

---

### Post by nothingspecial on 2009-01-27
> **phanipalagummi said:**
> I have a splashy_0.3.10-1_i386.deb file on my desktop which when i installed i got a dependency problem saying
Error: Dependency is not satisfiable: libdirectfb-1.0-0

i tried doing even this sudo apt-get install libdirectfb-1.0-0 but i find no use

how do i connect this dependency

I`ve got the package -

```
apt-cache search libdirectfb
[COLOR="Red"]libdirectfb-1.0-0 - direct frame buffer graphics - shared libraries[/COLOR]
```

Have you got all the repositories enabled in System > Administration > Software Sources?

---

### Post by nothingspecial on 2009-01-27
Speaking of which, I have splashy available also.

```
sudo apt-get install splashy
```

---

### Post by phanipalagummi on 2009-01-27
actually my basic doubt is how should we connect the dependencies of the softwares that were on my desktop.

I tried what you said but still i have problem

---

### Post by nothingspecial on 2009-01-27
If you install using using apt-get, add/remove or synaptic all dependencies will be installed also.

Dependencies get put in a certain place. All apps that require those dependencies should know where to look for them.

---

### Post by phanipalagummi on 2009-01-27
Well you said that dependencies will be installed pre in add/remove,synaptic etc..but what if i take some software from my friend (pen-drive)including there dependencies and wish to install in my system,how do i connect the dependencies among them,

actually if i type 

sudo apt-get update 

people say dependencies will connect among the softwares in the repositary,
but how do i connect the dependency among the softwares on my desktop

---

### Post by oldos2er on 2009-01-27
If you're not using the repositories, you'll need to download and install all the dependencies yourself.

---

### Post by wolfen69 on 2009-01-27
Here you go. [libdirectfb-1.0-0]("http://packages.ubuntu.com/intrepid/libdirectfb-1.0-0")

i'm assuming you're using intrepid. if not, just make the adjustment in the URL. download and click to install.

---

