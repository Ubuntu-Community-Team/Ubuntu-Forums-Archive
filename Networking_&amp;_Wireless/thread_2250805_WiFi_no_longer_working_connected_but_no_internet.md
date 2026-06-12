---
title: "WiFi no longer working: connected but no internet"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by robert-nurnberg on 2014-10-31
Hi there,

I am using the latest ubuntu 14.04 LTS. As late as Tuesday morning (three days ago) wireless worked fine. Did not change anything (apart from installing ubuntu updates) since then, no change on the router. However, as of today wireless is no longer working. The network manager connects to the correct wifi network, but I get no internet connection. Cannot even ping the router. Any ideas?

The laptop is a Dell inspiron 14z. I observe the same behaviour under unity and KDE. Ethernet works fine. And the wireless works fine on my iPad.

Cheers,
 Robert

---

### Post by kc1di on 2014-10-31
do you know which wireless card and driver your using?
if not could you post here the outputs of the following commands in  a terminal
```
lspci
lsmod
```

you may also want to run the [wireless script found here]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222"). and post the output.

---

### Post by robert-nurnberg on 2014-10-31
> **kc1di said:**
> do you know which wireless card and driver your using?
if not could you post here the outputs of the following commands in  a terminal
```
lspci
lsmod
```


Thanks for looking into this.
 
 ```
 lspci | grep -i network
```

returns

```
07:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
```

and

```
lsmod
```

returns the attached lsmod.txt. 

>  you may also want to run the [wireless script found here]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222"). and post the output.

I attach the output of the script. Thanks again.

---

### Post by kc1di on 2014-10-31
one thing I noticed in the wireless script is that the RFKill is reproting a hard block, which means their is a hardware switch some where that block wifi transmission.
on my dell laptop it's the f2 key.  you might want to research that first.

---

### Post by jeremy31 on 2014-10-31
It looks like a patch is needed to fix [https://launchpadlibrarian.net/186572668/0001-iwlwifi-dvm-drop-non-VO-frames-when-flushing.patch](https://launchpadlibrarian.net/186572668/0001-iwlwifi-dvm-drop-non-VO-frames-when-flushing.patch)
Bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809)  There is a kernel with the patch applied but the poster already has 3.13.0-39 and the patched one is -37

---

### Post by robert-nurnberg on 2014-10-31
Sorry, I had switched WiFi off with Alt-F2 when running the test. I have rerun the script and corrected the attachment in the above post.

---

### Post by robert-nurnberg on 2014-10-31
> **jeremy31 said:**
> It looks like a patch is needed to fix [https://launchpadlibrarian.net/186572668/0001-iwlwifi-dvm-drop-non-VO-frames-when-flushing.patch](https://launchpadlibrarian.net/186572668/0001-iwlwifi-dvm-drop-non-VO-frames-when-flushing.patch)
Bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809)  There is a kernel with the patch applied but the poster already has 3.13.0-39 and the patched one is -37

Thanks for the information. Please note that on my system everything was working fine until Tuesday, 2014-10-28. The information on the bug from your first link seems to show that this was reported on 2013-04-13 and "fixed" on 2014-10-14, see [https://bugzilla.kernel.org/show_bug.cgi?id=56581](https://bugzilla.kernel.org/show_bug.cgi?id=56581)

Could this mean that this fix actually broke something on my system? (I am updating my system regularly.)

Any help is much appreciated.

---

### Post by jeremy31 on 2014-10-31
It may have been the newer kernel that caused your problem.  Reboot and hold shift key to show grub menu, scroll to Previous ubuntu then select one with the 3.13.0-37 kernel and see if wifi is normal

---

### Post by robert-nurnberg on 2014-10-31
> **jeremy31 said:**
> It may have been the newer kernel that caused your problem.  Reboot and hold shift key to show grub menu, scroll to Previous ubuntu then select one with the 3.13.0-37 kernel and see if wifi is normal

Thanks, that solved the issue. However, when I reboot again into the 0-39 kernel, it now also works. I do not understand that! I attach the output of the wireless script in the new situation, just for completeness.

Anyway, I am happy that wireless seems to work again. Many thanks for your help!

---

### Post by jeremy31 on 2014-10-31
> **robert-nurnberg said:**
> Thanks, that solved the issue. However, when I reboot again into the 0-39 kernel, it now also works. I do not understand that! I attach the output of the wireless script in the new situation, just for completeness.

Anyway, I am happy that wireless seems to work again. Many thanks for your help!

I bet the bug is still there and it will occur on any reboot is wifi is toggled off ```
rfkill block wifi
``` or by using the keyboard combo to disable wifi but if wifi is enabled and rebooted things will work

---

### Post by robert-nurnberg on 2014-10-31
> **jeremy31 said:**
> I bet the bug is still there and it will occur on any reboot is wifi is toggled off 

Arrgh! I went to test your theory: With wifi toggled off at boot time, the bug occurs for kernel 0-39, but it also occurs for the kernel 0-37. So if something broke recently, it must have already been broken in 0-37.

Now the bad news: toggling wifi on at boot time no longer fixes the issue. So the fact that it worked earlier must have been by chance or something.

I would like to test whether the same error occurs with even older kernels. Unfortunately, I have auto-removed them. How do I install an older kernel?

Thanks!

---

### Post by robert-nurnberg on 2014-10-31
> **jeremy31 said:**
> I bet the bug is still there and it will occur on any reboot is wifi is toggled off 

I finally figured out a stable work-around. This works also for the latest kernel.

If upon booting the wifi is toggled on AND the ethernet cable is connected, then wireless will work even after the ethernet cable is disconnected. Wireless will continue to work after rebooting, even with the cable removed at all times.

However, toggling wifi off breaks this cycle again, and it will need a reboot with both the ethernet cable in and wifi toggled on to make it work again.

Should I file this as an official bug somewhere?

---

### Post by jeremy31 on 2014-10-31
Time to test the patched -37 kernel. download and install these [http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-headers-3.13.0-37_3.13.0-37.64+lp1361809v201410060628_all.deb](http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-headers-3.13.0-37_3.13.0-37.64+lp1361809v201410060628_all.deb)
[http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-headers-3.13.0-37-generic_3.13.0-37.64+lp1361809v201410060628_amd64.deb](http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-headers-3.13.0-37-generic_3.13.0-37.64+lp1361809v201410060628_amd64.deb)
[http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-image-3.13.0-37-generic_3.13.0-37.64+lp1361809v201410060628_amd64.deb](http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-image-3.13.0-37-generic_3.13.0-37.64+lp1361809v201410060628_amd64.deb)
And this won't hurt
[http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-image-extra-3.13.0-37-generic_3.13.0-37.64+lp1361809v201410060628_amd64.deb](http://people.canonical.com/~sforshee/lp1361809/linux-3.13.0-37.64+lp1361809v201410060628/linux-image-extra-3.13.0-37-generic_3.13.0-37.64+lp1361809v201410060628_amd64.deb)

If you have gdebi installed, double click on each file in the order they were downloaded and choose install, you will likely need to use the shift key after rebooting to use the 3.13.0-37 patched kernel if it isn't the newest installed from the grub, previous versions menu, look for the version with 3.13.0-37.64+lp1 as the kernel

Then again, if wifi is toggled on before rebooting, everything works even after a failure. Correct?  I mean enabling wifi through network manager or ```
rfkill unblock all
``` before rebooting, not trying a keyboard shortcut during a boot

---

### Post by robert-nurnberg on 2014-11-01
> Then again, if wifi is toggled on before rebooting, everything works even after a failure. Correct?  I mean enabling wifi through network manager or ```
rfkill unblock all
``` before rebooting, not trying a keyboard shortcut during a boot

Just to clarify: when I described the workaround in my previous post, then with "toggling wifi on/off" I meant the hardware switch with Fn-F2 on my DELL laptop. Note also that I can only get this to work after a failure if the ethernet cable is connected as well at boot time.

---

