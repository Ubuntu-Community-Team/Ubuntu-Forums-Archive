---
title: "network settings change on boot"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by piusvelte on 2007-10-20
Good afternoon,

I'm running into a problem, on xubuntu 7.04, where my network settings change every time the machine reboots. It just started a few days ago, since I started setting up apache2 and mysql. Apache has been serving out pages fine, but I couldn't download packages using synaptic, or browse out to any sites, like google or digg.

I checked the network settings and the dns server and search domain are wrong. There are 2 dns servers listed, each starting 66..., and the search domain is something like hd1.state.comcast... I reset them and could get back online and install updates, but whenever I reboot, those incorrect settings come back. Where are they coming from? Is there perhaps something wrong with my apache configuration that is cause this? I'm getting more comfortable with linux, but this is over my head.

Any help is, of course, extremely appreciated!

---

### Post by Jermski on 2007-10-20
By "reset them" do you mean changing to DHCP?

---

### Post by Hero of Time on 2007-10-20
What is your current network setup? That your dns servers and search domain change, could be because of your ISP. Have you tried a whois query on the ip addresses? I'm almost sure that they would direct to Comcast. What is the IP address you get upon boot and what do you use after you fixed it?

---

### Post by piusvelte on 2007-10-20
***UPDATE***

Apache is not the problem, at least I don't think so. I forgot that I installed mysql after apache, so everything was fine. The last thing that I installed and attempted to configure is proftp. That is likely the problem.

***

Thank you for the responses!

My network is setup so that all of the machines use dhcp and my router assigns static ips using the mac addresses.

I'm curious about the comcast domain search entry as my isp is verizon.

I'll have to reboot and get the exact ips and the domain.

I don't recall having set any records initially, and I'll check my other xubuntu machines to confirm, but I just entered my router as the dns server, and my network domain name as the domain search, and everything seems fine, at least until the next reboot.

I'll look in the proftp configuration and post it here.

---

### Post by piusvelte on 2007-10-20
I originally tried the configuration from here:
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/5](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/5)

But apparently there are known issues with it and this is the substitute, which isn't working for me:
[http://forums.bit-tech.net/showpost.php?p=1492124&postcount=95](http://forums.bit-tech.net/showpost.php?p=1492124&postcount=95)

The port isn't forwarded for ftp right now, but that shouldn't be a problem.

proftpd.conf:

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"Lin01"
Serverident                     on "FTP"
ServerType			standalone
DefaultAddress                  Lin01
DeferWelcome			on
TimesGMT                        off


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

AllowForeignAddress             on
AllowRetrieveRestart            on

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
SocketBindTight                 on

PassivePorts                    11000 20000


# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

AllowForeignAddress             on
AllowRetrieveRestart            on
AllowStoreRestart on

# Speed up the server, no DNS lookups, just plain ip's. Turn off when being hax0r3d.
UseReverseDNS off
IdentLookups off

DefaultRoot                     ~
ExtendedLog                     /var/log/proftpd.all ALL


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
DelayEngine 			off

#<Anonymous ~ftp>
#  User                          ftp
#  Group                         nogroup
#  UserAlias                     anonymous ftp
#  DirFakeUser                   on ftp
#  DirFakeGroup                  on ftp
#  RequireValidShell             off
#  MaxClients                    10
#  DisplayLogin                  welcome.msg
#  DisplayFirstChdir             .message
#  AccessGrantMsg                "Anonymous access granted for user %u connecting."

#  MaxClientsPerHost             1

#  <Directory>
#    #DenyAll
#    TransferRate        RETR 50
#    <Limit WRITE>
#      DenyAll
#    </Limit>
#  </Directory>

---

### Post by piusvelte on 2007-10-21
Somehow between last night and now, the network settings changed again. I didn't reboot or even use the machine. I reset them to my router and domain and everything is fine again. Suspecting proftp, I restarted proftp to see if the settings would change but they didn't. So now I'm not so sure about proftp being the problem.

Here are the ips that are replacing the dns servers:
68.87.64.146
68.87.75.194

The domain search is:
hsd1.state.comcast.net

As guessed, both ips belong to comcast, though my isp is verizon. What now? Is there something in the logs that I should look for as far as changing the network settings? I use the gui to edit the network settings, however, what files are actually holding them? I know that /etc/hosts is involved.

Thanks!

---

