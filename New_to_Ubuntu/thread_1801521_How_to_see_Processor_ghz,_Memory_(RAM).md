---
title: "How to see Processor ghz, Memory (RAM)?"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-07-10
Can someone tell me how to find this information? I know how to find the available RAM by going to System Monitor, but at the CPU section it doesn't tell me the processor specs. Where is this located?

---

### Post by patchwork on 2011-07-10
Open a terminal and type
```
sudo lshw|grep -i cpu
```

and enter your password as needed.

The lshw command in general will list your hardware.  More information can be found in the man pages```
man lshw
```

---

### Post by the.phantom on 2011-07-10
go to
applications
ubuntu software center
and install
system profiler and benchmark
will give you all the info on yopur whole system
in a easy to read format

and you can run benchmarks ( several) on your system 
and then if you click ( at the top) information and then 
network updater it will download and upload results and you can see how your system compaires against others


note after install it shows up under system tools

---

### Post by matt_symes on 2011-07-10
Hi

You might find a small variant on patchwork's post provides a bit more information.

```
sudo lshw -C cpu
```This will also provide information

```
cat /proc/acpi/processor/CPU*/*
```and so will the files under

```
/sys/devices/system/cpu/cpu*/
```depending on what you need to know.

There are also gui methods. sysinfo is small and sweet

```
sudo apt-get install sysinfo
```Kind regards

---

