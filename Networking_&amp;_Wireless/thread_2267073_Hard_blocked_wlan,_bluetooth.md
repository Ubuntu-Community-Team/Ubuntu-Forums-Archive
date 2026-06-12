---
title: "Hard blocked wlan, bluetooth"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by kosmozfr on 2015-02-27
Hi :)
Here is the output of the wireles_script : [link]("https://drive.google.com/open?id=0ByB5L4XS8rLudE1ERHI2WjVYUWs&authuser=0")
I actually have a lenovo ThinkPad T410, and my wifi / bluetooth always worked, but since like two weeks ( I was on Manjaro at the time, switched to Ubuntu now ), my computer is like on Airplane mode. I have a button combo to switch it on and off, but it doesn't change anything :/

Here is the output of rfkill list :
```

[COLOR=#000000][FONT=Arial]0: tpacpi_bluetooth_sw: Bluetooth[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Soft blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Hard blocked: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1: tpacpi_wwan_sw: Wireless WAN[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Soft blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Hard blocked: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2: phy0: Wireless LAN[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Soft blocked: no[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Hard blocked: yes[/FONT][/COLOR]

```

Is there a solution ? :/

---

### Post by TheFu on 2015-02-27
**sudo rfkill unblock {number}**

The {number} comes from **rfkill list** and changes.

If you need more control, the manpage has details.

---

### Post by jeremy31 on 2015-02-27
Any chance this is the reason [http://coldfusion-guy.blogspot.com/2011/03/lenovo-thinkpad-t410-wireless.html](http://coldfusion-guy.blogspot.com/2011/03/lenovo-thinkpad-t410-wireless.html)

---

### Post by kosmozfr on 2015-02-27
> **jeremy31 said:**
> Any chance this is the reason [http://coldfusion-guy.blogspot.com/2011/03/lenovo-thinkpad-t410-wireless.html](http://coldfusion-guy.blogspot.com/2011/03/lenovo-thinkpad-t410-wireless.html)
Awesome !! I can't believe it was that tiny little switch ! Thanks a lot !

---

