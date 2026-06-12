---
title: "Remote Desktop (Headless PC)"
date: 2024-09-23
forum: Networking &amp; Wireless
---

### Post by Shibblet on 2024-09-23
I need to set-up a headless PC.  I will also need to log-in to it remotely.

I am currently running Remmina to remote into a Windows PC, but I want to change it to a Linux-PC (Kubuntu).

Remmina uses RDP, and apparently the server software is pre-installed on Windows 11.

What would I need to do, in order to set-up a remote login for Kubuntu?

---

### Post by TheFu on 2024-09-23
KDE uses plasma, which doesn't work well with any remote desktop solution.
Better to use LXQt or XFCE or Mate or no DE at all.

And of course, you should use ssh most of the time for remote needs, not a full desktop.  ssh for text, ssh -X for remote GUI apps when you are on the same LAN.  If you must have a remote desktop while outside the LAN, x2go is about the best option that doesn't depend on a 3rd party to work AND doesn't require local GUI capability.  That's why something the VNC-based tools won't work.

Remmina supports lots of different protocols, not just RDP.  From wikipedia:
> Remmina is a free and open source remote desktop _client_ for POSIX-based computer operating systems. It supports the Remote Desktop Protocol (RDP), VNC, NX, XDMCP, SPICE, X2Go and SSH protocols and uses FreeRDP as foundation. 

If you put your "desktop" under a virtual machine managed with libvirt, then you can use the remote desktop protocols that libvirt provides as well.  Most are tunneled through either ssh or TLS.  I've used SPICE+QXL for this but never over the internet. Over the internet, I use x2go for a full remote desktop using ssh for authentication.  I've done this from 5 continents when I didn't want to bring **any** local data with me on a laptop, just a minimal OS install and ssh keys.  Ventoy on a USB3/SDHC drive is excellent for this "travel OS" purpose. Just don't forget to remove all internal storage before your trip.

---

### Post by Shibblet on 2024-09-24
Wow!  Thanks for the info!

> **TheFu said:**
> KDE uses plasma, which doesn't work well with any remote desktop solution.  Better to use LXQt or XFCE or Mate or no DE at all.
Xubuntu it is.  ;-)

> **TheFu said:**
> And of course, you should use ssh most of the time for remote needs, not a full desktop.  ssh for text, ssh -X for remote GUI apps when you are on the same LAN.  If you must have a remote desktop while outside the LAN, x2go is about the best option that doesn't depend on a 3rd party to work AND doesn't require local GUI capability.  That's why something the VNC-based tools won't work.
I really need it to be a remote desktop.  Not necessarily outside my LAN though.

> **TheFu said:**
> Remmina supports lots of different protocols, not just RDP.  From wikipedia:  Remmina is a free and open source remote desktop client for POSIX-based computer operating systems. It supports the Remote Desktop Protocol (RDP), VNC, NX, XDMCP, SPICE, X2Go and SSH protocols and uses FreeRDP as foundation.
Which one of the protocols works the best?  I have these strange "freeze-up" issues with Remmina RDP to Windows 11 from my Kubuntu Machine.  Sometimes it will freeze for a good 10 seconds, and then go back to working... other times, it will freeze, and then around 10 seconds later it will put digital garbled mess of pixels all over the screen and will be locked up for good.  I can't even kill the app at this point, I have no choice but to hard-boot my Kubuntu computer.  It doesn't seem to affect the Windows 11 computer though.

> **TheFu said:**
> If you put your "desktop" under a virtual machine managed with libvirt, then you can use the remote desktop protocols that libvirt provides as well.  Most are tunneled through either ssh or TLS.  I've used SPICE+QXL for this but never over the internet. Over the internet, I use x2go for a full remote desktop using ssh for authentication.  I've done this from 5 continents when I didn't want to bring **any** local data with me on a laptop, just a minimal OS install and ssh keys.  Ventoy on a USB3/SDHC drive is excellent for this "travel OS" purpose. Just don't forget to remove all internal storage before your trip.
One of the problems I have had in the past with "remote desktops," is that I log-in, start the apps that I want running, then log-off.  The next time I log-in, I don't log-in to the same desktop.  The apps are still running, but I am on a new desktop and cannot access the apps that are running on the "other" desktop.

---

### Post by TheFu on 2024-09-25
When the system locks up, can you not ssh in outside the remote desktop and safely restart the computer?  Just because the GUI locks up, that doesn't mean the OS is locked up.

I suspect the problem is with Remmina.  I've never used it.  For remote desktop into MS-Windows, you are limited to RDP if it is a physical install.  MSFT has been adding more encryption trying to prevent bad guys from having trivial access to RDP sessions (which has mostly failed).  MSFT doesn't ask or share their changes with anyone else, so all the Linux tools that use RDP have to play catch up and reverse engineer the protocol as best they can. 

I don't have any MS-Windows installs on physical machines anymore, just inside 1 VM.  The hypervisor that controls the Windows VM allows remote access without MS-Windows knowing anything about it, so I use it that way. My client connection is using **virt-viewer** into the KVM/QEMU server, but to the specific Windows VM. I did install QXL video drivers from Redhat into the VM for better performance.  If your Windows install isn't inside a VM, this isn't an option for you.  I never use the SPICE/QXL connection over the internet. I don't think it is secure enough.  When I want to access that Windows system over the internet, I'll actually use x2go from my laptop into my normal desktop at home, then on the desktop, run virt-viewer into the Windows VM.  Nested remote desktops does work, which is a bit surprising, but all of it is Unix-based protocols, not MSFT.   The x2go client will see a list of x2go sessions on the server, so just click on the one you want to connect to gain access to your desktop with the programs running just like you left them.  Of course, you can always logout using the remote OS desktop logoff method to close the x2go session too, but if you just close the x2go-client window, it assumes there was a network hiccup and you will want to reconnect later.  Not sure how clear this is.  Lots of words for things that are easily seen.

Basically, don't use Remmina. Use the correct client tool to connect into the correct desktop.

---

### Post by Shibblet on 2024-09-25
> **TheFu said:**
> When the system locks up, can you not ssh in outside the remote desktop and safely restart the computer?  Just because the GUI locks up, that doesn't mean the OS is locked up.
It's not the host machine, it's the client.  And the client software freezes up the computer to a point where nothing works.  I can't CTRL+ALT+F2 to get a terminal.  It's just frozen solid.  My only option is to hard-boot the client computer.

The host computer is still working just fine.  Once I hard-boot, and log back in, it's right where it was...  It's infuriating.

> **TheFu said:**
> I suspect the problem is with Remmina.  I've never used it.  For remote desktop into MS-Windows, you are limited to RDP if it is a physical install.  MSFT has been adding more encryption trying to prevent bad guys from having trivial access to RDP sessions (which has mostly failed).  MSFT doesn't ask or share their changes with anyone else, so all the Linux tools that use RDP have to play catch up and reverse engineer the protocol as best they can.
I suspect it is with Remmina as well... but I also wondered if it didn't have something to do with Microsoft's Software.

> **TheFu said:**
> I don't have any MS-Windows installs on physical machines anymore, just inside 1 VM.  The hypervisor that controls the Windows VM allows remote access without MS-Windows knowing anything about it, so I use it that way. My client connection is using **virt-viewer** into the KVM/QEMU server, but to the specific Windows VM. I did install QXL video drivers from Redhat into the VM for better performance.  If your Windows install isn't inside a VM, this isn't an option for you.  I never use the SPICE/QXL connection over the internet. I don't think it is secure enough.  When I want to access that Windows system over the internet, I'll actually use x2go from my laptop into my normal desktop at home, then on the desktop, run virt-viewer into the Windows VM.  Nested remote desktops does work, which is a bit surprising, but all of it is Unix-based protocols, not MSFT.   The x2go client will see a list of x2go sessions on the server, so just click on the one you want to connect to gain access to your desktop with the programs running just like you left them.  Of course, you can always logout using the remote OS desktop logoff method to close the x2go session too, but if you just close the x2go-client window, it assumes there was a network hiccup and you will want to reconnect later.  Not sure how clear this is.  Lots of words for things that are easily seen.

Basically, don't use Remmina. Use the correct client tool to connect into the correct desktop.
That's what I am attempting to do.  I want to change this host computer to Linux.  XFCE was your suggestion, so I will load up Xubuntu on it.  However, I still need a decent remote desktop client/host software.

I am hoping that Remmina will work better with a different connection protocol, like VNC.  Ultimately, I don't need Windows on either computer, so there's no real need to run a VM.  Sounds like you are saying x2go is the software I need to log-in to a Xubuntu computer?

---

### Post by TheFu on 2024-09-25
I wouldn't use Remmina for anything.
Use x2go-server and x2go-client programs. BTW, x2go doesn't work with Wayland.  There is x2go client programs for Linux, Windows, and OSX.  The x2go-server only runs on Linux.  x2go leverages ssh, so ensure that ssh is working between the client and server too.  Standard ssh, not Putty, if you are doing that.  ssh-keys are supported automatically on MacOS and Linux clients.

---

### Post by Shibblet on 2024-09-25
> **TheFu said:**
> I wouldn't use Remmina for anything.
Use x2go-server and x2go-client programs. BTW, x2go doesn't work with Wayland.  There is x2go client programs for Linux, Windows, and OSX.  The x2go-server only runs on Linux.  x2go leverages ssh, so ensure that ssh is working between the client and server too.  Standard ssh, not Putty, if you are doing that.  ssh-keys are supported automatically on MacOS and Linux clients.

I'll give it a try soon.  Not worried about Wayland for the headless PC, but thanks for the warning.  ;-)

---

### Post by Shibblet on 2024-10-11
So, I spent the last week fighting "x2go-server" on my Headless PC.  For the life of me, I could not get a connection.  I even went so far as to try different distros that use XFCE.  I really couldn't figure out what the problem was.

Search, after search, after forum, after forum... all of the walkthroughs just didn't work.

Then I came across a video from one of my favorite YouTubers:  [https://www.youtube.com/watch?v=hjnsVpodkUM]("https://www.youtube.com/watch?v=hjnsVpodkUM")

He was showing how Ubuntu has it built into the settings menu.  Just navigate to "Remote Desktop" and turn it on.  Then your computer can connect with any VNC or RDP client program.

So, I loaded up Ubuntu on my Headless PC (it's got a monitor while I set it up, of course.)  Turned on the remote desktop, and login... and it all works great!

I do appreciate all of the information and assistance for how to do it with x2go, this just worked out a lot easier.

---

### Post by TheFu on 2024-10-11
As long as the client and the server are on the same LAN and it works, fine.
If the connections are going over the internet, need to use a full VPN for security.  x2go uses ssh, so the network authentication and encryption are built into x2go, unlike RDP and VNC.

---

