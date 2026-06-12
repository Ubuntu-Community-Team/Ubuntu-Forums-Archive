---
title: "Segfault from PPTP on Fiesty"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by chengt on 2007-04-07
I see the following when trying to connect to a PPTP VPN configured using the instructions at [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)
```

Apr  7 00:45:13 gemini kernel: [ 1869.627601] nm-ppp-auth-dia[7983]: segfault at 0000000000000088 rip 00002b356c4da21b rsp 00007fff44161a70 error 4

```
Anyone seen this before and know how to fix it?

---

### Post by kkovach on 2007-04-09
I am seeing the same thing here, but am not sure if it's a problem with my configuration or not.  Would be interested in knowing what others think.

---

### Post by superG on 2007-04-10
Same for me. But using pptp directly always work. If I reboot my computer several times it works, but only some time.

---

### Post by siddhadev on 2007-04-10
I (a newbie) have the same problem. Can this be a 64bit issue?

---

### Post by siddhadev on 2007-04-10
after downloading the sources from the svn repository and building the [FONT="Courier New"]NetworkManager/vpn-deampns/pptp[/FONT] I have now VPN and the [FONT="Courier New"]nm-ppp-auth-dialog[/FONT] up and running. It was however necessary to modify the [FONT="Courier New"]/etc/NetworkManager/VPN/nm-ppp-starter.name[/FONT] like this:
> 
#auth-dialog=/usr/lib/network-manager/nm-ppp-auth-dialog
#properties=/usr/lib/network-manager/libnm-ppp-properties
auth-dialog=/usr/libexec/nm-ppp-auth-dialog
properties=/usr/lib/libnm-ppp-properties

because [FONT="Courier New"]make install[/FONT] has installed the binaries under [FONT="Courier New"]/usr/libexec[/FONT] und [FONT="Courier New"]/usr/lib/[/FONT] and not under [FONT="Courier New"]/usr/lib/network-manager[/FONT].

At some point I also called:
> 
 ./autogen.sh --prefix=/usr **--enable-nm-vpn-dbus-old**

to get rid of a compilation error.

Compiling and installing the NetworkManager from the sources didn't work, therefore I reinstalled the network-manager with apt-get remove/install, and executed afterwards [FONT="Courier New"]make install[/FONT] under [FONT="Courier New"]vpn-deamons/pptp[/FONT].   

[SIZE="1"]I guess, I was not quite sure what I'm doing, but it works now :-)[/SIZE]

---

### Post by chengt on 2007-04-20
I found this [http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2006/11/24/networkmanager-pptp-with-ubuntu-610-edgy-eft-on-amd64-crash-workaround/]("http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2006/11/24/networkmanager-pptp-with-ubuntu-610-edgy-eft-on-amd64-crash-workaround/")
while trying to solve the problem.
It seems to work. Problem is that I'm getting this now:

```

Apr 20 09:12:34 GEMINI pppd[12590]: Plugin nm-pppd-plugin.so loaded.
Apr 20 09:12:34 GEMINI pppd[12590]: nm-pppd-plugin: plugin initialized.
Apr 20 09:12:34 GEMINI kernel: [391845.508923] PPP generic driver version 2.4.2
Apr 20 09:12:34 GEMINI pppd[12602]: pppd 2.4.4 started by root, uid 0
Apr 20 09:12:34 GEMINI pptp[12605]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Apr 20 09:12:34 GEMINI pppd[12602]: Using interface ppp0
Apr 20 09:12:34 GEMINI pppd[12602]: Connect: ppp0 <--> /dev/pts/1
Apr 20 09:12:35 GEMINI pppd[12602]: nm-pppd-plugin: CHAP check hook.
Apr 20 09:12:39 GEMINI dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 20 09:12:45 GEMINI pppd[12602]: Terminating on signal 15

```

Looking online it looks like I might have the auth type incorrect.
At least its not segfaulting now :)

---

### Post by garoth2 on 2007-06-07
Patch for this here:

[http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/](http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/)

---

