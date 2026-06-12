---
title: "Ubuntu 20.04.2 LTS sharing with network bond -&gt; no networks selected for sharing"
date: 2021-07-18
forum: Networking &amp; Wireless
---

### Post by latoschik on 2021-07-18
Hi all,

I am running a little home server under Ubuntu 20.04.2 LTS to serve plex, lms, nexcloud, virtualbox, etc. on a mirrored zfs pool for all the data. The system has two NICs so I enabled a network bond on the two (setup depicted below) for faster access and backup over the network. Everything is working  properly and fine. System services are available, network outside is reachable and updates come in frequently. Now I decided to also enable sharing, i.e., remote desktop, to be able to use some of the GUI applications without sitting at the cellar (where the machine is installed). For example, I use several virtual machine for high quality audio ripping from a pool of 12 attached CD/DVD drives and it just makes it easier to monitor the rip progress without visiting the cellar over-frequently :).

However, enabling sharing using the well-documented default desktop GUI settings/sharing failed. Every sharing option in the GUI cold not be enabled since it requires the selection of the network for the share which is not available. This is what you see in that case (note that I did get this picture from a different thread since my setup is set to German language, hence the **[FONT=courier new]vnc://root [/FONT]**is actually is not what I see since it depends on your local setup):

[https://ubuntuforums.org/attachment.php?attachmentid=288829&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=288829&stc=1)


As you can see, you can't enable sharing since there is no network selected but there is none from select from. So I did a bit of reading first and learned that Ubuntu changed its way to handle networks quite some time ago. After getting familiar with the new **[FONT=courier new]netplan[/FONT]** system I finally managed to get the bond show up in the networks section of the GUI. Since it took me some time I thought you might ne interested in the solution. This is the **[FONT=courier new]/etc/netplan/cat 50-cloud-init.yaml[/FONT]** before my change:

```
[COLOR=#000000][FONT=Menlo]network:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    version: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    ethernets:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        eno1:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          dhcp4: no[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          dhcp6: no[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          optional: true[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        eno2:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          dhcp4: no[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          dhcp6: no[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          optional: true[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    bonds:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      bond0:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]         interfaces: [eno1, eno2][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]         addresses: [192.168.0.10/24][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]         gateway4: 192.168.0.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]         nameservers:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]            search: [local][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]            addresses: [192.168.0.1][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]         parameters:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]            mode: balance-rr[/FONT][/COLOR]

```

This is what has to be changed to solve the problem:

```
[COLOR=#000000][FONT=Menlo]network:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    version: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    ethernets:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    renderer: NetworkManager
    ...

[/FONT][/COLOR]

```

Then it looks like this (now taken directly from my system, since in German ;):

[https://ubuntuforums.org/attachment.php?attachmentid=288830&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=288830&stc=1)

What I haven't figured out, though, is how I ended up in this situation since I installed a vanilla Ubuntu 20.02 and did enable the bond as it is documented. Turns out that one then has to explicitly set the renderer for the network to **[FONT=&amp]NetworkManager[/FONT]** to be able to select the networks in sharing. Hope it is of help for some of you, have fun.

Marc

---

