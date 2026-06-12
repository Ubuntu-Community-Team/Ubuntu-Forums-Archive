---
title: "Netgear WNDA 3100 v2 wireless adapter installation problem"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by jonny8 on 2014-09-10
[COLOR=#000000]*Hi I'm new on this forum ; I've recently bought the netgear wnda 3100 v2 and I'm experimenting the same issue that the guy in this thread ( *[/COLOR]http://ubuntuforums.org/showthread.php?t=1964173 )[COLOR=#000000]* was dealing with ... I've followed all your steps listed in that thread but when it comes to execute the last commands *[/COLOR]
[COLOR=#000000]*"sudo modprobe ndiswrapper" it gives me this error "FATAL: Module ndiswrapper not found."*[/COLOR]
[COLOR=#000000]*Any ideas ??*[/COLOR]
[COLOR=#000000]*Please help me ,thanks in advance.*[/COLOR]

---

### Post by chili555 on 2014-09-11
There are two things you might try. Let's start easy and work up from there. With a temporary working internet connection, open a terminal and do:```
sudo apt-get install --reinstall ndiswrapper-common
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo apt-get install ndiswrapper-dkms
```After it finishes, try again:```
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by jonny8 on 2014-09-11
Sorry if i haven't replayed you earlier, but no improvement :

First command
> [COLOR=#000000][FONT=monospace]Done.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Loading new bcmwl-5.60.48.36+bdcom DKMS files...[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]First Installation: checking all kernels...[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Building only for 3.2.6[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Building for architecture i686[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Building initial module for 3.2.6[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]Error! Bad return status for module build on kernel: 3.2.6 (i686)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Consult the make.log in the build directory[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dpkg: error processing bcmwl-kernel-source (--configure):[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]subprocess installed post-installation script returned error exit status 10[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Setting up ndiswrapper-common (1.54-2ubuntu1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]

Second command
> [COLOR=#000000][FONT=monospace]Done.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Loading new bcmwl-5.60.48.36+bdcom DKMS files...[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]First Installation: checking all kernels...[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Building only for 3.2.6[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Building for architecture i686[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Building initial module for 3.2.6[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]Error! Bad return status for module build on kernel: 3.2.6 (i686)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Consult the make.log in the build directory[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dpkg: error processing bcmwl-kernel-source (--configure):[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]subprocess installed post-installation script returned error exit status 10[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Setting up ndiswrapper-utils-1.9 (1.54-2ubuntu1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]

Third command
> [COLOR=#000000][FONT=monospace]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Building dependency tree      [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]E: Couldn't find package ndiswrapper-dkms[/FONT][/COLOR]

---

### Post by chili555 on 2014-09-11
Hmmm. If you have the famous WNDA 3100 v2, you don't want or need bcmwl-kernel-source. Please do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install ndiswrapper-dkms
```Thanks.

---

### Post by jonny8 on 2014-09-11
Done it but the third command keep giving me the same error..

---

### Post by chili555 on 2014-09-11
Before we get out the big hammer, are there clues here?```
cat /var/log/syslog | grep ndis | tail -n20
```

---

### Post by chili555 on 2014-09-11
Also tell us:```
uname -r
```

---

### Post by jonny8 on 2014-09-11
[COLOR=#000000][FONT=monospace]uname -r:
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]3.2.6

[/FONT][/COLOR]cat /var/log/syslog | grep ndis | tail -n20:[COLOR=#000000][FONT=monospace]
Sep  7 17:21:14 bt kernel: [  671.114506] usbcore: registered new interface driver rndis_host[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Sep  7 17:21:14 bt kernel: [  671.124990] usbcore: registered new interface driver rndis_wlan[/FONT][/COLOR]

---

### Post by chili555 on 2014-09-11
I'm sorry I didn't see your backtrack tag. I know nothing about backtrack and don't intend to learn. I am fairly certain of two things; first, if you installed Ubuntu 14.04, we could easily get your device working. Second, you will never get any ndiswrapper device into Monitor mode needed for penetration testing.

Sorry.

---

### Post by jonny8 on 2014-09-12
No problem , thanks for all...

---

