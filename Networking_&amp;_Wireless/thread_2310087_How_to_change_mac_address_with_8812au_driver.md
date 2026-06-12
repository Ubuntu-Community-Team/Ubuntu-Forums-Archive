---
title: "How to change mac address with 8812au driver"
date: 2016-01-16
forum: Networking &amp; Wireless
---

### Post by Landmine on 2016-01-16
I'm using this driver for my wireless usb [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) 

The problem with this driver is that is keeps resetting the mac address to the original each time an attempt to change it is made (no matter what kind)

I guess there might be something to change in the driver's code or something to enable this

Does anyone know how can I change the mac address using this driver?

I have tried all the traditional ways with no success. Also tried several other versions of the same driver like:

[https://github.com/Grawp/rtl8812au_rtl8821au](https://github.com/Grawp/rtl8812au_rtl8821au)

**I presume there is an option to read the mac from file with this driver**, but where is this file and how can I use this feature?

I found this feature in the 'make' file and I edited it to include it. Basically all one has to do is put 'y' on the feature the user wants to use in the 'make' file then compile. It says something like read_phy_from_file, but I dont know where the file is
 
If there is some other way to force change the mac address please advice.

Thanks

---

### Post by papibe on 2016-01-16
Hi Landmine. Welcome to the forum ):P

Change MAC:
[LIST]
[*]Open 'Network Connections'.
[*]Select the connection you want to change (for instance, either wired over ethernet or wireless).
[*]Press the 'Edit' button.
[*]Go to either the tab 'Ethernet', or WiFi depending on which interface you selected.
[*]Edit the MAC field.
[*]Press 'Save.
[*]
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Landmine on 2016-01-17
> **papibe said:**
> Hi Landmine. Welcome to the forum ):P

Change MAC:
[LIST]
[*]Open 'Network Connections'. 
[*]Select the connection you want to change (for instance, either wired over ethernet or wireless). 
[*]Press the 'Edit' button. 
[*]Go to either the tab 'Ethernet', or WiFi depending on which interface you selected. 
[*]Edit the MAC field. 
[*]Press 'Save. 
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

Thanks for your kind welcome

I have **updated the thread info** to include more information about what the problem actually is

Please advice

The method you described doesnt work nor does [B]sudo ifconfig wlan0 hw ether <new mac here>

[/B]The interface just returns to the original mac address

---

### Post by Landmine on 2016-01-18
Please flex your superior knowledge on this people

I am out of ideas and this is a pain in the coco

---

### Post by chili555 on 2016-01-19
I don't know for sure because I am just a tinkerer not a dev, but I see there is a driver parameter:```
modinfo 8812.au
```...that says:```
parm:           rtw_initmac:charp
```Reading here: [http://lxr.free-electrons.com/source/drivers/staging/rtl8188eu/core/rtw_ieee80211.c#L1078](http://lxr.free-electrons.com/source/drivers/staging/rtl8188eu/core/rtw_ieee80211.c#L1078)> 1078         if (rtw_initmac && mac_pton(rtw_initmac, mac)) {
1079                 /* [COLOR="#FF0000"]Users specify the mac address[/COLOR] */
1080                 memcpy(mac_addr, mac, ETH_ALEN);Therefor, I suggest you implement the driver parameter like this:```
sudo -i
echo "options 8812au rtm_initmac=11:22:33:aa:bb:cc
exit
```Then unload and reload the module:```
sudo modprobe -rv 8812au
sudo modprobe -v 8812au
```The -v for verbose may give us clues as to the success or not of the procedure.

Check:```
ifconfig
```With luck, it now says something like:> wlp3s0    Link encap:Ethernet  [COLOR="#FF0000"]HWaddr 11:22:33:AA:BB:CC[/COLOR]
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5a94:6bff:fe99:55a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


I have never seen or tried this before and I haven't the device, so this is entirely experimental.

---

### Post by Landmine on 2016-01-20
> **chili555 said:**
> ```
sudo -i
echo "options 8812au rtm_initmac=11:22:33:aa:bb:cc
exit
```

I appreciate your input on this..

I dont know what you meant by the above?

where is the command? could you please check it for typos?

In general, how can the driver be given parameters after its installed?

did you mean its like this ? ```
modprobe 8812au options rtm_initmac=11:22:33:aa:bb:cc
```

---

### Post by chili555 on 2016-01-20
Wow. Just. Wow.

I haven't missed a post that badly in quite a while but I really missed it there! Sorry for my mis-step. Let's try this again.

Therefor, I suggest you implement the driver parameter like this:

```
sudo -i
echo "options 8812au rtm_initmac=11:22:33:aa:bb:cc"  >  /etc/modprobe.d/8812au.conf
exit
```
Then unload and reload the module:

```
sudo modprobe -rv 8812au
sudo modprobe -v 8812au
```
The -v for verbose may give us clues as to the success or not of the procedure.

Check:

```
ifconfig
```Again, I apologize for my error.> In general, how can the driver be given parameters after its installed?It is installed in the operating system with several loadable parameters. The usual process would be:```
sudo modprobe 8812au rtm_initmac=11:22:33:aa:bb:cc
```Placing the details in a conf file in modprobe.d makes the process automatic. In that way, you needn't repeat the long, complicated command every time you boot.

---

### Post by Landmine on 2016-01-21
Hello again! You are great but no one is perfect :p
> **chili555 said:**
> 

```
sudo -i
echo "options 8812au rtm_initmac=11:22:33:aa:bb:cc"  >  /etc/modprobe.d/8812au.conf
exit
```

I am not sure about what **sudo -i** supposed to mean here. There should be a command where -i is an option to.

anyway, I've implemented this manually by creating the .conf file and adding the rtm_initmac line to it and placed it in modprobe.d, so this step is done and it worked but with some issues, please keep reading

> 
```
sudo modprobe 8812au rtm_initmac=11:22:33:aa:bb:cc
```Placing the details in a conf file in modprobe.d makes the process automatic. In that way, you needn't repeat the long, complicated command every time you boot.

It worked -kind of-. This code alone makes the mac change successfully but then the driver stops discovering networks so the module needs to be unloaded/reloaded during this automation. which brings us to this part ```
sudo modprobe -rv 8812au
sudo modprobe -v 8812au
```

Could you please suggest a small script that can do all this automatically and where to place it so it runs at boot or gets triggered upon plugging the usb adapter in?

Additionally, could ```
macchanger -r wlan0
``` be included in this script so that rtm_initmac takes the output from it?

---

### Post by chili555 on 2016-01-21
> I am not sure about what sudo -i supposed to mean here. From *man sudo*:> -i, --login
                 Run the shell specified by the target user's password data&#8208;
                 base entry as a login shell.  This means that login-specific
                 resource files such as .profile or .login will be read by the
                 shell.> Could you please suggest a small script that can do all this automatically and where to place it so it runs at boot or gets triggered upon plugging the usb adapter in?I am not a shell script guy, so the larger answer is no. However, if I were to experiment, I'd place the script in /etc/rc.local right above 'exit 0'; something like:```
modprobe 8812au rtm_initmac=11:22:33:aa:bb:cc
modprobe -rv 8812au
modprobe -v 8812au
```...Or some such. 'sudo' is not needed here.

Sorry, I haven't any real experience with scripting.

---

