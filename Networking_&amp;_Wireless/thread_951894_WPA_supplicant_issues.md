---
title: "WPA supplicant issues"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by gdinoia on 2008-10-18
I just had my mini 9 delivered and to use it on my university's wireless network I had to use WPA_supplicant.  I followed these instructions and got on my university's network without any problems.
 Internet at the University of Pittsburgh
To access the network at Pitt, here is what is needed to be done:
1. Create the following file.
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=0
network={
key_mgmt=WPA-EAP
eap=PEAP
priority=10
}
Name this file wpa.conf.
2. From the a command prompt enter the following commands (the $ represents
the command prompt).
Following each of these commands you will be prompted for your root
password.
$ sudo ifconfig eth1 up
$ sudo wpa_supplicant -B -Dwired -ieth1 -cwpa.conf
These commands turn on your ethernet connection and the WPA Supplicant
daemon.
3. From the command line type the following command the enter the WPA
client:
$ sudo wpa_cli
You should now be in the WPA client.
4. In the WPA client type the following changing USERNAME to your username
and PASSWORD to your
password. (The > represents the prompt and is not to be typed.)
> identity 0 USERNAME
> password 0 PASSWORD
> quit

The only problem is that now I can't seem to connect to my home network, or any other network for that matter.  it seems as though it overrode the built in wireless configuration utility.

is there any way to change this back to normal or will i need to reinstall Ubuntu?

Thanks in advance.

---

### Post by CodeAlias on 2008-11-09
Hi,

You need to add a

network={
...

}

section in your wpa.conf for your home network. What goes in this section depends on how you configured your access point at home.

Cheers,
CodeAlias
[Wireless Security and More]("http://codealias.info")

---

