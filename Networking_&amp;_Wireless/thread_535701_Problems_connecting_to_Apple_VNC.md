---
title: "Problems connecting to Apple VNC"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by vik.vaughn on 2007-08-26
I was following these directions, but I cannot remove xvncviewer, when I try to remove that the package manager tells me I have to remove ubuntu-desktop which is not really an option. Anyone know a workaround for this or a better way to access the remote desktop of an OS X machine?

---------------------------------------------------------------------------------------------------------------------
Need to access your Mac from your Linux desktop? While Apple Remote Desktop software might be compatible with VNC, anyone who’s tried to use a regular VNC client will know it doesn’t work. Here’s how to fix it.

First, the Mac:
- Open Finder and click System Preferences
- Under Internet & Network, open Sharing
- Enable Apple Remote Desktop. Then Access Privileges
- Enable VNC viewers may Control the screen with password, and then pop in a password.

Then on Ubuntu:
- Click System &#8594; Administration &#8594; Synaptic Package Manager
- Install the tsclient and xtightvncviewer packages
- Uninstall the xvncviewer package.This is the important part – Apple Remote Desktop isn’t compatible with regular VNC. Uninstalling it makes Ubuntu prefer the alternative Tight VNC version (which uses a compression that works with Apple Remote Desktop).
- Click Applications &#8594; Internet &#8594; Terminal Server Client
- Under Computer type the IP address of the Mac, select VNC as the protocol and click Connect.
- If all goes well, a window will pop up in the top left of your screen asking for a password, and you’ll be connected to your Mac.
source:venturecake.com

---

### Post by 0graham0 on 2007-09-08
Hi,

I was following the same instructions, and it is okay to remove vncviewer and ubuntu-desktop...it seems ubuntu-desktop is just an index of files, and does not really remove any ubuntu components. Let me know how things end up working, I haven't been able to get a connection, recieving the error:

vncviewer: connecttotcpadr:connect: no route to host
Unable to connect to VNC server

---

### Post by vik.vaughn on 2007-09-08
I've read up on removing "ubuntu-desktop" and it doesn't look like it will immediately break anything, but supposedly keeping it makes upgrading ubuntu easier as newer versions come out.


When you are unable to connect, it says no route to host? have you tried running a traceroute to the host you are trying to connect to? is it on the same network? if not, are you trying to connect to a private IP from outside the network?

---

### Post by 0graham0 on 2007-09-08
turns out the network i was on was down...its working like a charm now

---

### Post by yagodr on 2007-09-30
Hi. I have the opposite problem...I would really like to access an ubuntu Desktop from Apple Remote desktop beacuse I control more than 5  MACs and a few PCs on a network with ARD, and would find it easier if I didn't have to change application for the control. 

I am able to observe the Ubuntu desktop but I can't control it. By the way, I think I touched something and now the "remote Desktop" option doesn't exist under the admin menu...how can I get it back?

I'm new to Linux as you can see, and I need some help.

Thanks.

---

### Post by ipguru99 on 2008-03-08
THIS works!  just an "sudo apt-get install xtightvncviewer" and I was off and running! 

Thanks vic.vaughn!

---

