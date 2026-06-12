---
title: "&quot; FATAL: Module rtl8188ee not found&quot; error"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by diniz-cpm on 2013-10-22
Hi everyone! I recently solved my problem with wireless, as you can see in [this thread]("http://ubuntuforums.org/showthread.php?t=2177758"). Every time I booted Ubuntu I'd run the "sudo modprobe -r rtl8188ee && sudo modprobe rtl8188ee" command. However, when I turned on my notebook today the response to this command was "FATAL: Module rtl8188ee not found". Does anyone know what happened?
I'm having troubles connecting with wireless on Windows 8 too (it runs in dual boot with Ubuntu), and even with an ethernet cable I can't connect to the internet (I'm using my college's computers now). It says I'm connected with a connection but the connection cannot acess the internet.
I don't know if there's a problem with the internet connection itself, but I thought that if the module "wasn't found" then there must some problem with my wireless driver too. I already provided many information about my notebook on the other thread, but let me know if there's anything important I've missed.
Thank you everyone! ^^

---

### Post by chili555 on 2013-10-22
At the time you posted that thread, you were running kernel version 3.8.0-31-generic. Is that still the case today?```
uname -r
```If you have installed a newer kernel, please refer to the original post where I said:> When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd Desktop/backports-3.11-rc3-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8188ee
```


---

### Post by Hadaka on 2013-10-22
Hi, there was an linux image update today so you will
need to re run the commands chilli555 gave you in the post
you refered to that fixed it last time. post #9

---

### Post by diniz-cpm on 2013-10-24
I rerun the commands you've mentioned and now wireless is working again! Thank you very much!
Just one last quick question: my kernel now is "3.8.0-32-generic". I have no idea how it changed. So everytime the kernel changes I'll have to rerun those commands?

---

### Post by chili555 on 2013-10-24
>  I have no idea how it changed.I'm certain Update Manager offered you a long list of updates; the kernel update was among them.> So everytime the kernel changes I'll have to rerun those commands? Yes. Your clue, of course, will be when your wireless magically stops working!

---

### Post by diniz-cpm on 2013-10-25
oh, I see. Thank you very much again! ^^

---

