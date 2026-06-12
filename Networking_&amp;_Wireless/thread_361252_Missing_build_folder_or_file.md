---
title: "Missing build folder or file"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by skywatcher on 2007-02-14
Hi

I have been following Tazz-Tux's guidelines (MyASDL forum) for setting up my 3G card. Everything went well until I tried to compile the driver by running the commands

make clean && make

This went OK until I got this message:
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory. Stop.

When I look under /lib/modules/2.6.15-23-386/ there is no 'build'

Please can someone help me out here.

Thanks

---

### Post by spd106 on 2007-02-14
Hi, check that you have the kernel headers installed. These should have been installed along with the build-essential package.

If you already have them, then check that there is a symlink from the /lib/module/2.6.15-28/build directory to the /usr/src/linux-headers-2.6.15-28/ directory. If not you should be able to add it with this command ```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/module/`uname -r`/build
```

---

### Post by skywatcher on 2007-02-14
Hi spd106

My /usr/src directory is empty??

---

### Post by wydra on 2007-11-18
I'm having the same problem. Anyone?

---

### Post by spd106 on 2007-11-19
Oops, looks like I forgot about this thread some time ago, sorry skywatcher.

To get the kernel sources you need to install the linux-headers-* packages for your kernel version. They should be automatically linked to the build folder, though this wasn't always done pre-Dapper.

Try Synaptic 

or this command for the 386 kernel (there's also 686, smp and server versions).
```
sudo aptitude install linux-headers-386
```

---

