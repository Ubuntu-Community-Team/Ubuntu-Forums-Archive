---
title: "[SOLVED] Setting up a VPN Connection"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by TheUbGuy on 2008-09-12
I've gone though the posts here but maybe I've missed a few things or someone here may have already done what I'd like to do. Basically, I would like to create a VPN connection to work and then Remote Desktop into my system at work. If I was doing this from Winblows, I just create a new network connection (Connect to a Workplace) and use the Windows VPN connection, then use Remote Desktop once the VPN is connected.

I know that there is Remote Desktop in Ubuntu that should work - it's getting the VPN connection setup that I am not sure of.

Currently I connect over a broadband cable connection.

Any help with this would be appreciated. I do believe I grabbed openvpn from Synaptic Package Manager but am not sure of where to go from there. I would like to completely remove Windows from my system and this is pretty much the only thing left holding me back. I know I could probably do this if I ran Winblows in a Vmware session but I'd rather not.

---

### Post by TheUbGuy on 2008-09-12
Well, I have been able to set up a VPN connection, and have no problem connecting. I just installed the pptp plugin to NetWork Manager, put in the info, and connected.

However, I still can't get remote desktop working. I keep getting a 'not found' message for the computer I'm trying to connect to. I have no problem remote desktop'ing from Windows.

Does anyone here remote desktop to a Windows box using a VPN connection?

---

### Post by TheUbGuy on 2008-09-13
Sometimes you just need to do things yourself :)

I was able to VPN to work easy enough ... but I could not get remote desktop to work. I set things up with Gnome-RDP, but when I tried to connect I would get the 'Not Found' message.

Booting back into Windows :gag: I connected to work via VPN and then used Remote Desktop. On my system at work I ran ipconfig and got the IP address of my workstation. Then I logged off, and then got back into Ubuntu on my home PC. I started my VPN connection. From there, I got back into Gnome-RDP. I edited the entry for my work PC, changing the computer name to the IP address. Clicked on the connection and *voila* - I was able to sign in to my work PC with no problem. Apparently GNOME-RDP could not recognize the work PC name - but easily found the PC when I specified the IP address.

Guess I solved this one myself :lolflag:

---

