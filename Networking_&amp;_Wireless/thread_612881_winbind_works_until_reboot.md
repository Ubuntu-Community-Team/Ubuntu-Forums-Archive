---
title: "winbind works until reboot"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by OsGnuru on 2007-11-14
I am running winbind login on about six systems running Debian Sarge, it works great. I want to change to Ubuntu but so far I am having nothing but problems. I put my config files below so you can see what I have done.

I tried with Feisty and Gutsy. Feisty is totally broken with all sorts of unexplainable Gnome and KDE startup failures. Gutsy works much better but not as good as Debian Sarge does. Gutsy only works until you reboot then it will not work any more. Server logs do not even report an attempt from the user to login. GDM only reports “No Logon Servers” and when I set my Samba server to be the log server for Gutsy I see the SMB error NT_STATUS_NO_LOGON_SERVERS. No Samba messages show up on the server. It is as if Gutsy just does not actually start Samba.

I have PKI setup so I can SSH into the Gutsy system as root with the default nsswitch and pam files. I then modify the nsswitch and pam files to the ones shown below then I restart samba and winbind. I can then login from the GDM with an account on the domain. My home directory gets mounted and I am in. When I click the logout button in the top right of the screen it takes about 5 minutes before the logout control panel shows up. Open programs still work okay but the Gnome menu becomes un-responsive. When the logout control panel finally shows up I can click logout or restart and the home directory is automatically unmounted, unless evolution crap is left running, I need to find a way to kill it at logout time. Other then the very long delay this seems to work well. I don't know if the delay is related to the problem or not.

I reboot Gutsy, at boot time I set vga=6 so I can watch the services start, normally the screen is black when the system boots until it gets to GDM. Both samba and winbind start without any errors. When GDM starts up I can no longer login with domain accounts or the default user account that I put on the system. I also cannot login with SSH and PKI to the root account. The only thing I can do is boot with a live CD, restore the default nsswitch and pam files, reboot and then I am back to local accounts only.

I would very much like to get my pam config files setup so that local or domain accounts can login. To SSH in as root would be very helpful but my pam files are only allowing domain accounts and ignoring local accounts even for SSH logins. I must admit that I do not understand fully what each part of the pam config files is doing and have not had much luck with the documentation. I took most of the pam configs from examples of what others are using and tried to hack them together. I need the pam config files to do two things, authenticate users that login either from TTY or GDM and to authenticate users attempting to access network shares. I do not think that my pam files are the problem because as I stated before, they work great from Debian Sarge.

------- auth.log from Gutsy after reboot
Nov 14 09:00:01 desktopserver CRON[336]: (pam_unix) session opened for user smmsp by (uid=0)
Nov 14 09:00:01 desktopserver CRON[336]: (pam_unix) session closed for user smmsp
Nov 14 09:04:18 desktopserver sshd[647]: Accepted publickey for root from ::ffff:127.0.0.1 port 54456 ssh2
Nov 14 09:04:36 192.168.0.120 login[5371]: pam_winbind(login:auth): pam_get_item returned a password
Nov 14 09:04:36 192.168.0.120 login[5371]: pam_winbind(login:auth): request failed: No logon servers, PAM error was Authentication service cannot retrieve authentication info (9), NT error was NT_STATUS_NO_LOGON_SERVERS
Nov 14 09:04:36 192.168.0.120 login[5371]: pam_winbind(login:auth): internal module error (retval = 9, user = 'dex')
Nov 14 09:04:38 192.168.0.120 login[5371]: FAILED LOGIN (1) on 'tty2' FOR `UNKNOWN', Authentication failure
------- auth.log from Gutsy after reboot--

So I boot with a live CD, reset the sytem to defaults, reboot, ssh in, re-modify the pam and nsswitch config files, restart samba and winbind and I can login with domain accounts again.
------- auth.log from Gutsy after fix again
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=dex
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_winbind(gdm:auth): getting password (0x00000010)
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_winbind(gdm:auth): pam_get_item returned a password
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_winbind(gdm:auth): user 'dex' granted access
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_winbind(gdm:account): user 'dex' OK
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_winbind(gdm:account): user 'dex' granted access
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_unix(gdm:session): session opened for user dex by (uid=0)
Nov 14 09:33:31 192.168.0.120 gdm[5915]: pam_mount(mount.c:177) realpath of volume "/home/RADADOSGROUP/dex" is "/home/RADADOSGROUP/dex"
Nov 14 09:33:31 desktopserver smbd[2783]: (pam_unix) session opened for user dex by (uid=0)
------- auth.log from Gutsy after fix again--


This is something I am confused about, passwd and group have compat then winbind, shouldn't the system try to authenticate against local accounts first then use winbind if the account is not found. I also tried “files winbind” because I found a post that said compat was broken but that did not help.
------- /etc/nsswitch.conf
passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
------- /etc/nsswitch.conf--

------- /etc/samba/smb.conf
[global]
  # Network
  workgroup = RADADOSGROUP
  server string = %h
  security = domain
  password server = *

  # Stop virtual NIC's like Qemu and VmPlayer from fighting over domain control
  interfaces = eth0

  # Printing
  load printers = no

  # Logging
  log file = /var/log/samba/log.%m
  log level = 1
  max log size = 100

  # Winbind
  winbind uid = 10000-20000
  winbind gid = 10000-20000
  obey pam restrictions = yes
  winbind separator = +
  template shell = /bin/bash
  winbind enum users = yes
  winbind enum groups = yes
  winbind use default domain = yes

[public]
   comment = Public upload
   path = /home/samba/public
   public = yes
   printable = no
   write list = @netadmins
------- /etc/samba/smb.conf--

------- /etc/security/pam_mount.conf
... # This is the last line of the file and the only one that deals with volume.
volume * smbfs SERVER & /home/RADADOSGROUP/& uid=&,gid=users,dmask=0700,fmask=600 - -
------- /etc/security/pam_mount.conf--

------- /etc/pam.d/common-account
account required pam_winbind.so
------- /etc/pam.d/common-account--

------- /etc/pam.d/common-auth
auth required pam_mount.so
auth sufficient pam_unix.so use_first_pass nullok_secure
auth required pam_group.so use_first_pass
auth sufficient pam_winbind.so use_first_pass
auth required pam_deny.so
------- /etc/pam.d/common-auth--

------- /etc/pam.d/common-session
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
session required        pam_unix.so
session optional        pam_foreground.so
session optional pam_mount.so
------- /etc/pam.d/common-session--

------- /etc/pam.d/common-pammount
auth       optional   pam_mount.so use_first_pass
session    optional   pam_mount.so use_first_pass
------- /etc/pam.d/common-pammount--

---

### Post by OsGnuru on 2007-11-14
This could be a problem with SysV init script timing. I think winbind is starting up at boot time when there is no network yet. I exported the root (/) file system with NFS and set it up so I could mount the Gutsy after boot and look at the system when winbind is failing.

I booted with the winbind doamin files and tried to login. Again as before "No Logon Servers" so I mounted the system and looked at the logs.

I found in log.winbind that it is reporting no netowrk interfaces and that it cannot receive trustdoms

It looks like there is no network when winbind starts and when the network does start winbind is not getting reloaded.


[2007/11/14 11:24:49, 1] nsswitch/winbindd.c:main(990)
  winbindd version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2007/11/14 11:24:49, 0] lib/interface.c:load_interfaces(229)
  WARNING: no network interfaces found
[2007/11/14 11:24:49, 0] lib/interface.c:load_interfaces(229)
  WARNING: no network interfaces found
[2007/11/14 11:24:49, 0] nsswitch/winbindd_cache.c:initialize_winbindd_cache(2222)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2007/11/14 11:24:50, 1] nsswitch/winbindd_util.c:trustdom_recv(235)
  Could not receive trustdoms
[2007/11/14 11:29:50, 1] nsswitch/winbindd_util.c:trustdom_recv(235)
  Could not receive trustdoms

---

### Post by OsGnuru on 2007-11-14
Solved!!!

Winbind was being stated before the network was up. I added a script /etc/network/if-up.d/winbind that would cat /etc/init.d/winbind restart when the network did finaly start and it works great now.

And not the logout control panel pops-up fast like it should.

I had to write a hack for /etc/gdm/PostSession/Default to force the killing of evolution and other running processes. These programs would keep running after the user loged out and prevent the unmounting of home directories.

I also added a change to /etc/security/groups.conf so domain users would have local rights to audio so that the sound would work on the desktop.

I built a package for this to work on my own distribution but it also works with Gutsy. It is here [http://radados.org/deb/installer_cd/dists/prospector/main/binary-i386/network/](http://radados.org/deb/installer_cd/dists/prospector/main/binary-i386/network/)

---

### Post by bobpaul on 2008-02-07
Same problem with winbind starting before network on Gutsy. I was able to fix it by modifying my /etc/networking/interfaces file. I had:

```
auto eth0
#iface eth0 inet dhcp
```

I simply uncommented the second line. I'm still not sure why the installer would leave that line commented, or how networking even worked with that line gone, but my /etc/init.d/network script no longer gives errors, and this allows winbind to start with the network fully up.

---

### Post by megamaced on 2008-07-02
> **OsGnuru said:**
> 
Winbind was being stated before the network was up. I added a script /etc/network/if-up.d/winbind that would cat /etc/init.d/winbind restart when the network did finaly start and it works great now.

I've got the same issue with winbind. Can you share the script you created please! :)

---

### Post by bobpaul on 2008-07-08
> **megamaced said:**
> I've got the same issue with winbind. Can you share the script you created please! :)

Based on his post, it sounds like he has

```

#!/bin/sh

/etc/init.d/winbind restart

```

Save as /etc/network/if-up.d/winbind and mark as executable (chmod 755). Any executable file in the if-up.d will be run whenever the network is brought back up.

---

