---
title: "Nvidia Drivers - Two Installs"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by tehkane on 2009-06-16
A while back, I installed Nvidia drivers I downloaded from their website. At this time, I also had the restricted drivers from the repo installed. Due to things going to ****, I used the uninstaller that came with the website drivers to remove it. Things started working again.

However, when I remove/install files with apt-get from CLI, I get these errors:
> 
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libnvidia-cfg.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libvdpau.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libvdpau_trace.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libnvidia-tls.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libGL.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libvdpau_nvidia.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libXvMCNVIDIA.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libcuda.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libGLcore.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib32/libvdpau_trace.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib32/libnvidia-tls.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib32/libGL.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib32/libvdpau_nvidia.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib32/libcuda.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib32/libGLcore.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/tls/libnvidia-tls.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib32/tls/libnvidia-tls.so.180.51 is not an ELF file - it has the wrong magic bytes at the start.


I have 180.11 installed - The repo drivers. So I'm guessing these are files that were left behind from the website drivers...

How can I fix these errors? I read a forum post that said you need to reinstall these packeges to fix them. But I don't think I want them... If they are files from the old website drivers, I don't need them :/

Ideas?

---

### Post by kpkeerthi on 2009-06-16
If you installed the driver using the installer downloaded from the website, you should always uninstall it first
```
sh NVIDIA-Linux-x86-xxx.yy.zz-pkg0.run --uninstall
```
using the installer before installing the repo drivers.

---

### Post by tehkane on 2009-06-16
Yeah, I did that. Then I reinstalled the drivers from the repo. That was quite some time ago and I'm still getting these APT errors :/

---

### Post by tehkane on 2009-06-16
Bump >.<

---

### Post by Steelmourne on 2009-06-17
This should help: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

Generally, if you want new drivers purge your system of the old until no trace is left. THe above thread has instructions on this.

---

