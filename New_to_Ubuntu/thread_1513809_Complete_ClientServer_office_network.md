---
title: "Complete Client/Server office network"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by CrimsonRider on 2010-06-20
Gentlemen, and lady's of course,

I admit, this is a newbie question if there ever was one. I am by no means new to the linux game, but for some reason, I've never done this;

How does one replace a windows client/server network with a linux Ubuntu equivalent?

I've done the linux backend with windows clients before. Samba PDC and all, but now I need basicly windows 'domain' functionality in a linux flavor. Let me describe the situation.

I have 12 workstations, all of those need to run e-mail, shared calender and office. Some of those need to run a terminal application on a central server. All of those need to use the same software. The clients are in a corporate environment and users should not be able to install anything themselves.

OpenOffice will be fine for office.
Evolution or Thunderbird would do for mail.
Calender, I have no idea what app to use for shared calendering, nor wich server to use for that. Never did it before.
Internet, if the clients need it, can be done via FireFox and a Squid proxy on the server.

But, and here is my real kicker, cos no matter how much I Google, any answer relates only to Windows of Win/Lin combo's, any user must be able to log into any workstation. And keep his or her own settings, documents etc. In windows I would call those roaming profiles, in Linux, no idea.

Any help or hints, or plain search terms to look for, would be much appreciated.

---

### Post by spiky001 on 2010-06-20
is this what you are looking for
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by CrimsonRider on 2010-06-20
It seems that deals mostly with basic server installation. I can do most of that already, it's the clients that I am worried about. How do I make them behave as the equivalent of roaming profile windows clients?

Thank you.

---

### Post by spiky001 on 2010-06-20
Found this about half way down page
[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by CrimsonRider on 2010-06-20
That deals mostly with Samba. Is it neccessary to use Samba SMB/CIFS functions in a pure linux environment? I know how to set up Samba as a Primary Domain Server, but I don't think that's what I want here.

Thanks for your answer.

---

### Post by spiky001 on 2010-06-20
this is with ssh
[http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/](http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/)

---

### Post by hannaman on 2010-06-20
You could use LDAP for user authentication on all of the workstations and automount their home directories and/or a shared directory from a central location upon login.  That way no matter which workstation they log into they always have their home directory (assuming the network is available, etc.) with the same stuff in it.
Try looking through this web page:
[https://help.ubuntu.com/community/AutofsLDAP](https://help.ubuntu.com/community/AutofsLDAP)

---

### Post by CrimsonRider on 2010-06-21
Thank you.

It does look complex. I am looking for a simple replacement of the Windows roaming profiles functionality. Is this the best Ubuntu can manage?

---

### Post by CrimsonRider on 2010-06-21
I've now found a page about it [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

It also mention Kerberos, I'll look into it.

---

### Post by phr0ze on 2010-06-21
Can't you set all users home folders to a network location? I wonder what the performance would be.

LDAP is really to solve a different problem.
The downside is without LDAP you would have to create the user account on every machine. Then if you implement any sort of password change policy your account maintenance will be huge. so LDAP is a good solution.

---

### Post by eriktheblu on 2010-06-21
Are you looking for thin clients? [https://help.ubuntu.com/community/UbuntuLTSP]("https://help.ubuntu.com/community/UbuntuLTSP")

I think the shared calendar can be accomplished in Evolution using symbolic links.

---

### Post by hannaman on 2010-06-22
LDAP would probably be the best solution for name services.  LDAP would be like Active Directory in Windows.  Autofs can be used to map home directories and/or share directories from a central location.  The combination of the two would seem to meet the OP's requirements.  The article I linked described how to use LDAP to store the automount maps so there is a single place for administration.

---

