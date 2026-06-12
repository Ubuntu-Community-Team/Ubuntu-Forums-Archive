---
title: "how to switch from one network interface to other network interface"
date: 2017-11-09
forum: Networking &amp; Wireless
---

### Post by sathishvarma.p on 2017-11-09
need script code to automatically switch from eth0 to wlan0 if eth0 disconnected or internet is not available, and viceversa...

---

### Post by The Cog on 2017-11-09
In what context? What do you want to switch? 
The reason I ask is that the IP routing should automatically switch. Although any existing connections may get broken, you should be able to reconnect (outgoing). In terms of incoming connections, whatever is connecting to you will need to know that your IP address has changed, and to now to connect to the new address.

---

### Post by sathishvarma.p on 2017-11-09
my system has both eth0 and ppp0 networks(if i type route -n in terminal it shows 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
).. 
  default it is iam getting internet from eth0 .. if internet got stopped by unplugging the internet cable from router or because of some reason , in my 
 terminal if i type route -n ,still eth0 will be shown but iam unable to access internet . 
In this case i want my system automaticlly connect to ppp0 . and in background i need to check for whether net is back on ethernet. if it is back i need to switch back to eth0.

---

### Post by aromo2 on 2017-11-09
In your first post you asked how to fall-back to wlan0 when the Ethernet cable is unplugged, which happens automatically by default.

Now you're saying that even though the Ethernet connection is still up (cable still plugged) you want to fall-back, and not to wlan0 but to ppp0 for which you need a command to bring up.

This is what you need to do in a background process:

```
loop
    if can't ping say 8.8.8.8 from eth0 then
        initiate ppp0 and make it active connection
    else
        if active connection is ppp0 then
            stop ppp0 and make eth0 the active connection
        fi
    fi
end-loop
```

I hope this helps.

---

### Post by sathishvarma.p on 2017-11-10
thank you so much. this one really helps ,but the problem is i don't know scripting .
if you provide the code for the above case will be really helpful..
thank you...

---

### Post by The Cog on 2017-11-10
If you unplug the cable from eth0 then it should go down and remove the default route from the routing table. ifconfig should no longer say RUNNING for eth0, and "ip link" should no longer say LOWER_UP.  If that doesn't happen then there is something wrong with your computer that I'm not sure I know how to fix. Of course, if the router loses internet access for some other reason (like if you pull the cable from the other side of the router) then eth0 will remain up and your default route will remain.

If the default route disappears when your cable is unplugged and your problem is that no default route for ppp replaces it, then this command (just once after you reboot) should do the trick. It adds a lower priority default route on the ppp link that will only be used when the eth0 default route disappears:
```
ip route del default dev ppp0 metric 100
```

If you want to manually switch the default route, these two commands should do the trick. To switch to ppp:
```
ip route del default via 192.168.100.1
ip route add default dev ppp0
```

To switch back, use the above commands but swap the **add** and **del** words.

A script like this (untested) should test every 10 seconds:
```
while true ; do
    ping -c3 -I eth0 8.8.8.8
    if [ $? == 0 ] ; then
        echo eth0 is working
        ip route add default via 168.100.1
        ip route del default dev ppp0
    else
        echo eth0 is busted
        ip route add default dev ppp0
        ip route del default via 168.100.1
    fi
    sleep 10
done

```

---

### Post by sathishvarma.p on 2017-11-10
Sorry if the question is trivial, but I can't figure out..

  I've my eth0 connection and I've created a ppp0 connection.

  Now, keeping alive eth0 connection, how can I test ppp0 connection?
  by typing something like this (ping -I ppp0 8.8.8.8) in terminal to check whether my ppp0 connection is active or not.

---

### Post by SeijiSensei on 2017-11-10
Do both have routes out to the Internet, or just the PPP connection?  If you run the command "route" how many "default" routes do you have?  

If you only have one default route, and it goes through the PPP connection, then "ping 8.8.8.8" will confirm that it is working.  If you have multiple routes, post the results of "route -n" inside of [noparse]```

```[/noparse] tags.

---

### Post by sathishvarma.p on 2017-11-12
both the routes out to the internet. i have only one default route i.e, eth0. 
in this case can i check wthether my ppp0 is transmitting packets or not, while iam accesing net with eth0.

---

### Post by sathishvarma.p on 2017-11-14
any suggestions or solution is avaialble with anyone , please respond to this post

---

### Post by SeijiSensei on 2017-11-14
If the default route uses eth0, it is very unlikely that any traffic will travel over ppp0.  If you run the command "ifconfig" you should see traffic counts for each interface.  For instance, that command shows this traffic (Receive/Transmit) for my eth0:

```
RX bytes:232279445619 (232.2 GB)  TX bytes:11870552123 (11.8 GB)
```

What do you see for ppp0?

Why do you need a PPP connection if you already have a connection to the Internet via eth0?

If you want to check the PPP connection, you can ping the IP address on the other side of the connection.

---

### Post by sathishvarma.p on 2017-11-15
if internet via eth0 stopped because of some reasons, in that case i dont want to stop the work which iam currently working. 
so in that case i  want to switch to ppp0 by removing eth0 as default and making ppp0 as default and continue my work.

i want to switch back to eth0 whenever my eth0 is back .

so for this purpose i need to check whether my eth0 is back or not while iam using ppp0..

---

### Post by sathishvarma.p on 2017-11-16
any one have  solution for this..???/

---

### Post by sathishvarma.p on 2017-11-17
my system have two network interfaces 1. ppp0 2.eth0. 
presently my default gateway is eth0 and due to some reasons the internet connection is lost, i'm  checking the connection for every 10 seconds. by  Ping -I eth0 8.8.8.8  .
when iam not reachable to internet ,iam switching my default interface to ppp0 by deleting the previous default intreface eth0 by $route del default dev eth0 and accessing internet through ppp0.
while iam continuing with my work through ppp0 , i need to check whether my intrenet from eth0 is back or not having my default intreface as ppp0.

any answer will be helpful . plz respond ASAP

---

### Post by Hadaka on 2017-11-17
Hi you didnt need to open a new thead.,
please mark your original thread SOLVED
[https://ubuntuforums.org/showthread.php?t=2377111](https://ubuntuforums.org/showthread.php?t=2377111)
and thank The Cog for helping you.
Here is the same basic script modified to do what you need.
It has been  tested it and it works.

```
#!/bin/bash
while true ; do
          ping -c3 -I eth0 8.8.8.8
          if [ $? == 0 ] ; then
                clear
                echo eth0 is working
                ip route add default via 168.100.1
                ip route del default dev ppp0
           else
                  clear
                  echo eth0 is busted
                  sleep 5
                  ip route add default dev ppp0
                  ip route del default via 168.100.1           
             ping -c3 -I ppp0 8.8.8.8
             if [ $? == 0 ] ; then
                  clear
                  echo ppp0 is now active default 
                  echo
                  echo Checking eth0
             fi
           fi
sleep 10
done
```

#This script checks the availability of eth0 every 10 seconds even if ppp0 is active.
#So in the event eth0 becomes available ppp0 is deleted and eth0 is added as default.

---

### Post by SeijiSensei on 2017-11-17
To make this happen automatically you would need to learn about routing metrics and routing tables.  It's not easy to do.

You could write a simple script that you could run from the command line like:
```

#!/bin/bash

case ($1) in 
    "ppp")
     ip route del default
     ip route add default via x.x.x.x
     ;;

     "eth")
     ip route del default
     ip route add default via y.y.y.y
     ;;

     *)
     echo "Syntax "switch-gateway ppp|eth"
     exit 2

esac

exit 0

```
Replace x.x.x.x with the IP address of the other end of the PPP connection, and y.y.y.y with the IP address of the router to which eth0 is connected.

Call the script something like "switch-gateway", mark it executable, and put it somewhere in your path like /usr/local/sbin.  Now you can run "switch-gateway ppp" or "switch-gateway eth" to make the appropriate interface the default gateway.

---

### Post by jeremy31 on 2017-11-17
Multiple threads merged
sathishvarma.p please do not start new threads about this issue

---

