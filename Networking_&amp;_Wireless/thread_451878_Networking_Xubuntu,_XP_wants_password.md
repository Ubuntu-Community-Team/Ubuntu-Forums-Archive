---
title: "Networking Xubuntu, XP wants password?"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Blofeld on 2007-05-22
OK, I'm terribly ignorant about networking.
I've hooked up an XP and a Xubuntu box via ethernet and a switch, which sits behind a DSL router.  Both computers connect to the internet, but I have my difficulties connecting between the two of them.
I have gnome-network-manager installed on the Xubuntu machine.
If I go on my XP computer to My network places > View workgroup computers > and click on my Xubuntu computer which is identified by name and as (Samba, Ubuntu) I'm asked for user name and password.  However my regular Xubuntu login doesn't work.
What do I have to do to login?
Where do I go from here?  Do I have to configure Samba?
Thanks!;)

---

### Post by rogier.de.groot on 2007-05-23
Please post the content of your /etc/samba/smb.conf file. But simply put - you can add a Samba user (different from regular users) by using the "smbpasswd -a username" command. Or you can change the Samba settings in /etc/samba/smb.conf to "security = share" in the global section and "public = yes" in your share's section. That would make the share available to everyone without asking for username/password crap.

---

### Post by Blofeld on 2007-05-24
IT WORKED!!!
\\:D/
Thank you Rogier!

---

### Post by ugm6hr on 2007-05-24
This seems so simple.  I'll have to give it a go.  I realise that security may be an issue - but a firewall should ensure that only local network users can get in.  And presumably that's only to your nominated Share folders anyway?

I really only use the Windows Networking / Shared folders facility to transfers files very infrequently, and configuring Samba seemed too confusing.

---

