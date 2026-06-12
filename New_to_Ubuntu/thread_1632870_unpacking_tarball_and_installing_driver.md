---
title: "unpacking tarball and installing driver"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by pottzie on 2010-11-28
This comes from me posting in the networking part of the forum, but the question I have concerns tarballs. I have to install a driver for the wireless card I got, and the only thing I can come up with is a .tgz file. I found out that the file downloaded to tmp, and after changing to the tmp directory, I untarred the file using the zxfv command. Now what i need to find out is if I need to do something else to have to work with Ubuntu, like the make or makeinstall commands. I guess the file untarred while still in the temp directory, and what needs to happen to get it to work with my operating system?
 Thanks.

---

### Post by sikander3786 on 2010-11-28
Hi. First of all, it would be just better to get the drivers from Ubuntu Repositories. They might be available there....

Regarding tar.gz packages, nearly 99.99% packages come with an instructions file named Install or Readme. Search the extracted contents.

---

### Post by stmiller on 2010-11-28
What version of Ubuntu?
What is your wifi card?

Yeah compiling drivers from a tar ball is pretty much a last ditch effort. It's better to use drivers already provided that perhaps just need to be installed via the regular Ubuntu software repositories.

---

### Post by pottzie on 2010-11-28
Azio AWD102N, Ubuntu 10.10  The files in the terminal show RT2860, imagine that's the real chip driver.

---

### Post by sikander3786 on 2010-11-28
> **pottzie said:**
> Azio AWD102N, Ubuntu 10.10  The files in the terminal show RT2860, imagine that's the real chip driver.
If you can connect via an ehternet cable, the drivers might pop up under System > Administration > Additional Drivers/Hardware Drivers.

---

### Post by pottzie on 2010-11-28
I'm connected now with my older g wireless usb. I have the AWD102N installed to the pc  also. It's a pcmi card, so I have both the usb and pcmi plugged in. Nothing poped up saying that other driver were needed or available. When I turned on the computer after installing the Azio, all that happened was that Network Manager didn't show any available networks.

---

### Post by sikander3786 on 2010-11-28
I found a guide here.

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by pottzie on 2010-11-28
Man..that's a lot of hoops to jump through! I'll do/try it if i have to, though. When I searched this, I noticed that a lot of peolpe needing this were EeeBox users. and there were several places saying that Railink's linux driver support was very poor. Lucky me!
 This is the second N receiver I've tried to install. I bought a Linksys usb600n last night, and had the same, if not worse experience. Ubuntu said that it needed additional firmware, nonexistent from the repositories, and with a Railink driver. Does Railink "own" the N type wireless receiver market?

---

