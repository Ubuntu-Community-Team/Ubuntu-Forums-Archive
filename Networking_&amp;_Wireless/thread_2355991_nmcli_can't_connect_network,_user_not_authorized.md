---
title: "nmcli can't connect network, user not authorized"
date: 2017-03-18
forum: Networking &amp; Wireless
---

### Post by fmsismo on 2017-03-18
Hi all, I'm trying to create a script in order to download the photos from my action camera, on my notebook I didn't have any problem, but with my server my user don't have enough permissions.

[INDENT]nmcli device wifi connect SJ5000 password secret
Error: Failed to add/activate new connection: Not authorized to control networking.[/INDENT]

The privileges with nmcli for my user.

[INDENT]```
nmcli general permissions
PERMISSION                                                 VALUE
org.freedesktop.NetworkManager.enable-disable-network      no
org.freedesktop.NetworkManager.enable-disable-wifi         yes
org.freedesktop.NetworkManager.enable-disable-wwan         no
org.freedesktop.NetworkManager.enable-disable-wimax        no
org.freedesktop.NetworkManager.sleep-wake                  no
org.freedesktop.NetworkManager.network-control             auth
org.freedesktop.NetworkManager.wifi.share.protected        no
org.freedesktop.NetworkManager.wifi.share.open             no
org.freedesktop.NetworkManager.settings.modify.system      no
org.freedesktop.NetworkManager.settings.modify.own         auth
org.freedesktop.NetworkManager.settings.modify.hostname    auth
org.freedesktop.NetworkManager.settings.modify.global-dns  unknown
org.freedesktop.NetworkManager.reload                      auth
[/INDENT]
```

I tried to get control creating a pkla file (/etc/polkit-1/localauthority/50-local.d/52-network-control.pkla)

[INDENT]```
cat /etc/polkit-1/localauthority/50-local.d/52-network-control.pkla
[Enable Controlling of Network Connections]
Identity=unix-group:adm
Action=org.freedesktop.NetworkManager.network-control
ResultActive=yes
ResultInactive=no
ResultsAny=no[/INDENT]
```

I'm in the adm group.

Can someone help me to solve this problem.  I was reading a few days but I didn't find the answer.

I'm using Ubuntu 16.04.2 LTS (server)

Thanks

---

### Post by wildmanne39 on 2017-03-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

