---
title: "Wireless issue Ubuntu Mate 18.04"
date: 2019-10-10
forum: Networking &amp; Wireless
---

### Post by jmbell1989 on 2019-10-10
I am unable to see any wireless devices on my ThinkPad P53. I am able to connect to the internet via ethernet.. I have run the attached shell script provided here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) Below is the output.
[B][ATTACH]284170[/ATTACH]
[/B]

Any help is appreciated!

---

### Post by praseodym on 2019-10-11
```
52:00.0 Network controller [0280]: Intel Corporation Device [8086:2723] (rev 1a)
	Subsystem: Intel Corporation Device [8086:0080]
	Kernel modules: wl
```
Not (yet) supported by this kernel. Run

```
sudo apt-get remove --purge bcmwl-kernel-source
```

and see here

[https://ubuntuforums.org/showthread.php?t=2387339&page=2&p=13759604#post13759604](https://ubuntuforums.org/showthread.php?t=2387339&page=2&p=13759604#post13759604)

ALternatively, update to kernel 5.1

---

### Post by jmbell1989 on 2019-10-11
Thank you so much for the help. Ended up updating the kernel. Works like a charm!

---

### Post by praseodym on 2019-10-12
Updating the kernel is better, otherwise you need to compile again after a kernel update of 5.0

---

