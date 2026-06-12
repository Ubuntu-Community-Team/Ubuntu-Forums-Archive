---
title: "Linksys WUSB54G (rt2570) question"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by tdizz on 2008-06-25
I haven't been able to find a solution to this problem. I am trying to install the patched rt2570 drivers from [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/).

However, make gives me the following error:

```
tom@tom-laptop:/usr/src/rt2570-k2wrlz-1.6.1/Module$ sudo make && make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/src/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o
/usr/src/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c: In function &#8216;usb_rtusb_probe&#8217;:
/usr/src/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1964: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/usr/src/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1984: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
/usr/src/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:2015: error: too few arguments to function &#8216;first_net_device&#8217;
make[2]: *** [/usr/src/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/usr/src/rt2570-k2wrlz-1.6.1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

```

I'm sort of new at this, any help at all would be greatly appreciated.

---

### Post by chili555 on 2008-06-25
Please see post #3 here: [http://ubuntuforums.org/showthread.php?t=838124&highlight=rt2570](http://ubuntuforums.org/showthread.php?t=838124&highlight=rt2570)

---

### Post by tdizz on 2008-06-25
No go on those, either. make install completes, then modprobe gives an error, saying the module is not found.

```
tom@tom-laptop:~/rt2570-cvs-2008062520/Module$ sudo make install
2.6 module install
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/tom/rt2570-cvs-2008062520/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  INSTALL /home/tom/rt2570-cvs-2008062520/Module/rt2570.ko
  DEPMOD  2.6.24.3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for rausb0
tom@tom-laptop:~/rt2570-cvs-2008062520/Module$ modprobe rt2570
FATAL: Module rt2570 not found.

```

---

### Post by chili555 on 2008-06-26
It works for me when I do:```
**sudo** modprobe rt2570
```

---

### Post by tdizz on 2008-06-26
Doesn't matter either way; still gives Module rt2570 not found.

---

### Post by chili555 on 2008-06-26
After you:```
sudo updatedb
```and let it think a few moments, does:```
locate rt2570.ko
```give an entry like this?```
/lib/modules/2.6.24-19-generic/extra/rt2570.ko
```I am wondering if it actually got installed in the right spot, although I can't imagine a reason why not.

This is about the only compile I have done in months, and I do quite a few, that made, installed and modprobed without a single warning.

---

### Post by tdizz on 2008-06-27
It gives:

```
tom@tom-laptop:~$ sudo updatedb
[sudo] password for tom: 
tom@tom-laptop:~$ locate rt2570.ko
/home/tom/rt2570-cvs-2008062520/Module/.rt2570.ko.cmd
/home/tom/rt2570-cvs-2008062520/Module/rt2570.ko
/lib/modules/2.6.24.3/extra/rt2570.ko

```

I really appreciate your trying to figure this out. I'm usually not the type to have to ask for help; I'm pretty good about figuring things out. This has had me completely stumped, though.

---

### Post by acad1 on 2008-06-27
[http://ubuntuforums.org/showthread.php?t=797823&page=4](http://ubuntuforums.org/showthread.php?t=797823&page=4)

Have you tried installing as per the above - post# 34 I think.

This has worked for me.

---

### Post by tdizz on 2008-06-27
Yup, that's pretty much step for step what I did.

---

### Post by acad1 on 2008-06-27
[http://ubuntuforums.org/showthread.php?t=739139&page=3](http://ubuntuforums.org/showthread.php?t=739139&page=3)

Here is another link to installing rt 2570 which got me up and running initially. I also installed "rutilt"

---

### Post by chili555 on 2008-06-27
tdizz-

I don't quite understand this. You compiled with the kernel headers for:> Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
However, the module shows up in:> /lib/modules/2.6.24.3/extra/rt2570.koWhere did kernel 2.6.24.3 come from? 

In any case, we can probably cheat this up a bit by copying the module to the 2.6.24-19-generic location:```
sudo cp /lib/modules/2.6.24.3/extra/rt2570.ko /lib/modules/2.6.24-19-generic/extra/rt2570.ko
sudo depmod -a
sudo modprobe rt2570
```Let us know.

---

### Post by acad1 on 2008-06-27
chili555,
You asked "Where did kernel 2.6.24.3 come from?"

I note that 2.6.24.3 is mentioned in post #3 i.e
DEPMOD 2.6.24.3

I am interested in seeing the final resolution to this problem. My knowledge of linux is very limited so am learning all the time!

---

### Post by tdizz on 2008-06-27
chili: That did it, thanks a lot bro.

I've never had that happen before compiling something.

---

