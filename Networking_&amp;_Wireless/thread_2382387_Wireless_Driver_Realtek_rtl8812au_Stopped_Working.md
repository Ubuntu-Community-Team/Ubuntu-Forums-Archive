---
title: "Wireless Driver Realtek rtl8812au Stopped Working"
date: 2018-01-12
forum: Networking &amp; Wireless
---

### Post by cboujoukos on 2018-01-12
About six weeks ago I got my Realtek wireless adapter up and running on my new computer (running Ubuntu 16.04) by following Chili5555's advice to another user at this thread: [https://ubuntuforums.org/showthread.php?t=2339960](https://ubuntuforums.org/showthread.php?t=2339960) . Yesterday, I booted up my computer, and had no wireless connection. This happened about two weeks ago as well, at which time i was able to quickly get it up and running again using the following commands, as per the advice in the aforementioned thread:

Code:
cd  ~/Documents/wifi_adapter/rtl8812AU
make clean
make
sudo make install
sudo modprobe 8812au

Unfortunately, attempting the same fix yesterday got me nowhere, and since then i have scoured the forums for other solutions to no avail. If anybody feels up to the task of walking a relatively new linux user through troubleshooting this issue, I would really appreciate it.

Thanks Ubuntu Community!

---

### Post by chili555 on 2018-01-12
```
cd ~/Documents/wifi_adapter/rtl8812AU
make clean
make
sudo make install
sudo modprobe 8812au
```One of these steps ended in an error, I strongly suspect. Please run through the process again and note the result of each step. Post the one that ends in an error. once a step ends in an error, stop. All further steps will be errors, too.

If a command produces no output at all, that typically means that it was executed as requested and that there are no errors or even warnings to report.

---

### Post by cboujoukos on 2018-01-12
Thank you so much for the reply! I receive an error after the make command.

```
[11:56:58] (driver-4.3.14) rtl8812AU
// &#9829; make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-26-generic/build M=/home/chris/Documents/wifi_adapter/rtl8812AU  modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-26-generic'
  CC [M]  /home/chris/Documents/wifi_adapter/rtl8812AU/core/rtw_cmd.o
In file included from /home/chris/Documents/wifi_adapter/rtl8812AU/include/drv_types.h:32:0,
                 from /home/chris/Documents/wifi_adapter/rtl8812AU/core/rtw_cmd.c:22:
/home/chris/Documents/wifi_adapter/rtl8812AU/include/osdep_service.h: In function ‘thread_enter’:
/home/chris/Documents/wifi_adapter/rtl8812AU/include/osdep_service.h:343:2: error: implicit declaration of function ‘allow_signal’ [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^
/home/chris/Documents/wifi_adapter/rtl8812AU/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/chris/Documents/wifi_adapter/rtl8812AU/include/osdep_service.h:353:6: error: implicit declaration of function ‘signal_pending’ [-Werror=implicit-function-declaration]
  if (signal_pending (current)) 
      ^
/home/chris/Documents/wifi_adapter/rtl8812AU/include/osdep_service.h:355:3: error: implicit declaration of function ‘flush_signals’ [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^
cc1: some warnings being treated as errors
scripts/Makefile.build:308: recipe for target '/home/chris/Documents/wifi_adapter/rtl8812AU/core/rtw_cmd.o' failed
make[2]: *** [/home/chris/Documents/wifi_adapter/rtl8812AU/core/rtw_cmd.o] Error 1
Makefile:1550: recipe for target '_module_/home/chris/Documents/wifi_adapter/rtl8812AU' failed
make[1]: *** [_module_/home/chris/Documents/wifi_adapter/rtl8812AU] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-26-generic'
Makefile:1576: recipe for target 'modules' failed
make: *** [modules] Error 2

```

---

### Post by chili555 on 2018-01-12
I suggest that you try a different driver package.

```
sudo apt update
sudo apt install git
git clone https://github.com/gnab/rtl8812au.git
sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2

```Reboot and tell us if the wireless is working.

---

### Post by cboujoukos on 2018-01-12
Still no wireless connection, upon running the last step in your previous reply, I got a response saying something along the lines of 
"Good news, Module rtl8812au/4.2.2 already installed on kernel 4.13.0-26-generic/x86_64". (I foolishly did not copy the exact response). I believe that I had previously cloned that repo, when I was initially trying to get the adapter set up.


After following the next step in that repo and running sudo dkms status:

[13:10:16] ~
// &#9829; sudo dkms status
amdgpu, 17.40-492261, 4.10.0-42-generic, x86_64: installed
amdgpu, 17.40-492261, 4.4.0-67-generic, x86_64: installed
ndiswrapper, 1.60, 4.10.0-42-generic, x86_64: installed
ndiswrapper, 1.60, 4.4.0-67-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-26-generic, x86_64: installed (WARNING! Diff between built and installed module!)
rtl8812au, 5.1.5, 4.13.0-26-generic, x86_64: built
rtl8812au, 5.1.5, 4.4.0-67-generic, x86_64: installed

---

### Post by chili555 on 2018-01-12
Let's hit it with a bigger hammer:

```
sudo dkms remove -m rtl8812au -v 5.1.5  --all
sudo dkms remove -m rtl8812au -v 4.2.2  --all
```We should be at a clean slate; check:```
sudo dkms status
```There should be no rtl8812au entries at all.

Now we install fresh:

```
rm -rf rtl8812au/
git clone https://github.com/gnab/rtl8812au.git
sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2

```Post any errors, warnings, smoke, sparks, etc.

---

### Post by praseodym on 2018-01-12
You may need to uninstall ndiswrapper, too.

---

### Post by cboujoukos on 2018-01-12
Alright no errors! Here is the output of dkms status:

```
[17:28:36] ~
// &#9829; sudo dkms status
amdgpu, 17.40-492261, 4.10.0-42-generic, x86_64: installed
amdgpu, 17.40-492261, 4.4.0-67-generic, x86_64: installed
ndiswrapper, 1.60, 4.10.0-42-generic, x86_64: installed
ndiswrapper, 1.60, 4.4.0-67-generic, x86_64: installed

```
No sign of the driver[IMG]https://ubuntuforums.org/images/icons/icon14.png[/IMG]

The very last command did not throw an error, but did return an interesting response:

```
[17:30:28] ~
// &#9829; sudo dkms install -m rtl8812au -v 4.2.2


8812au:
Running module version sanity check.


Good news! Module version v4.2.2_7502.20130517 for 8812au.ko
exactly matches what is already found in kernel 4.13.0-26-generic.
DKMS will not replace this module.
You may override by specifying --force.


depmod....


DKMS: install completed.

```


I am going to reboot now, and I will let you know the results!

---

### Post by cboujoukos on 2018-01-12
Okay, so not quite there. After the reboot I still don't have wifi connection but I ran sudo dkms status again and here is the result:

```
// &#9829; sudo dkms status
[sudo] password for chris: 
amdgpu, 17.40-492261, 4.10.0-42-generic, x86_64: installed
amdgpu, 17.40-492261, 4.4.0-67-generic, x86_64: installed
ndiswrapper, 1.60, 4.10.0-42-generic, x86_64: installed
ndiswrapper, 1.60, 4.4.0-67-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-26-generic, x86_64: installed (WARNING! Diff between built and installed module!)

```

---

### Post by cboujoukos on 2018-01-12
Is there a way I can find out if removing the ndiswrapper will cause any conflicts?

---

### Post by chili555 on 2018-01-12
Please try:```
sudo dkms install [COLOR="#FF0000"]--force[/COLOR] -m rtl8812au -v 4.2.2
```

---

### Post by praseodym on 2018-01-13
Uninstalling the wrapper
```

sudo apt-get remove --purge ndisgtk ndiswrapper*
```

---

### Post by cboujoukos on 2018-01-13
Hmm, still running into issues. 
Results:

```
[09:48:24] ~// &#9829; sudo dkms install --force -m rtl8812au -v 4.2.2
[sudo] password for chris: 
Module rtl8812au/4.2.2 already installed on kernel 4.13.0-26-generic/x86_64



```

ndiswrapper successfully removed.

Status:

```
[09:50:44] ~// &#9829; sudo dkms status
amdgpu, 17.40-492261, 4.10.0-42-generic, x86_64: installed
amdgpu, 17.40-492261, 4.4.0-67-generic, x86_64: installed
rtl8812au, 4.2.2, 4.13.0-26-generic, x86_64: installed (WARNING! Diff between built and installed module!)



```

Also thank you so much for all of your help, one of the main reasons I chose Ubuntu as a new linux user is because I was told the community support couldn't be beat, and I am so grateful to see just how true that is!

---

### Post by SeijiSensei on 2018-01-13
I'm running the beta for Kubuntu 18.04 and found it would install the driver from the Driver Manager screen.

It uses this package: [https://packages.ubuntu.com/search?keywords=rtl8812au-dkms](https://packages.ubuntu.com/search?keywords=rtl8812au-dkms)

You could try removing the driver you have and running "sudo apt install rtl8812au-dkms" or look into the Driver Manager app.

This package exists for 16.04LTS and later releases.

---

### Post by jeremy31 on 2018-01-13
SeijiSensei
Do you have any issues with that package when you have a kernel update?  Or have you patched the Makefile and/or dkms.conf?

---

### Post by SeijiSensei on 2018-01-14
Haven't seen a kernel update since I used this method.  I'll post back if one comes down the pike in the near future.

---

