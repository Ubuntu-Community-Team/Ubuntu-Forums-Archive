---
title: "iwconfig 8.04 =&gt; 8.10"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by davosmith on 2008-11-01
I have the following script running using cron:

```

ping -c 1 192.168.1.1

while [ "$?" -ne '0' ]; do
    currentdate=`/bin/date`
    echo "$currentdate - Wireless not detected -> restarting" >> /home/davo/wireless.log

    ifconfig wlan0 down
    dhclient -r wlan0
    ifconfig wlan0 up
    iwconfig wlan0 essid "<my essid, removed before posting>"
    iwconfig wlan0 key <key was here, but removed before posting>
    iwconfig wlan0 mode managed
    iwconfig wlan0 ap any
    iwconfig wlan0 bit auto
    
    dhclient wlan0
    
    sleep 0.10
    
    ping -c 1 192.168.1.1
done

```

Before I 'upgraded' to Ubuntu 8.10 this worked perfectly - I had my computer connected to my home wireless network before I logged in, which meant I could ssh to it from my laptop without any problems.

Now, however, it does not seem to work - the network applet connects without problem, once I have logged on, but no networking until then.

Any idea what might have gone wrong, as I'm rapidly running out of ideas.

---

