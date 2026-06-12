---
title: "Bluetooth connection to Microsoft Sculpt Mouse regression"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by zardoz262 on 2017-10-27
I have both an old Dell BT mouse and a newer (12 months old) Microsoft Sculpt Comfort mouse.  I have been using the Microsoft mouse on 16.04, 16.10 and 17.04 without any problems.

This week I upgraded to 17.10 and now the MS mouse is not connecting.  I have occasionally get a connection but mostly not.  If I put the mouse into discovery mode I can occasionally connect.

The old Dell BT mouse is working flawlessly.

I assume the newer mouse must be using some newer protocol which is now causing problems.  A connection results in:

[FONT=monospace][COLOR=#000000]Oct 28 09:51:14 carbon bluetoothd[7657]: Can't get HIDP connection info[/COLOR]
Oct 28 09:51:19 carbon bluetoothd[7657]: connect [COLOR=#ffffff]error[/COLOR][COLOR=#000000]: Host is down (112)[/COLOR]

[/FONT]A scan returns this when the mouse is in discovery:

[FONT=monospace][COLOR=#000000]root@carbon:/var/log# hcitool scan[/COLOR]
Scanning ...
        C0:33:5E:04:8E:63       Microsoft Sculpt Comfort Mouse
[/FONT][FONT=monospace][COLOR=#000000]root@carbon:/var/log# hcitool inq[/COLOR]
Inquiring ...
        C0:33:5E:04:8E:63       clock offset: 0x00db    class: 0x002580

[/FONT] [FONT=monospace][FONT=arial]The BT mouse returns the following:
[/FONT]
[/FONT][FONT=monospace][COLOR=#000000]root@carbon:/var/log# hcitool con[/COLOR]
Connections:
        > ACL 00:07:61:5B:B1:8A handle 11 state 1 lm MASTER  
root@carbon:/var/log# 

[/FONT][FONT=monospace][FONT=arial]As I said, I've been using this mouse for a year without fault so this is some specific to the versions of things (?) in 17.10.  I did try downgrading the kernel to 4.10 from 17.04 and it made no difference.  This morning I upgraded the 4.13 to 4.14 and it's still the same.

Once when I did get it to connect I saw the string "CRYPT" at the end of the hcitool con output so it's not the same connection that's being attempted. 

I just don't know where to look from here.  I'm not familiar with the hci commands.

Help!

Brett[/FONT][/FONT]

---

### Post by mörgæs on 2017-10-29
Hi, welcome to the fora.

Have you tried if it's the same pattern in Lubuntu 17.10?

---

### Post by zardoz262 on 2017-10-29
> **mörgæs said:**
> Hi, welcome to the fora.

Have you tried if it's the same pattern in Lubuntu 17.10?

I'm pretty sure it's not the window manager.  The rest should be the same.

Brett

---

### Post by mörgæs on 2017-10-29
When I am troubleshooting something myself I am not satisfied with 'should'. I want real proof.

It's not only about the window manager. There have been reports about the mouse behaving strangely under Wayland which is worth investigating. 

Besides, I am not sure that Ubuntu and Lubuntu use the same Bluetooth packages. Both of these possible explanations can easily be tested in Lubuntu 17.10.

---

### Post by zardoz262 on 2017-10-29
This laptop is my primary work device.  I also am a plasma user.  I'm not going to reinstall the laptop with lubuntu for a test of a mouse 

Also I think you're mistaken when you say that kubuntu 17.10 and lubuntu 17.10 use different underlying bluetooth packages.   Both those distros are just modified user environments on top of the same base.

Oh and thanks for your sage wisdom on troubleshooting.

---

### Post by wwwbrowse on 2017-11-14
Has there been any developments on this issue as I have the same problem.

---

### Post by kouber on 2017-12-05
I am experiencing the same problem. Not able to connect my bluetooth mouse since I upgraded to 17.10.

HP Spectre & Z5000 HP mouse

---

### Post by kouber on 2017-12-05
Found a workaround in one of the bug reports: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1729389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1729389)

In comment #17 you can see.

Simply add:

[B][COLOR=#333333][FONT=monospace]options iwlwifi bt_coex_active=0

[/FONT][/COLOR][/B][COLOR=#333333][FONT=monospace]to the end of:

[/FONT][/COLOR]**[COLOR=#333333][FONT=monospace]/etc/modprobe.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]d/iwlwifi.[/FONT][/COLOR]**[COLOR=#333333][FONT=monospace]**conf**

 and reboot.[/FONT][/COLOR]

---

