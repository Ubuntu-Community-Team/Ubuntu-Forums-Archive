---
title: "Setting up Internet using Dataone ADSL +USB Drivers"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by coder.com on 2008-08-19
Hello Friends
 I have BSNL Dataone connection. I have installed rp-pppoe-3.10 with lot of struggle. It's been installed successfully. 

Then when i say : root@phb:~# pppoe-status
it says : Note: You have enabled demand-connection; pppoe-status may be inaccurate.
pppoe-status: Link is down (can't read pppoe PID file /var/run/pppoe.conf-pppoe.pid.pppoe) 

==========>  root@phb:~# pppoe-setup <============

But What Should be values instead of([COLOR="DarkOrchid"]????[/COLOR])

Enter your PPPoE user name (default xxxxxx1234) ([COLOR="DarkOrchid"]????[/COLOR])

Enter the Ethernet interface connected to the DSL modem
For Solaris, this is likely to be something like /dev/hme0.
For Linux, it will be ethn, where 'n' is a number.

(default eth0): eth1 ([COLOR="DarkOrchid"]????[/COLOR])

Do you want the link to come up on demand, or stay up continuously?
If you want it to come up on demand, enter the idle time in seconds
after which the link should be dropped.  If you want the link to
stay up permanently, enter 'no' (two letters, lower-case.)
NOTE: Demand-activated links do not interact well with dynamic IP
addresses.  You may have some problems with demand-activated links.
>>> Enter the demand value (default 10): no ([COLOR="DarkOrchid"]????[/COLOR])

Please enter the IP address of your ISP's primary DNS server.
If your ISP claims that 'the server will provide DNS addresses',
enter 'server' (all lower-case) here.
If you just press enter, I will assume you know what you are
doing and not modify your DNS setup.
>>> Enter the DNS information here: server ([COLOR="DarkOrchid"]????[/COLOR])

Please enter your PPPoE password: ([COLOR="DarkOrchid"]????[/COLOR])   
>>>

Please choose the firewall rules to use.  Note that these rules are
very basic.  You are strongly encouraged to use a more sophisticated
firewall setup; however, these will provide basic security.  If you
are running any servers on your machine, you must choose 'NONE' and
set up firewalling yourself.  Otherwise, the firewall rules will deny
access to all standard servers like Web, e-mail, ftp, etc.  If you
are using SSH, the rules will block outgoing SSH connections which
allocate a privileged source port.

The firewall choices are:
0 - NONE: This script will not set any firewall rules.  You are responsible
          for ensuring the security of your machine.  You are STRONGLY
          recommended to use some kind of firewall rules.
1 - STANDALONE: Appropriate for a basic stand-alone web-surfing workstation
2 - MASQUERADE: Appropriate for a machine acting as an Internet gateway
                for a LAN
>>> Choose a type of firewall (0-2): 1 ([COLOR="DarkOrchid"]????[/COLOR])

Summary of what you entered **

Ethernet Interface: eth1
User name:          xxxxxx1234
Activate-on-demand: No
Primary DNS:        server
Firewalling:        STANDALONE

>>> Accept these settings and adjust configuration files (y/n)? y
Adjusting /etc/ppp/pppoe.conf
Adjusting /etc/resolv.conf
Adjusting /etc/ppp/pap-secrets and /etc/ppp/chap-secrets
  (But first backing it up to /etc/ppp/pap-secrets-bak)
Congratulations, it should be all set up

====>THEN AFTER THAT WHEN I SAY <====
root@phb:~# pppoe-start
................TIMED OUT
Please Help me :(
**[COLOR="Magenta"]What should be vaules in the place of(????)[/COLOR]**

=================================================================

In XP we install USB driver by inserting setup cd in cd rom n everything happens Automatically............ Ok
However do i need to install any USB driver in UBUNTU ???
I am attaching my USB-Driver folder for your reference.


Thanks n Regards
Coder.com

---

### Post by coder.com on 2008-08-19
I have done it.. however I can't browse any website......... What has to be network configuration when I am connecting through an USB port [BSNL Line -> ADSL Modem -> USB Post].

---

