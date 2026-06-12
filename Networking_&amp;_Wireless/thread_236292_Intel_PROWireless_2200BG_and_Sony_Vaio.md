---
title: "Intel PRO/Wireless 2200BG and Sony Vaio"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by adverseyaw on 2006-08-14
Hello all. I have been using linux for about 5 months now. I had Breezy on my laptop, a Sony Vaio VGN-FS550 and Debian at home. I just upgraded to Dapper Drake on my laptop am having problems with the wireless connection. :-({|=   It isn't showing up under 'Network Configuration'.
When I installed Breezy I had to set the display to the proper resolution with [FONT="Courier New"]915resolution[/FONT]. The sound didn't work either, but I fixed that (I don't remember how):D . The wireless network worked fine from the beginning. I assume that it recognized the card (inbuilt Intel PRO/Wireless 2200BG) and set up everything for me. The wireless was [FONT="Courier New"]eth0 [/FONT]and the wired connection was [FONT="Courier New"]eth1[/FONT].

After the upgrade to Dapper Drake I did the [FONT="Courier New"]915resolution [/FONT]thing again and am still trying to figure out how to configure the sound, but my real problem is that I have no wireless connection. Now [FONT="Courier New"]eth0 [/FONT]is the wired connection and the modem connection is in there, but no wireless connection. I don't have a '+ADD' button to add the wireless as I saw in the ubuntu help. So I am at a loss.
When I do [FONT="Courier New"]lspci [/FONT]command I find that it recognized the 'Intel PRO/Wireless 2200BG' but I don't know how to set up devices for it, and get it into the Network Configuration dialog. I tried [FONT="Courier New"]ndiswrapper [/FONT]with the recommended driver [8.1.1.0] from their list on the site but I get the dreaded *'ndiswrapper line 135'* error. All the files in the package are in the directory (*inf, *cat, *sys) it just doesn't want to Copy to the dev folder.
Any help anyone can give will be greatly appreciated. [-o< 
Thanks in advance,
AdverseYaw

---

### Post by coffeecat on 2006-08-14
When I installed Dapper on my Sony Vaio VGN-FS215B (with Intel 2200BG), I simply installed network-manager and network-manager-gnome with Synaptic. It's a gnome panel applet and should appear somewhere on the top right. It was then just a matter of entering my WPA (yes, that's right - WPA) pass-phrase and choosing a keyring password. The only minor irritation is that you have to enter your keyring password every time you boot up, but apart from that it's all been very reliable. I've also got Fedora 5 and SuSE 10.1 on this laptop, but I use Ubuntu mostly. I'm relying on gnome-network-manager in those too. In Fedora I had to download the Intel firmware (fairly sure I didn't have to do this in Ubuntu) and in SuSE it connects without me having to put in my keyring password each time.

What I didn't do was to use the instructions [here]("http://ubuntuguide.org/wiki/Dapper#How_to_get_ipw2200_and_wpa_to_work"). It's a great shame they're still linking to a necessarily complicated howto on this forum for Breezy when it all just works with network manager in Dapper.

**Edit:** particularly as just a few lines down they're telling you 'How to configure Ubuntu/Kubuntu with WPA using Network-Manager'. :wink:

---

### Post by adverseyaw on 2006-08-14
Yes, I beleive that I have the applets, as they show up for the wired connection.  I just don't have the wireless listed in the Network Configuration Dialog.  A driver problem apparently.
After quite a bit of research it seems that I need to use the [FONT="Courier New"]ipw2200[/FONT] driver.  This is installed by Dapper Drake 6.06.  It doesn't seem to be installed on my machine though.  
How do I go about finding out if it is installed?
If it isn't installed, then it seems I will have to build it. 
I have already downloaded the three files that I require according to the [HOWTO]("http://ubuntuforums.org/showthread.php?t=26623"):
[LIST]
[*]ipw2200-fw-2.4.tgz
[*]ieee80211-1.1.0.tgz
[*]ipw2200-1.0.6.tgz
[/LIST]
But I am having trouble finding the kernel-headers.  The repository doesn't list the headers for my kernel version (2.6.12-10-686)[from  apt-get install kernel-headers-$(uname -r)].  What kernel headers do I need?  Can I use other kernel headers?  When building the kernel is the -686 just a compile flag?  Or are there other files that I need compared to -386.
There is so much that I need to learn...:oops:
Thanks
AdverseYaw

---

### Post by adverseyaw on 2006-08-14
> **adverseyaw said:**
> 
...
But I am having trouble finding the kernel-headers.  The repository doesn't list the headers for my kernel version (2.6.12-10-686)[from  apt-get install kernel-headers-$(uname -r)].  What kernel headers do I need?  Can I use other kernel headers?  
...


To top it all off I can only access the internet with wireless at this hotel.  So all my replies have to be from the Window$ side of my laptop.  If I do download the kernel-headers for my version as a  *.deb file and place it on the windows partition, then go into linux and copy it to the linux partition (~/Desktop :-? ) How do I install it with apt-get?  Do I have to add a repository that is my Desktop?
...
Thanks.
AdverseYaw

---

