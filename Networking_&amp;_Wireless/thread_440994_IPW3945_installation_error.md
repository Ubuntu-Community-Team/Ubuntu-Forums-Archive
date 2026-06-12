---
title: "IPW3945 installation error"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by novakry on 2007-05-12
Hi,

I've been attempting to get the IPW3945 wireless drivers working on my laptop, so far everything is going well. I hit a snag when I got to installing the drivers.

I followed this code

"Now we install the firmware files (first finding where to install them):"

```
	% wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz .
	[COLOR="Red"]% DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
		/etc/hotplug/firmware.agent)[/COLOR]
	% tar xzvf ipw3945-ucode-1.14.2.tgz 
	% less ipw3945-ucode-1.14.2/LICENSE.ipw3945-ucode
	# cp ipw3945-ucode-1.14.2/ipw3945.ucode $DIR
```

The second line of code is where I get stuck, I'm not sure what its doing but I tried it anyway I get the following error.

```
james@ubuntu:~/Desktop/ipw3945-linux-1.2.0/ipw3945-1.2.0$ sudo DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" /etc/hotplug/firmware.agent)
sed: can't read /etc/hotplug/firmware.agent: No such file or directory
sudo: DIR=: command not found
```

I'm not exactly sure what /etc/hotplug/firmware.agent is all about, so I was hoping if someone could shed some light on the matter.

thanks,

Novakry

---

### Post by chili555 on 2007-05-12
The only light I can shed is that the kernel has an excellent driver built-in, if you add the package 'linux-restricted-modules.' Then sudo modprobe ipw3945 and you'll be all set.

---

