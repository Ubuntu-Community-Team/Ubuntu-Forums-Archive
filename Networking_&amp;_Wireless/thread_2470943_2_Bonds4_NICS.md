---
title: "2 Bonds/4 NICS"
date: 2022-01-17
forum: Networking &amp; Wireless
---

### Post by chefytim on 2022-01-17
Seeing if anyone can see what I am doing wrong.
I have 4 NICS trying to create 2 different bonds (Management/Production).

Here is what I am trying to get working now.
I keep getting a "eno4 is not defined"

> 
**network:**
  **bonds:**
    **bond0:**
      **interfaces:**
        - eno1
        - eno2
**parameters:**
   **mode:** active-backup
         **ethernets:**
            eno1: {}
            eno2: {}
  **version:** 2
  ** bridges:**
    **     br0:**
      **       addresses:**
            - 192.168.0.2/24
      **       dhcp4:** false
       **gateway4:** 192.168.0.1
      **nameservers:**
       **addresses:**
           - 192.168.0.1
        **search:** [mylab.local]
      **interfaces:**
   - bond0
    **bond1:**
      **        interfaces:**
          - eno3
          - eno4
      **parameters:**
        **mode:** active-backup
  **ethernets:**
    **    eno3:** {}
    **    eno4:** {}
  **version:** 2
  **bridges:**
    **br1:**
      **    addresses:**
        - 192.168.0.3/24
    **dhcp4:** false
      **gateway4:** 192.168.0.1
      **nameservers:**
        **addresses:**
    - 192.168.0.1
        **search:** [mylab.local]
      **interfaces:**
    - bond1



Any ideas?

---

### Post by TheFu on 2022-01-18
Edit the post above with "code-tags", not "quote tags" - that would be the first place to start.
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

Might be useful to explain which file you are posting too.

---

### Post by chefytim on 2022-01-18
I am using netplan and a file in /etc/netplan called 00-installer-config.yaml

```

network:
  bonds:
    bond0:
      interfaces:
      - eno1
      - eno2
      parameters:
        mode: active-backup
  ethernets:
    eno1: {}
    eno2: {}
  version: 2
  bridges:
    br0:
      addresses:
        - 192.168.0.2/24
      dhcp4: false
      gateway4: 192.168.0.1
      nameservers:
        addresses:
          - 192.168.0.1
        search: [mylab.local]
      interfaces:
        - bond0
    bond1:
      interfaces:
      - eno3
      - eno4
      parameters:
        mode: active-backup
  ethernets:
    eno3: {}
    eno4: {}
  version: 2
  bridges:
    br1:
      addresses:
        - 192.168.0.3/24
      dhcp4: false
      gateway4: 192.168.0.1
      nameservers:
        addresses:
          - 192.168.0.1
        search: [mylab.local]
      interfaces:
        - bond1

```

---

### Post by TheFu on 2022-01-19
An example link: [Https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629](Https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629)

I don't see a 'renderer' in the yaml either. Isn't that mandatory?

---

