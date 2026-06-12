---
title: "mixed up network configuration in 18.04"
date: 2019-01-10
forum: Networking &amp; Wireless
---

### Post by gkampou on 2019-01-10
Recently upgraded to 18.04 from 14.04 (in steps of course)


  Just about everything works. Have network access, and remote access via ssh.


  Desktop sharing (VNC) however doesn't work and can't be enabled. When  I'm trying to enable, it shows "no networks selected for sharing" as  shown below
[[IMG]https://i.stack.imgur.com/l2qvP.png[/IMG]]("https://i.stack.imgur.com/l2qvP.png")  Dug in a bit and found that I can't access NetworkManager GUI. /etc/network/interfaces still exists and configures eth0. nmtui works however...


  netplan generate doesn't generate anything. Created a yaml file under /etc/netplan pointing to NetworkManager as renderer, but netplan apply doesn't fix my problem...


  By the way, nmtui shows the netplan-eth0 interface but it is not active, nor can it be activated...

---

