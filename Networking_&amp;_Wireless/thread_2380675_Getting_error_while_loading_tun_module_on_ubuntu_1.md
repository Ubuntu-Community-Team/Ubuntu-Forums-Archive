---
title: "Getting error while loading tun module on ubuntu 14.04."
date: 2017-12-20
forum: Networking &amp; Wireless
---

### Post by osticker on 2017-12-20
Hi  Team, I have openVZ VPS with fresh Ubuntu 14.04 (64bit) installed. Tap/Tun is  enabled on my VPS. 
When I run the command  "cat /dev/net/tun" it returns   "File descriptor in bad state"   which is good. 

 But when I load the  tun module by running command "modprobe tun" it returns the following  error:-

  modprobe: ERROR: ../libkmod/libkmod.c:507  kmod_lookup_alias_from_builtin_file() could not open builtin file  '/lib/modules/2.6.32-openvz-042stab123.9-amd64/modules.builtin.bin' modprobe: FATAL: Module tun not found.
  
Please help, how to resolve this issue? I want to install OpenVPN later then. Thanks.

---

