---
title: "Joining Windows Domain"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2008-06-02
I am trying to join a windows domain with domainjoin-cli
When I type this command```
 sudo domainjoin-cli join affordablerto.net brian
``` I get this error ```
Error: Manual configuration required [code 0x00080043]

The configuration stage 'open ports to DC' cannot be completed automatically.
Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please
update your firewall settings to ensure that the following ports are open to
'affordablerto.net':
    88  UDP
    137 UDP
    389 UDP
    464 UDP
    123 UDP
    88 TCP
    139 TCP
    389 TCP
    445 TCP
    464 TCP

```

Is there something I need to do on the linux side or windows server side?

I do not have a firewall between me and the server (other than the stock IPTables).
Thanx in advance

---

### Post by lsutiger on 2008-06-13
Anybody?? Bueller? Bueller? Bueller?

---

### Post by lsutiger on 2008-06-20
Can't find any info online about this ( other than this post)

---

### Post by greenzrx on 2008-08-28
I'm having the same issue on ubuntu 8.04 64bit.

chris@ubuntu64:~$ sudo domainjoin-cli join olafe.com Administrator
Joining to AD Domain:   olafe.com
With Computer DNS Name: ubuntu64.olafe.com


Error: Manual configuration required [code 0x00080043]

The configuration stage 'open ports to DC' cannot be completed automatically. Please manually perform
the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please update your firewall
settings to ensure that the following ports are open to 'idc03.olafe.com':
    88  UDP
    137 UDP
    389 UDP
    464 UDP
    139 TCP

I've synced the date up to the AD Domain using ntpdate, and stil can't join the domain.  This is on a virtual machine.  Cloning it and running samba/winbind/kerberos i can join the ad domain though.

---

### Post by lsutiger on 2008-08-29
Ok, I did a little homework and ran a few tests with nmap.
On the server, reaching it by IP, all of the ports listed (UDP and TCP are open).
But if I go to the domain name, it only shows the ports open on the router.
Is there a way to join via the ip address with likewise-open?
I tried and got a few errors.
```
brian@brian-linux:~$ sudo domainjoin-cli join 192.168.1.15 brian@affordablerto.net
Joining to AD Domain:   192.168.1.15
With Computer DNS Name: brian-linux.192.168.1.15

brian@affordablerto.net's password: 
[2008/08/29 16:48:31,  0] utils/net_ads.c:ads_startup_int(493)
  ads_connect: No logon servers
Failed to contact DC when trying to synchronize local system clock!
None of the domain controllers listed in DNS could be contacted, or there are no DCs listed in DNS.

Error: Unable to join domain [code 0x0008000e]

Creating the computer account in Active Directory failed. Common causes are a bad administrator password, a bad OU name, or an existing computer account but not modificiation permissions.
brian@brian-linux:~$ 

```

---

### Post by abhi300 on 2008-09-02
Hi all, 

I tried this in joining ubuntu in a windows 2003 domain. here for you -


 Step 1. Installing

I assume that Ubuntu has been installed with no erros.

Make sure that following packages are installed, if not, install the following packages with the Synaptic Package Manager. You may need to specify “universe” as an extra source for packages.

    *      Samba (version 3):
          o samba
          o samba-common (installed by default)
          o smbclient (installed by default)
          o winbind
    *      Kerberos:
          o krb5-config
          o krb5-user

Step 2. Edit configuration files

Edit the following configuration files. I assume the following:

    * The local DNS domain is **example.com**
    * The Windows 2003 server is **server.example.com**

Open this file "/etc/samba/smb.conf" for editing either in GUI mode or by gedit.

You will need to edit this file to look like following -

[global]
security = **ADS**
realm = **EXAMPLE.COM**
workgroup = **example**
password server = **server.example.com**
wins support = no
wins server = 10.0.20.202
invalid users = root
# Winbind settings
idmap uid = 10000-20000
idmap gid = 10000-20000
# For testing
debuglevel = 2

# A shared folder for testing purposes
[SharedFolder]
path = /home/onno2/Shared_Folder
available = yes
public = yes
writable = yes
force create mode = 0666
force directory mode = 0777

Make sure the path (/home/onno2/Shared_Folder or whatever you choose) exists and that the rights are set properly (chmod 777 <mapnaam> or something similar)


Open this file "/etc/krb5conf" for editing to make it like this

[libdefaults]
 default_realm = **EXAMPLE.COM**
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
**EXAMPLE.COM** = {
        kdc = **SERVER.EXAMPLE.COM**
        admin_server = **SERVER.EXAMPLE.COM**
}
[domain_realm]
 .server.com = **SERVER.EXAMPLE.COM**
 server.com = **SERVER.EXAMPLE.COM**
[login]
 krb4_convert = true
 krb4_get_tickets = true

Now open "/etc/nsswitch.conf" for editing.

The only change we have to do here is to add winbind twice.

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.
passwd:         compat **winbind**
group:          compat **winbind**
shadow:         compat
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

Now when you have done with editing the files...take a breath. :)

Step 3. Start or restart services


/etc/init.d/samba restart
/etc/init.d/winbind restart

Step 4. Join domain

type in terminal - "net ads join -U administrator" without quotes. Needless to mention that you will need to give administrator password here :guitar:

If this doesn’t work, check the logs in Linux (/var/log/samba/*) and in Windows - Event Viewer.

Step 5. Test your setup

Type in terminal (without quotes)-

"testparm" to check if your smb.conf has a correct syntax.
"kinit" [email]onno@EXAMPLE.COM[/email] test if kerberos works properly.
"wbinfo -u" should give a list of users of domain.
"wbinfo -g" should give a list of groups of domain.
"getent passwd" should give a list of users in the passwd style.
"getent group" should give a list of groups.
"ls -ltr /var/log/samba" gives a list of log files, sorted by time of last change.
"smbclient -L <hostname> -U onno" should give you a list of available shares.

If this all works properly, try to access the share (/home/onno2/Shared_Folder) from any Windows machine in the domain by using network neighborhood /My Network Places.

I am sorry for being so long but it worked seamlessly.

/Abhishek

---

### Post by likeWiseGuy on 2008-09-25
> **lsutiger said:**
> Ok, I did a little homework and ran a few tests with nmap.
On the server, reaching it by IP, all of the ports listed (UDP and TCP are open).
But if I go to the domain name, it only shows the ports open on the router.
Is there a way to join via the ip address with likewise-open?
I tried and got a few errors.
```
brian@brian-linux:~$ sudo domainjoin-cli join 192.168.1.15 brian@affordablerto.net
Joining to AD Domain:   192.168.1.15
With Computer DNS Name: brian-linux.192.168.1.15

brian@affordablerto.net's password: 
[2008/08/29 16:48:31,  0] utils/net_ads.c:ads_startup_int(493)
  ads_connect: No logon servers
Failed to contact DC when trying to synchronize local system clock!
None of the domain controllers listed in DNS could be contacted, or there are no DCs listed in DNS.

Error: Unable to join domain [code 0x0008000e]

Creating the computer account in Active Directory failed. Common causes are a bad administrator password, a bad OU name, or an existing computer account but not modificiation permissions.
brian@brian-linux:~$ 

```

Hi Brian,

There are a few things you can do here to join your Ubuntu system to the Windows 2003 domain.

**1.** To test TCP ports, you can try this: telnet <domain controller fqdn> <port #>. For example, telnet dc1.affordablerto.net 88. If you don't get a connection refused, then you'll know that that port is blocked. If you got a connection refused, it indicates that you got through but no telnet service is running on that port (so it's a good thing). You can do the same for the rest of the TCP ports.

**2.** When you join a domain, you must use a domain account that has sufficient privileges to join computers to the domain. If you're not sure, check with your sysadmin to see if your "brian" account has sufficient rights. All you need for rights is to be able to create computer objects in the computers container. 

**3.** Your initial attempt had proper usage of the domainjoin-cli tool: sudo domainjoin-cli join <domain fqdn> <domain account w/ join privileges>

**4.** If you continue to have issues doing a join and want to investigate yourself, try: sudo domainjoin-cli --loglevel verbose --log /tmp/domainjoin.log join <domain fqdn> <domain account w/ join privileges>. This will log to /tmp/domainjoin.log and hopefully give you enough information to tell you what is going on.

Let me know if you need more information and I'll see how I can assist you.

Thanks.

---

### Post by lsutiger on 2008-09-25
WOW! Thanx for the informative post! Wil do when in the office Monday.

---

### Post by theDaveTheRave on 2008-09-26
Hi all,

I get the impression I am trying to do something similar!

I have an Ubuntu install (Hardy) that I want to join into my works domain.

I can ping all the various machines, with a good response, I can see the router / server (using pathping on windows terminal and route -r on the ubuntu laptop).

I can happily use the internet via the ethernet interface, and connect to the printers / scanners etc.

I'm going to have to sort this out onto my laptop etc, because eventually I'm going to be setting up local MySQL server and will need this functionality for everyone to connect to the system and for packup purposes.

I planto run through the above help things to see what happens, most likely I'll do this Monday next week.

I'll post back on my success (or otherwise!).

Dave

---

### Post by kblood on 2008-11-25
Hello, I am having the same issue mentioned here.

Here is the situation:

I have installed an Ubuntu 8.04 server, and added likewise-open-gui.

This server is placed in the DMZ area of our network, so its access to the internal network is severely restricted. So I have to open only the required ports, and nothing more.

I was happy to see that likewise-open gives me a list of ports, but it is definitely incomplete.

When I open all the ports in that list on our firewall to the domain controllers, joining the domain fails, and I see the error message:
ads_connect: No logon servers

When I open ALL possible ports to the domain controllers, joining the domain succeeds.

I have run the verbose log, but I can't see anything on it that can give a clue.

Side note: when the computer joins the domain, the DNS servers don't get updated. I can't resolve the name from other computers in the network. Windows clients don't have this problem: when they join the domain, I can resolve their names from other computers in the network.

Help is needed!! Thanks!!

---

