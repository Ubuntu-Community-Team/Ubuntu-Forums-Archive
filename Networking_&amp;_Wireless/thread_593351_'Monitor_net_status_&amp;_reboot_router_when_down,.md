---
title: "'Monitor net status &amp; reboot router when down, script' help needed"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by JoJoRaz on 2007-10-27
'm running a web server on a Mac G4 Powerbook Titanium(Tit), with Ubuntu Linux PPC server OS, so there's no GUI. The Tit is connected to the router via a network switch. I use an XP machine for everything else. The router has a dynamic IP setup where, on boot, it reports the new IP to the name server so the site domain is immediately recognised from the web (Dynamic DNS).
However, in this part of the world the internet connection is quite unreliable and goes down regularly, whether there's internet activity or not, and I should reboot the router with telnet or through the router web interface, but it's quicker to pull the plug. The router seems oblivious to the dropped connection as all the indicator lights remain illuminated.

I need a solution to (1) determine the connection status and, if necessary, (2) telnet the router with the user ID and password to perform a reboot.
I know I need to use 'Expect' and 'Tcl' but I'm having trouble installing/calling  Expect and I don't know how to determine if Tcl is even installed, and if necessary, install it where Expect will see it.

OBJECTIVES
Monitor connection //possibly ping remote server
IF no_connection
telnet 192.168.1.1
expect User_ID //User ID request from router
echo User_ID
expect Password //Password request from router
echo Password
expect Login_confirmation //not sure if this is necessary
reboot
expect reconnection notice //not sure if this is necessary
exit (telnet)
restart script //with a n-second delay
ELSE restart script //with a n-second delay

I don't want to keep the XP machine on continuously as it's quite power-hungry and we are on solar power, so it will have to be a script running on the Tit from startup or called by Apache.

Mac G4 Powerbook (Titanium)
Ubuntu 7.04 Feisty Server
Xavi X8821r+ Router (Viking)

Precise instructions if possible please, there seem to be far too many factors to any task in Linux.

Thanks in advance.

---

### Post by fishy6969 on 2007-11-07
I'm looking to do exactly the same thing!

Flaky internet connection? You're not on ADSL2 in London are you by chance? My connection is about as robust as the England Soccor team!

I've done some research and found a good script to monitor the internet connection at the following post-

[http://ubuntuforums.org/showthread.php?t=297025](http://ubuntuforums.org/showthread.php?t=297025)

the relevant script being (with thanks to the originator)

> #!/bin/sh

HOST=google.com            # host to spam ping
FAILLOG=fail_log.txt       # file to log failures to
TMPFILE=/tmp/conn_monitor  # temporary file
INTERVAL=30                # how often to ping, in seconds

append_log()
{
    OLDIFS=$IFS
    IFS=$
    for LINE in `cat -E $TMPFILE`; do
        LINE=`echo $LINE | tr -d "\n"`
        echo "    " $LINE >> $FAILLOG
    done
    IFS=$OLDIFS
}

while [ 1 ]; do
    ping -c 4 $HOST &> $TMPFILE
    if [ $? -eq 0 ]; then
        echo "PING SUCCESS at "`date`"."
    else
        echo "PING FAILURE at "`date`"."
        # we failed, so run a traceroute for diagnostic purposes
        traceroute $HOST 1>> $TMPFILE 2>&1
        echo "PING FAILURE at "`date`"." >> $FAILLOG
        append_log
    fi
    sleep $INTERVAL
done

It works well, though I've changed the interval variable to 300. I'm still trying to work out how to  send the "system reboot' message via telnet to the router. ?any suggestions anyone

---

### Post by fishy6969 on 2007-11-07
I've scrubbed up a script to reboot the modem -

> 

#!/bin/sh
USERNAME=routerusername
PASSWORD=routerpassword
ROUTERIP=routerip
ROUTERREBOOT=routerrebootcommand
  (
  sleep 5
    echo "$USERNAME\r"
    sleep 5
    echo "$PASSWORD\r"
    sleep 5
    echo "$ROUTERREBOOT\r"
    sleep 40
 ) | telnet $ROUTERIP 23



the final script would look something like -

> 
#!/bin/sh

HOST=google.com # host to spam ping
FAILLOG=fail_log.txt # file to log failures to
TMPFILE=/tmp/conn_monitor # temporary file
INTERVAL=30 # how often to ping, in seconds
USERNAME=routerusername
PASSWORD=routerpassword
ROUTERIP=routerip
ROUTERREBOOT=routerrebootcommand

append_log()
{
OLDIFS=$IFS
IFS=$
for LINE in `cat -E $TMPFILE`; do
LINE=`echo $LINE | tr -d "\n"`
echo " " $LINE >> $FAILLOG
done
IFS=$OLDIFS
}

while [ 1 ]; do
ping -c 4 $HOST &> $TMPFILE
if [ $? -eq 0 ]; then
echo "PING SUCCESS at "`date`"."
else
echo "PING FAILURE at "`date`"."
# we failed, so run a traceroute for diagnostic purposes
traceroute $HOST 1>> $TMPFILE 2>&1
echo "PING FAILURE at "`date`"." >> $FAILLOG
(
  sleep 5
    echo "$USERNAME\r"
    sleep 5
    echo "$PASSWORD\r"
    sleep 5
    echo "$ROUTERREBOOT\r"
    sleep 40
) | telnet $ROUTERIP 23
append_log
fi
sleep $INTERVAL
done


replace the appropriate variables at the start of the script to match your situation and "chmod +x" the script file.

Hope this helps (and works!)

---

### Post by JoJoRaz on 2007-11-08
Many thanks to **fishy6969** for the response.  I'm actually 7000 miles from, and 100 years behind, London in northern Thailand. The connection dropping wouldn't be such a problem if I wasn't running a web server.  I actually found a solution on the web using Expect & Tcl but, as is usually the case, the first step in the instructions was a dead end, therefore the rest was irrelevant.  I'll give this a whirl tonight.  Thanks again.

---

