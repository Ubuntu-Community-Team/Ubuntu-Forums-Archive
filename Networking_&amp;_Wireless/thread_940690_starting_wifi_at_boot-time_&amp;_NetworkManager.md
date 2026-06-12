---
title: "starting wifi at boot-time &amp; NetworkManager"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by mitya on 2008-10-07
Good day.

I have a notebook with wifi-card (Kubuntu 8.04).
The system checks credentials against LDAP-server and the /home directory is mounted over NFS.
That's why I need to start wifi BEFORE logging in.

Is there any way to make the system  connect to wifi at boot-time BEFORE loggin in and still use NetworkManager while logged in (for using outside my office)?

As I understand if one configures the network manually in /etc/network/interfaces than interface would become "invisible" for NetworkManager.

I've heard about some drop-in replacements for NetworkManager. Are they usable for such a task or there is a simple 'standard' solution?

Thanks

---

