---
title: "Drivers Installed But...."
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by JHQ_623 on 2008-10-01
Ok i have the drivers installed but it still acts as if theres no adapter or card:confused:??
<a href="http://s66.photobucket.com/albums/h265/JHQ623/?action=view&current=Screenshot.png" target="_blank"><img src="http://i66.photobucket.com/albums/h265/JHQ623/Screenshot.png" border="0" alt="Photobucket"></a>

---

### Post by JHQ_623 on 2008-10-01
[IMG]http://i66.photobucket.com/albums/h265/JHQ623/Screenshot.png[/IMG]

---

### Post by cariboo on 2008-10-01
What is the output of in a Applications-->Accessories-->Terminal:

```
sudo iwconfig
```

also in the same terminal:

```
sudo lshw -C network
```

This will give us way more information than a picture. I know they say a picture is worth a thousand words, but in this case the picture doesn't tell us much, except that you have two network interfaces.

Jim

---

### Post by JHQ_623 on 2008-10-03
Alright here you go..

> lo        no wireless extensions.

eth0      no wireless extensions.

jhq@jhq-desktop:~$ sudo lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by JHQ_623 on 2008-10-04
Well im still learning but i think this means it not working..

---

