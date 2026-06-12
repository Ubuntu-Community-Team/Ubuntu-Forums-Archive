---
title: "how to make proftpd use hosts.allow/deny files?"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by r0ck80y on 2007-06-11
Just set up a proftpd server and its working fine. When i try to limit certain ips from accessing the server, things dont work the way i want. Heres my proftpd.conf file :
```

ServerName        "ProFTPD Server"
ServerType                      standalone
DefaultServer                   on
RequireValidShell               off
AuthPAM                         off
AuthPAMConfig                   ftp
# Port 21 is the standard FTP port.
Port                            21

# Do not perform ident nor DNS lookups (hangs when the port is filtered)
IdentLookups                    on
UseReverseDNS                   on

# User access settings
<Limit LOGIN>
        Order  Allow,Deny
        Allow  10.5., 10.1., 10.2.
        Deny   All
</Limit>

# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30. If you need to allow more than 30 concurrent connections
# at once, simply increase this value. Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit the maximum number of processes per service
# (such as xinetd).
MaxInstances            5

# Set the user and group under which the server will run.
User                            fender
Group                           fender

# Log format and location
LogFormat               default "%t %h %a %s %m %f %b %T \"%r"\"
ExtendedLog             /var/log/proftpd ALL default
SystemLog               /var/log/proftpd ALL default
TransferLog             /var/log/proftpd ALL default

#--------------------My Settings -------------------------------------------#
# grant login only for members of the group
<Limit LOGIN>
DenyGroup !fender !ftp
</Limit>

# alternatively u can write this to deny all users to access ftp. You can then
# enable user-specific settings and 'AllowALL' there.
#<Limit LOGIN>
#   DenyALL
#</Limit>

# Normally, we want files to be overwriteable.
<Directory />
        AllowOverwrite          on
</Directory>


#----------------Settings for 'fender' start here---------------------------#
# A basic anonymous configuration, with no upload directories.
<Anonymous /var/ftp>
User                            fender
Group                           fender
AnonRequirePassword             on

# Limit the maximum number of anonymous logins.
MaxClients      3 "The server is full, hosting %m users"

# We want clients to be able to login with "anonymous" as well as "ftp".
#UserAlias                      fender ftp

DefaultChdir                  /var/ftp

# We want 'welcome.msg' displayed at login, and '.message' displayed
# in each newly chdired directory.
DisplayLogin                    welcome.msg

<Limit ALL>
        Deny ALL
</Limit>

# Hide all files owned by user 'root'
#HideUser         root

# Disallow clients from any access to hidden files.
<Limit READ DIRS>
IgnoreHidden         on
</Limit>

# Allow clients to do the options listed with Limit (obtained from net and
# gproftpd conf file)
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
        AllowAll
</Limit>

# Deny clients to do the options as listed with Limit (obtained from net and
# gproftpd conf file)
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
        DenyAll
</Limit>

# Limit WRITE everywhere in the anonymous chroot.
<Limit WRITE>
        DenyAll
</Limit>

# Uploading permissions
# <Directory /var/ftp/upload_here>
#       Umask   022  022
#    <Limit MKD STOR STOU>
#          Allow   All
#    </Limit>
# </Directory>

</Anonymous>
#---------------Settings for 'fender' end here -----------------------------#
```

I want the server to use the settings in the hosts.allow and hosts.deny files to give access to ips. These settings are:
1) for /etc/hosts.allow
```


ALL: 10.1. 10.2. 10.3. 10.4. 10.5. 10.6. 10.7. 10.8. 10.9. 10.10. 10.11. 10.12. 10.13. 10.21. 10.22. 10.129.
```

2) for /etc/hosts.deny
```

ALL: ALL
```

Also the following section in proftpd.conf file:
```

# User access settings
<Limit LOGIN>
        Order  Allow,Deny
        Allow  10.5., 10.1., 10.2.
        Deny   All
</Limit>
```
actually disallows all ips from connecting. If i write 10.5.1.1 or 10.1.1.10 etc, only these ips get access. How can i enable proftpd to use the hosts.allow/deny files? Is there anything wrong with my config? A l'il help will be much appreciated.

---

