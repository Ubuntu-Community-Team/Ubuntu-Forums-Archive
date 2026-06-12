---
title: "[SOLVED] ipw2200 cannot connect to WEP or WPA network in Intrepid, can we devise a wo"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by al_mckin on 2008-11-08
Hi everyone,

I'm sorry if this is a duplicate.

I cannot connect to a WEP or WPA network with my ipw2200 on Intrepid, which was working fine until I upgraded from Hardy.  

Trying to set the WEP key with iwconfig leads to this:

```

alastair@alastair-laptop:/usr/src$ sudo iwconfig eth1 key CCCC-CCCC-CC
Password or swipe finger: 
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.

```

It might be related to this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104") but this entry claims that this bug is fixed.

My next question is, can I do a git-bisect on the ubuntu kernel to try and find the offending commit?  Is it possible to do such a thing and are there any instructions on how to do so?  Or would it be better to just do a bisect on the mainline kernel?

Alastair

---

### Post by drunknmunky1 on 2008-11-24
I'm having a similar problem.
I can't connect to any encrypted wireless networks using any methods that I've tried so far (network-manager-gnome, knetworkmanager, wpa_supplicant command line).  I can connect to unencrypted networks with no trouble.
I've read through several threads without a solution. Any ideas?

---

### Post by arcik on 2008-11-30
The same problem here (Thinkpad T42p):(, had no problems in Hardy. Anybody with a solution out there? Thanks beforehand!

---

### Post by jeremycobert on 2008-12-10
same problem here. and nothing seems to fix it, except turning off wep.

---

### Post by al_mckin on 2008-12-10
A freshly compiled 2.6.27.7 works for me.

The diff between the two ipw2200.c files is as follows:

```
alastair@alastair-laptop:~/linux$ diff linux-source-2.6.27/drivers/net/wireless/ipw2200.c linux-2.6.27.7/drivers/net/wireless/ipw2200.c
90c90
< static int associate;
---
> static int associate = 1;

```

The above change was mentioned in the bug report I linked to in my initial post as a fix for this problem, but it doesn't for me.

I think it might be a problem with some other kernel related package that is installed.

I will experiment and report back.

Alastair

---

### Post by al_mckin on 2008-12-10
Ok I think I have the fix of sorts.

Uninstall the linux-backports-modules package for your kernel. When I uninstalled this package my ipw2915 abg worked fine again on an encrypted network!

Current for intrepid would be linux-backports-modules-2.6.27-9-generic.

I'm not sure if you will lose any other functionality.

Hope this fixes the problem for everyone!

Alastair

---

### Post by al_mckin on 2008-12-10
Here is a full bug report with an explanation and a manual workaround if you cant remove the backports-modules package.

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390")

---

### Post by coffeecat on 2008-12-11
Just for the record, I'm posting from a live 8.10 CD running on my laptop connecting wirelessly with an ipw2200 wireless chipset. I had no problem connecting with WPA-PSK.

The problem, as the OP points out in a later post, is with the backports package. The thread title could be read as implying that there's an intrinsic issue with the ipw2200 chipset in Intrepid, which is not so.

I just thought I'd emphasise this for any inexperienced users searching the forum: Intrepid works fine ootb with ipw2200.

---

### Post by taralluccio on 2009-03-27
I've experienced the same problem (albeit on Hardy) and I've found the relevant bugs.

[https://bugs.launchpad.net/bugs/322434](https://bugs.launchpad.net/bugs/322434)
[https://bugs.launchpad.net/bugs/297390](https://bugs.launchpad.net/bugs/297390)

---

