---
title: "rtl8723as driver - loads successfully but no wlan0 or similar device is created"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by ronniepinsky on 2014-11-25
edit:
I wanted to update that I seem to have gotten it working!

Apparently the code hack I referenced did not work in the way I thought.   I investigated inside the "virtual folder" of the SDIO device and  found the device ID and replaced the one for "CONFIG_RTL8723B" in **sdio_intf.c **that  I referenced earlier.  The first address (0x024c) is the vendor ID  which should remain the same.  The second address (0xB723) is the device  ID which should be changed to (for my hardware) 0x0523.  I then  recompiled and ran insmod and it works.  I knew it worked because there  was a slight delay when loading the module.

Thanks for encouraging me to press on with this.

-----------

I have a device with an rtl8723bs SDIO wireless card.  The rtl8723as driver should support it as seen here: [http://ubuntuforums.org/showthread.php?t=2249936&page=3&highlight=rtl8723bs](http://ubuntuforums.org/showthread.php?t=2249936&page=3&highlight=rtl8723bs), and on this source code page it seems to show support for all SDIO wireless adapters: [https://github.com/hadess/rtl8723as/blob/3dd8594d850502fb76d0170209ef24d93e372753/os_dep/linux/sdio_intf.c](https://github.com/hadess/rtl8723as/blob/3dd8594d850502fb76d0170209ef24d93e372753/os_dep/linux/sdio_intf.c) .

I see the same lines in dmesg when the driver is loaded that the person on the thread here did:
```

[   46.589898] 8723bs: module verification failed: signature and/or  required key missing - tainting kernel
[   46.604071] RTL871X: module init start version:v4.1.3_8883.20130902_v2
[   46.964685] RTL871X: module init ret=0

```

Unfortunately for me, the wlan0 device or similar is not created.  I have compiled under the shipped 14.10 kernel and the 3.16.2 kernel referenced in the thread here.  I do see the device under /sys/bus/sdio/devices like referenced in the thread here.  In the past when I have had this happen it was the result of a conflict between wireless drivers.  I am unsure how to directly troubleshoot that.

1. Could this be a wireless driver conflict?
2. Could I have a different hardware ID causing problems even though the source code seems set to accept all devices?
3. What troubleshooting steps can I take from here?

---

### Post by chili555 on 2014-11-25
Why do they always do this to me? Why do they push me to take on and solve the stickiest cases? Wouldn't it be easier to invent time travel or turn lead into gold?

Let's do some diagnostics.>  I do see the device under /sys/bus/sdio/devices like referenced in the thread here.What, exactly, do you see?```
cat /sys/bus/sdio/devices
```> Could I have a different hardware ID causing problems even though the source code seems set to accept all devices?My reading of the source code isn't that it covers **all** devices; it is that it covers the devices enumerated:> #ifdef CONFIG_RTL8723A
	{ SDIO_DEVICE(0x[COLOR="#FF0000"]024c[/COLOR], 0x[COLOR="#FF0000"]8723[/COLOR]),.driver_data = RTL8723A},
#endif //CONFIG_RTL8723A
#ifdef CONFIG_RTL8723B
	{ SDIO_DEVICE(0x024c, 0x[COLOR="#FF0000"]B723[/COLOR]),.driver_data = RTL8723B},
#endif
#ifdef CONFIG_RTL8188E
	{ SDIO_DEVICE(0x024c, 0x[COLOR="#FF0000"]8179[/COLOR]),.driver_data = RTL8188E},
#endif //CONFIG_RTL8188E
#ifdef CONFIG_RTL8821A
	{ SDIO_DEVICE(0x024c, 0x[COLOR="#FF0000"]8821[/COLOR]),.driver_data = RTL8821},No? What am I missing?

---

### Post by ronniepinsky on 2014-11-25
Thanks a lot for your reply.

I figured the part of the code just below the device ID section might do it:

```

[TABLE="class: highlight tab-size-8 js-file-line-container"]
[TR]
[TD="class: blob-code js-file-line"] 
[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]#if defined(RTW_ENABLE_WIFI_CONTROL_FUNC) /* temporarily add this to accept all sdio wlan id */
[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]	{ SDIO_DEVICE_CLASS(SDIO_CLASS_WLAN) },[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]#endif[/TD]
[/TR]
[/TABLE]


```

It seems to specify a whole class of devices rather than just the devices listed.  I don't have experience with this kind of programming though.  I also don't know if "RTW_ENABLE_WIFI_CONTROL_FUNC" is actually "turned on" or if I am even on the right track with that thought.

As far /sys/bus/sdio/devices goes I see:
```

mmc1:0001:1

```

Which is the same address as here: [http://ubuntuforums.org/showthread.php?t=2249936&p=13155167#post13155167](http://ubuntuforums.org/showthread.php?t=2249936&p=13155167#post13155167)

I can supply any other information needed also.

---

### Post by ronniepinsky on 2014-11-25
edit: see above.

edit 2:
I wanted to add that I am using kernel 3.16.2 from the Ubuntu mainline kernel ppa and the second commit from the repository referenced which matches up with the version used in the thread referenced.

edit 3:
The latest commit works with 3.16.2 with these modifications and autostarts at boot.

---

### Post by chili555 on 2014-11-25
Awesome! Glad it's working.

Just for the benefit of the searchers, and I'm sure there will be some, please tell us where you derived the device ID of 024c:0523. Also, please show the additions to the code; something like:```
static const struct sdio_device_id sdio_ids[] =
{
#ifdef CONFIG_RTL8723A
	{ SDIO_DEVICE(0x024c, 0x8723),.driver_data = RTL8723A},
#endif //CONFIG_RTL8723A
#ifdef CONFIG_RTL8723B
	{ SDIO_DEVICE(0x024c, 0xB723),.driver_data = RTL8723B},
#endif
#ifdef CONFIG_RTL8188E
	{ SDIO_DEVICE(0x024c, 0x8179),.driver_data = RTL8188E},
#endif //CONFIG_RTL8188E
#ifdef CONFIG_RTL8821A
	{ SDIO_DEVICE(0x024c, 0x8821),.driver_data = RTL8821},
#endif //CONFIG_RTL8188E

[COLOR="#FF0000"]Some text you added
wherever you added it
blah and foo[/COLOR]

#if defined(RTW_ENABLE_WIFI_CONTROL_FUNC) /* temporarily add this to accept all sdio wlan id */
	{ SDIO_DEVICE_CLASS(SDIO_CLASS_WLAN) },
#endif
	{ /* end: all zeroes */				},
};
```The SDIO explorers and I will appreciate it.

---

### Post by ronniepinsky on 2014-11-25
Sure thing.  This is an excerpt from the latest sdio_intf.c.  The change is still hard to see with the weird code formatting on this forum but it is in bold and underlined.
Original:
```

[TABLE="class: highlight tab-size-8 js-file-line-container"]
[TR]
[TD="class: blob-code js-file-line"]static const struct sdio_device_id sdio_ids[] =[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]{[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8723A[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0x8723),.driver_data = RTL8723A},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif //CONFIG_RTL8723A[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8723B[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0xB723),.driver_data = RTL8723B},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8188E[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0x8179),.driver_data = RTL8188E},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif //CONFIG_RTL8188E[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8821A[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0x8821),.driver_data = RTL8821},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif //CONFIG_RTL8188E[/TD]
[/TR]
[/TABLE]

```

Changed:
```

[TABLE="class: highlight tab-size-8 js-file-line-container"]
[TR]
[TD="class: blob-code js-file-line"]static const struct sdio_device_id sdio_ids[] =[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]{[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8723A[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0x8723),.driver_data = RTL8723A},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif //CONFIG_RTL8723A[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8723B[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0x_**05**_23),.driver_data = RTL8723B},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8188E[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0x8179),.driver_data = RTL8188E},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif //CONFIG_RTL8188E[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#ifdef CONFIG_RTL8821A[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]    { SDIO_DEVICE(0x024c, 0x8821),.driver_data = RTL8821},[/TD]
[/TR]
[TR]
[TD="class: blob-code js-file-line"]#endif //CONFIG_RTL8188E[/TD]
[/TR]
[/TABLE]

```

---

### Post by chili555 on 2014-11-26
Awesome! And where did you derive the device ID of 024c:0523?

Thanks.

---

### Post by ronniepinsky on 2014-11-27
> **chili555 said:**
> Awesome! And where did you derive the device ID of 024c:0523?

Thanks.

As I mentioned above, they are inside the "virtual folder" at /sys/bus/sdio/devices.

---

### Post by chili555 on 2014-11-27
> **ronniepinsky said:**
> As I mentioned above, they are inside the "virtual folder" at /sys/bus/sdio/devices.Sorry, I guess I missed that:> As far /sys/bus/sdio/devices goes I see:
```
mmc1:0001:1
```

---

