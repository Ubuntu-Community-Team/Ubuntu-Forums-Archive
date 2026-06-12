---
title: "Apcupsd monitoring multiple Network UPS help!"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by solo23 on 2008-01-23
I have over 50 APC UPS on my local network and I installed Apcupsd because I read it allows for multiple SNMP UPS monitoring. 

I was able to configure Apcupsd to monitor 1 using the apcupsd.conf and gapcmon; but in the manual it states that I have to use multimon.config to monitor more than 1 and that I have to set up a web server to see the out put.

Can same one please help me I've been at it for over a week and I can't seem to find all the answers over google! 

PS 
I'm a NeewB

---

### Post by solo23 on 2008-01-24
I was able to install apache2 using this How to;
[http://ubuntuforums.org/showthread.php?t=508332&highlight=apache2+setup](http://ubuntuforums.org/showthread.php?t=508332&highlight=apache2+setup)

I can see 1 local ups by configuring the apcupsd.conf file  but not the remote ups on the hosts.conf. What I'm trying to do now is monitor 49 more ups with out installing the apcupsd in the severs hooked up to the APC Smart-UPS since they are all network ups.

Do I have to run multiple copies of apcupsd to achive my goal?

---

### Post by tgalati4 on 2008-01-24
What specifically are you trying to achieve?  If you run apcupsd on each machine that has a cable plugged into it then each machine will shut down on it's own.  In the /var/log of each machine is an apcupsd.events and status file.  You could write a script to simply query each machine, grab it's status file and grep the needed info.

I use ruptime (sudo apt-get install rwhod)  as a helpful tool to see the load on each machine and if any machine has gone down.

I modified a script that I found on the forums to display these remote uptimes on my status bar.

-------------------------------------------

#!/bin/bash
function uptim {
export RUPT=`ruptime`
    zenity --text "$RUPT" --notification
uptim
}
uptim

# Line-by line explanation:
# 1 - Set the shell to be used (if using Dapper, change this line to 
#!/bin/sh )
# 2 - define a function and call it "uptim" (without "e" so as not to 
not confuse
# things too much)
# 3 - Read the output of the 'uptime' command.
# 4 - Use Zenity to create a status icon (click to refresh!)
# 5 - Have the funtion call itself to keep the status icon in the tray.
# 6 - The accolade marks the end of the function.
# 7 - This line gets the script running. Doesn't work without it.

---------------------------------------------------------------------

There is also gapcmon which is a graphical apcupsd monitor and you can set up multiple machines to query.  It does the same thing, query the status of each machine running apcupsd.  I don't know of a way to query the UPS's by themselves without using apcupsd for each UPS to generate those event/status files.  The daemon was really not designed for multiple UPS.  There are some programming guides out there, perhaps you can write a simple query script that talks to each UPS directly and grabs the info that you need.

---

### Post by solo23 on 2008-01-24
tgalati4 Thanx for the reply. 
After looking at what I wrote I can see it makes no sense.


My network mostly runs switches so I can't load Apcupsd to them, but they do have ups witch I need to have up to date status of.

Basically I would like to run multiple instances of Apcupsd in Ubuntu 7.10 to monitor all my ups from one computer. I have a few servers on the network but I don't want to load Apcupsd to them (there running Win2k3).

This is were I'm currently stuck, I can't figure out how to run multiple instances of Apcupsd in Ubuntu. This is what I was trying to copy in my /etc/init.d/apcupsd 


case "$1" in
    start)
       rm -f /etc/apcupsd/powerfail
       rm -f /etc/nologin
       for conf in /etc/apcupsd/apcupsd.*.conf ; do
          inst=`basename $conf`
          echo -n "Starting UPS monitoring ($inst):"
          daemon /sbin/apcupsd -f $conf -P /var/run/apcupsd-$inst.pid
          RETVAL=$?
          echo
          [ $RETVAL -eq 0 ] && touch /var/lock/subsys/apcupsd-$inst
       done
       ;;
    stop)
       for conf in /etc/apcupsd/apcupsd.*.conf ; do
          inst=`basename $conf`
          echo -n "Shutting down UPS monitoring ($inst):"
          killproc -p /var/run/apcupsd-$inst.pid apcupsd
          echo
          rm -f /var/run/apcupsd-$inst.pid
          rm -f /var/lock/subsys/apcupsd-$inst
       done
       ;;
    restart|force-reload)
       $0 stop
       sleep 15
       $0 start
       ;;
    reload)
       echo "$0: reload not implemented"
       exit 3
       ;;
    status)
       for conf in /etc/apcupsd/apcupsd.*.conf ; do
          inst=`basename $conf`
          status -p /var/run/apcupsd-$inst.pid apcupsd-$inst
          RETVAL=$?
          if [ $RETVAL -eq 0 ]
          then
             NISPORT=`grep ^NISPORT < $conf | sed -e "s/NISPORT 
*\([0-9]\)/\1/"`
             /sbin/apcaccess status localhost:$NISPORT | egrep 
"(STATUS)|(UPSNAME)"
          fi
       done
       ;;
    *)
       echo "Usage: $0 {start|stop|restart|status}"
       exit 1
       ;;
esac
exit 0

taken from 
 [http://www.kroptech.com/mailimport/showmsg.php?msg_id=3120658615&db_name=apcupsd-users](http://www.kroptech.com/mailimport/showmsg.php?msg_id=3120658615&db_name=apcupsd-users)

Again I'm not very good in linux but I'm trying.

---

### Post by tgalati4 on 2008-01-25
The command you posted only starts or stops the daemon, as in:
```
sudo /etc/init.d/apcupsd restart
```

A better approach would be to get a list of smart ups commands and write a script to pulse each UPS and retrieve the status.  I assume that these are ethernet-style UPS's each with their own unique, static IP.

A google search may turn up some appropriate snippets of code.  Again, apcupsd was designed to be run on one computer and capture the status of one UPS.  That UPS could be a locally-connected through a special serial cable or through the net via ethernet.

You could do something really spastic:  Create 50 configuration files each one with the static IP of an UPS then write a script that runs apcupsd with each configuration file each hour.  After 50 hours you will have complete status for all UPS.

Pseudo script would look like:
```

#!/bin/sh
# Super cheesy UPS monitoring script that only a monkey could come up with
apcupsd -f UPS_1.conf
sleep 3600
(capture /var/log/apcupsd.events and status and put somewhere useful)
apcupsd -f UPS_2.conf
sleep 3600
(capture data from UPS2)
apcupsd -f UPS_3.conf
.
.
.
.

```

There's got to be a better way.  Search the SUSE/Red Hat/IBM Linux forums for clues on multi-UPS monitoring.

Another super cheesy way to monitor them is to ping them in order.  No response means it's probably down.  Run the script once a day and you have a punch list for that day.

---

### Post by solo23 on 2008-01-25
Thanx again tgalati4

I was able to get Apcupsd to monitor multiple static ip netword ups by doing the folling;

set up acpupsd.conf under /etc/apcupsd with the address of the desired ups, but save it to something like apcupsd.ups1.conf. Right know I'm doing it with apcupsd.ups0.conf, apcupsd.ups1.conf, apcupsd.ups2.conf

Also you have to set up the NISPORT diferently in every one. I have 3551, 3552, 3553

Next set up hosts.conf under /etc/apcupsd to MONITOR 127.0.0.1:[COLOR="Magenta"]*[/COLOR] "[COLOR="Red"]@[/COLOR]"  

were * is the NISPORT of the specific ups and @ is the name of the ups you want to see in the multimon.cgi

from in terminal goto  /etc/apcupsd then type
sudo /sbin/apcupsd -f apcupsd.ups0.conf
sudo /sbin/apcupsd -f apcupsd.ups1.conf
sudo /sbin/apcupsd -f apcupsd.ups3.conf 

this will monitor the multiple ups from 1 system. I'm still working on how to set up the logs.

Would this be the proper format of a script to make my life easier?

#!/bin/sh
# Start UPS multi-monitor
sudo /sbin/apcupsd -f apcupsd.ups0.conf
sudo /sbin/apcupsd -f apcupsd.ups1.conf
sudo /sbin/apcupsd -f apcupsd.ups3.conf

---

### Post by tgalati4 on 2008-01-30
Add super cheesy to the comments, but otherwise that is what I was thinking.  The only issue I see is that you will have 50 simultaneous instances of apcupsd running (each with a different config file).  Not sure what the load on the machine would be.  Try running htop.  (sudo apt-get install htop)

If this is the only thing running on the machine, then it should work fine.  If you are relying on the machine to do other server functions, then having 50 instances of a program means that one memory leak will blow up pretty quickly.  Of course testing will tell.

---

### Post by solo23 on 2008-02-12
I was able to setup Apcupsd to monitor a total of 45 network enable ups, for those out there that are trying the same;

Configure all your "apcupsd.ups.conf", under the logs entry in this file chang the name so you have a log file for every ups. 

Also you have to make individual action script for every ups, I made a sub folder in /etc/apcupsd/*** for every ups. I also modify the script to send me an e-mail using sendEmail, now I can even e-mail it to my sprint phone as a text.

the most important thing to do is set up individual loopback address for every ups, so when the program pulls the ups they won't get a lost communication message.

---

