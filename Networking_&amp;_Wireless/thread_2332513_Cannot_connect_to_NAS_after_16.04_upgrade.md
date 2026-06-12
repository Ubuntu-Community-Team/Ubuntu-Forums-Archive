---
title: "Cannot connect to NAS after 16.04 upgrade"
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by lou6 on 2016-08-01
I originally posted this problem in another thread implying that the culprit was Samba but now I'm not so sure so I closed that thread and started this one.

I have a WD My Cloud NAS which I've been using for several years through Nautilus using a location bookmark (smb://000.000.0.000, not all zeros of course but the ip of the device). I have smbclient installed (but not Samba itself) and all was well until the 16.04 LTS upgrade.

Now, I cannot connect to the NAS at all - no error messages, just no connection.

I originally assumed this was due to a Samba bug (and on Launchpad there are a few) but now I'm not so sure because I can't connect using Gigolo either (which uses GVFS for network connections, an entirely different method than Samba).

So far I've reinstalled smbclient, gigolo, gvfs-fuse, restarted the computer and recreated my Nautilus bookmark (several times) all with no good result.

I don't have a great deal of Linux experience and am hoping someone here can help me solve this issue.

EDIT: not to over-simplify this but it seems to me that whatever gvs-open and smbclient have in common is what isn't working.

Thanks in advance...

---

### Post by lou6 on 2016-08-02
Following the advice on a post in the Networking forum I added the following lines to etc/samba/smb.conf

client use spnego = no
client ntlmv2 auth = no
client ipc max protocol = NT1

The problem persists - still cannot connect with Nautilus, Thunar or Gigolo with no error message or any other indication of the cause.

EDIT: I have the results of smbtree -d3 ready to share if anyone who wishes to help would like to chime in

---

### Post by lou6 on 2016-08-02
I removed the three client mods from the beginning of smb.conf before this since they did not seem to affect my results.

```

lou@lou-Latitude-D620:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface wlan0 ip=192.168.1.102 bcast=192.168.1.255 netmask=255.255.255.0
Enter lou's password:
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: No such file or directory
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: No such file or directory
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\WDMYCLOUD              WD My Cloud
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WDMYCLOUD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WDMYCLOUD<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WDMYCLOUD<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: No such file or directory
Connecting to 198.105.244.69 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=18 destlen=16 - 'LOU-LATITUDE-D620'
Connecting to 198.105.244.69 at port 139
Connecting to 198.105.254.69 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=18 destlen=16 - 'LOU-LATITUDE-D620'
Connecting to 198.105.254.69 at port 139




```

At this point a box pops up on the Nautilus screen saying "OOPS! something went wrong" or words to that effect...

---

### Post by lou6 on 2016-08-03
After hours of searching and experimentation I found a solution to this problem:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1409032](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1409032)

Post #29 provides a workaround.

The question raised in the discussion "how can this bug be unassigned after 18 months" is a valid one and needs to be answered.

I'm going to wait until I see this resolved before installing the 16.04 upgrade on my primary computer...

---

