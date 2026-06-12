---
title: "Ubuntu 18.04 suspend hardblocking bcm43142 wifi"
date: 2019-05-13
forum: Networking &amp; Wireless
---

### Post by hopefeda on 2019-05-13
[COLOR=#222222][FONT=Verdana]Hello everyone,[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I am using ubuntu 18.04 on a dual booted HP Pavilion Notebook -17-g005nx (ENERGY STAR). (ubuntu/windows 10) UEFI with secure boot.I'm also using a cheap chinese usb wifi adapter/antenna for better wireless connection.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Upon bootup from OFF state, both cards work properly. However, after a wakeup from suspend both get disabled and produce the following:[/FONT][/COLOR]

```

[COLOR=#222222][FONT=Verdana]user@computer:~$ rfkill list all[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]4:phy2: Wireless LAN[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Softblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Hardblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]13:phy7: Wireless LAN[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Softblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Hardblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]14:brcmwl-0: Wireless LAN[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Softblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Hardblocked: yes[/FONT][/COLOR]

```

**[COLOR=#222222][FONT=Verdana]What I tried:[/FONT][/COLOR]**

**[COLOR=#222222][FONT=Verdana]After checking:[/FONT][/COLOR]**
```

[COLOR=#222222][FONT=Verdana]user@computer:~$ lspci -knn[/FONT][/COLOR]

```

**[COLOR=#222222][FONT=Verdana]..scrolling down to bcm43142[/FONT][/COLOR]**
```

[COLOR=#222222][FONT=Verdana]08:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142802.11b/g/n [14e4:4365] (rev 01)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]            Subsystem:Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]            Kernelmodules: bcma, wl[/FONT][/COLOR]

```

[B][COLOR=#222222][FONT=Verdana]...reseting bcma/wl module
[/FONT][/COLOR][/B]```

[COLOR=#222222][FONT=Verdana]user@computer:~$ sudo modprobe -r bcma[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]user@computer:~$ sudo modprobe bcma[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]user@computer:~$ sudo modprobe -r wl[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]user@computer:~$ sudo modprobe wl[/FONT][/COLOR]

```

but it didn't work..

**[COLOR=#222222][FONT=Verdana]However: [/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana]disabling wl module, which disables BCM43142, enables the cheap usb wifi. Resetting it back however disables both of them again.[/FONT][/COLOR]

[B][COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR][/B]**[COLOR=#222222][FONT=Verdana]Also tried: [/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana]creating a file called config inside /etc/pm/config.d/ and giving it executable permission (chmod +x). Also tried putting the file inside /etc/pm/sleep.d.
```

user@computer:~$[/FONT][/COLOR]cat /etc/pm/config.d/config
SUSPEND_MODULES="wl0,rt2800usb"

```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]

But none of these helped so far.. How can I get around this issue?

---

### Post by chili555 on 2019-05-13
If the cheap Chinese USB works better, why do you need the internal Broadcom to work at all? Why not simply blacklist *wl*?

---

### Post by hopefeda on 2019-05-13
The cheap Chinese USB wifi is kind of huge and not practically portable.. So when I move around with my laptop I still need my built-in wifi and the ubuntu suspend functionality. Initially, I wanted to hibernate but since Linux can't deal with Secure Boot and hibernation I just settled for suspend, which also turns out to be problematic. What good is a laptop nowadays with not sleep and hibernation functionalities? This is why I want to take the hard road and fix the issue rather than just opting back into windows.

---

