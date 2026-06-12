---
title: "sssd instead of winbind to authenticate against Active Directory?"
date: 2016-05-05
forum: Networking &amp; Wireless
---

### Post by jeff.sadowski on 2016-05-05
I had seen some posts talking about using sssd to allow Active Directory users to use a linux machine.

Currently I am using winbind and samba and I have that working but I was going to experiment with getting sssd working but am not having any luck.

my smb.conf file while using winbind
> [global]
   security = ads
   realm = SUBDOMAIN.DOMAIN.TLD
   workgroup = SUBDOMAIN
   idmap config * : backend = tdb
   idmap config * : range = 2000-7999
   idmap config SUBDOMAIN:backend = ad
   idmap config SUBDOMAIN:schema_mode = rfc2307
   idmap config SUBDOMAIN:range = 8000-9999999
   winbind nss info = rfc2307
   winbind use default domain = yes
   # so that the users show up in getent
   winbind enum users = yes
   # so that the groups show up in getent
   winbind enum groups = yes
   restrict anonymous = 2
   #added the following 2 for the Badlock updates that change the defaults
   #to no longer work with my domain controllers
   ldap server require strong auth = no
   client ldap sasl wrapping = plain


I then started following this howto

[https://help.ubuntu.com/lts/serverguide/sssd-ad.html](https://help.ubuntu.com/lts/serverguide/sssd-ad.html)

my krb5.conf after following the howto
> [libdefaults]
 default_realm = SUBDOMAIN.DOMAIN.TLD
 ticket_lifetime = 24h
 renew_lifetime = 7d



my smb.conf file after following the howto
> [global]
   security = ads
   realm = SUBDOMAIN.DOMAIN.TLD
   workgroup = SUBDOMAIN
   log file = /var/log/samba/%m.log
   kerberos method = secrets and keytab
   client signing = yes
   client use spnego = yes
#I tried with and without these to see if the badlock bug fixes had anything to do with it
   ldap server require strong auth = no
   client ldap sasl wrapping = plain


my sssd.conf
> [sssd]
services = nss, pam
config_file_version = 2
domains = SUBDOMAIN.DOMAIN.TLD

[domain/SUBDOMAIN.DOMAIN.TLD]
id_provider = ad
access_provider = ad


my /etc/nsswitch.conf
> passwd:         compat winbind sss
group:          compat winbind sss
shadow:         compat
hosts:          files mdns4_minimal [NOTFOUND=return] dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis sss
sudoers:        files sss


my 14.04 system did not recognize systemctl so I used service instead

service ntp restart
service smbd restart
service nmbd restart
service sssd restart

kinit myadminusername

"klist" shows
>  
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [email]myadminusername@SUBDOMAIN.DOMAIN.TLD[/email]

Valid starting       Expires              Service principal
05/05/2016 11:25:49  05/05/2016 21:25:49  krbtgt/SUBDOMAIN.DOMAIN.TLD@SUBDOMAIN.DOMAIN.TLD
	renew until 05/05/2016 21:25:49
05/05/2016 11:26:24  05/05/2016 21:25:49  cifs/DC2.SUBDOMAIN.DOMAIN.TLD@SUBDOMAIN.DOMAIN.TLD
05/05/2016 11:26:23  05/05/2016 21:25:49  ldap/dc2.SUBDOMAIN.DOMAIN.TLD@SUBDOMAIN.DOMAIN.TLD


"net ads join -k" shows
> Using short domain name -- SUBDOMAIN
Joined 'MYMACHINENAME' to dns domain 'SUBDOMAIN.DOMAIN.TLD'


And here is where it fails for me

getent passwd myadminusername

returns empty
And  can not login

reverting to my original smb.conf I had to remove and install winbind to get it working again

Does anyone know sssd enough to be able to help me in where I should look to start troubleshooting this?
grep "" /var/log/sssd/*
shows as follows
> 
sssd_SUBDOMAIN.DOMAIN.TLD.log:(Thu May  5 14:08:29 2016) [sssd[be[SUBDOMAIN.DOMAIN.TLD]]] [ad_account_info_complete] (0x0010): Bug: dp_error is OK on failed request
sssd_SUBDOMAIN.DOMAIN.TLD.log:(Thu May  5 14:10:47 2016) [sssd[be[SUBDOMAIN.DOMAIN.TLD]]] [ad_account_info_complete] (0x0010): Bug: dp_error is OK on failed request
sssd_SUBDOMAIN.DOMAIN.TLD.log:(Thu May  5 14:10:47 2016) [sssd[be[SUBDOMAIN.DOMAIN.TLD]]] [ad_account_info_complete] (0x0010): Bug: dp_error is OK on failed request


---

### Post by bmorgenthaler on 2016-08-31
Have your tried to login with:

```
[EMAIL="myadminusername@subdomain.domain.tld"]myadminusername@subdomain.domain.tld[/EMAIL]
```

It appears that in your /etc/sssd/sssd.conf you haven't set
```
use_fully_qualified_names = False
```

If you don't set that, then it is going to want your fully qualified [email]username@domain.tld[/email]

---

### Post by campermike on 2016-11-15
I am having the same issue trying to use realmd... I did change the use_fully_qualified_names  setting in the sssd.conf file and it did not help.

---

### Post by campermike on 2016-11-17
> **campermike said:**
> I am having the same issue trying to use realmd... I did change the use_fully_qualified_names  setting in the sssd.conf file and it did not help.

I figured this out, but it was a bit painful.  It turned out that our AD domain is quite large, and sssd was unable to map many of our IDs to Linux IDs.  Here's what I did to find and fix this issue:

1) added the following line to /etc/sssd/sssd.conf underneath my domain config:
*debug_level = 9*
   This logs pretty much every sssd event in the domain in the file in /var/log/sssd/domain_name.log.  This is very helpful during troubleshooting, but remember to remove it when done as it will create a large log file pretty rapidly!

2) I restarted the sssd service to read the new log setting:
[I]sudo service sssd restart

[/I]3) I tried to look up some AD ids*id username*

4) I noticed the following error in the log which eventually lead me to the solution:(unimportant SID information is x'd out):
(Wed Nov 16 16:51:25 2016) [sssd[be[mw.na.cat.com]]] [sdap_idmap_sid_to_unix] (0
x0080): Could not convert objectSID [S-1-x-xx-xxxxxxxxx-xxxxxxxxxx-xxxxxxxxxx-28
0310] to a UNIX ID

5) After more research, I learned that the default range for SID to unix ID mapping is only 200000.  The AD id for my account was 280310!  We have a very large domain and many if not most accounts are above the 200000 number.

6) I tried to increase the range to a more reasonable number by adding the line below to the /etc/sssd/sssd.conf underneath the domain:

ldap_idmap_range_size = 800000

7) After restarting sssd, I had a new error in the log file:
(Wed Nov 16 16:58:57 2016) [sssd[be[mw.na.cat.com]]] [sdap_idmap_add_domain] (0x
0020): BUG: Range maximum exceeds the global maximum: 3545200000 > 2000200000

8) The cause of the new error was that I did not clear out the sssd cache file.  You need to stop sssd, remove the cache_ *domain_name*.ldb file from /var/lib/sss/db and then start sssd

9)After removing the db and restarting sssd, it all works.  The final step was to remove the debug line to go back to normal logging.  Hope this helps someone that has a problem like this in the future!

---

