---
title: "MTU change for AOL, how?"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by LandRoverMan on 2008-05-12
I've just upgraded to Hardy Heron and I was delighted by how well the new new network manager set up picked up my adapter and worked with roaming mode after having to set it up manually for the last few releases.

I am however having a problem. I need to reduce my MTU from the default 1500 down to 1400 to work properly with AOL (I know but the girlfriend pays for it because she likes the chat:redface::redface: ). I can't find how to do this and my searches are providing little help.

Oh BTW she is AOL chatting on a M$ machine which I set up using DRTCP

Regards Rob.

---

### Post by chili555 on 2008-05-12
```
sudo ifconfig eth0 mtu 1400
```Substitute your interface, if it's not eth0. You might also check in the administration pages of your router to see if there is an MTU setting to adjust.

---

### Post by LandRoverMan on 2008-05-12
That's solved it!
Thanks a lot.
It was wlan0 in my case.

```
sudo ifconfig wlan0 mtu 1400
```

---

### Post by chili555 on 2008-05-12
Does it survive a reboot? if not, you can add the command, without sudo to */etc/rc.local* above exit 0, on it's own line.

---

### Post by LandRoverMan on 2008-05-12
> **chili555 said:**
> Does it survive a reboot? if not, you can add the command, without sudo to */etc/rc.local* above exit 0, on it's own line.

In a word NO! lol

your solution does though thanks.

Open a text editor
```
sudo nano /etc/rc.local
```
then paste in as described above.
```
sudo ifconfig wlan0 mtu 1400
```
then just for good measure I did a
```
sudo /etc/init.d/networking restart
```

[COLOR="Blue"]*[MonkeyMotorSport](http://www.monkeymotorsport.co.uk)*[/COLOR]

---

### Post by con on 2008-06-01
I did the above on my laptop, but it doesn't survive a suspend. Its been suggested in other threads to append the line "mtu 1440" to the file /etc/network/interfaces, but this doesn't seem to work.

This is what I have in /etc/networking/interfaces

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
mtu 1440

---

