---
title: "Wireless on and connected to WAP at startup?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by BuRn_sLuG on 2008-05-18
Hey guys,

Have a thread in the server category with this question in it, however thought I'd ask here as I should get more responses.

I have just installed Ubuntu Server on my desktop machine, as I now use my notebook as a primary PC. I will be using SSHFS (used to use NFS but apparently SSHFS is more secure, which is important to me) to store media on my server for access from my notebook, and will be using SSH to control my server from my notebook.

I connect the notebook to the server via a crossover cable and static IP settings. I can ping between the two just fine.

The server will connect to the internet via wifi (through my wifi router), and I am wondering how I can set it up so that my server connects to my WAP on boot (specify somewhere in /etc/network/interfaces?). Running "iwconfig" returns my wifi card as being up and "wlan0", so driver support is not an issue. The WAP uses WPA2-PSK AES encryption, and I can get the hex for the key from my laptop (in the keyring manager).

How would I go about setting up the server to connect to the WAP on boot? 

Input much appreciated, thanks.

---

### Post by BuRn_sLuG on 2008-05-20
Help, anyone?

---

