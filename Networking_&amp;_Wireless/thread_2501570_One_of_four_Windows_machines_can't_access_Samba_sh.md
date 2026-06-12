---
title: "One of four Windows machines can't access Samba share"
date: 2024-10-13
forum: Networking &amp; Wireless
---

### Post by Dave_Davis on 2024-10-13
[COLOR=#141618][FONT=Lato]I've just built a new Ubuntu server and set up samba shares for myself and my wife.[/FONT][/COLOR]

[FONT=arial][COLOR=#141618]Two hard wired windows machines access shares with no problem[/COLOR]
[COLOR=#141618]Two Android tablets access shares with no problem.

[/COLOR]Laptop accesses shares wirelessly.

[COLOR=#141618]However, one Windows (W10) wireless machine  connects but access to shares is denied). It sees the shares but simply can't access them.[/COLOR]
[COLOR=#141618]I've rebooted several times  to no avail

 It did connect to my old server.[/COLOR]


[COLOR=#141618]Any suggestions?[/COLOR]

[COLOR=#141618]Thanks,[/COLOR]
[COLOR=#141618]-dmd-[/COLOR][/FONT]

---

### Post by Morbius1 on 2024-10-14
Questions:

[1] What version of Ubuntu are you using?

[2] Are all the Windows >= Win10?

[3] Are you using Ubuntu Server or Ubuntu Desktop as a server?

[4] Ubuntu Server doesn't run avahi by default so did you install it?
```
sudo apt install avahi-daemon
```

[5] Neither Ubuntu's install wsdd ( windows host discovery protocol ) so did you install that?

If Ubuntu 24.04:
```
sudo apt install wsdd-server
```
If < Ubuntu 24.04:
```
sudo apt install wsdd
```

[6] How is your samba server set up?

The output of this command will tell us that:
```
testparm -s
```

---

### Post by Dave_Davis on 2024-10-15
Thanks for this.  

Version 24.04.1  LTS

3 Win10 machines / 1 w11 machine

Ubuntu desktop

Installed [COLOR=#000000][FONT=&quot]wsdd-server no change

The server has...
2 internal NVME
2 internal SSD + internal SSD boot
1 USB connect SSD

When I create a share from an NVME it can't be accessed by one of the three Win10 machines.  The other two have no problem.  Win11 machine has no problem.

Any share created on an internal (or USB connected) drive is accessed by ALL machines.

So, it seems that I can't share anything on the NVME drives with the one specific Win 10 machine.  I've been over ownership several times and can't find any problems.

Thanks,
-dmd-

[/FONT][/COLOR]

---

