---
title: "Dell Latitude; Network &gt; Wireless shows all networks out of range."
date: 2017-11-26
forum: Networking &amp; Wireless
---

### Post by oldbotbuilder on 2017-11-26
[FONT=arial]My computer is a Dell Latitude E6420 laptop.  [/FONT][FONT=arial][FONT=arial]Ubuntu is the only OS on this PC.
I am using Ubuntu for a ROS environment.

The WiFi has worked on this machine with Ubuntu, but now all networks show "Out of range."

I am connected to the internet via wired connection.

[/FONT]  My pastebin is [http://paste.ubuntu.com/26074356/](http://paste.ubuntu.com/26074356/)

 I have spent many days trying to resolve the problem w[SIZE=2]ith no succes[/SIZE]s.
I have tried:

[/FONT][SIZE=2]*[FONT=arial]sudo systemctl restart network-manager[/FONT]*
[/SIZE]
[SIZE=2][FONT=arial]    *sudo service network-manager restart*    
Did not help,  All Networks still indicate "Our of range"
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Reinstalling Broadcom Corp. BCM43228 802.11a/b/g/n did not help.
[/FONT][/SIZE]
[SIZE=2][FONT=arial] *rfkill unblock* all did not work.
[/FONT][/SIZE]
[SIZE=2][FONT=arial]*rfkill list*     results are: 
[/FONT][/SIZE]
[SIZE=2][FONT=arial]0: phy0: Wireless LAN[/FONT][/SIZE]
        [SIZE=2][FONT=arial]    Soft blocked: no[/FONT][/SIZE]
        [SIZE=2][FONT=arial]    Hard blocked: no[/FONT][/SIZE]
[SIZE=2][FONT=arial]1: brcmwl-0: Wireless LAN[/FONT][/SIZE]
        [SIZE=2][FONT=arial]    Soft blocked: no[/FONT][/SIZE]
        [SIZE=2][FONT=arial]    Hard blocked: no[/FONT][/SIZE]
[SIZE=2][FONT=arial]2: dell-wifi: Wireless LAN[/FONT][/SIZE]
        [SIZE=2][FONT=arial]    Soft blocked: no[/FONT][/SIZE]
        [SIZE=2][FONT=arial]    Hard blocked: no    
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Tried Ubuntu Wireless network troubleshooter
[/FONT][/SIZE]
     [SIZE=2][FONT=arial]    Verified Network is On[/FONT][/SIZE]
    [SIZE=2][FONT=arial]*    nmcli device* shows:
[/FONT][/SIZE]
[SIZE=2][FONT=arial]DEVICE    TYPE              STATE                   CONNECTION  [/FONT][/SIZE]
[SIZE=2][FONT=arial]eno1           ethernet        connected          eno1        [/FONT][/SIZE]
[SIZE=2][FONT=arial]wlp3s0      wifi                  disconnected    --          [/FONT][/SIZE]
[SIZE=2][FONT=arial]lo                 loopback       unmanaged          --   

None of the Wireless network troubleshooter suggestions helped.[/FONT][/SIZE]

 My robot development attempt has come to an end.

Please help.

Thank you

[FONT=Courier 10 Pitch]



[/FONT]

---

