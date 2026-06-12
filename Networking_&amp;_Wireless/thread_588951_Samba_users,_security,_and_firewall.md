---
title: "Samba: users, security, and firewall"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Meson on 2007-10-23
I'm trying to setup Samba and I have a few questions.

1) I'd like windows users to be able to access my computer without entering a password.  Can this be done?

2) I'd like to set specific permissions per folder for users.  Can this be done?

3) Samba was working fine until I installed Firestarter (which I thought was just a gui for netstat/iptables).  However once installed Samba only worked when I stopped it.  I tried to enable all the things that were blocked, but it still never worked.  How can I configure my firewall to allow access to samba from a specific machine/in a specific network?

4) Unrelated but, does number 3 mean that before firestarter was installed or after it's uninstalled that the interfaces on my computer are wide open?  This is scary.

---

### Post by froy02 on 2007-10-23
I do not think that you could access Ubuntu files from  windows XP, Vista home and premium editions.  But you could access your shared windows folder from Ubuntu mchines using samba.  I was never successful.  

You have to disable firestarter to network or else you would not connect to other computer.  I have tried to configure firestarter different ways but it was a no go.  From what I read in the forums firestarter is not necessary for linux.

---

### Post by Meson on 2007-10-23
> **froy02 said:**
> I do not think that you could access Ubuntu files from  windows XP, Vista home and premium editions.  But you could access your shared windows folder from Ubuntu mchines using samba.  I was never successful.  
This is not correct

> You have to disable firestarter to network or else you would not connect to other computer.  I have tried to configure firestarter different ways but it was a no go.  From what I read in the forums firestarter is not necessary for linux.
I know it's not necessary but I don't know much about writing my own configuration files for iptables.

---

