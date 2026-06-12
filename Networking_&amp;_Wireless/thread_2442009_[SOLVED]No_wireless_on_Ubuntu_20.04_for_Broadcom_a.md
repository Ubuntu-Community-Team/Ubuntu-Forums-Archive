---
title: "[SOLVED]No wireless on Ubuntu 20.04 for Broadcom adapter"
date: 2020-04-28
forum: Networking &amp; Wireless
---

### Post by gordan-vrbanec-vepar on 2020-04-28
Hello! 

I'm fixing my mother's laptop that had a Windows 8 on it. 
It was beyond repair so i wiped the whole disk and installed Ubuntu 20.04 on it.
it has efi, /boot, swap, /, and /home partitions (adding this info just in case it's relevant).

The laptop is Lenovo G500.

Everything so far is dandy, except i can't get wireless to work. 

Now bear in mind, i haven't done this in a while and i have 0 knowledge about what has changed from the last time i dealt with ubuntu so i might need more info except just wireless if that's ok.
Like, do i still need to install restricted extras? What do i need to do to a fresh installation? She'll be using it for internet, office, email and watching movies from time to time. I can set her email etc, but idk about what to use for video - is there VLC in software center? Do i need codecs? 

But first thing's first. Wireless. She can't have it wired all the time so this is kind of required. Otherwise i wouldn't bother.

I tried this:
[https://itsfoss.com/fix-no-wireless-network-ubuntu/](https://itsfoss.com/fix-no-wireless-network-ubuntu/)
[https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

So far, none of this worked, still no wireless showing. If i unplug the cable, it just says wired connection unplugged.

lspci -nn -d 14e4: output:
```
Broadcom Inc. adn subsidiaries BCM4142 802.1 1b/g/n [14e4:4356] (rev 01)
```

Any help would be greatly appreciated!
If you need further output, just tell me what you need and i'll copy it here.

---

### Post by chili555 on 2020-04-28
Did you install the correct driver? From the terminal (Ctrl+Alt+t), run and post:

```
sudo dpkg -s bcmwl-kernel-source | grep Status

```
Is the wireless switch or key combination set to enable or disable wireless?

```
rfkill list all
```

Are there any informative clues in the log?

```
dmesg | grep wl
```> 
 is there VLC in software center? Do i need codecs?
Yes and yes.

---

### Post by gordan-vrbanec-vepar on 2020-04-28
Hey! Thanks for responding!

Well dpkg for bcmwl-kernel-source is


```
Status: deinstall ok config-files
```

But that's because i first tried that - and that was installed by default. 
I looked up the table in [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers) and the correct driver for that was bcmwl-kernel-source.
So i tried what was said in [https://itsfoss.com/fix-no-wireless-network-ubuntu/](https://itsfoss.com/fix-no-wireless-network-ubuntu/) and installed another one.

I'm going to switch to the laptop now and post other outputs. Just a sec.

---

### Post by gordan-vrbanec-vepar on 2020-04-28
Here's the rest:

rfkill list all
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

dmesg | grep wl has no output at all

---

### Post by chili555 on 2020-04-28
> 
So i tried what was said in [https://itsfoss.com/fix-no-wireless-network-ubuntu/](https://itsfoss.com/fix-no-wireless-network-ubuntu/) and installed another one.

To paraphrase the cool kids, howz that workin' out for ya?? There are many issues I have with the itsfoss post. For instance, there is no way Jose, no way in God's green earth that a 4360 802.11ac device is going to work AT ALL with b43 and firmware. That's a subject for another rant.

Please do:

```
sudo apt install --reinstall bcmwl-kernel-source.
```

Reboot and tell us the result.

---

### Post by gordan-vrbanec-vepar on 2020-04-28
Do i uninstall the other drivers i got first?

---

### Post by gordan-vrbanec-vepar on 2020-04-28
dpkg:

```
Status: install ok half-configured
```

rfkill list all:

```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

dmesg grep wl again no output

---

### Post by chili555 on 2020-04-28
> **gordan-vrbanec-vepar said:**
> Do i uninstall the other drivers i got first?No need. bcmwl-kernel-source will blacklist them automagically.

---

### Post by gordan-vrbanec-vepar on 2020-04-28
> **chili555 said:**
> No need. bcmwl-kernel-source will blacklist them automagically.

Yeah, i didn't uninstall them. I posted the outputs.

---

### Post by chili555 on 2020-04-28
What does this report:

```
sudo dpkg -s bcmwl-kernel-source | grep Version
sudo modprobe wl && dmesg | grep wl 
```

---

### Post by gordan-vrbanec-vepar on 2020-04-28
dpkg reports:

```
Version: 6.30.223.271+bdcom-0ubuntu5
Config-Version: 6.30.223.271+bdcom-0ubuntu5

```

modprobe:

```
modprobe: FATAL: Module wl not found in directory /lib/modules/5.4.0-26-generic
```

---

### Post by chili555 on 2020-04-28
I wonder if there was an error that you missed when you installed it. Please run again:

```
sudo apt install --reinstall bcmwl-kernel-source
```

Does it end with:

> wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-26-generic/updates/dkms/

depmod...

DKMS: install completed.Or does it end differently? Please post.

---

### Post by gordan-vrbanec-vepar on 2020-04-28
Hmm, i get:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

i did what it said and then i get this:
[https://imgur.com/a/vteq1Ru](https://imgur.com/a/vteq1Ru)

i press enter and nothing happens

---

### Post by jeremy31 on 2020-04-28
The build log for the 5.4.0-26 kernel is not pretty
```
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.4.0-26-generic (x86_64)
Tue 28 Apr 2020 04:34:37 PM CDT
make: Entering directory '/usr/src/linux-headers-5.4.0-26-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  AR      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/built-in.a
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;wl_pci_probe&#8217;:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:780:2: warning: this &#8216;if&#8217; clause does not guard... [-Wmisleading-indentation]
  780 |  if ((val & 0x0000ff00) != 0)
      |  ^~
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:782:3: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;if&#8217;
  782 |   bar1_size = pci_resource_len(pdev, 2);
      |   ^~~~~~~~~
In file included from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:40:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function &#8216;wl_set_auth_type&#8217;:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.h:52:5: warning: this statement may fall through [-Wimplicit-fallthrough=]
   52 |  if (wl_dbg_level & WL_DBG_DBG) {   \
      |     ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:816:3: note: in expansion of macro &#8216;WL_DBG&#8217;
  816 |   WL_DBG(("network eap\n"));
      |   ^~~~~~
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:817:2: note: here
  817 |  default:
      |  ^~~~~~~
In file included from ./include/linux/bitmap.h:9,
                 from ./include/linux/cpumask.h:12,
                 from ./arch/x86/include/asm/cpumask.h:5,
                 from ./arch/x86/include/asm/msr.h:11,
                 from ./arch/x86/include/asm/processor.h:21,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/seqlock.h:36,
                 from ./include/linux/time.h:6,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:10,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/include/linuxver.h:40,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:27:
In function &#8216;strncpy&#8217;,
    inlined from &#8216;_wl_add_monitor_if&#8217; at /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2980:2:
./include/linux/string.h:281:9: warning: &#8216;__builtin_strncpy&#8217; specified bound depends on the length of the source argument [-Wstringop-overflow=]
  281 |  return __builtin_strncpy(p, q, size);
      |         ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;_wl_add_monitor_if&#8217;:
./include/linux/string.h:302:10: note: length computed here
  302 |   return __builtin_strlen(p);
      |          ^~~~~~~~~~~~~~~~~~~
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.o
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  Building modules, stage 2.
  MODPOST 1 modules
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.mod.o
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.ko
make: Leaving directory '/usr/src/linux-headers-5.4.0-26-generic'
```

Build log for broadcom-sta-dkms isn't much better
```
DKMS make.log for broadcom-sta-6.30.223.271 for kernel 5.4.0-26-generic (x86_64)
Tue 28 Apr 2020 04:36:27 PM CDT
/bin/sh: 1: [: Illegal number: 
/bin/sh: 1: [: Illegal number: 
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
KBUILD_NOPEDANTIC=1 make -C /lib/modules/5.4.0-26-generic/build M=`pwd`
make[1]: warning: jobserver unavailable: using -j1.  Add '+' to parent make rule.
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-26-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
Kernel architecture is X86_64
  AR      /var/lib/dkms/broadcom-sta/6.30.223.271/build/built-in.a
  CC [M]  /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_linux.o
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_linux.c: In function &#8216;wl_pci_probe&#8217;:
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_linux.c:787:2: warning: this &#8216;if&#8217; clause does not guard... [-Wmisleading-indentation]
  787 |  if ((val & 0x0000ff00) != 0)
      |  ^~
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_linux.c:789:3: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the &#8216;if&#8217;
  789 |   bar1_size = pci_resource_len(pdev, 2);
      |   ^~~~~~~~~
In file included from ./include/linux/bitmap.h:9,
                 from ./include/linux/cpumask.h:12,
                 from ./arch/x86/include/asm/cpumask.h:5,
                 from ./arch/x86/include/asm/msr.h:11,
                 from ./arch/x86/include/asm/processor.h:21,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/seqlock.h:36,
                 from ./include/linux/time.h:6,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:10,
                 from /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/include/linuxver.h:40,
                 from /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_linux.c:27:
In function &#8216;strncpy&#8217;,
    inlined from &#8216;_wl_add_monitor_if&#8217; at /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_linux.c:2989:2:
./include/linux/string.h:281:9: warning: &#8216;__builtin_strncpy&#8217; specified bound depends on the length of the source argument [-Wstringop-overflow=]
  281 |  return __builtin_strncpy(p, q, size);
      |         ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_linux.c: In function &#8216;_wl_add_monitor_if&#8217;:
./include/linux/string.h:302:10: note: length computed here
  302 |   return __builtin_strlen(p);
      |          ^~~~~~~~~~~~~~~~~~~
  CC [M]  /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_cfg80211_hybrid.o
In file included from /var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_cfg80211_hybrid.c:43:
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_cfg80211_hybrid.c: In function &#8216;wl_set_auth_type&#8217;:
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_cfg80211_hybrid.h:52:5: warning: this statement may fall through [-Wimplicit-fallthrough=]
   52 |  if (wl_dbg_level & WL_DBG_DBG) {   \
      |     ^
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_cfg80211_hybrid.c:817:3: note: in expansion of macro &#8216;WL_DBG&#8217;
  817 |   WL_DBG(("network eap\n"));
      |   ^~~~~~
/var/lib/dkms/broadcom-sta/6.30.223.271/build/src/wl/sys/wl_cfg80211_hybrid.c:818:2: note: here
  818 |  default:
      |  ^~~~~~~
  LD [M]  /var/lib/dkms/broadcom-sta/6.30.223.271/build/wl.o
CFG80211 API is prefered for this kernel version
Using CFG80211 API
Kernel architecture is X86_64
  Building modules, stage 2.
  MODPOST 1 modules
  CC [M]  /var/lib/dkms/broadcom-sta/6.30.223.271/build/wl.mod.o
  LD [M]  /var/lib/dkms/broadcom-sta/6.30.223.271/build/wl.ko
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-26-generic'
```

---

### Post by chili555 on 2020-04-28
Please disable Secure Boot in the BIOS/EFI and then try again:

```
sudo dpkg --configure -a
```Secure Boot was probably the underlying issue all along!

---

### Post by gordan-vrbanec-vepar on 2020-04-28
> **chili555 said:**
> Please disable Secure Boot in the BIOS/EFI and then try again:

```
sudo dpkg --configure -a
```Secure Boot was probably the underlying issue all along!

I see! I'll go do that, i'll google how to disable it. This will i'm sure require a restart so i'll post again when it's done.
Hopefully that solves it!

---

### Post by chili555 on 2020-04-28
> **jeremy31 said:**
> The build log for the 5.4.0-26 kernel is not pretty

Yeah, mine is ugly, too. However, the driver does build and load. I don't know if it properly drives the device. I haven't a Broadcom to test.

---

### Post by gordan-vrbanec-vepar on 2020-04-28
Well, it works now, although, i'm not sure secure boot is off...

I found online that i should run:

```
sudo mokutil --disable-validation
```

So i did that, it prompted me for a password and upon reboot in MOK i selected Change Secure boot state to off.

I then ran:

```
sudo dpkg --configure -a
```

again, but i was greeted with the same screen. I pressed Alt+C and the screen was gone and it prompted me to make a key which i did. Then the configuration continued.
After it was done, i did sudo reboot and was greeted with MOK. The second option had something about a key, so i chose that, entered the key i made, and now i have wireless.

Weird. I don't know what happened now, is the secure boot off or not? Because i turned it off, but i still got the same message that it's on. Yet i still managed to complete the configuration and now it works.

So yes, thank you **chili555** 					[[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13951727#post13951727") secure boot was indeed the issue! Hopefully it won't cause future problems.

---

