---
title: "Wi-Fi works only 10-15 minutes"
date: 2014-12-13
forum: Networking &amp; Wireless
---

### Post by nedim4 on 2014-12-13
Hi there,

I'm new Ubuntu (xubuntu) user and there are really some strange problems with my Wi-Fi. It works only for 10-15 minutes. After that, I should restart my notebook and it will work again for 10-15 minutes.

With ethernet cable it works correctly without any problem.

I just wonder if someone could help me.

Thank you.

---

### Post by pfeiffep on 2014-12-13
Possibly a power saving setting on your wifi??

---

### Post by nedim4 on 2014-12-13
I don't think so. Adapter is turned on and still same problem.

---

### Post by pfeiffep on 2014-12-13
> **nedim4 said:**
> I don't think so. Adapter is turned on and still same problem. I wasn't explicit ... I meant power management on your laptop ... [Check this out]("http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on")

---

### Post by nedim4 on 2014-12-16
I did this:

> [COLOR=#333333][FONT=UbuntuRegular]Wireless powermanagement is run by a hook in [/FONT][/COLOR]pm-utils[COLOR=#333333][FONT=UbuntuRegular]. You can turn it off in any of the following way:[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]Create a file in /etc/pm/config.d . I have named it blacklist:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]gksu gedit /etc/pm/config.d/blacklist and inside the file keep:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]HOOK_BLACKLIST="wireless"[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]If you want to disable any other hooks, default hooks are located at /usr/lib/pm-utils/power.d/[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]OR[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]You can just create an empty hook in either /etc/pm/sleep.d or /etc/pm/power.d See which one works for you. i.e.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Just do[/FONT][/COLOR]
sudo touch /etc/pm/sleep.d/wireless[COLOR=#333333][FONT=UbuntuRegular] OR [/FONT][/COLOR]sudo touch /etc/pm/power.d/wireless

But nothing happend. The problem is still there. 

This is my iwconfig:

> eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 28:10:7B:60:FB:98   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0




---

