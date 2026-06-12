---
title: "adding Ubuntu server as a file server in Windows network"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by it_suppport on 2008-10-31
Hi All,

We are trying to install & connect Ubuntu server as a member server in our windows 2003 Std network. For this we are using 
the latest Ubuntu server 8.04 LTS Hardy.
Our windows Network is made up of win2003 ADS server(adserver) with another as a seperate GC server (gcserver). 
We've installed krb5, winbind, Samba, samba-swat in our Ubuntu server.

Whenever I'm trying to connect the ubuntu server in ads, using command **net ads join -U <domain_admin_username>%<password>** it gives us the error message that the **"Host is not configured as a member server"**. 
Please let me know, how can I add the host as a member server to windows AD network.

P.S.: I've also gone thru the ActiveDirectroyWinbindHowto, but it is not helping me much as it has not described the kerberos configuration properly ( this is my personal feeling) or I've not understood it properly. Either way, its not working for me.

---

### Post by it_suppport on 2008-11-01
can anyone help me on this?

---

### Post by ardenen on 2008-11-26
I'm having a similar issue only with a Desktop. 
The error I am getting is:
[B]Host is not configured as a member server.
   Invalid configuration. Exiting....
   Failed to join domain: Invalid domain role
[/B]

It looks like for some reason the device wants to join as a domain server? Or something higher than a desktop. I followed the Activedirectory winbind tutorial and am stuck at this critical point.

---

### Post by ardenen on 2008-11-26
never mind -- i figured it out -- you have to use the config file from the tutorial -- I renamed my original smb.conf to orig.smb.conf then created a new with only the settings from the AD tutorial.

Also ran into another issue where even though I could kinit and have a valid kinit cache file I was getting an error whenever I tried sudo net ads join:
[I]Kinit failed: Client not found in Kerberos database
   Failed to join domain: Improperly formed account name[/I]
To solve this I used sudo net ads join -U [email]myaccount@mydomain.com[/email]

---

