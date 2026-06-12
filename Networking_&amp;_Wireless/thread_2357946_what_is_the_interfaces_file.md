---
title: "what is the interfaces file?"
date: 2017-04-07
forum: Networking &amp; Wireless
---

### Post by jeff666 on 2017-04-07
ok so as far as i know only Debian and Ubuntu use the /etc/network/interfaces file which is really easy to use, and i like alot. I would like to use it on LFS system, so my Ubuntu machines and LFS have the same networking setup (opposed to the RedHat, centos and lfs /etc/sysconfig/ scripts). I also know arch doesn't have anything like this pre installed and had documentation on setting up similar things up with systemd directly:  [https://wiki.archlinux.org/index.php/Systemd-networkd](https://wiki.archlinux.org/index.php/Systemd-networkd)  [https://wiki.archlinux.org/index.php/Wireless_bonding](https://wiki.archlinux.org/index.php/Wireless_bonding)    here is LFS boot scripts package where this netmanager/script is set up:  [http://www.linuxfromscratch.org/lfs/view/stable/chapter07/bootscripts.html](http://www.linuxfromscratch.org/lfs/view/stable/chapter07/bootscripts.html)   so Im guessing Ubuntu/Debain has some modified version of the LFS boot scripts (Debian is older i think, but they must have come form the same place considering that both have ifup/ifdown) any way does any know what i would need to copy over/ change on my lfs to get the interfaces file to work like that (is simple or is this going to be really complex)?

---

### Post by papibe on 2017-04-07
Hi jeff666.

Is your Ubuntu installation running the Desktop edition or the Server one?

Only on the server the /etc/network/interfaces is fully used. In the desktop, it is only used to raise the loop (lo) interface, and then NetworkManager does the rest.

If you want to use 100% /etc/network/interfaces on the desktop, you would have to [disable NetworkManager]("https://help.ubuntu.com/community/NetworkManager#Stopping_and_Disabling_NetworkManager"), and then edit your interfaces file (example [here]("http://askubuntu.com/questions/339249/how-to-connect-to-internet-after-removing-network-manager")).

Does that help?
Regards.

---

### Post by TheFu on 2017-04-07
Cannot help with your direct question. LFS is *Linux From Scratch* for the uninitiated.  If your LFS isn't based on Debian, I don't know what to say. If it is, then you'll get to use the interfaces file.

Otherwise, you are on your own and really should ask this question in an "other distros" forum, not Ubuntu.

Can help with some Linux history - Debian is one of the oldest distros - older than Redhat, but not older than Slackware or SLS.
Ubuntu is a child of Debian. When they want to make a new Ubuntu, they pull the base from Debian - even today.

These days, almost all distros are based off 4 main lines.
[LIST]
[*]Debian
[*]Slackware (the parent SLS is dead)
[*]Redhat
[*]Gentoo
[/LIST]
Here's an amazing image: [http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png](http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png) - zoom in and be certain to go to the bottom left to get some dates.

---

### Post by Skaperen on 2017-04-08
> **TheFu said:**
> Here's an amazing image: [http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png](http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png) - zoom in and be certain to go to the bottom left to get some dates.
we need one of those that goes to 2017.

---

### Post by jeff666 on 2017-04-08
@[**[COLOR=#C61919][B]papibe**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=774785") I use a cut down version of Ubuntu server 16.04 lts/custom kernel for my desktop/laptop because it gives me a arch like system with the Ubuntu features i really like (examples: apt package manager, ifconfig, interfaces file, systemd/sysint) and i use ltfs for other server projects. So yeah I have no networkmanager on anything (although i have heard of the interfaces & /etc/sysconfig scripts referred to as network managers so depending who you ask).

@Skaperen yeah that would be awesome ( I have seen that image before and it is awesome!) I think I'm going to build a small  website on Linux one day, one thing i want to do is a really nice  technical comparison of Distros including package manager, difference between  default apps (for cut down versions), networking, upgrading, installer, default gui. I would love to have that info all in one place for the main branches like slackware, debian, ubuntu, red hat, opensuse, arch, lfs, fedora, centos, gentoo, etc.

@THEflu I am trying to base that part off Debian hence the question and sorry i thought it would be just as relevant for Ubuntu as for Debian since both distros seam to support interfaces file and i have a account here. Is there a way to base a LFS off Debian? I could figure it out (my original question) myself but maybe some one on heres a expert on systemd and can just tell me so i can do my homework which is learning c not systemd.

---

### Post by papibe on 2017-04-08
A few thoughts:
[LIST]
[*]By default 16.04 uses systemd as the init system.
[*]The network is initialized by the networking.service located in /lib/systemd/system.
[*]The service it is based on the ifupdown package (not systemd-networkd),
[*]Although it is ifup/down based, it does not uses the traditional /etc/init.d/networking script.
[*]Nevertheless, the file /etc/network/interfaces is still used to configure the network interfaces.
[*]If you change the from ifupdown to systemd-networkd, the file interfaces won't be use, but config files located at /etc/systemd/network
[*]
[/LIST]
Does that help?
Regards.

---

