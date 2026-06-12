---
title: "[SOLVED] 15 character NetBIOS hostname limitation in SAMBA/CIFS causing mount failure"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by uconnkoala on 2016-03-27
I just spend the last 5 hours irrationally yelling at my server before finding an external post which really helped point me in the right direction.

Symptoms: 

Unable to log into my previously working SAMBA server and mount my shares.

Troubleshooting:

Completely rebuilt my user accounts, both UNIX and SMBPASSWD.
Tried to change smb.conf authentication from tdbsam to smbpasswd, and back again.
Attempted logins from Windows, Linux, using domain as part of the username "DOMAIN\username", "username@DOMAIN"
Copied previously working server config and tdb databases and reinstalled samba.
Turned up smb.conf log level to 10 (it didn't go to 11, unfortunately).

Resolution:

NetBIOS has a legacy limitation of 15 characters in a hostname....which I apparently ran into because my server hostname was 17 characters after my upgrade.

[B]I changed my hostname to something less than 15 characters, rebooted, and viola! Working!
[/B]

Helpful post: [https://bbs.archlinux.org/viewtopic.php?id=190592]("https://bbs.archlinux.org/viewtopic.php?id=190592")

Helpful Log Messages:

```

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


[883148.023038] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[883148.023053] CIFS VFS: Send error in SessSetup = -13
[883148.023210] CIFS VFS: cifs_mount failed w/return code = -13

```

```
  
[2016/03/26 23:44:29.728645,  3, pid=31971, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:177(auth_check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [KOALA-SUPERMICRO1]\[xxxxxxx]@[] with the new password interface
[2016/03/26 23:44:29.728672,  3, pid=31971, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:180(auth_check_ntlm_password)
  check_ntlm_password:  mapped user is: [KOALA-SUPERMICRO1]\[xxxxxxx]@[]

[2016/03/26 23:44:29.728881,  8, pid=31971, effective(0, 0), real(0, 0)] ../source3/lib/util.c:1200(is_myname)
  is_myname("KOALA-SUPERMICRO1") returns 0

[2016/03/26 23:44:29.728908,  6, pid=31971, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth_sam.c:88(auth_samstrict_auth)
  check_samstrict_security: KOALA-SUPERMICRO1 is not one of my local names (ROLE_STANDALONE)

check_ntlm_password:  Authentication for user [xxxxxxx] -> [xxxxxxx] FAILED with error NT_STATUS_NO_SUCH_USER
[2016/03/26 23:44:29.728989,  5, pid=31971, effective(0, 0), real(0, 0)] ../source3/auth/auth_ntlmssp.c:144(auth3_check_password)
  Checking NTLMSSP password for KOALA-SUPERMICRO1\xxxxxxx failed: NT_STATUS_NO_SUCH_USER
[2016/03/26 23:44:29.729019,  5, pid=31971, effective(0, 0), real(0, 0)] ../auth/ntlmssp/ntlmssp_server.c:454(ntlmssp_server_check_password)
  ../auth/ntlmssp/ntlmssp_server.c:454: Checking NTLMSSP password for KOALA-SUPERMICRO1\xxxxxxx failed: NT_STATUS_NO_SUCH_USER

  NT error packet at ../source3/smbd/sesssetup.c(263) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE

```

```
[2016/03/26 23:49:58.450777,  3, pid=32070, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:177(auth_check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [KOALA-SUPERMICRO1]\[xxxxxxx]@[] with the new password interface
[2016/03/26 23:49:58.450804,  3, pid=32070, effective(0, 0), real(0, 0), class=auth] ../source3/auth/auth.c:180(auth_check_ntlm_password)
  check_ntlm_password:  mapped user is: [KOALA-SUPERMICRO1]\[xxxxxxx]@[]

```

---

