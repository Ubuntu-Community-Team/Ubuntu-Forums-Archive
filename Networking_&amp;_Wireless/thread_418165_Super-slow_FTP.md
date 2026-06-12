---
title: "Super-slow FTP"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Cene on 2007-04-22
Hi,

I installed proftpd and set the users etc up. Everything seems to be working fine, except that starting to transfer a file takes about 5 minutes per file.
I need to send over 6 gigabytes of data on lan from laptop to this Ubuntu computer. Most of them are images and small files. The laptop, with FileZilla, shows "Transferring" on files, but nothing actually happens. When the transfer actually begins, the speed is good.
I don't remember having this problem back in 5.10 and 6.06 days.

Here's my proftpd.conf:
```
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			300

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>
```

---

### Post by Jordanwb on 2007-05-04
Good I'm not the only one having this problem. Putty is also very slow as well.

---

### Post by tgpfarm on 2007-05-04
any transfer is slow for me
ftp:
windows to linux = slow
linux to windows = slow
samba:
windows to linux = slow
linux to windows = slow
http:
linux = slow

and slow is less than 200kB/s my server can download a torrent faster than me downloading from the server!

---

### Post by ariejan on 2007-06-01
Any cahnce you're using encrypted wireless connections? You should also check that you use the proper drivers for you network devices.

---

### Post by figjam on 2007-10-04
Seeing this issue as well.

I do not think the overhead of encryption will slow down the transfer down to the kilobyte range.

I can download a vmware image from a torrent (thoughtpolice) and achieve over 2000kb/s on downloads. On normal ftp on the same network it is painfully slow typically only about 146kb/s

So it does not seem to be the wireless' fault. Or is it? 

A hardwire connection is very very fast.

---

### Post by deep75 on 2007-11-22
Same problem for me with Ubuntu Gutsy, wireless connection and WPA on rt73 chipset with Ubuntu rt2x00 bundeled driver and about 150kb/sec :cry:

---

### Post by deep75 on 2007-11-24
Switch to rt73 legacy driver, ftp speed 2.5 MB/sec now

---

### Post by Jordanwb on 2008-04-04
Sorry about reviving a dead topic but I have some useful input. When I reinstalled Server on my little computer I installed only proftpd but not gproftpd and I haven't had any problems.

---

