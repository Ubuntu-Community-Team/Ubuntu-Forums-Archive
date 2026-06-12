---
title: "Edubuntu 7.10, winbind - Windows Domain Users No Sound"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by plaforest on 2008-04-23
Hello,

We have a school network that uses Win2K AD for authentication/home directories/app server.

First attempt at integrating Edubuntu (trying to progressively eliminate Windows).

I can authenticate against DC using winbind, but Windows domain virtual users have no sound control - actually message says no sound devices were found.

Found some documentation that suggested adding domain users to the audio group in /etc/group - but this won't work because I can't possibly put all of the users in every possible machine - this kinda defeats the whole purpose of using winbind anyway.

Found other documentation that suggested adding this line to my /etc/security/group.conf

* ; *; * ; Al0000-2400; floppy, cdrom, video, audio, plugdev, users

besides the assumed security risks in granting all users on all terminals for all services at all times access to these groups it just doesn't work

The same documentation said that the pam_unix.so line needed to come before the pam_winbind.so line in my /etc/pam.d/common-auth file, but it doesn't work either way.

Any help will be appreciated.  Config files below.

Thanks

/etc/samba/smb.conf

[global]

   security = ads
   encrypt passwords = true
   passdb backend = tdbsam

   obey pam restrictions = yes
   domain master = no

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template homedir = /home/%D/%U
   template shell = /bin/bash
   client use spnego = yes
   client ntlmv2 auth = yes
   restrict anonymous = 2
   local master = no
   preferred master = no
   os level = 0
   realm = DOMAIN.NAME
   password server = XXX.XXX.XXX.XXX
   winbind use default domain = yes
   winbind refresh tickets = yes
   winbind use nested groups = yes
   acl compatibility = win2k

   winbind enum groups = yes
   winbind enum users = yes




/etc/pam.d/common-account

account sufficient      pam_winbind.so
account required        pam_unix.so


/etc/pam.d/common-auth

auth    sufficient      pam_unix.so nullok_secure use_first_pass
auth    sufficient      pam_winbind.so krb5_auth krb5_ccache_type=FILE
auth    required        pam_deny.so


/etc/pam.d/common-password

password   required   pam_unix.so nullok obscure md5


/ect/pam.d/common-session

session required        pam_unix.so
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel
session optional        pam_foreground.so

/etc/security/group.conf

* ; *; * ; Al0000-2400; floppy, cdrom, video, audio, plugdev, users

---

