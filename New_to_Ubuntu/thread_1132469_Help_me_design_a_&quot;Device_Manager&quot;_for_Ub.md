---
title: "Help me design a &quot;Device Manager&quot; for Ubuntu!!!"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-21
i decided take it upon my self to implement this idea: 

[http://brainstorm.ubuntu.com/idea/19278/](http://brainstorm.ubuntu.com/idea/19278/)
(which was found to be similar to this idea: [http://brainstorm.ubuntu.com/idea/17321/](http://brainstorm.ubuntu.com/idea/17321/))

everyone else thinks linux is fine. [I]"why do you need that? we have blahblahblah. just edit the config file with a text editor"
[/I]
where others see linux as fine as it is, i see it as having a lot of room for drastic improvements. 

i'm trying to learn python. it seems to be the easiest to learn. does anyone know of any other language that would be better suited for making an Ubuntu app???

---

### Post by ugriffin on 2009-04-21
1) You posted in the wrong section dude.

2) If you are so desperate for a device manager, get Kubuntu. It has one already.

```

sudo aptitude install kubuntu-desktop

```

Just should you want it ;)


EDIT: As a third option, browser for device managers with Synaptic.

---

### Post by jsowoc on 2009-04-21
I agree that Python is easier to learn than other languages, and if you don't know any languages, it might be a good 1st one.

However, most of the GNU Operating System is written in C/C++. I checked that Synaptic Package Manager is written in C/C++. If your app is going to be licensed under the GNU GPL (as most of GNU/Linux programs), you could easily (legally) take what you need from Synaptic and build on it.

---

### Post by asuastrophysics on 2009-04-23
> **ugriffin said:**
> 1) You posted in the wrong section dude.

2) If you are so desperate for a device manager, get Kubuntu. It has one already.

```

sudo aptitude install kubuntu-desktop

```

Just should you want it ;)


EDIT: As a third option, browser for device managers with Synaptic.

thanks ugriffin, i downloaded a device manager from synaptic. 
i think it's a good start for me to build off of, but as it is now, the device manager is a joke :lolflag: and really needs overhauling.

has anyone heard of kommander editor? will it create programs in python and c++?

---

### Post by ugriffin on 2009-04-23
I suggest you use CodeBlocks for C++ development, and search for Python IDEs under Synaptic.

If you need help with CodeBlocks just give me a PM.

---

### Post by asuastrophysics on 2009-04-26
thanks for the help guys. i will be releasing ubuntu's new and official driver central soon :popcorn:

i might need help along the way. if i do, i will come back and post

---

### Post by asuastrophysics on 2009-04-28
do you know what i just realized???

linux doesnt need a device manager (well, it does, just not one with an "update driver" function)

apparently, (i've only just plunged into ubuntu january) all the drivers linux needs are included in the kernel. when you update the kernel, you update all the drivers with it. neat! :guitar:

however, i still think that my device manager will include an option that will let you install/update GRAPHICS drivers, as these never seem to work quite out of the box

---

