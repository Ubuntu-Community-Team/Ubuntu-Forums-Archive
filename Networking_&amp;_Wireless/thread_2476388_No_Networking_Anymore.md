---
title: "No Networking Anymore"
date: 2022-06-24
forum: Networking &amp; Wireless
---

### Post by criageek on 2022-06-24
I was having problems getting Android Studio to work after many years away from it.  I found a site that suggested that running this command might solve my problem:

sudo ubuntu-drivers autoinstall

So I ran it and it did indeed solve the problem in Android Studio.  But now I have absolutely no networking.  When I open the Network tab in Settings, there are no connections.  But I can run nmtui and see my connections, but can't activate them (wireless or wired).  When I try to ping google or yahoo I get an error that says "Temporary failure in name resolution" but I really don't think name resolution is the issue...I just don't have any networking.

I'm posting this from a different computer.  Help!  I'm running Ubuntu 22.04.

Thanks,
Rich

---

### Post by TheFu on 2022-06-25
Can you 
ping 1.1.1.1?

Can you ping your router's IP?

---

### Post by criageek on 2022-06-25
> **TheFu said:**
> Can you 
ping 1.1.1.1?

Can you ping your router's IP?

It says:

ping: connect: Network is unreachable

Rich

---

### Post by criageek on 2022-06-25
Here is a little more info in case it helps troubleshoot this.  When I run nmtui I can go to "Edit a connection" it shows my wired connection as well as the USB wireless adapter I plugged in to see if that would work.  But when I go to "Activate a connection" it doesn't show any connections.

Rich

---

### Post by #&amp;thj^% on 2022-06-25
It sounds to me as the  ubuntu-drivers autoinstall uninstalled your Net Driver.
Will this report anything?
```
sudo lshw -C network

```

---

### Post by criageek on 2022-06-25
> **1fallen said:**
> It sounds to me as the  ubuntu-drivers autoinstall uninstalled your Net Driver.
Will this report anything?
```
sudo lshw -C network

```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290648&stc=1[/IMG]

Thanks for your help!

Rich

---

### Post by #&amp;thj^% on 2022-06-25
Thought so, omg I love Realtek :P
Try this driver i find it the best option for now.
```
sudo apt-get install dkms r8168-dkms
```
You will need to reboot after a **_successful_** install.

---

### Post by criageek on 2022-06-25
How can I do that with no networking??

Rich

---

### Post by #&amp;thj^% on 2022-06-25
You'll have to download it from another machine and the link is here: [https://ubuntu.pkgs.org/20.04/ubuntu-universe-amd64/r8168-dkms_8.048.00-1_all.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-universe-amd64/r8168-dkms_8.048.00-1_all.deb.html)
Sorry I haven't had my morning coffee yet :)
```
inxi -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi

```

---

### Post by criageek on 2022-06-25
Thanks 1fallen!  I want to be sure I'm doing this right.

I downloaded r8168-dkms_8.048.00-1ubuntu0.20.04.2_all.deb from the site you pointed me to.
I copied that onto a thumb drive
I moved the thumb drive to my primary computer and copied r8168-dkms_8.048.00-1ubuntu0.20.04.2_all.deb onto it
I will then execute dpkg -i r8168-dkms_8.048.00-1ubuntu0.20.04.2_all.deb

Is this the proper process?

Thanks
Rich

---

### Post by #&amp;thj^% on 2022-06-25
Correct!

---

### Post by TheFu on 2022-06-25
I've been avoiding any realtek stuff due  to issues like this for a long time.  Best to spend $25 more and get Intel, always and avoid nearly all dumb issues like this. 

The 8111x NICs from realtek have like 40 different versions, so getting the correct driver is always fun.

Also, you got the system installed somehow, probably using a working "Try Ubuntu" flash drive. You can use that to download the drivers, almost always.
  Plus, in that Try Ubuntu environment, you can run the lshw command to see which working driver it is using. It might not be the 8169 driver at all, perhaps the 8168 driver will work better with your specific version?  Using the output from the lshw command, 

well, I wanted to copy/paste the exact lines that were important, but since you posted an image, I cannot. Oh well.  Please don't post images of text.  Post the text and wrap it in forum code tags.

---

### Post by criageek on 2022-06-25
Rats!  I was hopeful until I remembered that the USB wifi adapter I plugged in does not work either.  And indeed, the output of lshw -C  network still says 

*-network UNCLAIMED

:(

Rich

---

### Post by #&amp;thj^% on 2022-06-25
> **TheFu said:**
> I've been avoiding any realtek stuff due  to issues like this for a long time.  Best to spend $25 more and get Intel, always and avoid nearly all dumb issues like this. 

The 8111x NICs from realtek have like 40 different versions, so getting the correct driver is always fun.


Amen and Testify. ;)

---

### Post by criageek on 2022-06-25
> **TheFu said:**
> I've been avoiding any realtek stuff due  to issues like this for a long time.  Best to spend $25 more and get Intel, always and avoid nearly all dumb issues like this. 

The 8111x NICs from realtek have like 40 different versions, so getting the correct driver is always fun.

Also, you got the system installed somehow, probably using a working "Try Ubuntu" flash drive. You can use that to download the drivers, almost always.
  Plus, in that Try Ubuntu environment, you can run the lshw command to see which working driver it is using. It might not be the 8169 driver at all, perhaps the 8168 driver will work better with your specific version?  Using the output from the lshw command, 

well, I wanted to copy/paste the exact lines that were important, but since you posted an image, I cannot. Oh well.  Please don't post images of text.  Post the text and wrap it in forum code tags.

OK...thanks for the tips TheFu.  This process is pretty cumbersome since I am copying output onto a thumb drive and moving it to another working computer.  But it's no more cumbersome to copy text that it is to do a screenshot  ;)

Just FYI...this system has been working since September.  Prior to that it had been working for many, many years, but the hard disk took a dup and had to be rebuilt.  The network adapter is onboard.

Rich

---

### Post by #&amp;thj^% on 2022-06-25
> **criageek said:**
> Rats!  I was hopeful until I remembered that the USB wifi adapter I plugged in does not work either.  And indeed, the output of lshw -C  network still says 

*-network UNCLAIMED

:(

Rich

Is this after a reboot?

---

### Post by TheFu on 2022-06-25
> **1fallen said:**
> Amen and Testify. ;)

Yes, Brother 1fallen.  We must follow the tech bible, always. ;)  I remember people telling me this for all hardware and I was so value oriented that I'd buy something just to save $5.  I'd been burned a few times with odd things, then a different version of realtek NIC gave me issues and someone suggested a number of reasons that just spending $25 and getting an add-on Intel Gbps NIC was the long term solution.  From that point, I started only buying motherboards with Intel NICs and routers (x86-64 boxes) with Intel NICs, and addon NICs to have multiple network support from Intel.  They've all been plug in and use.  

Intel 82574L Gigabit  (e1000e)
Intel I211 Gigabit  (igb)
Intel I210 Gigabit  (runs BSD)
Intel 82575GB Gigabit (igb)  a quad port NIC.


The all work well.

---

### Post by criageek on 2022-06-25
> **1fallen said:**
> Is this after a reboot?

Sadly, yes.  Just to be sure I did it again, but this time I shut down and then powered it on.

Rich

---

### Post by #&amp;thj^% on 2022-06-25
By any chance do you have a Nvidia GPU and the driver installed?

---

### Post by criageek on 2022-06-25
> **1fallen said:**
> By any chance do you have a Nvidia GPU and the driver installed?

Actually, I think the main point of running the offending "ubuntu-drivers autoinstall" command was to get a bunch of Nvidia stuff installed.  What to I need to run to answer your question?  I consider myself somewhat of a power user but I'm not really into the nuts and bolts of Ubuntu ;)

Thanks,
Rich

---

### Post by #&amp;thj^% on 2022-06-25
> **criageek said:**
> Actually, I think the main point of running the offending "ubuntu-drivers autoinstall" command was to get a bunch of Nvidia stuff installed.  What to I need to run to answer your question?  I consider myself somewhat of a power user but I'm not really into the nuts and bolts of Ubuntu ;)

Thanks,
Rich

I've been impressed by your knowledge so far, there is a couple or more ways to see that.
```
nvidia-smi 
```
and 
```
inxi -G
```
and
 ```
grep "X Driver" /var/log/Xorg.0.log
```
dang  forgot this one
```
modinfo /usr/lib/modules/$(uname -r)/kernel/drivers/video/nvidia.ko | grep ^version
```

---

### Post by TheFu on 2022-06-25
> **criageek said:**
> Actually, I think the main point of running the offending "ubuntu-drivers autoinstall" command was to get a bunch of Nvidia stuff installed.  What to I need to run to answer your question?  I consider myself somewhat of a power user but I'm not really into the nuts and bolts of Ubuntu ;)

Thanks,
Rich

If the nvidia driver is installed and working, then forget the ubuntu-drivers command.  BTW, I think in 22.04 the autoinstall is deprecated.  I've only used it specifically for GPU drivers. NIC drivers are discovered by the kernel during the the HW discovery phase.

For the Realtek 8111 ..... yadda, yadda drivers, there is either the r8169 or r8168 driver.  In theory, the r8169 replaced all the older wons, but you have a very old version of the NIC, so if it were me, I'd blacklist the r8169, **rmmod** it and **insmod/modprobe** the r8168.  If that works, the **lsmod** should show it, as should **ip addr**

In theory.  And no reboot should be needed.

---

### Post by jeremy31 on 2022-06-25
Any result from terminal for ```
dpkg -l | grep linux-modules-extra-$(uname -r)
```

---

### Post by #&amp;thj^% on 2022-06-25
> **jeremy31 said:**
> Any result from terminal for ```
dpkg -l | grep linux-modules-extra-$(uname -r)
```

+1 Howdy Stranger....
The Nvidia Drivers have been known to break Networks, more common WiFi

---

### Post by criageek on 2022-06-25
Just fyi - I'm working on this.  I've issued all the suggested commands and redirected the output to text files.  I need to copy these to the thumb drive then try to follow TheFu's suggestion for the proper way to post them.

Thanks for all the help...be back in a few minutes...

Rich

---

### Post by criageek on 2022-06-25
Ok, here is nvidia-smi:

```
Sat Jun 25 14:07:13 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 510.73.05    Driver Version: 510.73.05    CUDA Version: 11.6     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   37C    P8    N/A /  30W |    252MiB /  2048MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1733      G   /usr/lib/xorg/Xorg                192MiB |
|    0   N/A  N/A      1885      G   /usr/bin/gnome-shell               56MiB |
|    0   N/A  N/A      2440      G   gnome-control-center                1MiB |
+-----------------------------------------------------------------------------+

```
inxi is not installed so I can't run that command.

Here is grep "X Driver" /var/log/Xorg.0.log

```
[    87.320] (II) NVIDIA dlloader X Driver  470.129.06  Thu May 12 22:49:34 UTC 2022



```

modinfo says nvidia.ko does not exist...here is the ls for the kernel/drivers/video folder:

```
total 36
drwxr-xr-x  3 root root  4096 Jun 24 11:40 .
drwxr-xr-x 42 root root  4096 Jun 24 11:40 ..
drwxr-xr-x 14 root root  4096 Jun 24 11:40 fbdev
-rw-r--r--  1 root root 22177 Jun 15 07:14 vgastate.ko



```

And finally, dpkg -l | grep linux-modules-extra-$(uname -r) has no output.

Whew!  I'm thinking that nvidia.ko missing and no output from dpkg -l are pretty critical...let me know what's next!

Thanks guys!

Rich

---

### Post by jeremy31 on 2022-06-25
Can you use Grub at boot to boot into an older kernel?  Other kernels should be in the Advanced Options

---

### Post by criageek on 2022-06-25
> **jeremy31 said:**
> Can you use Grub at boot to boot into an older kernel?  Other kernels should be in the Advanced Options
I have two older kernels available...I didn't take note of the numbers but will the next time I reboot.  I have tried both and each time it went through the boot up process part way then stopped.  It displays the Ubuntu logo and activity indicator, then it scrolls some text pertaining to the operations it's performing, then that goes away and the screen goes blank except for an underscore cursor flashing in the upper left corner.  On the first attempt I waited 3 or 4 minutes then did a ctrl-alt-del and it rebooted.  The second attempt is still at the flashing cursor...

Rich

---

### Post by jeremy31 on 2022-06-25
What does ```
uname -r
``` tell you?

---

### Post by criageek on 2022-06-25
> **jeremy31 said:**
> What does ```
uname -r
``` tell you?

5.15.0-40-generic

---

### Post by jeremy31 on 2022-06-25
Down this and copy it to Ubuntu desktop [http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-modules-extra-5.15.0-40-generic_5.15.0-40.43_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-modules-extra-5.15.0-40-generic_5.15.0-40.43_amd64.deb)
Double click to install it, then reboot

---

### Post by criageek on 2022-06-25
Still no joy :(  lshw -C network still shows *-network UNCLAIMED

What else can I try?

I really appreciate you guys helping me out  ;)

Rich

---

### Post by criageek on 2022-06-25
Obviously you guys are the experts and I'm looking for guidance.  But doesn't the fact that a usb wifi adapter doesn't work either tell us something?

Rich

---

### Post by jeremy31 on 2022-06-25
Try ```
sudo modprobe r8169
```

---

### Post by criageek on 2022-06-25
> **jeremy31 said:**
> Try ```
sudo modprobe r8169
```

sudo modprobe r8169 shows nothing

sudo modprobe r8168 says

```
modprobe: FATAL: Module r8168 not found in directory /lib/modules/5.15.0-40-generic

```
Rich

---

### Post by jeremy31 on 2022-06-25
Try the lshw command again, see if still unclaimed

---

### Post by criageek on 2022-06-25
Wow!  My network is up and running!  Why does it work now?

Rich

---

### Post by #&amp;thj^% on 2022-06-25
It just needed a kick in the boot. ;)

---

### Post by jeremy31 on 2022-06-25
The r8169 module must be blacklisted in /etc/modprobe.d/ somewhere

---

### Post by criageek on 2022-06-25
> **jeremy31 said:**
> The r8169 module must be blacklisted in /etc/modprobe.d/ somewhere
So, I'm assuming that installing linux-modules-extra... was the real key but it didn't work after installing that and rebooting.  It started after doing the modprobe r8168.  I assume that tells the kernel to use that module?  Will it still work after a reboot?  Just trying to understand  :)

Thanks,
Rich

---

### Post by jeremy31 on 2022-06-25
This command might find it ```
grep [[:alnum:]] /etc/modprobe.d/* | grep r8169
```

---

### Post by criageek on 2022-06-25
> **jeremy31 said:**
> This command might find it ```
grep [[:alnum:]] /etc/modprobe.d/* | grep r8169
```

```
/etc/modprobe.d/r8168-dkms.conf:# map the specific PCI IDs instead of blacklisting the whole r8169 module
/etc/modprobe.d/r8168-dkms.conf:# to blacklist the whole r8169 module
/etc/modprobe.d/r8168-dkms.conf:#blacklist r8169
```

Rich

---

### Post by jeremy31 on 2022-06-25
```
sudo rm /etc/modprobe.d/r8168-dkms.conf
```
Then it should work by itself after reboot

---

### Post by criageek on 2022-06-25
> **jeremy31 said:**
> ```
sudo rm /etc/modprobe.d/r8168-dkms.conf
```
Then it should work by itself after reboot

Yep!  I rebooted and it didn't work.  I ran that command to delete r8168-dkms.conf and then it worked after a reboot.

Thanks so much!  I really appreciate everyone's help with this...it's great to have my network back  :)

Rich

---

### Post by #&amp;thj^% on 2022-06-25
Yep this is uncle jeremy's specialty..

---

### Post by criageek on 2022-06-25
Now I need to figure out why VirtualBox no longer works :(  I think it quit working at the same time the network quit. Working on it...

Rich

---

