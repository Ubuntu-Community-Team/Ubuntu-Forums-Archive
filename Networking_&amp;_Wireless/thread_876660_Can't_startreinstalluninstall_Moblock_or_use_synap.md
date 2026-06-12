---
title: "Can't start/reinstall/uninstall Moblock or use synaptic"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by 3eyedsamurai on 2008-08-01
Very new to linux. Ubuntu 8 64bit. I tried jre's posted suggestions but nothing has worked. I appreciate your help. I want to be able to use synaptic and fix moblock.

I have tried many options but here is just a few samples.

```
xxxx@xx-ubuntu:~$ sudo apt-get remove moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnetfilter-queue1 libnfnetlink0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  moblock
0 upgraded, 0 newly installed, 1 to remove and 36 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
xxxx@xx-ubuntu:~$ sudo apt-get remove moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnetfilter-queue1 libnfnetlink0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  moblock
0 upgraded, 0 newly installed, 1 to remove and 36 not upgraded.
1 not fully installed or removed.
After this operation, 279kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing moblock (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)
xxxx@xx-ubuntu:~$ aptitude purge moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
xxxx@xx-ubuntu:~$ sudo aptitude purge moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libnetfilter-queue1 libnfnetlink0 
The following packages have been automatically kept back:
  kdebase-bin kdebase-bin-kde3 kdebase-kio-plugins kdesktop libkonq4 
The following packages have been kept back:
  deskbar-applet eog gcalctool gnome-about gnome-cards-data gnome-desktop-data gnome-games gnome-games-data 
  gnome-panel gnome-panel-data gnome-system-monitor gtk2-engines gvfs gvfs-backends gvfs-fuse hal libglib2.0-0 
  libglib2.0-dev libglibmm-2.4-1c2a libgnome-desktop-2 libgtksourceview2.0-0 libgtksourceview2.0-common 
  libgvfscommon0 libhal-storage1 libhal1 libpanel-applet2-0 libsmbios1 libwnck-common libwnck22 procps ufw 
The following packages will be REMOVED:
  moblock{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 422kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing moblock (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

```


```
Stopping MoBlock
#[109G[#[31mfail#[39;49m]
2008-07-31 10:20:50 PM CDT End: moblock-control stop
2008-07-31 10:20:50 PM CDT Begin: moblock-control stop
Deleting iptablesiptables v1.3.8: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: Bad rule (does a matching rule exist in that chain?)
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 #[33m*#[39;49m Some iptables rules could not be deleted. The most common reason for this is
 #[33m*#[39;49m that they did not exist. If MoBlock was not running this is the correct
 #[33m*#[39;49m behaviour. But if MoBlock was running there is some problem. Make sure that
 #[33m*#[39;49m MoBlock inserts its iptables rules correctly and that other software, e.g.
 #[33m*#[39;49m firewall applications, don't delete them. Make sure that MoBlock is started
 #[33m*#[39;49m after other firewall applications.
Stopping MoBlock
#[109G[#[31mfail#[39;49m]
2008-07-31 10:20:50 PM CDT End: moblock-control stop
2008-07-31 10:20:50 PM CDT Begin: moblock-control start
Inserting iptablesiptables v1.3.8: host/network `192.168.1.0-192.168.1.254' not found
Try `iptables -h' or 'iptables --help' for more information.

#[109G[#[31mfail#[39;49m]
```


```
sudo moblock-control status
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 314K packets, 386M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 223K packets, 25M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain moblock_fw (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:443:65535 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is not running.
xxx@xx-ubuntu:~$
```

---

### Post by jre on 2008-08-01
Maybe its a problem with the LSB init functions in Hardy. What version of the LSB init functions do you have? Please post ```
dpkg -l lsb-base moblock
```
What does happen when you start MoBlock manually ```
/usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 -t -r 10 -a 20 /var/log/moblock.log
``` and then try to uninstall it? (The uninstall doesn't work because stopping the non-running moblock daemon fails, although this should not result in a "fail" normally. Note that the manual "start" command above is not enough to get a functional MoBlock - with other words it is enough for aptitude but not for you.)

Are there any **Ubuntu Hardy users** who run MoBlock successfully?

If this is not the reason we have to search others ;-)
Please post ```
sudo find /etc/ -name "moblock"
sudo moblock-control show_config
```

Greets
jre
> **3eyedsamurai said:**
> ```
Inserting iptablesiptables v1.3.8: host/network `192.168.1.0-192.168.1.254' not found
```
I doubt that this is the reason for your problems, but anyway: I guess you misconfigured moblock. You may only add such IP ranges to /etc/moblock/allow.p2p - but not to the variables WHITE_IP_... in /etc/moblock/moblock.conf or /etc/default/moblock.

---

### Post by 3eyedsamurai on 2008-08-01
I really appreciate the help. I have posted the responses that you asked for in the same order. 

moblock Version
```
$ dpkg -l lsb-base moblock

Desired=Unknown/Install/Remove/Purge/Hold

| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend

|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)

||/ Name           Version        Description

+++-==============-==============-============================================

ii  lsb-base       3.2-4ubuntu1   Linux Standard Base 3.2 init script function

iFR moblock        0.9~rc2-11~har An IP blocker for Linux


```

Manual Start
```
$ /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 -t -r 10 -a 20 /var/log/moblock.log

Unable to create pid_file


```

I tried removing it again...

```
sudo aptitude remove moblock

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information       

Initializing package states... Done

Building tag database... Done      

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


```

Add this way too...

```
$ /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 -t -r 10 -a 20 /var/log/moblock.log
Unable to create pid_file
xxxx@xx-ubuntu:~$ sudo aptitude remove moblock
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```


Additional Output as requested...
```
$ sudo find /etc/ -name "moblock"


/etc/moblock

/etc/logrotate.d/moblock

/etc/default/moblock

/etc/cron.daily/moblock

/etc/init.d/moblock


sudo moblock-control show_config

 * Usage: moblock-control {start|stop|restart|reload|update|status|test}


```

So far switching to Ubuntu has been very easy and the few issues have been enjoyable challenges. Guess I was getting bored with Windows. Just have to decide which UPnP server I want to use to send video to my XBOX 360.

---

### Post by jre on 2008-08-02
1.
You have to make sure that for the aptitude/synaptic/apt-get/dpkg operations no other of these processes is running. This is the reason why you get these messages:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

2.
For the manual start of the moblock daemon you need root privileges (I forgot that in my mail, sorry). So use:
```
**sudo** /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 -t -r 10 -a 20 /var/log/moblock.log
```
Please try to uninstall (aptitude purge moblock) again after issuing this command.

3.
You are using an outdated version of MoBlock which neither allows "sudo moblock-control show_config" nor has the "/etc/moblock/allow.p2p". So forget about those two hints. Of course I know that you can't update currently because of these problems.

4.
Again I posted an incomplete command, sorry. Please post
```
sudo find /etc/ -name "*moblock*" | sort
```
But still these 2 issues are not the reason for your problems.

5.
I had no look at the LSB init functions, yet. Will do that later ...

jre

---

### Post by 3eyedsamurai on 2008-08-02
Thanks for such quick replies. Sorry I didn't realize the #2 was an admin command and needed sudo and synaptic to be closed.

New Results:

#2 - output

```
sudo /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 -t -r 10 -a 20 /var/log/moblock.log
....new merge

new merge

new merge

* Ranges loaded: 316612

* Using .p2p file format

* Log timestamp enabled

* DROP MARK: 10

* ACCEPT MARK: 20

* Merged ranges: 3086

* Skipped useless ranges: 7446

NFNETLINK answers: Invalid argument

```

It just sat there, never brought me back to $... Then I realized that Synaptic open and that it was the process that you were talking about. So I closed Synaptic and then ran...

```
sudo /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 -t -r 10 -a 20 /var/log/moblock.log
pid file /var/run/moblock.pid exists. Not startingXXXX@XX-ubuntu:~$ sudo aptitude purge moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libnetfilter-queue1 libnfnetlink0 
The following packages will be REMOVED:
  moblock{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 422kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing moblock (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
XXXX@XX-ubuntu:~$ sudo find /etc/ -name "*moblock*" | sort
/etc/cron.daily/moblock
/etc/default/moblock
/etc/default/moblock~
/etc/init.d/moblock
/etc/logrotate.d/moblock
/etc/moblock
/etc/moblock/moblock.conf
/etc/rc0.d/K20moblock
/etc/rc1.d/K20moblock
/etc/rc2.d/S20moblock
/etc/rc3.d/S20moblock
/etc/rc4.d/S20moblock
/etc/rc5.d/S20moblock
/etc/rc6.d/K20moblock

```

This is all a straight copy paste so the formatting is coming from the terminal. Synaptic still has other updates, including one for moblock. But I haven't tried it since doing the above commands.

---

### Post by jre on 2008-08-03
> **3eyedsamurai said:**
> It just sat there, never brought me back to $...
This is the normal behavior, don't worry.

Unfortunately uninstalling didn't work. I'd like to figure out what went wrong but I'm short on time currently, so I'd suggest the following:
```
sudo killall moblock
sudo iptables -F
sudo iptables -X
sudo update-rc.d moblock remove
sudo rm -Rf /etc/init.d/moblock
sudo aptitude purge moblock
```
Step 1-3 aren't really necessary, they just stop any running moblock processes and clean up your iptables rules (in case you have additional firewall software running, you better should not do it.)
Step 4+5 remove the trouble causing init script, step 6 completely removes moblock.

In case this works please try to install the actual moblock version again.

In any case please report what happens.

---

### Post by 3eyedsamurai on 2008-08-03
Great Success! :)

I ran the scripts as you discribed but was prompted to force the 4th one...
```
sudo update-rc.d moblock remove
update-rc.d: /etc/init.d/moblock exists during rc.d purge (use -f to force)
xxx@xx-ubuntu:~$ sudo update-rc.d -f moblock remove 
 Removing any system startup links for /etc/init.d/moblock ...
   /etc/rc0.d/K20moblock
   /etc/rc1.d/K20moblock
   /etc/rc2.d/S20moblock
   /etc/rc3.d/S20moblock
   /etc/rc4.d/S20moblock
   /etc/rc5.d/S20moblock
   /etc/rc6.d/K20moblock

```

After the last step I was able to run all of my updates.

Current status...
```
sudo moblock-control status
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 208K packets, 163M bytes)
 pkts bytes target     prot opt in     out     source               destination         
   20  1386 moblock_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 moblock_fw  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain OUTPUT (policy ACCEPT 188K packets, 31M bytes)
 pkts bytes target     prot opt in     out     source               destination         
  101  6201 moblock_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 RETURN     all  --  *      *       192.168.1.0/24       192.168.1.0/24      
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
   13   780 RETURN     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    4   349 RETURN     all  --  *      *       192.168.1.0/24       0.0.0.0/0           
    3   257 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    3   120 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
   13   780 RETURN     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
   38  2541 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.0/24      
   20  1200 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
   24  1440 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    3   120 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 14215.

```

and its current config...
```
sudo moblock-control show_config
moblock-control current settings:
BLOCKLIST_FORMAT="p"
LOG_TIMESTAMP="1"
LOG_SYSLOG="0"
LOG_IPTABLES=""
VERBOSITY="1"
MOBLOCK_INIT="1"
MOBLOCK_CRON="1"
IPTABLES_MODULES="1"
IPTABLES_TARGET="NFQUEUE"
NFQUEUE_NUMBER="0"
IPTABLES_SETTINGS="1"
IPTABLES_ACTIVATION="1"
REJECT="1"
REJECT_MARK="10"
REJECT_IN="DROP"
REJECT_OUT="REJECT"
REJECT_FW="DROP"
ACCEPT="1"
ACCEPT_MARK="20"
IPTABLES_TARGET_WHITELISTING="RETURN"
WHITE_LOCAL="1"
WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT="80 443"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""
WHITE_IP_IN=""
WHITE_IP_OUT=""
WHITE_IP_FORWARD=""
IP_REMOVE=""
PATH="/sbin:/bin:/usr/sbin:/usr/bin"
NAME="moblock"
DAEMON="/usr/bin/moblock"
CONTROL_SCRIPT="/usr/bin/moblock-control"
CONF_DIR="/etc/moblock"
CONTROL_DEFAULT="/etc/default/moblock"
MASTER_BLOCKLIST_DIR="/etc/moblock"
BLOCKLISTS_DIR="/var/spool/moblock"
BLOCKLISTS_DIR_USED="/var/spool/moblock/used"
BLOCKLISTS_LIST="/etc/moblock/blocklists.list"
ALLOW_IN="/etc/moblock/allow.p2p"
ALLOW_OUT="/etc/moblock/allow.p2p"
ALLOW_FW="/etc/moblock/allow.p2p"
IPTABLES_CUSTOM_INSERT="/etc/moblock/iptables-custom-insert.sh"
IPTABLES_CUSTOM_DELETE="/etc/moblock/iptables-custom-remove.sh"
LOG_DIR="/var/log"
DAEMON_LOG="/var/log/moblock.log"
CONTROL_LOG="/var/log/moblock-control.log"
STATFILE="/var/log/MoBlock.stats"
PIDFILE="/var/run/moblock.pid"
LSB="/lib/lsb/init-functions"
TESTHOST="www.bluetack.co.uk"
LSB_MODE="0"

```

Later I will have to check its setup and make sure it is running the way I need it to but for now I am just happy that I have my updates installed.

Thanks so much JRE:KS. You really helped me out.

---

### Post by jre on 2008-08-03
Great!
I just wish I knew what went wrong the first time. By the time I think it was a configuration error. But since such user made errors should be caught by error messages and proper exit codes, I suppose that there is a bug in moblock-control :-/

Have fun
jre

---

