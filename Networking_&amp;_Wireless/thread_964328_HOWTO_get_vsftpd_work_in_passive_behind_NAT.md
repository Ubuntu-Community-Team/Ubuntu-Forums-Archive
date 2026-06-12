---
title: "HOWTO: get vsftpd work in passive behind NAT"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by ais77 on 2008-10-30
Brilliant secure vsftp server has a pity: 
while it runs behind a NAT in dynamic IP environment it gives to clients wrong IP-address for passive connections. 
Instead of real external IP (i.e. 215.23.67.12) it sends out NAT-ted internal one (i.e. 192.168.1.2) for pasv_address value (500 PORT command illegal). Even advanced pasv_addr_resolve option needs vsftpd restart at the moment when external IP changes - but there is no watchers to catch this moment.
These two scripts are designed to correct this issue and get vsftpd's passive connections work in dynamic IP environment behind the NAT.

Place this script in the file named **vsftpd.ip** in /usr/sbin/
```
#!/bin/sh
# Script is dedicated for setting real (external) IP-address in pasv_address=
# parameter in vsftpd.conf.
# It's neccessary for running vsftp in dynamic DNS environment
# behind NAT in passive mode. It checks external IP every 5 minutes, then sleeps.
# Wriiten by: ais77 (http://forum.ubuntu.ru)


# Configure these settings:
CONFIG_FILE=/etc/vsftpd.conf    # Location of vsftpd.conf
CONFIG_FILE_TMP=/etc/vsftpd.conf.tmp   # Location of temporary file
DOMAIN=ais77.homeftp.net   # Your external domain (i.e. from DynDNS.com)
LOG_FILE=~/vsftpd.ip.log

touch $CONFIG_FILE_TMP
touch $LOG_FILE

while :
do
realIP=`dig $DOMAIN +short`
vsftpdIP=`sed -n "/pasv_address=/s/pasv_address=//p" $CONFIG_FILE`
  if [ $realIP != $vsftpdIP ]; then
     sed "s/$vsftpdIP/$realIP/" $CONFIG_FILE > $CONFIG_FILE_TMP
     mv -f $CONFIG_FILE_TMP $CONFIG_FILE
     /etc/init.d/vsftpd restart
     echo "["`date`"] IP changed: from "$vsftpdIP" to "$realIP >> $LOG_FILE
  fi
  sleep 5m
done

exit 0

```

Make shure to set your data for DOMAIN= 
and get this file executable:
```
~$ sudo chmod +x /usr/sbin/vsftpd.ip
```


Second one will be a daemon run wrapper (if you want to your vsftpd.ip run as daemon at startup)
Place this one in file named **ipftp** in etc/init.d/
```
#!/bin/sh
# /etc/init.d/ipft
# vsftpd.ip daemon script
# Written by ais77 <http://forum.ubuntu.ru>

set -e

DAEMON=/usr/sbin/vsftpd.ip
NAME=ipftp
PIDFILE=/var/run/vsftpd/vsftpd.ip.pid

# Exit if vsftpd.ip is already running
test -x $DAEMON || exit 0
. /lib/lsb/init-functions

case "$1" in
  start)
    log_begin_msg "Starting vsftpd.ip daemon: $NAME"
    [ -d /var/run/vsftpd ] || mkdir -p /var/run/vsftpd
    start-stop-daemon --start --background -m --pidfile $PIDFILE --exec $DAEMON && log_end_msg 0 || log_end_msg 1
    ;;
  stop)
    log_begin_msg "Stopping vsftpd.ip daemon: $NAME"
    start-stop-daemon --stop --pidfile $PIDFILE --oknodo && log_end_msg 0 || log_end_msg 1
    rm -f $PIDFILE
    ;;
  restart)
    $0 stop
    $0 start
    ;;
  *)
    log_success_msg "Usage: /etc/init.d/$NAME {start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```
Also make shure to set this file executable:
```
~$ sudo chmod +x /etc/init.d/ipftp
```

To start daemon execute:
```
~$ sudo /etc/init.d/ipftp start
```

To set vsftpd.ip daemon run at startup automatically:
```
~$ sudo update-rc.d ipftp defauts
```

Enjoy. ;)

---

### Post by runes on 2009-04-27
The easist way without having to run a script:

sudo nano /etc/vsftpd

pasv_min_port=(enter a free available tcp port)
pasv_max_port=(enter a free available tcp port)

remember you are opening a range of ports so try not to add too many ie:

pasv_min_port=2005
pasv_max_port=2010

this basically says you are going to use port 2005-2010 for passive mode (5 ports)

You will then have to redirect those ports to your server ip address in your router or firewall.

Currently passive mode is not fully documented in vsftpd man pages so after some thorough digging around on the net I tried a few options and this was the easiest, cleanest way I could muster.

---

### Post by ais77 on 2009-04-27
> **runes said:**
> The easist way without having to run a script:
sudo nano /etc/vsftpd


It seems thet you have slightly messed up with the "passive" strings in vsftpd.conf.. ;)
The main dance was about "pasv_address" - wich could be set only once there by your "sudo nano /etc/vsftpd". 

Then if your ISP dynamically changes your external IP (dynamic one) you couldn't even access yor FTP server from outside. Therefore vsftpd will work for outside only in static IP environment - regardless is passive_port range set or not.

Please read trough the very first paragraph of the HOWTO a bit carefully :)

Anyway - tnx for your reply)

---

### Post by runes on 2010-02-15
> **ais77 said:**
> It seems thet you have slightly messed up with the "passive" strings in vsftpd.conf.. ;)
The main dance was about "pasv_address" - wich could be set only once there by your "sudo nano /etc/vsftpd". 

Then if your ISP dynamically changes your external IP (dynamic one) you couldn't even access yor FTP server from outside. Therefore vsftpd will work for outside only in static IP environment - regardless is passive_port range set or not.

Please read trough the very first paragraph of the HOWTO a bit carefully :)

Anyway - tnx for your reply)

OOPS--sorry!  
I tried your script in Ubuntu 9.10 64 bit...unfortunately it failed :-(

I first tried to modify your script to work but it was a bit overwhelming for a first attempt, so I had to cheat with sample scripts online until mine worked.  

But I was wondering

Would you be able to help me modify this script?
I f yes then I am trying to get the script to first create a backup of the vsftpd.conf file before updating it and how to get the script to check every 15 minutes if there is a change in the outside ip?

If no would you be willing to modify your existing script to work with Ubuntu 9.10?
 
 #!/bin/bash
 sed -e '64,$D' /etc/vsftpd.conf > /etc/vsftpd.mod
 echo pasv_address=`dig +short **mydomain.com**`>>/etc/vsftpd.mod
 mv /etc/vsftpd.mod /etc/vsftpd.conf


Thanx either way!

Runes

---

### Post by ais77 on 2010-02-15
> **runes said:**
> OOPS--sorry!  
I tried your script in Ubuntu 9.10 64 bit...unfortunately it failed :-(
...
I f yes then I am trying to get the script to first create a backup of the vsftpd.conf file before updating it and how to get the script to check every 15 minutes if there is a change in the outside ip?


What failed? Please be a bit specific..

1. Try add before ```
mv -f $CONFIG_FILE_TMP $CONFIG_FILE

```
something like
```
cp $CONFIG_FILE whateveryouwant.backup
```
2. Change ```
sleep 5m
```
to ```
sleep 15m
```

BTW, I wonder if scrip you've pasted works - without restarting of vsftpd?

---

### Post by runes on 2010-02-17
I'll retry your original script tomorrow and post the results!  I will also change the ip in the vsftpd.conf manually, restart vsftpd and then run the script I posted, then try ftp to it to see if we do not need to restart vsftpd. Once done I will also post the results of it then add your changes to the script I posted and test again!  Now that I have a tld registered and have to redirect while running off of a dymanic IP I can see the necessity of this workaround!


BTW I really appreciate the help you are providing!

---

### Post by runes on 2010-02-21
Testing it now

---

### Post by runes on 2010-02-21
Here's the results so far:

In the vsftpd script I put in a fake ip  

pasv_address=222.222.222.222

then follwed you steps below, copying the script to avoid typos.

Result is vsftpd updated on first run, however, I received this error

> @Hosting:/etc# sudo update-rc.d ipftp defauts
update-rc.d: warning: /etc/init.d/ipftp missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl]  [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
        -n: not really
        -f: force
  
The disable|enable API is not stable and might change in the future.
[I]
after typing in 

[/I]~$ sudo update-rc.d ipftp defauts

---

### Post by ais77 on 2010-02-21
It's not an error - just the warning: I skipped all unnecessary system-wide descriptions in the beginnig of ipftp.
If you like - you can copy such from any automatically installed script in /etc/init.d and modify this copypaste accordingly to ipftp purpose.

---

### Post by apamix on 2010-05-04
Hello 2 all i get an error on the 26 line  :confused:

/usr/sbin/vsftpd.ip: line 26: [: too many arguments
and my 26 line is 
  if [ $realIP != $vsftpdIP ! ];then
Anybody have a idea why ?

---

### Post by ais77 on 2010-05-06
I've dicieded to answer here instead of private message to you.

It's strange one... I've never experinced it.
Could you paste output of separate commands executed (just copypaste them to console) from vsftpd.ip?

---

### Post by Celoxocis on 2010-10-12
nice script, exactly what i have been looking for! :)  just setup everything and started it! its works just fine here lucid 10.04 :)

---

### Post by rsjaffe on 2011-07-03
Here's a simpler solution. A script that checks that IP against the one currently in vsftpd.conf and updates it if necessary. It'll email root when the ip address changes with two lines--one with the new ip address and one confirming that vsftpd has restarted. Edit dyn_name to match your site's name.

This is based on the script by [http://boeniger.net/home/index.php?option=com_content&task=view&id=17&Itemid=9]("http://boeniger.net/home/index.php?option=com_content&task=view&id=17&Itemid=9").
```

#!/bin/bash
vsftpd_conf=/etc/vsftpd.conf
dyn_name=yoursites.namehere.com

my_ip=$(host $dyn_name | cut -d" " -f4)

vsftpd_ip=$(grep pasv_address $vsftpd_conf | cut -f2 -d=)

if [ "$my_ip" != "$vsftpd_ip" ] ; then
   ( echo ",s/$vsftpd_ip/$my_ip/g" && echo w ) | ed - $vsftpd_conf
   echo New ip $my_ip
   /sbin/restart vsftpd
fi

```
Put this script in /usr/local/bin and make executable. 
Add this to cron (assuming you've named it ftpipupdate.sh) as

*/5 * * * * /usr/local/bin/ftpipupdate.sh

---

### Post by mcgyver83 on 2013-02-05
Sorry to resume this old thread but is very very useful for my system.
I have a raspberry pi with Raspbian OS and I have a vsftpd running.
The script proposed here is fantastic when there is a passive ftp but I have a problem. On Raspbian I don't have "host" command, I can use ping mydns-host -c 1 but here the ****: my ISP, Vodafone, gave me a router (Vodafone station) with the ping disabled and blocked.
A work-around?

Found: as wrote here: [passive vsftpd passive]("http://ubuntuforums.org/showpost.php?p=7570765&postcount=2") there is a property to configure vsftpd to use a domain name and it works fine!

---

### Post by wildmanne39 on 2013-02-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

