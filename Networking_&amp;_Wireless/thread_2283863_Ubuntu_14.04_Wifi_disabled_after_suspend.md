---
title: "Ubuntu 14.04: Wifi disabled after suspend"
date: 2015-06-25
forum: Networking &amp; Wireless
---

### Post by john-assy on 2015-06-25
[COLOR=#111111][FONT=Ubuntu]I recently bought a new HP pavilion 15 (has windows 8) and installed (dual boot) a fresh version of ubuntu 14.04 (64bit).

After installation, the built-in wifi wasn't working so i used a usb wifi stick to connect to Internet. Few minutes later, i tried the built-in wifi and it started working fine.

However i noticed that it gets disabled after i suspend and re-relogin. The wifi switch gets greyed and can't click it anymore and i see the message "wifi is disabled by hardware switch), although there's no hardware switch in this HP.

The only solution to get the wifi back is by restart (and that's really annoying).

I spent days trying solutions that i found for similar problems in this forum and other websites but with no luck.

The ```
sudo rfkill list
``` displays the following:
```

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```
The unblock command doesn't change anything.

(wifi works well on windows)

Please help me find a solution for this problem.[/FONT][/COLOR]

---

### Post by Elizine on 2015-06-25
Hi,

Please go through this tutorial on YouTube - [https://www.youtube.com/watch?v=4VVosf9p5GM](https://www.youtube.com/watch?v=4VVosf9p5GM)

Hope this will help you.

---

### Post by john-assy on 2015-06-26
Thanks but it doesn't really help. wifi is working but gets disabled after suspend.

> **Elizine said:**
> Hi,

Please go through this tutorial on YouTube - [https://www.youtube.com/watch?v=4VVosf9p5GM](https://www.youtube.com/watch?v=4VVosf9p5GM)

Hope this will help you.

---

### Post by steveo314 on 2015-06-26
> **john-assy said:**
> [COLOR=#111111][FONT=Ubuntu]I recently bought a new HP pavilion 15 (has windows 8) and installed (dual boot) a fresh version of ubuntu 14.04 (64bit).

After installation, the built-in wifi wasn't working so i used a usb wifi stick to connect to Internet. Few minutes later, i tried the built-in wifi and it started working fine.

However i noticed that it gets disabled after i suspend and re-relogin. The wifi switch gets greyed and can't click it anymore and i see the message "wifi is disabled by hardware switch), although there's no hardware switch in this HP.

The only solution to get the wifi back is by restart (and that's really annoying).

I spent days trying solutions that i found for similar problems in this forum and other websites but with no luck.

The ```
sudo rfkill list
``` displays the following:
```

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```
The unblock command doesn't change anything.

(wifi works well on windows)

Please help me find a solution for this problem.[/FONT][/COLOR]

See how far you get with this:
```
sudo touch /etc/pm/sleep.d/wakenet.sh

sudo chmod +x /etc/pm/sleep.d/wakenet.sh

sudo gedit /etc/pm/sleep.d/wakenet.sh

Insert the following lines:
   #!/bin/bash
   case "$1" in
   thaw|resume)
   nmcli nm sleep false
   ;;
   *)
   ;;
   esac
   exit $?

Save
```

found [here]("http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153")

---

### Post by john-assy on 2015-06-30
Unfortunately it didn't work :sad::sad::sad::sad:

> **steveo314 said:**
> See how far you get with this:
```
sudo touch /etc/pm/sleep.d/wakenet.sh

sudo chmod +x /etc/pm/sleep.d/wakenet.sh

sudo gedit /etc/pm/sleep.d/wakenet.sh

Insert the following lines:
   #!/bin/bash
   case "$1" in
   thaw|resume)
   nmcli nm sleep false
   ;;
   *)
   ;;
   esac
   exit $?

Save
```

found [here]("http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153")

---

