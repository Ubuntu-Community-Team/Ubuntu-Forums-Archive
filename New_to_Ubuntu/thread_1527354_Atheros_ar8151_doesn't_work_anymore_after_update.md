---
title: "Atheros ar8151 doesn't work anymore after update"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Elysius on 2010-07-09
Hi, I've got an acer timelinex 4820t laptop, it has an atheros ar8151  wired network card inside. With a fresh install of ubuntu 10.04, the card isn't recognized. 

From another _[thread]("http://ubuntuforums.org/showthread.php?t=1476231")_ I learned to install the driver, afther this is being done all works well.
I unpacked the driver followed by these commands:

```

sudo su
make install
modprobe atl1e
exit

```But afther I update ubuntu, since it's a fresh install it also installs a new linux-image, after this install the atheros card doesn't work anymore. I want to keep using the new kernel, but how can I re-enable the network card?

Just installing the driver again followed by modprobe doesn't work.

---

### Post by lkraemer on 2010-07-10
The previous instructions were:
```

mkdir AR81Family
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
sudo su
make install
modprobe atl1e
exit

```
So, if you followed those, and had it all working with the atl1e module,
you should be able to repeat the process.

1.  Be sure you have build-essential installed.
2.  Be sure you have the linux headers installed for the new Kernel
3.  Remove the module.
4.  Second compile the code again.
5.  Install the module.
 
In a Terminal Window (Console) Do:
```

lsmod
modprobe -r atl1e
lsmod

```
You should verify that atl1e is no longer installed.
then continue with:
```

cd AR81Family
make clean
make
sudo make install
sudo modprobe atl1e
sudo /etc/init.d/networking restart #(OR reboot)

```

That should get it working again.

---

### Post by nothingspecial on 2010-07-10
You will have to do this every time you get a new kernel.

---

### Post by Elysius on 2010-07-11
Thank you both for your replies. lkraemer it worked like a charm. What exactly does just "make" do? If I would skip that part, so just;

```

make clean
make install

```

Would it work as well? __

---

### Post by nothingspecial on 2010-07-11
Very simply, and not very accurately, "make" turns the source code into something that can be used by your computer, in the sense that it translates a human computer programming language into a language your computer can understand.

So yes, you need to do it.

---

