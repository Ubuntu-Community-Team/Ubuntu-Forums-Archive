---
title: "Windows to Ubuntu networking - IPv6 - Can't connect to web server using etc/hosts"
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by patrick19 on 2016-06-24
My setup is:

Windows 10 OS
Ubuntu Virtual Instance - VirtualBox
Bridged ethernet device for VirtualBox

I tend to move around from various coffee shops and libraries to get my work done (too many distractions at home, lol).

One of places I go to is using specifically IPv6 for LAN DHCP.

I am having some trouble connecting to my virtualbox Ubuntu server under a specified hostname in the windows hosts file for this IP. 

I AM ABLE to connect to the server in the web browser (port 80), sftp (port 22) and ssh using JUST the IPv6 address. My problem is that I need to assign a hostname for the IPv6 address because of an issue I'm having with Notepad++ for web development (Notepad++ programmatically tries to create a working cache directory using the username@hostname/ipaddress. By connecting to the server with just the IPv6 address, Notepad++ tries to create a cache directory using illegal directory characters that are in the IPv6 string). I can't seem to find a way to override this setting for each profile/connection; there is however a global setting that I can edit. But, this is not preferred as I normally connect to LANs that assign IPv4, and it will be very annoying having to change that global each time I decide to connect to a different LAN. I figured this should be a very simple fix: Add the IP to the Windows host file, and assign a domain (ie localipv6.com), however I was completely wrong. Maybe I'm missing something simple?

This may be more of a Windows question, so I apologize if this is in the wrong section.

Thanks.

EDIT: Ok, I've managed to solve the issue without using the host file. I didn't realize that you can set up a "cache file map" in Notepad ++ that allows you to set the directory, per profile.

---

