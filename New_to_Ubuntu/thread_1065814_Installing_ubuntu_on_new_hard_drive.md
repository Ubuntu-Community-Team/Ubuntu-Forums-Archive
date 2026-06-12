---
title: "Installing ubuntu on new hard drive"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by bobn on 2009-02-10
hello all, new beginner here, i mean im as green as it gets. just obtained ubuntu 8.10  desktop edition and the server edition. I have a new formatted fat 32 quantum harddrive(30 gb) i picked up off ebay totally clean and want to install ubuntu on this new harddrive for kids pc.starting from scratch.So what are the step by step online sites to download,install,partition  ubuntu onto a new harddrive or will the disk just talk me through it? thanks!.....told ya i was green! LOL!:lolflag:also i intend to go wireless in about a week or so starting point my pc to kids pc, i have windows xp and kids will have ubuntu, will this be compatable for them to still connect to internet with two different programs?

---

### Post by LowSky on 2009-02-10
ubuntu live cd can handle thinstallation and partitioning very easily

its easier than installing windows XP
connecting to the interweb will be fine

---

### Post by bobn on 2009-02-10
is the live cd the same as the ubuntu 8.10 desktop edition disc i explained i have.? or a different one i need? thank you!

---

### Post by sydbat on 2009-02-10
> **bobn said:**
> is the live cd the same as the ubuntu 8.10 desktop edition disc i explained i have.?Yes.

---

### Post by boof1988 on 2009-02-10
> **bobn said:**
> ...also i intend to go wireless in about a week or so...

Getting the wireless to work/connect may take a little bit of jumping-through-hoops.  It depends on your hardware.

One way to get (some of) the wireless hardware info is go to (while booted into the LiveCD) ***Applications >> Accessories >> Terminal*** then type the following and press enter.

To display some PCI stuff:
```
lspci
```

To display some USB stuff:
```
lsusb
```

There have been instances (but I don't know why) when I have had to use the "lsusb" twice for my hardware to show up.

If you want to post the results here then hopefully someone can help more with the wireless networking (if you need any help with it).

These commands will output more lines than just the network hardware.  The network line from "lspci" for my system (wired connection) is (for camparison purposes only):
```

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
```

---

