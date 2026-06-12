---
title: "Systemwide proxy settings?"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Sirron on 2007-10-01
My university has a wireless network that requires users to connect via their proxy (AirNet). It looks like whatever site you try to browse to after connecting to the network, you get redirected to their login page, and have to login to the network. That works.

In order to browse pages not hosted by the university, I've found I need to set Firefox to use their proxy configuration file. On windows, you can set it to automatically detect proxy settings. But that won't work on Ubuntu.

But of course, other software, Synaptic for example, can't connect as it is set to directly connect to the internet. You can set simple proxy settings in the application's options menu, but the settings aren't at all simple so I wouldn't know what to put. And I don't really want to have to go through all my applications and set proxy settings for each of them.

So is it possible to somewhere configure something to use the proxy configuration file I use in Firefox, so that every application I use can connect?

Also, I'd rather this setting can be simply reverted, as I also use this laptop at home sometimes.

Thanks

---

### Post by strabes on 2007-10-01
System, Preferences, Network Proxy.

Or, you can add an http_proxy environment variable into the end of your ~/.bashrc, like this:

> export http_proxy="http://proxylocation:yourport"

Then, to apply the new variable:```
source ~/.bashrc
```

When you go home, just comment out that line with a "#" and run the above command.

---

### Post by Sirron on 2007-10-01
Thanks for the reply, I'll have to wait till tomorrow to try it.

Is there no way to use the automatic configuration file? I don't know actual the address of the proxy, and I get the impression that the uni's technicians don't either. I think the config file is really just about getting connections to pages hosted by the university to connect via the local network, rather than the internet, which of course I can cheekily ignore, but is it likely to be anything else as well?

The config file's located at [http://www.staffs.ac.uk/proxy.config](http://www.staffs.ac.uk/proxy.config) if it's any use.

---

### Post by bapoumba on 2007-10-01
Hmm. Someone at the univ should be able to give you the proxy setting...

Anyway, having a laptop too, a univ too and a home too, I'm in the same situation :)

I work with conf files, I have not find a GUI that would do it all.

For a general proxy setting, run:
```
gnome-network-preferences
```
and set it from there. 
Not using Firefox, I think you need to set the proxy directly in a Firefox menu.

For updates/upgrades (apt-get, aptitude, synaptic..) applications, I work with the /etc/apt/apt.conf file:
my home setting:
```
Acquire::http::Proxy "direct";
```
My univ setting:
```
[noparse]Acquire::http::Proxy "http://proxy.blah.fr:3128";[/noparse]
```

---

### Post by Sirron on 2007-10-02
gnome-network-preferences was very useful, thanks. It's exactly what I was looking for ^^

---

### Post by DaveDH on 2007-10-09
I am having similar problems, but I have a slightly different requirement.

When I move my laptop between work/home/work etc. I have to manually switch the network proxy between 'direct connect' or 'automatic' and it's a pain having to use system>pref>network proxy each time.

Does anyone know if there is a linux app that toggles this from a panel icon?

---

### Post by DaveDH on 2007-10-09
For my toggle needs above, I wrote a script that does it...

#!/bin/bash
# Toggle the status of the network proxy

if [ $(gconftool-2 -g /system/proxy/mode) = "none" ]; then 
	gconftool-2 -s -t string /system/proxy/mode auto
	echo "Proxy is now AUTO"
else
	gconftool-2 -s -t string /system/proxy/mode none
	echo "Proxy is now OFF"
fi
exit 0

and created a panel link to run it.

BUT, I would ideally like the icon to indicate the status of the proxy.  Is there any way from a script to change the icon that is shown on the panel?

---

### Post by DrMeers on 2008-05-04
DaveDH:

I stumbled upon this thread whilst trying to figure out why a script that I had written (similar to yours) for automated proxy switching wasn't working properly. I've since discovered the reason:

You need to also set the **/system/http_proxy/use_http_proxy** key, or the http_proxy and no_proxy environment variables will not be set/unset appropriately. I had to download the source of gnome-network-preferences to figure this out!

I've written two small scripts for turning the proxy on or off:
~/.bin/proxyOn:
```
gconftool-2 --set /system/proxy/mode --type string manual
gconftool-2 --set /system/http_proxy/use_http_proxy --type bool true
```

~/.bin/proxyOff:
```
gconftool-2 --set /system/proxy/mode --type string none
gconftool-2 --set /system/http_proxy/use_http_proxy --type bool false
```

And also a daemon script to automatically detect which wireless network I'm connected to (based on the output of nm-tool) and turn the proxy on/off accordingly:
```
#!/bin/bash

DELAY=10 #seconds
SCRIPTDIR="/home/simon/.bin"

while [ true ]
do
        WASATUNI=$ATUNI
        ATUNI=`nm-tool | grep ACHERNAR | wc -l` #network name is ACHERNAR
        if [ "$ATUNI" != "$WASATUNI" ] #only change things if network changes. Otherwise will override any manual changes.
        then
                STATE=`$SCRIPTDIR/proxyCheck`
                if [ "$ATUNI" = "1" ]
                then
                        if [ "$STATE" = "none" ]
                        then
                                $SCRIPTDIR/proxyOn
                                logger "[$0] Proxy set to manual."
                        fi      
                else
                        if [ "$STATE" = "manual" ]
                        then
                                $SCRIPTDIR/proxyOff
                                logger "[$0] Proxy set to none."
                        fi
                fi
        fi
        sleep $DELAY
done
```

Oh, and that uses ~/.bin/proxyCheck:
```
gconftool-2 --get /system/proxy/mode
```

This could be easily modified to handle more complex situations like changing proxy configuration rather than just turning proxy on/off, by modifying other gconf keys.

Having upgraded to Hardy and Firefox 3.0b5, I can now tell Firefox to "Use system proxy settings", so I never need to touch the proxy configuration any more. Other applications like apt, etc all seem to integrate nicely with the gconf proxy settings. Even wget, etc will work, since the http_proxy environment variables have been set.

I hope other people find this useful too.

Simon

---

### Post by cybernytrix on 2008-05-15
I put the following script in /etc/network/if-up.d/nm-proxy and no longer need to manually configure any proxy when I roam around. 
You need to change the IP address for this to work properly. Also make the script executable. You can add as many network addresses you wish in the switch/case part!

The basic idea is to detect the user logged into X session and call gconftool as that user to fix proxy settings. 

My .bashrc simply fetches proxy settings from gconf. If your proxy requires authentication then you need to do this since http_proxy will only contain host:port but not user:pass@host:port. Seems like a gnome bug to me.

#! /bin/sh
# Enable/disable proxy based on network interface address

set -e

# Don't bother when lo is configured.
if [ "$IFACE" = lo ]; then
	exit 0
fi

# Only run from ifup.
if [ "$MODE" != start ]; then
	exit 0
fi

#Execute gconf commands as this user
U=`w|grep x-session-manag| awk '{print $1}'`
if [ -z "$U" ]; then
    exit 0
fi

IP=`ip addr show dev $IFACE | grep 'inet ' | awk '{print $2}'`
ENABLED=""
case "$IP" in
    157.254.120*)
    su $U -c '/usr/bin/gconftool -t bool -s /system/http_proxy/use_http_proxy true'
    su $U -c '/usr/bin/gconftool -t string -s /system/proxy/mode manual'
    ENABLED="enabled"
    ;;
    *)
    su $U -c '/usr/bin/gconftool -t bool -s /system/http_proxy/use_http_proxy false'
    su $U -c '/usr/bin/gconftool -t string -s /system/proxy/mode none'
    ENABLED="disabled"
    ;;
esac

if [ -x /usr/bin/notify-send ]; then
    # This does not work as we need some credentials...
    su $U -c "/usr/bin/notify-send \"New IP: $IP. Proxy is $ENABLED\""
fi

exit 0

---

### Post by bschultzjames on 2008-05-17
It seems like I'm having similar problems as the first post, but just reverse the problem because I'm at home trying to connect to the internet.  

My proxy settings seem to work for firefox and every application when I set the system proxy settings to direct connect or auto detection.  My problem is that when I try to download updates/applications/drivers through the add/remove application, Ubuntu says that it cannot resolve the proxy.  I then get a little screen telling me that it's trying to resolve through "proxy.gcc.edu" [my school's proxy].  

How do I change the proxy settings for the add/remove application? 



I've attached a screenshot of the error message.  



Thanks!

---

