---
title: "Wireless drops on Ubuntu 20.04 on Acer Aspire 5 A514-52"
date: 2020-05-29
forum: Networking &amp; Wireless
---

### Post by tomsax on 2020-05-29
Can work after upgrading/updating or on first booting up but wielwaa connection then drops and nothing.  Icon says wireless is on in top right but firefox doesn't load any page.

Attaching diagnostics file.

Tom

---

### Post by chili555 on 2020-05-30
First, there are two SSIDs with the same name, VM6698172. One is the 2.4 gHz segment and the other is the 5 gHz segment of, I assume, the same router. I am quite confident that you have told Network Manager to connect automagically to VM6698172 when available and that your dropping is the wireless device hopping from one instance of VM6698172 to the other, always looking for a better connection, sort of like my ex-girlfriend! 

I suggest that you rename one or both to prevent this. Perhaps VM6698172-2.4 and VM6698172-5.

Next, we see several things that you might tweak to make your connection even better.

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Any improvement?

---

### Post by tomsax on 2020-06-06
I tried to follow the instruction above but found them difficult to interpret.  I thought it has improved but I still keep losing wifi.

In my list of wifi I seem to have the one I expect to see (my modum on Virgin Media) but I also see a strong Virgin Media signal.  I thought it might be a duplicate.  I renamed my wifi in settings.  

When you say check the setting in the wifi router is that in settings>wifi?  In settings.wife I don't have the opion of choosing WPA2-AES.  

I don't know how to change to "channel width of 20 MHz in the 2.4 GHz band" I'm afraid.  How do I do that?  And how do I set the other router settings.  It's not obvious to me but I might be being dumb.

I seemed to be able to implement the other commands in terminal as recommended with GB for country code.

Sorry I need more help.

---

### Post by chili555 on 2020-06-06
>  I don't have the opion of choosing WPA2-AES.
What are the choices? Maybe we can find one we like. 

I suspect that the dropping occurs when some setting in the router is set to autoselect and switches away from your wireless device that is going along perfectly well. Thus we do NOT want WPA or WPA2 autoselect. We want the most secure WPA2.

We do NOT want autoselect AES (sometimes referred to as CCMP) or TKIP. We want the more secure WPA2-AES.

We do NOT want to autoselect a channel. We want a fixed channel 1. 6 or 11.

We do NOT want autoselect 20 MHz or 40 MHz channel width. We know that most Linux drivers work much better at 20 MHz channel width.

If you still need help, please let me know the exact brand and model of your router. I'll find the setup pages in the manual on line and recommend settings for you.

---

### Post by tomsax on 2020-06-07
The problem is I don't know/can't see how to choose these options.  Here are some screenshots that show what I can see.

[ATTACH=CONFIG]286137[/ATTACH][ATTACH=CONFIG]286138[/ATTACH][ATTACH=CONFIG]286139[/ATTACH][ATTACH=CONFIG]286140[/ATTACH][ATTACH=CONFIG]286141[/ATTACH]

One photo shows all the options of "security" I have.

One I think shows the brand and model of router.


Tom

---

### Post by chili555 on 2020-06-07
These all click to "Invalid Attachment." Please try again.

---

### Post by tomsax on 2020-06-07
sorry trying again.

The problem is I don't know/can't see how to choose these options. Here are some screenshots that show what I can see.

[ATTACH=CONFIG]286142[/ATTACH][ATTACH=CONFIG]286143[/ATTACH][ATTACH=CONFIG]286144[/ATTACH][ATTACH=CONFIG]286145[/ATTACH][ATTACH=CONFIG]286146[/ATTACH]

One photo shows all the options of "security" I have.

One I think shows the brand and model of router.

---

### Post by CelticWarrior on 2020-06-07
The aforementioned settings are to be changed at the router.

---

### Post by chili555 on 2020-06-07
> **CelticWarrior said:**
> The aforementioned settings are to be changed at the router.Yes, indeed. Not in your own computer; in the router.

---

### Post by tomsax on 2020-06-07
Oh I see I can go to into my route.   I'm sure I should know that.  I have now gone in and changed some things making only 20 Mhz possible and not other option.  I'll  see if that helps.

---

### Post by chili555 on 2020-06-07
> **tomsax said:**
> Oh I see I can go to into my route.   I'm sure I should know that.  I have now gone in and changed some things making only 20 Mhz possible and not other option.  I'll  see if that helps.Please review my answer above. Please make *all* of the changes that I recommended in the router.

---

### Post by tomsax on 2020-06-13
The good news is that when the wifi is working, it is working and not dropping off now.  Thanks very much chilli555 for your help and undestanding.  The bad thing is that sometimes when I boot up on ubuntu there is no wifi at all.  It says "no router available/detected" or such like.  

Usually when I restart and boot up again it is then there but it is still a pain.

Any info on how to get it working without rebooting or how to solve this problem?

---

### Post by chili555 on 2020-06-13
Is this a dual boot with Windows? Could this be the issue? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

When there is no wireless, what does this tell us?

```
lsmod | grep iwl
dmesg | grep -e iwl -e 14.3
```

> it is working and not dropping off now.
Awesome! That's great news.

---

### Post by tomsax on 2020-06-22
Hi,

Sorry I have been distracted by work.  it doesnt seem to be the fast boot issue.

I run the commannds and copy results below:

tom@tom-Aspire-A514-52:~$ lsmod | grep iwl
iwlmvm                380928  0
mac80211              843776  1 iwlmvm
iwlwifi               331776  1 iwlmvm
cfg80211              704512  3 iwlmvm,iwlwifi,mac80211
tom@tom-Aspire-A514-52:~$ dmesg | grep -e iwl -e 14.3
[    0.048191] Memory: 3643116K/3890164K available (14339K kernel code, 2397K rwdata, 4952K rodata, 2712K init, 4992K bss, 247048K reserved, 0K cma-reserved)
[    0.142322] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS01._UPC], AE_ALREADY_EXISTS (20190816/dswload2-326)
[    0.142324] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.142325] ACPI: Skipping parse of AML opcode: Method (0x0014)
[    0.142326] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS01._PLD], AE_ALREADY_EXISTS (20190816/dswload2-326)
[    0.142328] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[    0.142329] ACPI: Skipping parse of AML opcode: Method (0x0014)
[    0.214231] pci 0000:00:14.2: [8086:02ef] type 00 class 0x050000
[    0.215082] pci 0000:00:14.3: [8086:02f0] type 00 class 0x028000
[    0.215107] pci 0000:00:14.3: reg 0x10: [mem 0x91318000-0x9131bfff 64bit]
[    0.215265] pci 0000:00:14.3: PME# supported from D0 D3hot D3cold
[    0.291413] clocksource: Switched to clocksource tsc-early
[    2.843105] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-50.ucode failed with error -2
[    2.843425] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-49.ucode failed with error -2
[    2.845858] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    2.845862] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    2.845863] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    2.846260] iwlwifi 0000:00:14.3: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[    2.885075] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x354
[    2.893120] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    2.894374] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    3.038833] iwlwifi 0000:00:14.3: base HW address: 04:33:c2:b9:4b:28
[    3.291476] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[    5.259235] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    5.403700] iwlwifi 0000:00:14.3: FW already configured (0) - re-configuring
[    5.414590] iwlwifi 0000:00:14.3: BIOS contains WGDS but no WRDS
tom@tom-Aspire-A514-52:~$

---

### Post by chili555 on 2020-06-23
> [ 2.846260] iwlwifi 0000:00:14.3: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[ 2.885075] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x354
[ 2.893120] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[ 2.894374] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[ 3.038833] iwlwifi 0000:00:14.3: base HW address: 04:33:c2:b9:4b:28
[ 3.291476] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0Nothing here suggests that the wireless is not working as expected. Does the interface show up here?

```
ip addr show
```

Does it scan and see networks?

```
nmcli device wifi list
```

Is the Network Manager icon present?

[IMG]https://images.techhive.com/images/article/2014/07/ubuntu-networkmanager-menu-100360176-large.png[/IMG]

Is Network Manager running?

```
ps aux | grep etwork
```

Does it try but fail to connect?

---

### Post by tomsax on 2020-06-24
It was working when I ran that command.  Its just when I boot up from dual boot sometimes there is no wifi icon, no wifi and I have to reboot again.  Then it usually appears on second attempt.  I think when I look for wifi it says "no adaptor detected" or such like.  

I'll try those commands tonight and tell you what I get tonight or tomorrow.

Tom

---

### Post by chili555 on 2020-06-24
> **tomsax said:**
> It was working when I ran that command.  Its just when I boot up from dual boot sometimes there is no wifi icon, no wifi and I have to reboot again.  Then it usually appears on second attempt.  I think when I look for wifi it says "no adaptor detected" or such like.  

I'll try those commands tonight and tell you what I get tonight or tomorrow.

TomDid you check Fast Boot as I suggested in post #13?

---

### Post by CelticWarrior on 2020-06-24
It seems the issue isn't about Fast Boot (UEFI feature, OS agnostic) but Fast Startup (Windows feature). In the link the terms are used interchangeably where they shouldn't:

> **About dual-boot with Windows and "fast-boot" enabled**

    If you have a dual-boot machine with a recent version of Windows and  start seeing problems during initialization of the WiFi device when  booting Linux, the problem could be due to the **“fast startup”** feature on  Windows. 



It's always recommended to disable Fast Startup when dual-booting and [arguably also with Windows alone]("https://www.windowscentral.com/how-disable-windows-10-fast-startup").

---

### Post by tomsax on 2020-06-29
Finally managed to sort this out using the above (re: fast boot).  Many thanks for your help.

---

