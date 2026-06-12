---
title: "TP-Link WN722N minor issues"
date: 2017-08-01
forum: Networking &amp; Wireless
---

### Post by fanialivio on 2017-08-01
Hello,

After discovering that my Netgear WNA 3100 wireless adapted was a terrible hardware under Linux, I decided to buy a [COLOR=#000000]TP-Link WN722N.
[/COLOR]Since it is a 2nd or 3rd generation (with a Realtek chip) I installed it with this source code : [https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu)

The device works, but I have two minor issues I would like to solve :

1) The device does not connect automatically. Every time I boot my computer, I have to unplug and replug it in order to be detected
2) After some major updates (I guess kernel updates) I have to compile and install it from source every time.

[https://pastebin.com/yJX4LMYP](https://pastebin.com/yJX4LMYP)

Does anybody have the same issue ?

Best regards

---

### Post by chili555 on 2017-08-01
You can solve the recompile issue with dkms; please see: [https://askubuntu.com/questions/912498/tl-wn722n-is-not-recognized](https://askubuntu.com/questions/912498/tl-wn722n-is-not-recognized)

After that is fixed, please post back to tell us if the wireless now starts on boot.

---

### Post by fanialivio on 2017-08-02
Thank you chili555. 

First problem solved. It works. The [COLOR=#000000]TP-Link WN722N[/COLOR] now connects automatically to the network.
Any clue for avoiding install the source code at every kernel update?

---

### Post by jeremy31 on 2017-08-02
Did you not use the dkms method of installing the driver provided from chili555's link?  Look at results for ```
dkms status
```
See if 8188eu shows in the results

---

### Post by fanialivio on 2017-08-03
Yes, 8188eu shows in the results. 
So if I understand well this means that the dkms should also solve the update problem. Perfect then!

Thank you for the help

---

### Post by fanialivio on 2017-08-09
Apparently installing the dkms does not solve the issue permanently. After updating the kernel a couple of days ago, the wireless adapter just stopped working.

liviux@liviux-workstation:~$ dkms status
8188eu, 1.0, 4.10.0-28-generic, x86_64: built
8188eu, 1.0, 4.10.0-30-generic, x86_64: installed
8188eu, 1.0, 4.4.0-89-generic, x86_64: installed

---

### Post by chili555 on 2017-08-09
Please post:```
uname -r
dmesg | grep 8188
```

---

### Post by fanialivio on 2017-08-10
liviux@liviux-workstation:~$ uname -r
4.10.0-30-generic
liviux@liviux-workstation:~$ dmesg | grep 8188
[    3.482224] Adding 8328188k swap on /dev/sda5.  Priority:-1 extents:1 across:8328188k SSFS
[    4.088217] 8188eu: version magic '4.10.0-28-generic SMP mod_unload ' should be '4.10.0-30-generic SMP mod_unload '

---

### Post by chili555 on 2017-08-10
Wierd! May we also see: ```
cat /var/lib/dkms/8188eu/1.0/4.10.0-30-generic/x86_64/log/make.log

```I suspect something went wrong here.

If you see that the module was built against the 4.10.0-28 headers like this:> DKMS make.log for 8188eu-1.0 for kernel 4.10.0-[COLOR="#FF0000"]30[/COLOR]-generic (x86_64)
Thu Aug 10 08:17:43 EDT 2017
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-30-generic/build M=/var/lib/dkms/8188eu/1.0/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-[COLOR="#FF0000"]28[/COLOR]-generic'
  CC [M]  /var/lib/dkms/8188eu/1.0/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/8188eu/1.0/build/core/rtw_br_ext.o
<snip>Then let's try to fix it:```
cd /usr/src/8188eu-1.0
sudo nano dkms.conf
```The file probably now reads:```
PACKAGE_NAME="8188eu"
PACKAGE_VERSION="1.0"
BUILT_MODULE_NAME="8188eu"
DEST_MODULE_LOCATION="/kernel/drivers/net/wireless/"
REMAKE_INITRD="yes"
AUTOINSTALL="yes"
MAKE="'make' all KVER=${kernelver}"
MAKE="'make' all"
CLEAN="'make' clean"

```Please comment out the second MAKE line with a hashmark # so that the file now reads:```
PACKAGE_NAME="8188eu"
PACKAGE_VERSION="1.0"
BUILT_MODULE_NAME="8188eu"
DEST_MODULE_LOCATION="/kernel/drivers/net/wireless/"
REMAKE_INITRD="yes"
AUTOINSTALL="yes"
MAKE="'make' all KVER=${kernelver}"
#MAKE="'make' all"
CLEAN="'make' clean"

```Proofread carefully, save and close nano. Now let's reinstall:```
sudo dkms remove 8188eu/1.0 -k $(uname -r)
sudo dkms install 8188eu/1.0
```Reboot. You should be all set.

---

### Post by jeremy31 on 2017-08-10
I didn't even notice that Larry didn't apply my change correctly.  I have commented on his commit at github to get that fixed.
My github fork is correct and the dkms.conf
```
PACKAGE_NAME="8188eu"
PACKAGE_VERSION="1.0"
BUILT_MODULE_NAME="8188eu"
DEST_MODULE_LOCATION="/kernel/drivers/net/wireless/"
REMAKE_INITRD="yes"
AUTOINSTALL="yes"
MAKE="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
```

---

### Post by chili555 on 2017-08-10
> **jeremy31 said:**
> I didn't even notice that Larry didn't apply my change correctly.  I have commented on his commit at github to get that fixed.
My github fork is correct and the dkms.conf
```
PACKAGE_NAME="8188eu"
PACKAGE_VERSION="1.0"
BUILT_MODULE_NAME="8188eu"
DEST_MODULE_LOCATION="/kernel/drivers/net/wireless/"
REMAKE_INITRD="yes"
AUTOINSTALL="yes"
MAKE="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
```I confess! I actually plagiarized the solution from you, Jeremy!

[https://ubuntuforums.org/showthread.php?t=2361347](https://ubuntuforums.org/showthread.php?t=2361347)

Thanks!

---

### Post by fanialivio on 2017-08-13
Thank you chili555,

You were right, commenting the second make did the trick.
 Now the wireless adapter works again, but I still need to unplug and plug each time I reboot. I guess there is no permanent solution to both allows it to connect automatically and avoid reinstalling at each kernel update...
At least I can have a working wireless adapter in Linux.

---

### Post by chili555 on 2017-08-13
If you boot with the device inserted, does the driver load?```
lsmod | grep 8188
```

---

### Post by fanialivio on 2017-09-17
Sorry for the late reply. I moved and I had no internet connection so I could not check. This is the output of lsmod :

8188eu                720896  0

So the driver is load each time, but is like it was switched off.

---

### Post by jeremy31 on 2017-09-17
Post results for ```
ifconfig; iwconfig; rfkill list
```

---

### Post by fanialivio on 2017-10-31
Hi everyone,

I just wanted to communicate that by installing (fresh install and not upgrading) Ubuntu 17.10 I solved the problem. The wireless card is plug and play now. No driver download or update needed.

Cheers

---

