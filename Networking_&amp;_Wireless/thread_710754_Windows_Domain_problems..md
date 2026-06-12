---
title: "Windows Domain problems."
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by Blice on 2008-02-28
Hi guys. I've been trying to get my Ubuntu computer to connect to the windows domain here at work... So, here's the problem I've ran into:

into the root terminal:

```

root@blice:/home/blice# net ads join -U Blice
[2008/02/28 19:35:50, 0] utils/net_ads.c:ads_startup_int(286)
  ads_connect: No logon servers
Failed to join domain: No logon servers

```

I don't know what conf file exactly it is where this is having a problem, if I did I could go in there and look it over again, but I dunno which it is. 


the domain is PCM.LOCAL
The domain controller, with active directory etc. etc., is 192.168.1.7

SO, here's what I have in each of the conf files:



smb.conf:
```

[global]
security = ADS
realm = PCM.LOCAL
password server = 192.167.1.7
workgroup = PCM
wins support = no
wins server = 192.168.1.7
winbind refresh tickets = yes
# Winbinds settings
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
restrict anonymous = 2
domain master = no
local master = no
preferred master = no
os level = 0
# For testing
debuglevel = 2

```


krb5.conf:
```

[libdefaults]
	default_realm = PCM.LOCAL
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        

# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.

#	default_tgs_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	default_tkt_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	permitted_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5

# The following libdefaults parameters are only for Heimdal Kerberos.

[realms]
	PCM.LOCAL = {
		kdc = 192.168.1.7
                default_domain = 192.168.1.7
	}

[domain_realm]
	.pcm.local = 192.168.1.7
	pcm.local = 192.168.1.7

```

common-account:
```

#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account sufficient	pam_winbind.so
account required	pam_unix.so

```

common-auth:
```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth sufficient	pam_winbind.so krb5_auth krb5_ccache_type=FILE
auth required 	pam_unix.so nullok_secure use_first_pass
auth required 	pam_deny.so

```

sudo:
```

#%PAM-1.0

@include common-auth
@include common-account

auth sufficient	pam_winbind.so
auth sufficient	pam_unix.so use_first_pass
auth required	pam_deny.so

```

I also did nsswitch.conf, but I don't think I need to post that since such little had to be done to it.

When I do "kinit [email]Blice@PCM.LOCA[/email]L", it asks me for my password, and it works.



So, can someone direct me to how I might solve my problem? Thanks.

---

### Post by Blice on 2008-02-28
Great, now my root password doesn't work. Ugh. I can't even get back into root terminal or use sudo...

Can someone PLEASE help me out here? I'm going insane.

---

### Post by Blice on 2008-02-29
Bump. I'm still hanging here, guys. Pleaaaaase help? :(

---

### Post by Squawk on 2008-02-29
As requested

sudo
```
#%PAM-1.0

@include common-auth
@include common-account

```

common account
```
account required        pam_unix.so
```

common auth
```
auth    required        pam_unix.so nullok_secure
```

common session
```
session required        pam_unix.so
session optional        pam_foreground.so
```

---

### Post by Blice on 2008-02-29
Thank's to Squawk's help I'm back into my computer and I can log in etc... 

But I still need to join this domain. 


So, in pam.d files, is where I messed up I guess. Where it says "use_first_pass", am I supposed to put my password there?

---

### Post by Blice on 2008-02-29
Okay, so, apparently I don't even need to edit my pam.d, argh.


I followed [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) this tutorial, and I don't get the "ads_connect: No logon servers" error anymore.

NOW, it goes like this:

```

root@blice:/# net ads join -U Blice
Blice's password: 
Failed to join domain: Operations error

```

Yay! 

Okay, so, now any clue what the problem is? Here's my new conf files:

krb5.conf:
```

[libdefaults]
 default_realm = PCM.LOCAL
 krb4_config = /etc/krb.conf
 krb4_realms = /etc/krb.realms
 kdc_timesync = 1
 ccache_type = 4
 forwardable = true
 proxiable = true
# The following libdefaults parameters are only for Heimdal Kerberos.
 v4_instance_resolve = false
 v4_name_convert = {
  host = {
   rcmd = host
   ftp = ftp
  }
  plain = {
   something = something-else
  }
 }
[realms]
PCM.LOCAL = {
        kdc = 192.168.1.7
        admin_server = 192.167.1.7
}
[domain_realm]
 .pcm.local = 192.168.1.7
 pcm.local = 192.168.1.7
[login]
 krb4_convert = true
 krb4_get_tickets = true

```


smb.conf:
```

[global]
        security = ads
        realm = PCM.LOCAL
        password server = 192.168.1.7
# note that workgroup is the 'short' domain name
        workgroup = PCM
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
# to avoid the workstation from
# trying to become a master browser
# on your windows network add the
# following lines
        domain master = no
        local master = no
        preferred master = no
        os level = 0


```

---

### Post by Blice on 2008-02-29
So, I went ahead and did the -d (debug) flag on net ads join...


Here's the first part:

```

root@blice:/home/blice# net -d 10 ads join -U blice
[2008/02/29 12:04:19, 5] lib/debug.c:debug_dump_status(391)
  INFO: Current debug levels:
    all: True/10
    tdb: False/0
    printdrivers: False/0
    lanman: False/0
    smb: False/0
    rpc_parse: False/0
    rpc_srv: False/0
    rpc_cli: False/0
    passdb: False/0
    sam: False/0
    auth: False/0
    winbind: False/0
    vfs: False/0
    idmap: False/0
    quota: False/0
    acls: False/0
    locking: False/0
    msdfs: False/0
    dmapi: False/0
[2008/02/29 12:04:19, 3] param/loadparm.c:lp_load(5039)
  lp_load: refreshing parameters
[2008/02/29 12:04:19, 3] param/loadparm.c:init_globals(1438)
  Initialising global parameters
[2008/02/29 12:04:19, 3] param/params.c:pm_process(572)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2008/02/29 12:04:19, 3] param/loadparm.c:do_section(3778)
  Processing section "[global]"
  doing parameter security = ads
  doing parameter realm = PCM.LOCAL
  doing parameter password server = 192.168.1.7
  doing parameter workgroup = PCM
  doing parameter winbind separator = +
  doing parameter idmap uid = 10000-20000
  doing parameter idmap gid = 10000-20000
  doing parameter winbind enum users = yes
  doing parameter winbind enum groups = yes
  doing parameter template shell = /bin/bash
  doing parameter client use spnego = yes
  doing parameter client ntlmv2 auth = yes
  doing parameter encrypt passwords = yes
  doing parameter winbind use default domain = yes
  doing parameter restrict anonymous = 2
  doing parameter domain master = no
  doing parameter local master = no
  doing parameter preferred master = no
  doing parameter os level = 0
[2008/02/29 12:04:19, 4] param/loadparm.c:lp_load(5070)
  pm_process() returned Yes
[2008/02/29 12:04:19, 7] param/loadparm.c:lp_servicenumber(5208)
  lp_servicenumber: couldn't find homes
[2008/02/29 12:04:19, 10] param/loadparm.c:set_server_role(4314)
  set_server_role: role = ROLE_DOMAIN_MEMBER
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS-2LE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS-2LE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-16LE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-16LE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS-2BE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS-2BE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-16BE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-16BE
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF8
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF8
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-8
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-8
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset ASCII
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset ASCII
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset 646
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset 646
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset ISO-8859-1
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset ISO-8859-1
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS2-HEX
[2008/02/29 12:04:19, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS2-HEX
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2008/02/29 12:04:19, 5] lib/util.c:init_names(287)
  Netbios name list:-
  my_netbios_names[0]="BLICE"
[2008/02/29 12:04:19, 2] lib/interface.c:add_interface(81)
  added interface ip=192.168.1.151 bcast=192.168.1.255 nmask=255.255.255.0
[2008/02/29 12:04:19, 5] lib/gencache.c:gencache_init(61)
  Opening cache file at /var/run/samba/gencache.tdb
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:19, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:19, 4] libsmb/namequery_dc.c:ads_dc_name(73)
  ads_dc_name: domain=PCM
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:19, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:19, 6] libads/ldap.c:ads_find_dc(294)
  ads_find_dc: looking for realm 'PCM.LOCAL'
[2008/02/29 12:04:19, 8] libsmb/namequery.c:get_sorted_dc_list(1626)
  get_sorted_dc_list: attempting lookup for name PCM.LOCAL (sitename Default-First-Site) using [ads]
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(212)
  Cache entry with key = SAF/DOMAIN/PCM.LOCAL couldn't be found
[2008/02/29 12:04:19, 5] libsmb/namequery.c:saf_fetch(133)
  saf_fetch: failed to find server for "PCM.LOCAL" domain
[2008/02/29 12:04:19, 3] libsmb/namequery.c:get_dc_list(1489)
  get_dc_list: preferred server list: ", 192.168.1.7"
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:19, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:19, 10] libsmb/namequery.c:remove_duplicate_addrs2(435)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2008/02/29 12:04:19, 4] libsmb/namequery.c:get_dc_list(1599)
  get_dc_list: returning 1 ip addresses in an ordered list
[2008/02/29 12:04:19, 4] libsmb/namequery.c:get_dc_list(1600)
  get_dc_list: 192.168.1.7:389 
[2008/02/29 12:04:19, 5] libads/ldap.c:ads_try_connect(180)
  ads_try_connect: sending CLDAP request to 192.168.1.7 (realm: PCM.LOCAL)
[2008/02/29 12:04:19, 10] libads/dns.c:sitename_store(638)
  sitename_store: realm = [PCM.LOCAL], sitename = [Default-First-Site], expire = [2147483647]
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_set(140)
  Adding cache entry with key = AD_SITENAME/DOMAIN/PCM.LOCAL; value = Default-First-Site and timeout = Mon Jan 18 22:14:07 2038
   (943178988 seconds ahead)
[2008/02/29 12:04:19, 3] libads/ldap.c:ads_connect(394)
  Connected to LDAP server 192.168.1.7
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:19, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:19, 10] libads/ldap.c:ads_closest_dc(149)
  ads_closest_dc: ADS_CLOSEST flag set
[2008/02/29 12:04:19, 10] libads/kerberos.c:create_local_private_krb5_conf_for_domain(614)
  create_local_private_krb5_conf_for_domain: fname = /var/run/samba/smb_krb5/krb5.conf.PCM, realm = PCM.LOCAL, domain = PCM
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(212)
  Cache entry with key = SAF/DOMAIN/PCM.LOCAL couldn't be found
[2008/02/29 12:04:19, 5] libsmb/namequery.c:saf_fetch(133)
  saf_fetch: failed to find server for "PCM.LOCAL" domain
[2008/02/29 12:04:19, 3] libsmb/namequery.c:get_dc_list(1489)
  get_dc_list: preferred server list: ", 192.168.1.7"
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:19, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:19, 10] libsmb/namequery.c:remove_duplicate_addrs2(435)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2008/02/29 12:04:19, 4] libsmb/namequery.c:get_dc_list(1599)
  get_dc_list: returning 1 ip addresses in an ordered list
[2008/02/29 12:04:19, 4] libsmb/namequery.c:get_dc_list(1600)
  get_dc_list: 192.168.1.7:389 
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(212)
  Cache entry with key = SAF/DOMAIN/PCM.LOCAL couldn't be found
[2008/02/29 12:04:19, 5] libsmb/namequery.c:saf_fetch(133)
  saf_fetch: failed to find server for "PCM.LOCAL" domain
[2008/02/29 12:04:19, 3] libsmb/namequery.c:get_dc_list(1489)
  get_dc_list: preferred server list: ", 192.168.1.7"
[2008/02/29 12:04:19, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:19, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:19, 10] libsmb/namequery.c:remove_duplicate_addrs2(435)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2008/02/29 12:04:19, 4] libsmb/namequery.c:get_dc_list(1599)
  get_dc_list: returning 1 ip addresses in an ordered list
[2008/02/29 12:04:19, 4] libsmb/namequery.c:get_dc_list(1600)
  get_dc_list: 192.168.1.7:389 
[2008/02/29 12:04:19, 10] libads/kerberos.c:get_kdc_ip_string(565)
  get_kdc_ip_string: Returning  kdc = 192.168.1.7
  
[2008/02/29 12:04:19, 5] libads/kerberos.c:create_local_private_krb5_conf_for_domain(683)
  create_local_private_krb5_conf_for_domain: wrote file /var/run/samba/smb_krb5/krb5.conf.PCM with realm PCM.LOCAL KDC = 192.168.1.7
[2008/02/29 12:04:19, 4] libsmb/namequery_dc.c:ads_dc_name(139)
  ads_dc_name: using server='PCMPDC.PCM.LOCAL' IP=192.168.1.7

```

So, now it asks me for my password, and then continues until I get the usual error and it stops...

```

blice's password: 
[2008/02/29 12:04:24, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:24, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:24, 6] libads/ldap.c:ads_find_dc(294)
  ads_find_dc: looking for realm 'PCM.LOCAL'
[2008/02/29 12:04:24, 8] libsmb/namequery.c:get_sorted_dc_list(1626)
  get_sorted_dc_list: attempting lookup for name PCM.LOCAL (sitename Default-First-Site) using [ads]
[2008/02/29 12:04:24, 10] lib/gencache.c:gencache_get(212)
  Cache entry with key = SAF/DOMAIN/PCM.LOCAL couldn't be found
[2008/02/29 12:04:24, 5] libsmb/namequery.c:saf_fetch(133)
  saf_fetch: failed to find server for "PCM.LOCAL" domain
[2008/02/29 12:04:24, 3] libsmb/namequery.c:get_dc_list(1489)
  get_dc_list: preferred server list: ", 192.168.1.7"
[2008/02/29 12:04:24, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/PCM.LOCAL, value = Default-First-Site, timeout = Mon Jan 18 22:14:07 2038
[2008/02/29 12:04:24, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for PCM.LOCAL: "Default-First-Site"
[2008/02/29 12:04:24, 10] libsmb/namequery.c:remove_duplicate_addrs2(435)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2008/02/29 12:04:24, 4] libsmb/namequery.c:get_dc_list(1599)
  get_dc_list: returning 1 ip addresses in an ordered list
[2008/02/29 12:04:24, 4] libsmb/namequery.c:get_dc_list(1600)
  get_dc_list: 192.168.1.7:389 
[2008/02/29 12:04:24, 5] libads/ldap.c:ads_try_connect(180)
  ads_try_connect: sending CLDAP request to 192.168.1.7 (realm: PCM.LOCAL)
[2008/02/29 12:04:24, 10] libads/dns.c:sitename_store(638)
  sitename_store: realm = [PCM.LOCAL], sitename = [Default-First-Site], expire = [2147483647]
[2008/02/29 12:04:24, 10] lib/gencache.c:gencache_set(140)
  Adding cache entry with key = AD_SITENAME/DOMAIN/PCM.LOCAL; value = Default-First-Site and timeout = Mon Jan 18 22:14:07 2038
   (943178983 seconds ahead)
[2008/02/29 12:04:24, 3] libads/ldap.c:ads_connect(394)
  Connected to LDAP server 192.168.1.7
[2008/02/29 12:04:29, 2] libads/ldap.c:ldap_open_with_timeout(70)
  Could not open LDAP connection to PCMPDC.pcm.local:389: Illegal seek
[2008/02/29 12:04:29, 1] utils/net_ads.c:net_ads_join(1470)
  error on ads_startup: Operations error
[2008/02/29 12:04:29, 10] intl/lang_tdb.c:lang_tdb_init(138)
  lang_tdb_init: /usr/share/samba/en_US.UTF-8.msg: No such file or directory
Failed to join domain: Operations error
[2008/02/29 12:04:29, 2] utils/net.c:main(1036)
  return code = -1
root@blice:/home/blice# 


```

---

### Post by shushotora on 2008-04-14
I am haveing a similiar problem and am unable to add my machine to the company domain. I keep getting:

Failed to join domain: Operations error

I know kerberos works, because I am able to get a valid ticket.

here is my smb.conf file, anybody have an idea?

```
[global]
        security = ads
        realm = CONVERGENCE.LOCAL
        password server = 192.168.1.51
# note that workgroup is the 'short' domain name
        workgroup = CONVERGENCE
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
# to avoid the workstation from
# trying to become a master browser
# on your windows network add the
# following lines
        domain master = no
        local master = no
        preferred master = no
        os level = 0
```

---

### Post by seeker1458 on 2008-04-14
I have been trying to work out the bugs on getting my gutsy box on an AD domain also.  I have actually gotten the "joined xxx.com" domain message but I am still not being managed by the DC.  Example, if I reset the user password in AD, it doesn't get reset on the linux box.  I am considering upgrading to Hardy to use the likewise-open app.  I can't find any support for Gutsy is the only reason im considering going beta.  May be worth it?

---

### Post by seeker1458 on 2008-04-14
This is straight out of the Likewise administrator manual.

>  Files Modified During a Domain Join
 When Likewise joins a computer to a domain, it modifies some system
 files. The files that are modified depend on the platform, the distribution,
 and the system's configuration. The following files might be modified.
 Note: Not all of these files are present on all computers.
&#8226;     /etc/nsswitch.conf
&#8226;     /etc/pam.conf or /etc/pam.d/*
&#8226;     /etc/ssh/{ssh_config,sshd_config} (or wherever sshd configuration is
      located)
&#8226;     /etc/hosts (To join a domain without modifying /etc/hosts, see Join
      Active Directory Without Changing /etc/hosts.)
                                                                           20
 Copyright © 2008 Likewise Software. All rights reserved.
                                           
Product Documentation
Likewise Open: Installation and Administration Guide
                                         &#8226;   /etc/apparmor.d/abstractions/nameservice
                                         &#8226;   /etc/X11/gdm/PreSession/Default
                                         &#8226;   /etc/vmware/firewall/services.xml
                                         &#8226;   /usr/lib/security/methods.cfg
                                         &#8226;   /etc/security/user
                                         &#8226;   /etc/security/login.cfg
                                         &#8226;   /etc/netsvc.conf
                                         &#8226;   /etc/krb5.conf
                                         &#8226;   /etc/krb5/krb5.conf
                                         &#8226;   /etc/rc.config.d/netconf
                                         &#8226;   /etc/nodename
                                         &#8226;   /etc/{hostname,HOSTNAME,hostname.*}
                                         &#8226;   /etc/sysconfig/network/config
                                         &#8226;   /etc/sysconfig/network/dhcp
                                         &#8226;   /etc/sysconfig/network/ifcfg-*
                                         &#8226;   /etc/sysconfig/network-scripts/ifcfg-*

---

### Post by chemist109 on 2008-04-15
I believe that the problem is the .local domain.  You can't do AD logins with a .local domain because .local is reserved for mdns.  I found this thread which addresses this problem:

[https://bugzilla.novell.com/show_bug.cgi?id=331036#c38](https://bugzilla.novell.com/show_bug.cgi?id=331036#c38)

---

### Post by shushotora on 2008-04-15
Well i got the machine added to domain i used this forum
[http://ubuntuforums.org/showthread.php?t=91510]("http://ubuntuforums.org/showthread.php?t=91510")
However, now when attempt to log in with a domain user I get a "Access Denied" Message, yet when i do a wlist -u i get the users and when i attempt to to a useradd i get a user already exists message. Any ideas.

---

