---
title: "Shared Folders Access on a Windows Network."
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by ajuntament on 2007-02-20
Hi people,
I'm using Ubuntu logged on a WIndows domain (Active Directory). When I go to shared resources on the network i get a login screen asking for username, domain and Password, wich is annoying because I have already been logged on Ubuntu with a username in the Domain. This same scenario works properly on ... yes, on windows :guitar: 
I guess I have to do something with smb.conf, but I'm not pretty sure. 
I attach  part of my smb.conf.

```

#======================= Global Settings =======================

[global]

	security = ads
	realm = my_realm
	password server = server_AD
	workgroup = my_workgroup
	idmap uid = 500-1000000
	idmap gid = 500-1000000
	winbind enum users = no
	winbind enum groups = no
	winbind use default domain = yes
	template homedir = /home/%U
	template shell = /bin/bash
	client use spnego = yes
	domain master = no
	encrypt passwords = yes

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700


[operador]
path = /home/operador
available = yes
browsable = yes
public = yes
writable = yes


```

---

### Post by apjone on 2007-02-20
You would have to install winbind + krb5 i think and have it join the domain . this should help with that.

[http://ubuntuforums.org/showthread.php?t=268633&highlight=active+directory+auth](http://ubuntuforums.org/showthread.php?t=268633&highlight=active+directory+auth)

I have done a proxy server , but not tried a desktop. May try it

---

### Post by ddoctor on 2007-02-21
I think winbind has krb5 built-in, as of some version half-way through last year, so you don't need a separate krb5 setup.

If you're logging onto the windows domain with the Ubuntu box, presumably you're doing this with pam_winbind.so. I think you need to also use pam_smb to get the single sign-on to shared folders stuff you're used to.

Your PAM config files would also be useful in diagnosing this issue.

In my experience, working linux with AD domains is do-able, but a pain in the butt. I'm trying to do similar... really, why hasn't someone just built a "log onto windows domain properly" function in Linux, which gives you:

- joins computer to domain
- makes domain groups members of local groups
- allows domain logins to terminal and gnome/kde sessions
- allows sso to windows/samba shares
- allows easy configuration of samba shares
- maintains network user profiles properly... so the desktop and documents are in the profile... however AD has set them up (local profiles, roaming profiles, folder redirection, network home folders etc)

i.e. - all the stuff that happens when you simply join a domain on a windows (or mac) client.

---

### Post by ajuntament on 2007-02-22
Hi, 
I have addet pam_smb.so on pam files but I still get the same error.

I have followeb this steps:
-install winbind, samba, krb5-user and libpam-krb5 (not seen kerberos included with winbind and in all the papers I have read they say to install kerberos)

Configure kerberos (krb5.conf):

```

[logging]
	default=FILE:/var/log/krb5.log

[libdefaults]
	ticket_lifetime = 24000
	clock_skew = 300	
	default_realm = domain

[realms]
	ajtarragona.es = {
		kdc = server.domain:88
		admin_server = server.domain
		default_domain = domain
	}

[domain_realm]
	.domain =domain
	domains = domain

```

Then:
```
$ sudo kinit administrator@DOMAIN, and works properly
```

Then I configure Samba, as I said in my pervious post.

Restart winbind and Samba

Join the computer to the domain:

```
$ sudo net ads join -U administrator@DOMAIN
```

And then make the following changes:

/etc/nsswitch.conf:

```

passwd:         compat winbind
group:          compat winbind
shadow:         compat

```

/etc/pam.d/common-account:
```

ccount	sufficient	pam_winbind.so pam_smb.so
account	required	pam_unix.so

```

/etc/pam.d/common-auth
```

auth 	sufficient	pam_winbind.so pam_smb.so
auth 	sufficient	pam_unix.so nullok_secure use_first_pass
auth	required	pam_deny.so 

```


/etc/pam.d/common-session:
```

session	required	pam_unix.so
session	required	pam_mkhomedir.so umask=0022 skel=/etc/skel

```

/etc/pam.d/common-password:
```

password   required   pam_unix.so nullok obscure min=4 max=50 md5

```

/etc/pam.d/sudo:
```

auth sufficient	pam_winbind.so
auth sufficient pam_unix.so use_first_pass
auth required	pam_deny.so

```

Finally I restart Ubuntu and it all works fine except the one thing that didn't worked before.
See attached image with the error on accessing the shared resource (in Catalan , sorry)
Thanks.

---

### Post by ajuntament on 2007-02-23
I forgot to comment that I get an error when trying to join to the domain. It is repeated many times, but at the end i get a message  saying that the computer has joined succesfully to the domain. In fact, the computer appears on the domain server.

This is the error that appears repeateadly:
```

[2007/02/23 14:33:13, 0] libads/kerberos.c:get_service_ticket(356)
  get_service_ticket: kerberos_kinit_password MY_UBUNTU$@DOMAIN@DOMAIN failed: Preauthentication failed
[2007/02/23 14:33:13, 0] libads/kerberos.c:get_service_ticket(356)

```

And this is the final message:
```

Joined 'MY_UBUNTU' to realm 'DOMAIN'

```

Thanks.

---

