---
title: "Auto reconnect"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by goldan on 2007-10-05
Hi
i'm using ubuntu 7.04 , cable modem and some script to get in to the internet.
how can i set my computer to reconnect when connection drop ?
i'm really a newbie and dont understand very much.. so if you can tell me in detils howto ill be very happy.
thanks ahead
:)

---

### Post by goldan on 2007-10-08
Well i think i have it (!)
it works when i operete it manual

pico ping.sh and paste the script down there
chmod +x ping.sh (or make it exuctable somehow i dont remember how i did that :\)
just add the command in cron to be checked every few min
change "cable-start" for your own ip-up command (thats my script command)
i dont have understanding in this but i guess it pings google.com and if the output shows what it say in line 4 then it will run the cable start command.

thanks to pipe| from dalnet.

 ping -c3 google.com > pingreport
 result=`grep "0 received" pingreport`
 truncresult="`echo "$result" | sed 's/^\(.................................\).*$/\1/'`"
 if [[ $truncresult == "3 packets transmitted, 0 received" ]]; then
 echo "The network is down!"
cable-start
else
   echo "The network is up!"
fi

---

### Post by graabein on 2008-01-01
I'm going to try this out but doing **ping -c3 google.com** resulted in some waiting time before one line output of:```
ping: unknown host google.com
```

So I guess the script needs a bit of modification...

---

### Post by graabein on 2008-03-17
I'm at my parents house this week and I'm experiencing similar problems... 

When I leave the machine on for a while it looses internet connection (I think it's in correlation to the screensaver on Xubuntu 7.10 kicking in). I'd like a script I can run to reconnect to the net without having to reboot.

Unfortunately I'm still a noob when it comes to scripts (bash and perl) so I could use some help. 

If I also can get this script running once every few minutes no matter who is logged on that would be sweet. 

I'm on wireless btw...



UPDATE: Started a [thread]("http://ubuntuforums.org/showthread.php?p=4537652") on the Programming Talk forum.

---

