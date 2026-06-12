---
title: "Ad-Hoc Troubles"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by stldirty on 2008-11-13
I'm trying to set up an ad-hoc network between my laptop and iphone 3g.  i can't get this to work for the life of me.  i've created the network on my laptop but whenever i select it, it immediately disconnects.  any help would be greatly appreciated.

---

### Post by tsbaker on 2008-11-13
I'm not the most Linux savvy, but I think your problem may due to a couple of things. 

A). Linux only sees the iPhone as a camera not a phone with data capabilities
B). The iPhone doest not support teathering, so unless your phone is jailbroken, I don't think it can be done.

Mine is jail broken, 3G, I have an app called PdaNet which works well in Windows, I haven't gotten around to trying in Linux yet without doing it through vbox.

Like I said I'm not an expert, just thought I'd try and help. I'm going to go try it myself now see if I can get it working and then I'll post again!

---

### Post by SnowflakeRV7 on 2008-11-27
tsbaker, if you could post anything you find that would be helpful.  Near as I can tell so far (still working on it), you'll need to disable Network Manager, and create the ad-hoc network manually.  Once it's up and shared, you should be good to go.

I say "should", because I haven't succeeded yet myself.

More info in these threads:

[http://ubuntuforums.org/showthread.php?t=952546](http://ubuntuforums.org/showthread.php?t=952546)
[http://ubuntuforums.org/showthread.php?t=781936](http://ubuntuforums.org/showthread.php?t=781936)

---

### Post by lswb on 2008-11-27
Ooops, double post 

Moderator, please delete.

---

### Post by lswb on 2008-11-27
I don't have an iphone so can't help with that end, but I have successfully set up ad-hoc networks between a couple laptops and an ipaq. I have found that Network Manager does indeed get in the way, though it can sometimes connect to an ad-hoc network that already exists.

Anyway, here is how I do it for hardy:

first stop Network Manager:

```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

```

Then configure the ad hoc network. Substitute the name of your wifi interface if it is different from eth1 and the network name after "essid". (Your system hostname is a good choice) This is for an open, unencrypted network, no WEP or WPA, though they can be used with proper arguments to the iwconfig line. This also uses the avahi zero-config service to self-assign ip addresses in the 169.254.x.x. range. avahi is included in a default ubuntu installation and I'd be very surprised if the iphone doesn't have a compatible equivalent, since Apple was more or less the first to implement this idea.

```

sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc essid "YourNameHere" channel 6 
sudo ifconfig eth1 up
sudo avahi-autoipd --daemonize eth1

```

Note 1:I get better results when specifying a channel, you can use anything from 1 to 11 in the US where I put "channel 6"

Note 2: With the avahi (sometimes called zero-config, apple originally called it "bonjour") service, your systems are addressible by using .local as the hostname suffix, like laptop.local Does the iphone use a hostname of some kind? If not you can connect by using the 169.254.x.x. address that is assigned to it.

To shut down the ad-hoc network,
```

sudo avahi-autoipd --kill eth1
sudo ifconfig eth1 down

```

To restart network manager, run the same 2 lines from the 1st code block but change "stop" to "start"

I have put 2 scripts in a directory (I used /usr/local/sbin) on my path so I don't have to type all this. If the commands work for your setup you could use them also, modify where necessary and remember to chmod 755 them and make them owned by root.

Start or stop the ad-hoc network, including starting or stopping NM, by typing "sudo radhoc start" or "sudo radhoc stop" It uses the system hostname as the essid.

radhoc
```

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

case $1 in

start)
/usr/local/sbin/netman stop
ifconfig eth1 down
iwconfig eth1 mode ad-hoc essid "$( cat /etc/hostname )" channel 6 
ifconfig eth1 up
avahi-autoipd --daemonize eth1 
;;


stop)
avahi-autoipd --kill eth1
ifconfig eth1 down
/usr/local/sbin/netman start
;;

*)
echo "
Usage: radhoc start|stop
Start or stop a wireless ad-hoc network. Uses /etc/hostname to set ESSID.
"
;;
esac

```

This one is just for starting/stopping NM which I find convenient at times, it also must be invoked as "sudo netman stop" or "sudo netman start"

netman
```

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

/etc/dbus-1/event.d/25NetworkManager $@
/etc/dbus-1/event.d/26NetworkManagerDispatcher $@



```

---

