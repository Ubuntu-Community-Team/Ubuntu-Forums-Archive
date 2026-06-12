---
title: "WI-Fi disconnects itself on Asus UX301"
date: 2015-01-19
forum: Networking &amp; Wireless
---

### Post by al.adab on 2015-01-19
hello,

the problem - I understand - has repeatedly been reported: specifically to my Asus UX301, on an (average) 100 to 120 MBit/s connection, the connection is gone every (roughly) half an hour. Which leads me to regularly have to suspend Ubuntu 14.04, to re-activate it to get the connection back. This is a home-connection, and if I get closer to the router, the maximum speed I get is about 160 MBit/s. At that speed, the connection usually remains stable for much longer, though it does occasionally disconnect (I wonder whether it does when the speed rate drops). My flatmate doesn't have any problem at either speed rate (old ThinkPad with Win XP...). 

I can't seem to find any workaround. Here's my CPU info: 

[I]vendor_id	: GenuineIntel
cpu family	: 6
model		: 69
model name	: Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
stepping	: 1
microcode	: 0x15
cpu MHz		: 759.000
cache size	: 3072 KB
physical id	: 0[/I]

I also tried and run *wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script* whose result I'm posting in attachment if it's of any help. 

Can you please help out? Please let me know if you need further info. Thanks!

---

### Post by chili555 on 2015-01-19
You attached the script itself. We need the result that is returned after you run the script on your system.

---

### Post by al.adab on 2015-01-19
you're right, sorry. 

the thing is that...I typed in *wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5...ireless_script](https://dl.dropbox.com/s/qjc87hzk1z5...ireless_script) && chmod +x wireless_script && ./wireless_script * again, got the following

    [I]DONE! All results saved in -

		 File Name: 	"wireless-info.txt" 
		 Directory: 	"/home/xxxx"[/I]

but the *wireless-info.txt* appears to be empty (at least I can't see any text in it...).

---

### Post by chili555 on 2015-01-19
I don't know exactly where you got the commands but I just tried this by copy and paste: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) 

It works for me.

---

### Post by al.adab on 2015-01-19
thanks tons, it looks like i used the wrong script. 
Plz see result in attachment. Thanks.

---

### Post by chili555 on 2015-01-19
It looks just perfect! That's the problem; it shows no clues as to what's going wrong. After it disconnects, please run and post:```
dmesg | grep iwl
```Thanks.

---

### Post by al.adab on 2015-01-19
thanx for your help! 
I'll be able to post the result tonight or tomorrow when I'm back home.

---

### Post by al.adab on 2015-01-21
so here you go: 
[I]
~$ dmesg | grep iwl

[    1.757306] iwlwifi 0000:02:00.0: irq 58 for MSI/MSI-X

[    1.814069] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm

[    1.911332] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144

[    1.911876] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled

[    1.912100] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled

[    2.127936] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'

[    4.280790] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled

[    4.281047] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled[/I]

---

### Post by chili555 on 2015-01-21
As you can probably see, it still looks perfect! 

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if performance is improved.

---

### Post by al.adab on 2015-01-21
I really appreciate your help! Thanks!

Can you please bear with me a little bit longer and point me to the right direction as where to find info on checking/modifying the router settings - and in particular how to set the router to be on WPA2-AES?

many thanks again.

---

### Post by chili555 on 2015-01-21
> **al.adab said:**
> I really appreciate your help! Thanks!

Can you please bear with me a little bit longer and point me to the right direction as where to find info on checking/modifying the router settings - and in particular how to set the router to be on WPA2-AES?

many thanks again.Log in to the administration pages of the router. Consult the manual, usually available on line, and enter the gateway address in the address bar of your browser. Often, the address is something similar to 192.168.1.1. Select 'Wireless Settings' or similar and look for the encryption settings. Here is an example: [http://www.lawtechguru.com/images/SelectAES.jpg](http://www.lawtechguru.com/images/SelectAES.jpg)

Be sure to then save and reboot the router.

---

### Post by al.adab on 2015-02-03
I can only hope it's not too late to follow up on this thread...

finally i learnt a few things about router settings: it's been set on WPA2-AES for a few days now, though i couldn't find anything about channel speed, though i could chose to connect through an 11-channel. My regulatory domain is set correctly, the IPv6 is set on "ignore", and I run the *sudo -i* + *echo "options iwlwifi 11n_disable=8" >> /etc/modprobe.d/iwlwifi.conf* + *exit* commands. 

I have to say that the connection is much more stable - it disconnected itself only three times over the past four days. I'm hesitant to edit the post as "solved", perhaps I could give further feedback in a few days?

thanks tons in the meantime for your help!

---

### Post by chili555 on 2015-02-03
>  perhaps I could give further feedback in a few days?

thanks tons in the meantime for your help!Certainly. We look forward to your report.

---

