---
title: "Intel pro/Wireless 9345 card not found on Gutsy"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by simonl2009 on 2008-02-20
Hi,
I recently bought a dell XPS m1530, and I'm having some trouble with my wireless broadband. When I boot up, ubuntu doesn't seem to see my wireless card: right-clicking on NetworkManager doesn't even show up an "enable wireless" option. I'm using 7.10, by the way.

(Edit: that should read Intel 3945 wireless in the title, sorry)

My current solution is to keep rebooting until it works, which it eventually does. This may take 3-4 tries though.

I'm quite new to linux, so I'm not even that sure what to look for. Here's the output from the various commands I've seen which might be helpful.

(this is the output when the wireless actually works)
```
]
simon@simon-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:36:51:c6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:aa:2c:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.64 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g

```

```

simon@simon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"BTHomeHub-A8F5"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:7F:92:C3:BF   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=65/100  Signal level=-67 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:345   Missed beacon:0

```


```

simon@simon-laptop:~$ dmesg | grep 3945
[   14.520000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.520000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.524000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.792000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)


```


Now, more often, the wireless doesn't work and I see:

```

simon@simon-laptop:~$ dmesg | grep 3945
[   14.884000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.884000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.884000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.584000] ipw3945: MAC is in deep sleep!
[   20.560000] ipw3945: Unable to int nic

```

```

simon@simon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Someone suggested trying "sudo iwconfig eth1 up", but that gives an error message saying something like "no such device", I can't remember the specific message.

I've heard ndiswrapper could help in a situation such as this, but I'm a bit clueless as to how to set it up. Dell's wireless drivers come in a .exe compressed file, and once I unrar that file, I get a big directory structure. I'm not sure where the actual driver is within that file.

 Oh, if it helps, I'm using WEP encryption (I know, I should use WPA, but my housemates are luddites).
Thanks for any advice you might be able to give.

---

### Post by nDrewPJ on 2008-02-20
try download the ucode for this wifi adapter from the Intel's site and put it into the /lib/firmware dir

but...restricted modules MUST do that by default.... stange. I have iwl3945 device present in gutsy default installation (2.6.22kernel) and even when updating ti 2.6.24 kernel it is still there

---

### Post by simonl2009 on 2008-02-20
someone suggested using the iwl3945 driver, but I wasn't sure how to. I'll have a look on the intel website, and post back here if I have trouble.
Cheers.

---

### Post by rustybronco on 2008-02-20
Something is very familiar about your problem, and I have been waiting for an answer to this post.
[http://ubuntuforums.org/showthread.php?p=4365793#post4365793](http://ubuntuforums.org/showthread.php?p=4365793#post4365793)

32 bit or 64 bit 7.10 install?

64 bit... [http://ubuntuforums.org/showpost.php?p=4343525&postcount=1](http://ubuntuforums.org/showpost.php?p=4343525&postcount=1)

in answer to your question about a ndiswrapper how to [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

***more***
> simon@simon-laptop:~$ dmesg | grep 3945
[   14.884000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.884000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.884000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.584000] ipw3945: **MAC is in deep sleep!**
[   20.560000] ipw3945: **Unable to int nic**

[http://ubuntuforums.org/showthread.php?p=4304762#post4304762](http://ubuntuforums.org/showthread.php?p=4304762#post4304762)
> For reference, my BIOS version is A06.

[quote=simonl2009]Hi,
I recently bought a **dell XPS m1530**, and I'm having some trouble with my wireless broadband. When I boot up, ubuntu doesn't seem to see my wireless card: right-clicking on NetworkManager doesn't even show up an "enable wireless" option. I'm using 7.10, by the way.[/quote]

---

### Post by simonl2009 on 2008-02-20
I followed the advice in 
[http://ubuntuforums.org/showpost.php...25&postcount=1](http://ubuntuforums.org/showpost.php...25&postcount=1)
even though I'm on 32-bit. I think it worked, but I'm not 100% certain. If the problem doesn't show up again in the next couple of days, I'll post back to confirm that this works.

Hope this is helpful to any other XPS M1530 users. (or anyone else, for that matter)

---

### Post by rustybronco on 2008-02-20
Thanks for the info on 32 bit it helps me figure out the other two threads problems.

---

### Post by simonl2009 on 2008-02-21
Sadly, it didn't work: It took three reboots before the wireless switched on this morning. Output from dmesg:

```
 imon@simon-laptop:~$ dmesg |grep 3945
[  221.808000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  221.808000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  221.808000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  226.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  226.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  226.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  226.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  226.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  226.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  229.748000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  229.748000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  231.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  231.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  231.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
[  231.804000] iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
 
```

and a lot more of the same

I'll try to get ndiswrapper set up tonight

---

### Post by rustybronco on 2008-02-21
let me know how it goes.

---

### Post by smashagnome on 2008-04-16
I have tried all the drivers available for this card - including NDISWRAPPER  (XP driver / win98 driver and win2k driver) same issue.
What I have found is that by adding the NOAPIC before the SPLASH in the /boot/grub/menu.lst file fixes it most of the time.  I still have to reboot once in a while to get it to work but that is rare. 

What I think is causing the problem for me is that I dual boot.  The windows driver seems to put the NIC in hibernation mode when I shut windows down, when windows comes up it is able to get it out of that mode but Ubuntu is not able to do that. (DMESG shows ipw3945: MAC is in deep sleep! when it isnt working)

I am going to try to find a better windows vista driver that may have more options in it and see if I can get rid of the NOAPIC in my grub.

I hope this helps a little 


=====================
EDIT:
  I found a Vista driver off Intel's site and updated.  This driver has an option to allow the computer to shut the device down (checked by default)  I have disabled it and will test for a while.  I bet this is part of the problem, my guess is that during the shutdown procedure Vista shuts down the NIC to save power (in case its suspend / hibernate mode).  I will keep you posted

Oh I should note I am running  2.6.22-14-generic (7.10) and ipw3945 at the time.  I know IWL is supposed to be the way to go - but IPW is way more stable.

-------
Nope - that windows driver changed nothing - same behavior.  When I boot into windows and back to Ubuntu more often then not I lose wireless.  A reboot has always corrected this.  I then can reboot Ubuntu as many times as I want and not lose wireless.  I wonder if anyone knows a command that I can send to the Nic to bring it out of "Deep Sleep"
Hmmm
------------------------------------

When all else fails Smashagnome

---

### Post by unicynic on 2008-04-23
Seems that you have same problem as mine - need to reboot several times or at least CTRL-ALT-DEL several times at grub and get it by chance.

Well, I've found a better workaround - put the notebook in sleep mode and wake it up again. Then, press the keyboard keys that enables the wireless. It should work.

If it goes off again (not to me), go back to sleep mode and wake the notebook up. The device will properly initialize then after you press the wireless keys.

On my notebook, this workaround also enables the bluetooth and sound in Gutsy - don't even need to update anything!

It's because somehow the ACPI keys are not loaded until after you press the sleep key. Funny. That's why it's in deep sleep: the hardware RF kill switch is on. I've tried so many ways for 2 weeks (sleepless) and accidentally after pressing the sleep key and wake it up again, all the problems just gone! A bug in the ACPI booting, I guess.

---

### Post by chili555 on 2008-04-23
@unicynic

Would you try an experiment to humor an old linux-ian? First, do:```
lsmod | grep 3945
```We want to know if you have **iwl3945** or **ipw3945** running. Then *sudo gedit /etc/modules* to add, on it's own line:```
alias eth1 ipw3945 disable=0
```Then reboot and tell us if the problem is fixed. Of course, substitute iwl3945 if that's your module.

---

### Post by unicynic on 2008-04-26
I'm on Hardy now.

In Gutsy, and in Mint 4, I was using the ipw driver with the ipw firmware. In Hardy, it uses the iwl driver. Both needed to be suspended first before working or it will say wireless kill switch is on. Also the bluetooth and sound. All work after resume.

In Hardy, lsmod shows the iwl driver. I put the line you suggested in /etc/modules and shutdown - tried not to warm reboot as in warm reboot sometimes if the wireless is on, it will be ok. On cold boot, it may not be on. So I cold booted to recreate the situation.

lsmod this time shows the iwl driver.

dmesg | grep 3945 shows that it won't get the MAC address as the wireless kill switch is on. The same as before.

In fact, I had more success with the ipw driver as I can connect to my adhoc. If using iwl, I have problems with adhoc... it may connect sometimes but won't get proper DHCP. But ever since in Hardy, I can't connect at all even if it detects the adhoc (and that too, sometimes). Well, maybe some firewall or dhcp client config but I don't know much in Linux.

Still, the suspend-resume workaround is the only way to turn on the ACPI keys and sound. After that, I can disable the wireless kill with the fn key and connect.

I saw a bug report that sound (intel hda) only works after suspend. In my case, it's also true for wifi and bluetooth. I tried by running the suspend script in /etc/acpi (to remove the possibility that it's the hardware fn key problem) and once resume, the same result that now the ACPI keys and sound work.

BTW, in Hardy with the iwl driver, even when I get the wifi working after resume, the wifi LED doesn't blink. In gutsy, it blinks but that's the ipw driver. I'll try ipw now.

---

### Post by unicynic on 2008-04-26
I tried the eth1 alias with both ipw3945 and iwl3945.

The result is the same. Only after suspend would the wifi keys work and dmesg will show that the driver is registered. Before suspend, nope.

So, I suspend. Resume, and check dmesg. It says failed to register network device (error -12).

So I press the wifi key and dmesg again. It says that RF kill switch is on. Expected.

I press wifi key again and dmesg. Now it shows that iwl is alive. But I don't get any wireless. Selecting "Manual configuration" in nm-applet will show now that's there's no network devices at all.

rf_kill in /sys/bus/pci/drivers/iwl3945/..... says that it's 0 meaning that it's on.

So, I type sudo gedit /etc/modules to remove that line but it just hangs. I select menu quit to reboot, it also hangs. The system monitor applet in the panel hang ever since I select manual configuration at nm-applet.

CTRL-ALT-DEL also does not have any effect.

I click CTRL-ALT-F1 to go to another virtual console and login. sudo shutdown now also hangs. So I ctrl-alt-del at the text console and it shows the ubuntu logo to shutdown and then just hangs (blank screen with a blinking cursor). I press the power button 4 seconds to turn it off.

All these have happened twice. Once with the modules using the iwl3945 disable=0, the other with ipw.. Of course, my system uses iwl so the other one does not have effect.

So, this time I boot, I edit /etc/modules first before suspending to remove the alias line and then reboot. Wifi now works. My mistake. I should have shutdown and do a cold boot... So I did that.

In a cold boot, as expected, dmesg shows that rf kill switch is on. So, I press suspend and then resume. Dmesg shows failed to register net device. Press wifi key and dmesg shows rf kill switch on. Press wifi key again and now iwl is alive. But still no wireless and manual configuration from nm-applet also now shows no network device.

Before this, at least it will work after suspend. Now, even though I've removed the alias line you suggested, it just won't work anymore after suspend. I am confused now. It's only a simple alias in modules... shouldn't have hanged the notebook, not after it has been removed and rebooted.

Sorry if this is long but I am documenting all my steps on this PC as I am trying it on the notebook.

---

### Post by unicynic on 2008-04-26
To update the steps I've tried:

I formatted and put a fresh install of Hardy. Still no wireless unless I suspend and resume. Tried the suggestion in /etc/modules. No luck. Suspend and resume, and then it works after pressing Fn+F5 to enable wifi. But somehow, couldn't connect to the adhoc network with internet connection sharing - no matter what key I used (ascii, hex, passphrase). No problem with XP.

So, I went out and bought a Belkin wireless modem/router. Cost me quite some money - not the cheapest around but well... cheap ones may cause problems, I've heard.

No problems connecting in non-secure mode. Once wpa2 is enabled, cannot connect. Then tried wpa. Still can't. Then tried wep, still can't. I got really confused and frustrated and so I turned off the notebook and let it cool down.

Here I am. Started it up and it works - after suspend+resume. I've already tried rebooting, shutdown, cold boot, doesn't work. Let the heat dissipates, it works. Heat problem?

Then decided to test chili's suggestion. Realized that in Hardy, iwconfig shows that it's on wlan0, instead of eth1. So used that in /etc/modules. Shutdown. Cold boot. No change. Still had to suspend > resume > fn+f5 before wireless works (and bluetooth + sound too).

So I guess it's back to studying the suspend and resume scripts to see what's going on. I don't know much of Linux although I've been using it since Caldera 1.0 / Red Hat 4.0 because I don't use it as my main OS until now.

---

