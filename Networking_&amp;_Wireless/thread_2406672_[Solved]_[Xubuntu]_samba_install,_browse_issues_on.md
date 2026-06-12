---
title: "[Solved] [Xubuntu] samba install, browse issues on linux machines"
date: 2018-11-24
forum: Networking &amp; Wireless
---

### Post by kirbo719 on 2018-11-24
Three workstations on a LAN.

One is Windows 7, in a workgroup

Two are Xubuntu 18.04.1 LTS, each running:
    --Samba 2:4.3.11 + dfsg-0ubuntu  2:4.3.11 + dfsg-0ubuntu
    --smbclient 2:4.3.11 +dfsg-0ubuntu  2:4.3.11+dfsg-0ubuntu


Each machine can ping the other two machines. The Windows 7 machine can see and access the shared directories of both Xubuntu machines. Neither Xubuntu machine can see the Win7 machine nor the other Xubuntu node.

-0-

The HOSTS file of each machine asserts the static IP addresses and aliases of the two other machines.

Firewalls on each machine are set to allow SMB inward with no restrictions outward.

One Xubuntu machine has Thunar v1.6.11. The other has Thunar v1.6.15. Regardless of version, Thunar behaves the same:

Thunar, when side pane displays "tree," Network does not appear.

If side pane is set to display "shortcuts," there is a Network listing, and below it "Browse Network." When one clicks "Browse Network," this message presents:

	Failed to open "/ on".
	The specified location is not supported.

I've been at this a number of hours today.  I no longer can see the forest for the trees, and am pre-embarrassed that I have overlooked something very fundamental.

Would someone kindly set me right?

Thank you in advance,

Bob

---

### Post by Morbius1 on 2018-11-24
You actually have three distinct issues. Let's go through the easy ones first:

> If side pane is set to display "shortcuts," there is a Network listing,  and below it "Browse Network." When one clicks "Browse Network," this  message presents:

    Failed to open "/ on".
    The specified location is not supported.
It really sounds like you are missing a package so add it:
```
sudo apt install gvfs-backends
```
> Neither Xubuntu machine can see the Win7 machine nor the other Xubuntu node.
The Xubuntu machines since they are all at the 18.04 level should see each other by default. Hopefully it's the missing package that's the cause but just in case make sure avahi is working on both Xubuntu machines:
```
sudo service avahi-daemon restart
```
And see if you can ping each other by it's mDNS ( avahi ) host name:
```
ping -c3 hostname.local
```
The Win7 machine is going to be a problem.

My suggestion is to try to access it by ip address first like this in a terminal:
```
thuanar smb://192.168.0.100
```

---

### Post by kirbo719 on 2018-11-24
I failed to mention in original message that the three workstations each can ping the other two without problem.

Based on your response, I pinged from the Xubuntu machines to the other two workstations. The cmd "ping -c3 hostname.local" was successful to the other Xubuntu workstation and unsuccessful to the Win7 machine. A ping to the Win7's IP address was successful from both Xubuntu machines.

Based on your response:  I verified gvfs-backends was NOT installed on either machine. I installed on both.

On one of the Xubuntu machines (opti7010), the two other workstations seem fully browseable. I can click an entry and view the shared folders on the other Xubuntu machine and the Windows7 machine.  Network appears in the side pane. In the view pane are entries for:

asus-laptop                                  [Win7 machine]
opti7010                                      [Xubuntu 18.04.1 LTS machine]
Windows Network
xps-15-9570 (file sharing)         [Xubuntu 18.04.1 LTS machine]
xps-15-9570 (file sharing)


On the other Xubuntu machine (xps-15-9570), there still is no browse capability to either other machine. On this machine in Thunar, Network is listed in the side pane. In the view pain are the entries:
Windows Network
xps-15-9570

Clicking "Windows Network" results in the error:
Failed to open "Windows Network".  Failed to retrieve share list from server: No such file or directory.

This troublesome machine (xps-15-9570) is new. I'm just now building it up to become a production machine - but it isn't there yet, and if need be I can slash-n-burn, start from scratch, reload the OS, then reload Samba.

You responded "The Xubuntu machines since they are all at the 18.04 level should see each other by default."  From that, should I infer  SMB Client need not be installed additional to Samba?

Morbius1, thank you for your help thus far. Any thoughts on the troublesome Xubuntu machine appreciated.

Bob

---

### Post by Morbius1 on 2018-11-24
> You responded "The Xubuntu machines since they are all at the 18.04  level should see each other by default."  From that, should I infer  SMB  Client need not be installed additional to Samba?
It's always good to install smbclient but libsmbclient should already be installed on your system and that is the mechanism Thunar uses to connect to a server.

There are two ways in Linux to browse the network for SMB hosts:

[1] The **Windows Way**. 
It's convoluted, a pain in the butt to get right, slow, unreliable, and so old that Microsoft keeps it running to support legacy systems but hasn't used it itself since Windows 2000. That is the Browse Network > Windows Network way.

[2] The [B]Linux Way. 
[/B]You used to have to configure this yourself but since 18.04 Samba will automatically "register" itseld using mDNS ( Avahi ) to the rest of the network. All other Linux machines as well as any macOS machines you may have on your network ( which also use Samba by default ) can see your machine. That is the Browse Network way. It's not under Windows Network since it's not using any Windows specific method.

I'm not sure why one Xubuntu works and the other does not. All it requires is that samba be installed, avahi-daemon is running, and you haven't gone out of your way to block either in either firewall. **Edit**: Actually there is one other requirement which may not apply here - all of the machines have to be in the same subnet. They all have to connect to the same router. You can have switches in the mix but not another router.

---

### Post by kirbo719 on 2018-11-24
Morbius1, once again thank you for lending a hand.

The troublesome Xubuntu machine, I intend to wipe the disk and reinstall the OS followed immediately by Samba. I marked the thread solved.

Best!

Bob

---

