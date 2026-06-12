---
title: "Need help with Samba and LDAP in 16.04 after upgrading to 14.04"
date: 2017-04-06
forum: Networking &amp; Wireless
---

### Post by xiaozhupa on 2017-04-06
Hi guys,

I have been having trouble fixing this last error (hopefully!) after my upgrade from 14.04 to 16.04.

Basically I am not able to get my smbldap list of users and their respective logins.  So basically:-

[B]sudo smbldap-usershow 
[/B]will give[INDENT]smbldap_search_domain_info: Adding domain info for ATHENA failed with NT_STATUS_UNSUCCESSFUL[/INDENT]
[INDENT]pdb_init_ldapsam: WARNING: Could not get domain info, nor add one to the domain. We cannot work reliably without it.[/INDENT]
[INDENT]pdb backend ldapsam:ldapi:/// did not correctly init (error was NT_STATUS_CANT_ACCESS_DOMAIN_INFO)[/INDENT]
[INDENT]WARNING: Could not open passdb[/INDENT]
[INDENT]Failed to get SID from Samba net command at /usr/share/perl5/smbldap_tools.pm line 250.[/INDENT]
[INDENT]Compilation failed in require at /usr/sbin/smbldap-usershow line 27.[/INDENT]
[INDENT]BEGIN failed--compilation aborted at /usr/sbin/smbldap-usershow line 27.[/INDENT]

**sudo ldapsearch -x**
will give[INDENT]# extended LDIF[/INDENT]
[INDENT]#[/INDENT]
[INDENT]# LDAPv3[/INDENT]
[INDENT]# base <> (default) with scope subtree[/INDENT]
[INDENT]# filter: (objectclass=*)[/INDENT]
[INDENT]# requesting: ALL[/INDENT]
[INDENT]#[/INDENT]
[INDENT]
[/INDENT]
[INDENT]# search result[/INDENT]
[INDENT]search: 2[/INDENT]
[INDENT]result: 32 No such object[/INDENT]
[INDENT]
[/INDENT]
[INDENT]# numResponses: 1[/INDENT]

The services samba, smbd, nmbd, slapd all run fine under --status-all.

**tail /var/log/samba/log.smbd**
gives me[INDENT][2017/04/04 21:36:41.396060,  0] ../source3/passdb/pdb_ldap.c:6534(pdb_ldapsam_init_common)[/INDENT]
[INDENT]  pdb_init_ldapsam: WARNING: Could not get domain info, nor add one to the domain. We cannot work reliably without it.[/INDENT]
[INDENT][2017/04/04 21:36:41.396124,  0] ../source3/passdb/pdb_interface.c:179(make_pdb_method_name)[/INDENT]
[INDENT]  pdb backend ldapsam:ldapi:/// did not correctly init (error was NT_STATUS_CANT_ACCESS_DOMAIN_INFO)[/INDENT]
[INDENT][2017/04/06 16:55:46.397709,  0] ../source3/passdb/pdb_ldap_util.c:313(smbldap_search_domain_info)[/INDENT]
[INDENT]  smbldap_search_domain_info: Adding domain info for ATHENA failed with NT_STATUS_UNSUCCESSFUL[/INDENT]
[INDENT][2017/04/06 16:55:46.397762,  0] ../source3/passdb/pdb_ldap.c:6534(pdb_ldapsam_init_common)[/INDENT]
[INDENT]  pdb_init_ldapsam: WARNING: Could not get domain info, nor add one to the domain. We cannot work reliably without it.[/INDENT]
[INDENT][2017/04/06 16:55:46.397774,  0] ../source3/passdb/pdb_interface.c:179(make_pdb_method_name)[/INDENT]
[INDENT]  pdb backend ldapsam:ldapi:/// did not correctly init (error was NT_STATUS_CANT_ACCESS_DOMAIN_INFO)[/INDENT]



Ok so I figure it is some domain issues but everything seems to be configured fine for me.
[B]sudo slapcat 
[/B]gives me[INDENT]dn: dc=gao,dc=com
objectClass: top
objectClass: dcObject
objectClass: organization
o: Gao
dc: gao
structuralObjectClass: organization
entryUUID: 132ba4e8-ab70-1036-82a8-3774dbf3d7a3
creatorsName: cn=admin,dc=gao,dc=com
createTimestamp: 20170401214406Z
entryCSN: 20170401214406.368951Z#000000#000#000000
modifiersName: cn=admin,dc=gao,dc=com
modifyTimestamp: 20170401214406Z


dn: cn=admin,dc=gao,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: e1NTSEF9Sk9VRnZBVHo3OWtLRFdTY1ZnekhkNU91Tzhzd2tIRGk=
structuralObjectClass: organizationalRole
entryUUID: 1355f0fe-ab70-1036-82a9-3774dbf3d7a3
creatorsName: cn=admin,dc=gao,dc=com
createTimestamp: 20170401214406Z
entryCSN: 20170401214406.646150Z#000000#000#000000
modifiersName: cn=admin,dc=gao,dc=com
modifyTimestamp: 20170401214406Z


[/INDENT]

What are the next steps I should be looking at to fix this?  

For reference, things that I had to fix and hopefully have been fixed are networking issues due to the naming of ethernet eth0 vs ens0 stuff, php upgrade breaking some stuff on apache websites loading, there was a crc error for a file after slapcat but I fixed that.  For some reason I think it has to do with networking still perhaps and perhaps me setting up the bridging wrong for my network.

---

