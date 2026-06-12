---
title: "VPN auto-connect"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by TonyS on 2008-05-19
Gidday all,

I connect to my work network from my laptop using network-manager's pptp VPN plugin. It works great.

One small hassle I've been trying to solve for YEARS now is to find a way to make this connection automatically establish whenever an internet connection is working.

If the angels were really singing it'd also be possible to try a "sudo mount -a" automatically when the VPN comes up, to mount the LAN drives.

Even if it would just give it a try at boot time it'd be GREAT!:guitar:

Anyone solved this one? It seems to me that there might be a way of creating a couple of command line in System|Preference|Session to do the business...

Cheers,

Tony

---

### Post by Cabalbl4 on 2010-03-23
Well... if it is still useful I have figured a way to do this in Karmic.
But it is qite a pain.
1) Use seahorse to delete your default keyring password (null password.)
2) make folowing script on your HD. Credit goes here [http://forum.ubuntu.ru/index.php?topic=81009.msg608218#msg608218]("http://forum.ubuntu.ru/index.php?topic=81009.msg608218#msg608218")
and here
[http://forum.ubuntu-fr.org/viewtopic.php?pid=3170479#p3170479]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3170479#p3170479")
 ```
#!/bin/bash


    ############
    # SETTINGS #
    ############

get_connections_paths()
{
    dbus-send --system --print-reply --dest="$1" "/org/freedesktop/NetworkManagerSettings" "org.freedesktop.NetworkManagerSettings.ListConnections" \
    | grep "object path" | cut -d '"' -f2
}

get_connection_settings()
{
    dbus-send --system --print-reply --dest="$1" "$2" org.freedesktop.NetworkManagerSettings.Connection.GetSettings
}

get_connection_string_setting()
{
    echo "$1" | grep -A 1 \""$2"\" | grep variant | cut -d '"' -f2
}

get_connection_id()
{
    get_connection_string_setting "$1" "id"
}

get_connection_type()
{
    get_connection_string_setting "$1" "type"
}

get_device_type_by_connection_type()
{
    echo "$1" | grep -q "ethernet" && echo 1 && return
    echo "$1" | grep -q "wireless" && echo 2 && return
    echo 0
}

find_connection_path()
{
    for connection_path in `get_connections_paths "$1"`
    do
        connection_settings=`get_connection_settings "$1" "$connection_path"`
        connection_settings_id=`get_connection_id "$connection_settings"`
        [ "$connection_settings_id" = "$2" ] && echo "$1" "$connection_path"
    done
}

find_connection_path_everywhere()
{
    find_connection_path "org.freedesktop.NetworkManagerSystemSettings" "$1"
    find_connection_path "org.freedesktop.NetworkManagerUserSettings" "$1"
}

print_connections_ids()
{
    for connection_path in `get_connections_paths "$1"`
    do
        connection_settings=`get_connection_settings "$1" "$connection_path"`
        connection_settings_id=`get_connection_id "$connection_settings"`
        echo "$connection_settings_id"
    done
}

print_connections_ids_everywhere()
{
    print_connections_ids "org.freedesktop.NetworkManagerSystemSettings"
    print_connections_ids "org.freedesktop.NetworkManagerUserSettings"
}


    ###########
    # DEVICES #
    ###########

get_devices_paths()
{
    dbus-send --system --print-reply --dest="org.freedesktop.NetworkManager" "/org/freedesktop/NetworkManager" "org.freedesktop.NetworkManager.GetDevices" \
    | grep "object path" | cut -d '"' -f2
}

get_device_property()
{
    dbus-send --system --print-reply --dest="org.freedesktop.NetworkManager" "$1" "org.freedesktop.DBus.Properties.Get" string:"org.freedesktop.NetworkManager.Device" string:"$2" \
    | grep variant | awk '{print $3}'
}

get_device_type()
{
    get_device_property "$1" "DeviceType"
}

get_device_path_by_device_type()
{
    device_path_by_device_type="/"
    for device_path in `get_devices_paths`
    do
        device_type=`get_device_type "$device_path"`
        [ "$device_type" = "$1" ] && device_path_by_device_type="$device_path"
    done
    echo "$device_path_by_device_type"
}


    #######################
    # ACTIVES CONNECTIONS #
    #######################

get_actives_connections_paths()
{
    dbus-send --system --print-reply --dest="org.freedesktop.NetworkManager" "/org/freedesktop/NetworkManager" "org.freedesktop.DBus.Properties.Get" string:"org.freedesktop.NetworkManager" string:"ActiveConnections" \
    | grep "object path" | cut -d '"' -f2
}

get_last_active_connection_path()
{
    get_actives_connections_paths | tail -n 1
}

get_parent_connection_path_by_device_type()
{
    parent_connection_path="/"
    [ "$1" = 0 ] && parent_connection_path=`get_last_active_connection_path`
    echo "$parent_connection_path"
}

get_active_connection_property()
{
    dbus-send --system --print-reply --dest="org.freedesktop.NetworkManager" "$1" "org.freedesktop.DBus.Properties.Get" string:"org.freedesktop.NetworkManager.Connection.Active" string:"$2" \
    | grep variant | awk -F '"' '{print $2}'
}

get_active_connection_service()
{
    get_active_connection_property "$1" "ServiceName"
}

get_active_connection_path()
{
    get_active_connection_property "$1" "Connection"
}

get_active_connection_path_by_connection_path()
{
    for active_connection_path in `get_actives_connections_paths`
    do
        service=`get_active_connection_service $active_connection_path`
        path=`get_active_connection_path $active_connection_path`
        [ "$service" = "$1" ] && [ "$path" = "$2" ] && echo "$active_connection_path"
    done
}

print_actives_connections_ids()
{
    for active_connection_path in `get_actives_connections_paths`
    do
        service=`get_active_connection_service $active_connection_path`
        path=`get_active_connection_path $active_connection_path`
        connection_settings=`get_connection_settings "$service" "$path"`
        connection_settings_id=`get_connection_id "$connection_settings"`
        echo "$connection_settings_id"
    done
}


    ##############
    # START/STOP #
    ##############

start_connection()
{
    my_connection_complete_path=`find_connection_path_everywhere "$1"`
    my_connection_settings=`get_connection_settings $my_connection_complete_path`
    my_connection_type=`get_connection_type "$my_connection_settings"`
    my_connection_device_type=`get_device_type_by_connection_type "$my_connection_type"`
    
    my_connection_service=`echo $my_connection_complete_path | awk '{print $1}'`
    my_connection_path=`echo $my_connection_complete_path | awk '{print $2}'`
    my_connection_device_path=`get_device_path_by_device_type "$my_connection_device_type"`
    my_parent_connection_path=`get_parent_connection_path_by_device_type "$my_connection_device_type"`
    
    echo "connection_service=$my_connection_service"
    echo "connection_path=$my_connection_path"
    echo "connection_device_path=$my_connection_device_path"
    echo "parent_connection_path=$my_parent_connection_path"
    
    dbus-send --system --print-reply --dest="org.freedesktop.NetworkManager" /org/freedesktop/NetworkManager "org.freedesktop.NetworkManager.ActivateConnection" string:"$my_connection_service" objpath:"$my_connection_path" objpath:"$my_connection_device_path" objpath:"$my_parent_connection_path"
}

stop_connection()
{
    my_connection_complete_path=`find_connection_path_everywhere "$1"`
    my_active_connection_path=`get_active_connection_path_by_connection_path $my_connection_complete_path`
    
    echo "active_connection_path=$my_active_connection_path"
    
    dbus-send --system --print-reply --dest="org.freedesktop.NetworkManager" /org/freedesktop/NetworkManager "org.freedesktop.NetworkManager.DeactivateConnection" objpath:"$my_active_connection_path"
}


    ########
    # MAIN #
    ########

invalid_arguments()
{
    echo "Usage: `basename "$0"` connexion_name start|stop"
    echo "---Available Connections:"
    print_connections_ids_everywhere
    echo "---Active Connections:"
    print_actives_connections_ids
    exit 0
}

[ "$#" != 2 ] && invalid_arguments

case "$2" in
    "start")
        start_connection "$1"
        ;;
    "stop")
        stop_connection "$1"
        ;;
    *)
        invalid_arguments
        ;;
esac
```

name this script nmcli

After that, make it executable as a command
```
sudo cp nmcli /usr/local/bin/
sudo chmod ugo+x /usr/local/bin/nmcli
```

3) create a script in your home folder
```

#!/bin/bash
sleep 25
nmcli VPNNAME start

```
(do not forget to make it executable by using chmod 777)
where VPNNAME is the name of your connection
sleep time is needed for all interfaces to self-configure before vpn starts. For example, I get VPN error if sleep is less than 15.
4) Add this script to system->settings->sessions preferences->startup programs.
5)Enjoy it on reboot^^
6) BTW You can add "sudo mount -a" in the end of script at step 3. (Not forgetting to add some more sleep time before command).

NOTE: This works on my system with autologin. Without autologin, some steps may need to be changed.

---

### Post by Cabalbl4 on 2010-04-05
Yay!!! I have figured a way to autoconnect it!!! :guitar:

My dear ISP sometimes resets the connection, and it is not nice when I am not at home.

But now I can check the connection for availability and, if needed, start it.
To do this, just follow my previous post until step 3, and, when at step 3, use the following script instead of given one (or, You may use them both, as the previous one is executed only once):
```

#!/bin/bash

for (( ; ; )); do

# creating ifinite loop

tested=$(nmcli|grep -c VPNNAME)
# VPNNAME here is the name of desired vpn connection to monitor. The results can be:
# 0 - this connection does not exist
# 1 - connection exists, but not active
# 2 - connection exists, and is active
case $tested in
"0")
echo "something is wrong, cannot find desired connection in avaliable list"
;;
"1")
echo "VPN avaliable, but not connected" 
nmcli VPNNAME start
;;
"2")
echo "VPN seems to work" 
;;
esac
# enter desired time between checks here.
sleep 30 
done

```
This script auto-checks VPN availability using nmcli from previous post, in a constant period of time. 

do not forget to make it executable and add it to autorun ):P

Works fine for me ^^

PS. However, this script requires a constant connection to lan, and it can only monitor the VPN connection status. It cannot do much good if the lan interface is down.

---

### Post by red_lego_man on 2010-08-20
Fantastic!  Just what I was looking for.  I had tried using "pon" and "poff" with pptp-linux, but I could get a stable connection to the VPN, whilst the NetworkManager connection was very stable.  Now I can schedule when the VPN is up or down.  Don't forget to set the DISPLAY variable if you want to run from cron.

---

### Post by outdooralex on 2010-09-10
wow... awesome! Just what I was looking for soooo much. Now let's see if a Noob like me can get it to work...

thanks a lot!

---

### Post by ptipton on 2010-09-30
Am struggling to get this to work when I try and manually start my connection from the command line I get the following:

paul@IBM-Frontend:~$ nmcli VPNUK start
bash: /usr/local/bin/nmcli: /bin/bash^M: bad interpreter: No such file or directory

Any help much appreciated.

---

### Post by red_lego_man on 2010-09-30
> **ptipton said:**
> Am struggling to get this to work when I try and manually start my connection from the command line I get the following:

paul@IBM-Frontend:~$ nmcli VPNUK start
bash: /usr/local/bin/nmcli: /bin/bash^M: bad interpreter: No such file or directory

Any help much appreciated.

Looks like you're editing the file in Windows.  You have carriage return character in there (^M).  You need to remove all the ^M characters from your script.

---

### Post by ptipton on 2010-09-30
> **red_lego_man said:**
> Looks like you're editing the file in Windows.  You have carriage return character in there (^M).  You need to remove all the ^M characters from your script.

Worked a treat. Thanks!!

---

### Post by MattiJ on 2010-10-02
Thanks! I had to mod it to get it working in Ubuntu 10.10 Maverick Meerkat.

Seems to wor for me now.

```
#!/bin/bash
VPNNAME=VPN1
# for ((;;)); do
while true; do

# creating ifinite loop

tested=$(nmcli con status|grep -c $VPNNAME)

date
case $tested in
"0")
echo "not connected, försöker ansluta"
nmcli con up id "VPN1"
;;
"1")
echo "VPN seems to work" 
#nmcli $VPNNAME start
;;
"2") # newer get here
echo "VPN seems to work" 
;;
esac
# enter desired time between checks here.
sleep 30

done
```

---

### Post by sonicb00m on 2010-10-03
Excellent stuff! Very good.

The 2nd reconnection script doesnt work in Meerkat but the original one does.

---

### Post by sreeslinux on 2010-10-29
Lovely little prog that does it all for you.
[http://sourceforge.net/projects/vpnautoconnect/](http://sourceforge.net/projects/vpnautoconnect/)

---

### Post by recluce on 2011-07-12
On my Xubuntu 11.04 installation, the script by MattiJ worked, but I replaced all explicit VPN names by the reference to $VPNNAME. In order to use the script below, you need to:

1.) Save it to a file, we use vpnon.sh as an example

2.) Replace <insert VPN name here> with the actual name of your VPN as listed under VPN in "Network Connections"

3.) Make it executable: 
```

sudo chmod +x vpnon.sh

```

4.) Test it from the shell with: 
```

./vpnon.sh

```

If all works, you can add it to startup applications/scripts.

Here is the modified script:

```

#!/bin/bash
VPNNAME=<insert VPN name here>
# for ((;;)); do
while true; do

# creating ifinite loop

tested=$(nmcli con status|grep -c $VPNNAME)

date
case $tested in
"0")
echo "not connected"
nmcli con up id $VPNNAME
;;
"1")
echo "VPN seems to work" 
#nmcli $VPNNAME start
;;
"2") # newer get here
echo "VPN seems to work" 
;;
esac
# enter desired time between checks here.
sleep 30

done

```

To stop it, use:
```

killall vpnon.sh

```

---

### Post by Cabalbl4 on 2011-11-13
Well, it seems I have figured out why my main script does not work sometimes. It has an error when your LAN connection has the same name as VPN. nmcli reports this name twice and the script does wrong things._ Only in THIS specific case_ the script by MattiJ works fine. Correct me if I am wrong.

---

### Post by Cabalbl4 on 2012-07-14
By the way, in ubuntu 12.04 nmcli comes out of the box, so there is no need to copy anything. **_Do not use the nmcli from my first post, as it is not working in 12.04! (at least 64 bit) _**. If you copy it the original nmcli will be overwritten - you will need to reinstall network-manager. 
So, utilizing its functions in kubuntu 12.04, I am now using this autocnnect script (working with out-of the box nmcli):
```

#!/bin/bash

# YourVPN here is the name of desired vpn connection to monitor
# edit this line:
##################
VPNNAME=YourVPN
# enter desired time between checks here (in seconds)
SLEEPTIME=30
##################



nice=0

for (( ; ; )); do

# creating ifinite loop

tested=$(nmcli con status id $VPNNAME | grep -c UUID)
#possible results:
# 0 - no connection - need to start
# 1 - working connection, continue.

case $tested in
"0")
echo "Not connected - starting"

#increase nice counter
nice=$[nice+1]

#if "nice start" fails for 3 times
if [ $nice -ge 3 ];
then
#TRY to knock hard way, resetting the network-manager (sometimes it happens in my kubuntu 12.04).
      echo "HARD RESTART!"
      nmcli nm enable false
      nmcli nm enable true
      sleep 5
      nmcli con up id $VPNNAME
      nice=0
else
#not yet 3 falures - try starting normal way
      echo "trying to enable."
      nmcli con up id $VPNNAME
fi


;;

"1")
echo "VPN seems to work" 

;;
esac

sleep $SLEEPTIME

done


```
The setup is same as here: [http://ubuntuforums.org/showpost.php?p=11041626&postcount=12](http://ubuntuforums.org/showpost.php?p=11041626&postcount=12)
The main difference with the script from recluce post is the ability to hard-reset network manager - sometimes usual way of starting VPN fails for some reason (many network cards maybe?).

And again, VPN connection name in network manager must differ from other connection names, or this script will work incorrectly.

---

### Post by Cabalbl4 on 2012-10-28
Another version of my script - now with ping check. It will ping 2 given sites and try to reconnect if both of them are unreachable. Usual connection check is still there.

This script mod is needed, because there is sometimes a kind of failure of my ISP, when the connection is up but all VPN packets are lost. In this case, the connection must be reset according to ping results. 

```

#!/bin/bash

##################
# VPNNAME here is the name of desired vpn connection to monitor
# edit this line:
VPNNAME=UltranetVPN
##################
# Other options:
# enter desired time between checks here (in seconds)

SLEEPTIME=5

# 2 sites to ping for connection 

SITEA=www.fsf.org
SITEB=www.google.com

##################



nice=0

for (( ; ; )); do

# creating ifinite loop

tested=$(nmcli con status id $VPNNAME | grep -c UUID)
#possible results:
# 0 - no connection - need to start
# 1 - working connection, continue.

case $tested in
"0")
echo "Not connected - starting"

#increase nice counter
nice=$[nice+1]

#if "nice start" fails for 3 times
if [ $nice -ge 3 ];
then
#TRY to knock hard way, resetting the network-manager (sometimes it happens in my kubuntu 12.04).
      echo "HARD RESTART!"
      nmcli nm enable false
      nmcli nm enable true
      sleep 5
      nmcli con up id $VPNNAME
      nice=0
else
#not yet 3 falures - try starting normal way
      echo "trying to enable."
      nmcli con up id $VPNNAME
fi


;;

"1")
echo "VPN seems to work" 

;;
esac

echo "Begin ping check"
#begin ping checks
testpinga=$( ping $SITEA -c 3 | grep -c "100% packet loss" )
testpingb=$( ping $SITEB -c 3 | grep -c "100% packet loss" )
testping=$(($testpinga+$testpingb))

if [ $testping -ge 2 ];
then
#all packets lost - reset connection!
      echo "PING RESTART!"
      nmcli con down id $VPNNAME
      sleep 5
      nmcli con up id $VPNNAME
fi




sleep $SLEEPTIME




done

```

---

### Post by Cabalbl4 on 2012-11-23
Update: a small tweak in script for not to stall in pings. Added ping timeout time, after which script will give up on pinging a site. Adjust pingtime if needed, it should be increased for slow connections, as the script will tend to reconnect them.  
```

#!/bin/bash

# VPNNAME here is the name of desired vpn connection to monitor
# edit this line:
##################
VPNNAME=UltranetVPN
# enter desired time between checks here (in seconds)
SLEEPTIME=5
# ping wait time - wait for connection to answer for this ammount of seconds before consider it dead for specific site
PINGWAIT=5
#sites to ping for coonection
SITEA=www.yandex.ru
SITEB=www.google.com
##################



nice=0

for (( ; ; )); do

# creating ifinite loop

tested=$(nmcli con status id $VPNNAME | grep -c UUID)
#possible results:
# 0 - no connection - need to start
# 1 - working connection, continue.

case $tested in
"0")
echo "Not connected - starting"

#increase nice counter
nice=$[nice+1]

#if "nice start" fails for 3 times
if [ $nice -ge 3 ];
then
#TRY to knock hard way, resetting the network-manager (sometimes it happens in my kubuntu 12.04).
      echo "HARD RESTART!"
      nmcli nm enable false
      nmcli nm enable true
      sleep 5
      nmcli con up id $VPNNAME
      nice=0
else
#not yet 3 falures - try starting normal way
      echo "trying to enable."
      nmcli con up id $VPNNAME
fi


;;

"1")
echo "VPN seems to work" 

;;
esac

echo "Begin ping check"
#begin ping checks
testpinga=$( ping $SITEA -c 3 -w $PINGWAIT | grep -c "100% packet loss" )
testpingb=$( ping $SITEB -c 3 -w $PINGWAIT | grep -c "100% packet loss" )
testping=$(($testpinga+$testpingb))

if [ $testping -ge 2 ];
then
#all packets lost - reset connection!
      echo "PING RESTART!"
      nmcli con down id $VPNNAME
      sleep 5
      nmcli con up id $VPNNAME
fi




sleep $SLEEPTIME




done

```

---

### Post by dadox on 2013-02-19
Hi Cabalbl4, your script is working greatly on my machine where I have the GUI network manager installed.

Now, I would like to use it on a second machine without GUI. 
I would have to export my vpn settings from my first machine, but the network manager has a bug in the export function. Do you know where does the network manager stores this settings so I could find it on my first machine and deploy it on my second headless machine? Thanks

---

### Post by Cabalbl4 on 2013-02-23
> **dadox said:**
> Hi Cabalbl4, your script is working greatly on my machine where I have the GUI network manager installed.

Now, I would like to use it on a second machine without GUI. 
I would have to export my vpn settings from my first machine, but the network manager has a bug in the export function. Do you know where does the network manager stores this settings so I could find it on my first machine and deploy it on my second headless machine? Thanks

try files in /etc/NetworkManager/system-connections

---

### Post by Cabalbl4 on 2013-02-23
New, improved version of script. It is far more responsive, as the ping check is now async. To ensure that there is only one ping check running, shared memory (/dev/shm) is used.

```
#!/bin/bash

# VPNNAME here is the name of desired vpn connection to monitor
# edit this line:
##################
VPNNAME=UltranetVPN
# enter desired time between checks here (in seconds)
SLEEPTIME=15
# ping wait time - wait for connection to answer for this ammount of seconds before concider it dead for specific site
PINGWAIT=5
#sites to ping for coonection
SITEA=www.yandex.ru
SITEB=www.google.com
##################

#init shared memory varible
echo 0 >/dev/shm/vpnAsyncVal


async_run() {
{

testedp=$(</dev/shm/vpnAsyncVal)

if [ $testedp -eq 1 ];
then
echo "ping check already in progress"
return 1
fi

echo 1 >/dev/shm/vpnAsyncVal
echo "Begin ping check"
#begin ping checks
testpinga=$( ping $SITEA -c 3 -w $PINGWAIT | grep -c "100% packet loss" )
testpingb=$( ping $SITEB -c 3 -w $PINGWAIT | grep -c "100% packet loss" )
echo "ping 1 done"
testpingc=$( ping $SITEA -c 3 -w $PINGWAIT | grep -c "unknown host" )
testpingd=$( ping $SITEB -c 3 -w $PINGWAIT | grep -c "unknown host" )
echo "ping 2 done"
testping=$(($testpinga+$testpingb+$testpingc+$testpingd))

if [ $testping -ge 2 ];
then
#all packets lost - reset connection!
      echo "PING RESTART!"
      nmcli con down id $VPNNAME
      sleep 5
      nmcli con up id $VPNNAME
fi
echo 0 >/dev/shm/vpnAsyncVal
return 0
}&
}

nice=0

for (( ; ; )); do

# creating ifinite loop

tested=$(nmcli con status id $VPNNAME | grep -c UUID)
#possible results:
# 0 - no connection - need to start
# 1 - working connection, continue.

case $tested in
"0")
echo "Not connected - starting"

#increase nice counter
nice=$[nice+1]

#if "nice start" fails for 3 times
if [ $nice -ge 3 ];
then
#TRY to knock hard way, resetting the network-manager (sometimes it happens in my kubuntu 12.04).
      echo "HARD RESTART!"
      nmcli nm enable false
      nmcli nm enable true
      sleep 5
      nmcli con up id $VPNNAME
      nice=0
else
#not yet 3 falures - try starting normal way
      echo "trying to enable."
      nmcli con up id $VPNNAME
fi


;;

"1")
echo "VPN seems to work" 

;;
esac

async_run


sleep $SLEEPTIME




done

```

---

### Post by user20372 on 2013-08-16
vpnautoconnect doesn't build for me:
configure: error: Could not find sys/capability.h

---

### Post by Cabalbl4 on 2013-09-06
> **user20372 said:**
> vpnautoconnect doesn't build for me:
configure: error: Could not find sys/capability.h
The script should not be built. It must be interpreted by bash.

---

### Post by papampi on 2013-12-26
Cabalbl4,
Thanks a lot for your awesome scripts
but seems I have some problems

I made some small changes and add date to your script 
I tested pings with : 
SITEA=www.gfhsakslkljkkl.com
SITEB=www.hjkdslfksljs.com

to check unknown hosts :
the result is :
```

Thu Dec 26 12:48:10 IRST 2013 : VPN seems to work
Thu Dec 26 12:48:10 IRST 2013 : Begin ping check
ping: unknown host www.hjkdslfksljs.com
Thu Dec 26 12:48:10 IRST 2013 : unknown host check done 0,0
ping: unknown host www.gfhsakslkljkkl.com
ping: unknown host www.hjkdslfksljs.com
Thu Dec 26 12:48:12 IRST 2013 : packet loss check done 0,0
ping: unknown host www.gfhsakslkljkkl.com
ping: unknown host www.hjkdslfksljs.com
Thu Dec 26 12:48:13 IRST 2013 : unknown host check done 0,0
Thu Dec 26 12:48:25 IRST 2013 : VPN seems to work
Thu Dec 26 12:48:25 IRST 2013 : Begin ping check
ping: unknown host www.gfhsakslkljkkl.com
ping: unknown host www.hjkdslfksljs.com
Thu Dec 26 12:48:27 IRST 2013 : packet loss check done 0,0
ping: unknown host www.gfhsakslkljkkl.com
ping: unknown host www.hjkdslfksljs.com
Thu Dec 26 12:48:29 IRST 2013 : unknown host check done 0,0

```

script i changed is :

```
#!/bin/bash

# VPNNAME here is the name of desired vpn connection to monitor
# edit this line:
##################
VPNNAME=vpn-makers
# enter desired time between checks here (in seconds)
SLEEPTIME=15
# ping wait time - wait for connection to answer for this ammount of seconds before concider it dead for specific site
PINGWAIT=5
#sites to ping for coonection
SITEA=www.gfhsakslkljkkl.com
SITEB=www.hjkdslfksljs.com
##################

#init shared memory varible
echo 0 >/dev/shm/vpnAsyncVal


async_run() {
{

testedp=$(</dev/shm/vpnAsyncVal)

if [ $testedp -eq 1 ];
then
echo $(date) : "ping check already in progress"
return 1
fi

echo 1 >/dev/shm/vpnAsyncVal
echo $(date) : "Begin ping check"
#begin ping checks
testpinga=$( ping $SITEA -c 3 -w $PINGWAIT | grep -c "100% packet loss" )
testpingb=$( ping $SITEB -c 3 -w $PINGWAIT | grep -c "100% packet loss" )
echo $(date) : "packet loss check done" $testpinga,$testpingb
testpingc=$( ping $SITEA -c 3 -w $PINGWAIT | grep -c "unknown host" )
testpingd=$( ping $SITEB -c 3 -w $PINGWAIT | grep -c "unknown host" )
echo $(date) : "unknown host check done" $testpingc,$testpingd
testping=$(($testpinga+$testpingb+$testpingc+$testpingd))

if [ $testping -ge 2 ];
then
#all packets lost - reset connection!
      echo "PING RESTART!"
      nmcli con down id $VPNNAME
      sleep 3
      nmcli con up id $VPNNAME
fi
echo 0 >/dev/shm/vpnAsyncVal
return 0
}&
}

nice=0

for (( ; ; )); do

# creating ifinite loop

tested=$(nmcli con status id $VPNNAME | grep -c UUID)
#possible results:
# 0 - no connection - need to start
# 1 - working connection, continue.

case $tested in
"0")
echo $(date) : "Not connected - starting"

#increase nice counter
nice=$[nice+1]

#if "nice start" fails for 3 times
if [ $nice -ge 3 ];
then
#TRY to knock hard way, resetting the network-manager (sometimes it happens in my kubuntu 12.04).
      echo $(date) : "HARD RESTART!"
      nmcli nm enable false
      nmcli nm enable true
      sleep 5
      nmcli con up id $VPNNAME
      nice=0
else
#not yet 3 falures - try starting normal way
      echo $(date) : "trying to enable."
      nmcli con up id $VPNNAME
fi


;;

"1")
echo $(date) : "VPN seems to work" 

;;
esac

async_run


sleep $SLEEPTIME




done
```

so i tested ping | grep 
result is weird :

payam@lubuntu-VirtualBox:~$ ping hgfhlasehklafkjlk.com -c 3 -w 5 | grep -c "unknown host" 
ping: unknown host hgfhlasehklafkjlk.com
0

---

### Post by Cabalbl4 on 2013-12-29
> **papampi said:**
> Cabalbl4,
payam@lubuntu-VirtualBox:~$ ping hgfhlasehklafkjlk.com -c 3 -w 5 | grep -c "unknown host" 
ping: unknown host hgfhlasehklafkjlk.com
0

It will not work so simple. Ping result is put to STDOUT, and it can be piped to grep.
However, "unknown host" is an error, and is put to STDERR, and is NOT piped to grep. 
If you wish to catch this error in grep, you should redirect output from STERR to STDOUT.
Usually it is a bad idea. Because there may be some other erros confusing the output and make grep return more strange results.
And "unknown host" will not work if DNS is cached.

---

### Post by papampi on 2013-12-29
Thanx for help,
problem was my openvpn hangs from time to time and ping could not resolve hosts 

so i solve openvpn hangs with sending STDERR to STDOUT too ( I know its not good idea, but it solves my problem for now):

testpingc=$( ping $SITEA -c 3 -w $PINGWAIT 2>&1 | grep -c "unknown host" )
testpingd=$( ping $SITEB -c 3 -w $PINGWAIT 2>&1 | grep -c "unknown host" )

---

### Post by Jason_Skala on 2014-06-08
***EDITED***
Nevermind I added to /etc/rc.local and it works perfect

Trying to get this script to not hang my system on shutdown. I added it to /etc/init.d and did a [COLOR=#000000][FONT=Verdana]*update-rc.d *[/FONT][/COLOR]vpnon.sh defaults. but on a reboot or shutdown the system hangs so hard I can only do a power off with the power button.
Any suggestions on the right way to do this

---

### Post by Cabalbl4 on 2014-06-09
Got to read it only today.
The script is not used to run as init.d script (lacks header, start, stop, restart sections, etc.). It will sure mess up startup if added to init.d.
My way is to use it in gui autolauncher, or put into rc.local as suggested.

Someday I intend to apply some upgrades and fixes to script, and I wonder if it needs to be rewritten as upstart job/init.d script?

---

