---
title: "How to update iwlwifi driver"
date: 2021-01-26
forum: Networking &amp; Wireless
---

### Post by gde061-www on 2021-01-26
Title says the issue.

Was  looking [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html)

Seems to suggest I get driver from the git firmware tree as I am running more recent kernel than 4.1

Cannot make sense of files on git tree.

---

### Post by grahammechanical on 2021-01-26
Why do you need to update the WiFi driver? What problems are you having? Please notice these statements from Intel:

> Linux drivers are part of the upstream Linux* kernel. They're available through the regular channels, distributions,

> The wireless device requires firmware to operate. Firmware usually ships with your distribution,

Every distribution of Ubuntu comes with a Linux kernel and complimentary to the packages that make up the kernel is a Hardware Enablement Stack (device drivers). From time to time the Linux kernel and the Hardware Enablement stack are upgraded. This happens all through the support life of the particular version of Ubuntu.

What version of Ubuntu are you using? Is it still supported? The 4.1 kernel was released in June 2015. So, all of us should by now be running on a kernel version later than, much later than, the 4.1 kernel. And we will also have a more up to date Hardware Enablement Stack with updated device drivers.

> the 4.15 default kernel in Ubuntu 18.04 LTS ... there is an 18.04.4 point release as of February 2020, which includes an updated 5.3.x kernel

[https://ubuntu.com/kernel](https://ubuntu.com/kernel)

Regards

---

### Post by gde061-www on 2021-01-26
First, thank you for your reply.  I am running 16.04 LTS.   It is still "supported" but near end of life.  I believe that is supposed to be on kernel v 4.15, so I am due for a kernel upgrade... which I have put off a bit because kernel upgrades have a way of messing up my SD card drivers, which I infer are (or at least were) proprietary binary drivers(?)

Why do I need to update the wifi driver?  Because I believe I've tracked down the source of a major problem I'm having connecting to wifi networks to the kernel / wifi driver.  Basically, I was doing some network setup that involved lots of connecting - disconnecting to wifi networks that I was trying to configure.  When I was done with that and got the the networks up and operating fine (as confirmed by other machines and handheld devices) I was left with a problem on my own PC that any time I try to change wifi networks using the nm-applet, it crashes.  I had another thread on that, trying to run to ground if there was corruption in the config files of network manager (that thread was just like asking to be hit on head with hammer by all the "help" I got, but I'm now thinking it's corruption of the iwlwifi that happened, so I want to go ahead and do clean install / update of iwlwifi.  

here is what I found in dmesg: 
```
edeangel@ThinkPad-L560:~$ dmesg | grep firmware | grep iwlwifi
[   15.088766] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-20.ucode failed with error -2
[   15.096284] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
[   15.096361] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[   15.096370] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[   17.235154] iwlwifi 0000:02:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm



```
So what I'm gathering from these messsages and your explanation is that iwlwifi v20, v19, v18 and v17 are incompatible with my kernel version?  So then it's falling back to version 16, which would have been maybe the second release (I think v13 was the original one that Intel has on their website for kernel v 4.1)  Strange though because there is no blob in the git tree that would look like versions 20, 19 or 18.... it appears to jump from 17 to 21.  Just trying to put the puzzle pieces together in my mind.  BTW, the contents of my /lib/firmware mirrors what is on the git tree... I have blobs that go all the way up to v. 36.

I appreciate the help.  What I don't appreciate are people who chime in with  "well, 16.xx is ancient".  The point of an LTS version is that you get a reasonably long full lifecycle without always being told to upgrade OS version - this is one big reason I traditionally prefer Ubutu over Fedora BTW.

---

### Post by gde061-www on 2021-01-26
Well, went on the *implied* advice received here so far and upgraded my kernel to 4.15.  

Restart machine greeted with host of newly appearing ACPI errors.  Nice.  Will have to sort those out later.

Go  to use wifi.  Same buggy behavior with a bit of twist.  Meaning now NM  doesn't want to switch wifi networks without crashing but the entire  nm-applet disappears from the systray rather than lingering around with  bluetooth status only (so probably -- just guessing here -- now my  bluetooth connectivity is also fragged. )  Also when switching wifi  networks, it now will crash sometimes without spawning the popup window for the authentication /  network PW that used to be where things died -- in those cases it it just dies quietly  without spawning any dialogue.  In other cases, where there is a saved key for the destination wireless network, it will successfully switch over (obviously no dialogue would pop up in that case).  So the problem still seems to be something with the nm-applet and it's ability to hash a key as you type it in the dialogue. I'm gonna assume it tries to build the hash as you type.  On the other hand, if the file exists with the key in it, then it can do the hash ok.  

The key to the myster seems to be the error message:  get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed

Anybody know what that means?  Somebody maintaining this code base must have an idea where the dup_data object is invoked in this process of user dialogue input?  Or is it considered "good community support" to expect the user to go find the source code for all the nm-applet stuff themselves?

---

### Post by jeremy31 on 2021-01-26
Have a look at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
The iwlwifi driver doesn't work well if TKIP encryption is being used or power management is enabled, check in terminal ```
iwconfig
```

The firmware errors you saw in dmesg are there because those firmware versions don't exist now, they might not have even been released by Intel for whatever reason.  The iwlwifi/iwlmvm/iwldvm driver group has settings in the source code that specifies the minimum and maximum firmware version supported.  I see at [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/) that versions 21, 22, 27, 31, 34, and 36 do exist,  It has been a while since I tried renaming a newer firmware version to see if it would load and I don't remember if it was successful

---

