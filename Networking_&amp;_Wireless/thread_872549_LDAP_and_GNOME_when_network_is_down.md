---
title: "LDAP and GNOME when network is down"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by larseko on 2008-07-28
Ok, sorry for the bad title. The thing is: I have about 25 laptops that we use as roaming workstations on the school I work at. These are setup with a fixed wireless network, and normally use LDAP/PAM for authentication, together with NFS and autofs for mounting of home areas. We also have a local account on the computers, in case of network troubles.

This has worked well until Ubuntu 6.06, but after setting up a laptop with 8.04 I have problems with hangups/timeouts in GNOME when I test to login locally when there is no network. The bootup goes just as normal, with no apparent delays, but when I login with a local user, it hangs there for some minutes before panel and desktop comes up. Some times I'll get an error message that some app didn't load. The last time I checked, for instance: "The panel encountered a problem while "OAFIID: GNOME_Panel_TrashApplet" was being loaded."

Our customized ldap.conf looks like this:

```

uri	ldap://our_ldapserver
ldap_version	3
base	dc=our_dc,dc=no
scope	sub
timelimit	30
pam_login_attribute	uid
pam_filter objectclass=posixAccount
ssl	start_tls
TLS_CACERT	/etc/ldap/cacert.pem
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,daemon,dhcp,games,gdm,gnats,haldaemon,hplip,irc,klog,libuuid,list,lp,mail,man,messagebus,news,polkituser,proxy,pulse,root,statd,sync,sys,syslog,uucp,www-data
network_timeout	3 # Just for testing, but didn't affect this problem

```

We also have a modified nsswitch.conf:

```


passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

nss_base_passwd ou=people,dc=our_dc,dc=no?one
nss_base_shadow ou=people,dc=our_dc,dc=no?one
nss_base_group ou=group,dc=our_dc,dc=no?one

```

Also, the timeouts/delays/hangups also happen if I for instance try to log off/shutdown. It will wait 15-20 secs before I get the logoff/shutdown dialog. Any app will start pretty instantly, but the GNOME system stuff seems to have this delay.

At first I thought it could be some DNS issue, and something to do with nss, but I'm not 100% confident how this works.

Has anyone got any idea here? I'd be grateful. I'll see if I can find something interesting in the logs.

---

### Post by larseko on 2008-07-29
No suggestions here? Could there be some configuration directives that has changed that I do not know of? 

I forgot to say that we specify the wireless network to connect to in the file /etc/interfaces. 

Am I maybe posting this in the wrong section? :)

---

### Post by torry_loon on 2008-07-29
Your passwd, shadow & group sections in nsswitch.conf should include "files", like so:

passwd: files ldap
group: files ldap
shadow: files ldap

The local authentication files will be checked first before LDAP. If the LDAP server is unavailable, you will still be able to log in with the local user without waiting for the LDAP connection to timeout.

Did you edit /etc/ldap.conf and /etc/ldap/ldap.conf?

---

### Post by larseko on 2008-07-31
Thanks, I've corrected those options in the nsswitch.conf, but my problem seems to be after login. Authentication goes without noticable delay, but the gnome session takes a long time to start.

Regarding ldap.conf, both are there, but looks nearly identical. I thought only one of them was being used, but it seems like both have been read today, but with 2 minutes apart. Strange.

---

### Post by larseko on 2008-08-07
Still in the dark on this one. The problem is making these PCs totally useless without network. Could it be network manager related? I've had many problems with that before. Probably should try disabling it.

---

### Post by kcnnc on 2008-10-09
Anyone has a solution for this yet? I'm also getting the same problem with my setup.

---

### Post by Den_Irk on 2008-10-13
Try to use IP-address instead of server_name in your ldap.conf file:

uri	ldap://ip_address_of_your_ldap_server

I had similar problem and this helped me.

---

### Post by larseko on 2008-10-27
I'm still having these problems. Also, Hardy Heron is generally very much slower than previous versions during logon when network actually is up. Users hare very unhappy with the situation, as Hardy Heron has made their PC experience much worse (slow GNOME, no longer support for external VGA, these LDAP problems etc.) than before. I'm considering going back to 6.06, which was better in many respects, but then I'd have to settle with old versions of much software or compile/customize stuff myself, which I'm not very keen on. 

Sorry about rant, but something must be wrong with this config? For instance, the "files ldap" didn't really do the trick. The login hangs forever (about 10 minutes) when network is down, even with local users, and not only GNOME, also the ordinary console.

---

### Post by Den_Irk on 2008-10-29
All local users and services must be in&#1089;luded in the "nss_initgroups_ignoreusers" section. Otherwise nss_ldap would try to find each local user or service in LDAP during loading or logon. Did you? You may want to read this article [https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto) Hope this helps.

---

### Post by larseko on 2008-10-29
Thanks, that worked! After adding the local users to that list, login is completely normal. Stupid mistake, but I thought that it would be sufficient to add the "files" bit to the nsswitch.conf file, making it look in the local auth files first. Thanks again, really saved my day!

---

