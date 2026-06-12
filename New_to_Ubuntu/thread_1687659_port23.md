---
title: "port23"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by PhilRogers34 on 2011-02-14
i read some threads on here that said port 23 shouldn't be open, i scanned myself and it shows prot 23 , 135 and 139 are visible to the outside world, i had a look to see what was using port 23 and got this

ESTABLISHED 4354/firefox-bin
tcp        0      0 192.168.1.10:41816      74.125.230.113:80       ESTABLISHED 4354/firefox-bin
tcp        0      0 192.168.1.10:42508      92.123.109.229:80       ESTABLISHED 4354/firefox-bin
tcp        0      0 192.168.1.10:41817      74.125.230.113:80       ESTABLISHED 4354/firefox-bin
tcp        0      0 192.168.1.10:41815      74.125.230.113:80       ESTABLISHED 4354/firefox-bin

without firefox running i got

phil2@JAHWEH:~$ sudo netstat -tunap|grep 23
tcp        0      0 192.168.1.10:47985      74.125.230.115:80       TIME_WAIT   -               
tcp        0      0 192.168.1.10:47984      74.125.230.115:80       TIME_WAIT   -               
tcp        0      0 192.168.1.10:47983      74.125.230.115:80       TIME_WAIT   -               
phil2@JAHWEH:~$ 

should firefox be using port 23? if not how do i configure it so port 23 is stealthed? what about 135 and 139? what do they do?

---

### Post by sydbat on 2011-02-14
> **CharlesA said:**
> First, How did you 'scan the connections' ?

Secondly, ufw and firestarter conflict, so I would suggest purging firestarter and just using ufw.

EDIT: Whoa that was weird.**I've had this happen a couple of times (posting an answer in another thread only to have it show up somewhere else), and yes...it is very weird.**

To the OP of THIS thread...it sort of looks like you have things figured out now?

EDIT - JUST LIKE THIS...AAAAAHHHHHHHHH...

---

### Post by CharlesA on 2011-02-14
Take 2:

First, How did you 'scan the connections' ?

Secondly, ufw and firestarter conflict, so I would suggest purging firestarter and just using ufw.

@sydbat: That's good to know, I thought I was going crazy.

---

### Post by sydbat on 2011-02-14
> **CharlesA said:**
> Take 2:

First, How did you 'scan the connections' ?

Secondly, ufw and firestarter conflict, so I would suggest purging firestarter and just using ufw.

**@sydbat: That's good to know, I thought I was going crazy.**Somebody's messing with us dude...

---

### Post by PhilRogers34 on 2011-02-14
yeah, sorry i posted it but it wouldn't put the paragraphs in and it was all mixed up so i deleted it and asked about making paragraphs, it wasn't letting me highlight the option in the reply box.

i used this to scan myself  [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)

how do i purge some thing of my pc and what does that actually do?

---

### Post by mcduck on 2011-02-14
Your IP address is a local one, so you seem to be behind a router of some kind. Which means that the scanning tool you used scanned the *router*, not your computer... :)

Also the netstats in your first post aren't showing Firefox as using port 23, it's simply showing any line that contains string "23" in it. :D

Firefox is using ports 41816, 42508, 41817 and 41815.

edit:
tcp 0 0 192.168.1.10:41816 74.125.**23**0.113:80 ESTABLISHED 4354/firefox-bin
tcp 0 0 192.168.1.10:42508 92.1**23**.109.229:80 ESTABLISHED 4354/firefox-bin
tcp 0 0 192.168.1.10:41817 74.125.**23**0.113:80 ESTABLISHED 4354/firefox-bin
tcp 0 0 192.168.1.10:41815 74.125.**23**0.113:80 ESTABLISHED 4354/firefox-bin

tcp 0 0 192.168.1.10:47985 74.125.**23**0.115:80 TIME_WAIT -
tcp 0 0 192.168.1.10:47984 74.125.**23**0.115:80 TIME_WAIT -
tcp 0 0 192.168.1.10:47983 74.125.**23**0.115:80 TIME_WAIT -

---

### Post by PhilRogers34 on 2011-02-14
so thats port 23 on my router is visisble to world then? gotcha.  and the bit from the terminal wasn't actualy port 23 that was anything with a 23 in it?

so how do i check my actual computer ports?  is there some sort of programme that can list every single port, what its doing , whats using it with pid and an open/shut switch? if not can somebody write one please?

---

### Post by smurphy_it on 2011-02-14
netstat -a | grep LISTENING | less

That will show you all port which are in a LISTENING state, hence waiting for a connection.

---

### Post by pricetech on 2011-02-14
Port 23 is telnet, so it looks like your router allows telnet connections from the outside world.  Not good.

135 and 139 are DCE Endpoint Resolution and NetBIOS Session Service respectively.

Check your router's configuration and see if you can turn that stuff off.  If not, black hole it by forwarding those ports to a "black hole" address where you will never have a node of any kind.  I use .250 as my black hole address, chosen for no particular reason but used consistently everywhere I set up a router / network.

---

### Post by PhilRogers34 on 2011-02-14
ok my router is a thomson livebox and there's not a great deal i can do with it, i just looked and i have an application called 'Telnet server' on the list that was showing as configured for port 23, i removed the configuration and had a scan but it was still showing as closed instead of stealthed, i removed 'Telnet server from the list of apps and scanned again but its still not showing as stealthed. will that be enough? i don't have the option to blacklist any apps.

ok next question,  ports 135 and 139 needed? or can i close them too?

next question, how do i purge firestarter? can i just go into the software centre and uninstall it?

cheers!

---

### Post by PhilRogers34 on 2011-02-14
i don't have netbios or dce on the list at all, this is all the ones on my router list, how many do i actually need? if i only want my pc and xbox to have access to the net?
[IMG]http://ubuntuforums.org/images/attach/jpg.gif[/IMG]

---

### Post by PhilRogers34 on 2011-02-14
right i rebooted my router and then tried a scan and it is now showing ports 23 ,135, and 139 as stealthed, good stuff!!

so how do i purge firestarter then please?

---

### Post by CharlesA on 2011-02-14
Run this:

```
sudo apt-get purge firestarter
```

---

### Post by PhilRogers34 on 2011-02-14
ok, i've run that, is that all i have to do?  

how should i configure ufw then?

---

### Post by CharlesA on 2011-02-14
You can use ufw or install the gufw package:

```
sudo apt-get install gufw
```

---

### Post by PhilRogers34 on 2011-02-14
i already had ufw, which is now running the listening report shows
tcp    8089     mono
udp 51294  avahi-deamon
udp 5353    avahi deamon
upd 68  dhclient3

is that normal?

---

### Post by CharlesA on 2011-02-14
Is your PC hooked directly to the internet?

---

### Post by PhilRogers34 on 2011-02-14
pc - ethernet cabele- router - adsl filter   is what i have at the moment

---

### Post by CharlesA on 2011-02-14
It sounds like it's scanning the localhost, not the router.

In any case, you should be fine.

---

### Post by PhilRogers34 on 2011-02-14
cool, is the local host my isp or my router?

---

### Post by CharlesA on 2011-02-14
Your local PC. A router wouldn't have mono, or avahi running on it.

---

### Post by PhilRogers34 on 2011-02-14
right, that's the listening report from ufw, thats why i wanted to know if it's normal or not

---

### Post by CharlesA on 2011-02-14
Ah ok. So yes it's normal. :)

---

### Post by PhilRogers34 on 2011-02-15
Excellent! so port 23 on my router is now shut and my firewall is doing what it should.

I ran the netstat command and got this

unix  2      [ ACC ]     STREAM     LISTENING     20313    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     24704    /tmp/orbit-phil2/linc-cc1-0-3d31f0e0b58ca
unix  2      [ ACC ]     STREAM     LISTENING     21528    /tmp/ssh-zXhRkc2984/agent.2984
unix  2      [ ACC ]     STREAM     LISTENING     21568    /tmp/.ICE-unix/2984
unix  2      [ ACC ]     STREAM     LISTENING     21609    /tmp/orbit-phil2/linc-bcf-0-1f6a0dc547a68
unix  2      [ ACC ]     STREAM     LISTENING     21797    /tmp/orbit-phil2/linc-ba8-0-ae697ec51a57
unix  2      [ ACC ]     STREAM     LISTENING     8207     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     21991    /tmp/keyring-7BYvTd/ssh
unix  2      [ ACC ]     STREAM     LISTENING     7449     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     21285    /tmp/keyring-7BYvTd/control
unix  2      [ ACC ]     STREAM     LISTENING     21993    /tmp/keyring-7BYvTd/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     22019    /tmp/orbit-phil2/linc-bd8-0-3ec02946b7430
unix  2      [ ACC ]     STREAM     LISTENING     21567    @/tmp/.ICE-unix/2984
unix  2      [ ACC ]     STREAM     LISTENING     22040    /tmp/orbit-phil2/linc-bd5-0-7fc2e85ec17b1
unix  2      [ ACC ]     STREAM     LISTENING     23497    /tmp/orbit-phil2/linc-c42-0-5e51e3332ef5f
unix  2      [ ACC ]     STREAM     LISTENING     22223    /tmp/orbit-phil2/linc-be6-0-2b79dd483273
unix  2      [ ACC ]     STREAM     LISTENING     7713     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     23313    /tmp/.esd-1001/socket
unix  2      [ ACC ]     STREAM     LISTENING     23316    /home/phil2/.pulse/336dd9661f2baaefffb0450200000008-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     22427    /tmp/orbit-phil2/linc-bec-0-74e4231945610
unix  2      [ ACC ]     STREAM     LISTENING     22443    /tmp/orbit-phil2/linc-bed-0-38896d3555f79
unix  2      [ ACC ]     STREAM     LISTENING     22460    /tmp/orbit-phil2/linc-beb-0-891904e61512
unix  2      [ ACC ]     STREAM     LISTENING     22561    /tmp/orbit-phil2/linc-bf5-0-3f4aedfea928f
unix  2      [ ACC ]     STREAM     LISTENING     22682    /tmp/orbit-phil2/linc-c00-0-7bc3f96cda314
unix  2      [ ACC ]     STREAM     LISTENING     22690    /tmp/orbit-phil2/linc-c01-0-dcc2521dc6e7
unix  2      [ ACC ]     STREAM     LISTENING     23011    /tmp/orbit-phil2/linc-c10-0-698dad627c64a
unix  2      [ ACC ]     STREAM     LISTENING     23017    /tmp/orbit-phil2/linc-c12-0-7e189ec27dcfa
unix  2      [ ACC ]     STREAM     LISTENING     23021    /tmp/orbit-phil2/linc-c13-0-1f99b1567e054
unix  2      [ ACC ]     STREAM     LISTENING     23072    /tmp/orbit-phil2/linc-c11-0-20b5f76c8d1c1
unix  2      [ ACC ]     STREAM     LISTENING     23235    /tmp/orbit-phil2/linc-c31-0-caeeb51e726
unix  2      [ ACC ]     STREAM     LISTENING     23295    /tmp/orbit-phil2/linc-c36-0-102bc1633c17
unix  2      [ ACC ]     STREAM     LISTENING     23377    /tmp/orbit-phil2/linc-c3b-0-59ba525720557
unix  2      [ ACC ]     STREAM     LISTENING     6193     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     20312    @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8290     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     21541    @/tmp/dbus-MDebJrLSRZ
unix  2      [ ACC ]     STREAM     LISTENING     20382    @/tmp/gdm-greeter-nHiTxMAK
unix  2      [ ACC ]     STREAM     LISTENING     20524    @/tmp/gdm-session-YCPHdIFf

This is with the pc sitting idle, no internet connections active.   are these all ports on my pc? and how many do i actually need? how do i close those that are not needed? cheers

---

### Post by CharlesA on 2011-02-15
Those are open sockets not ports and they aren't "listening" on an external interface.

I couldn't find anything that described them in detail, unfortunately.

---

### Post by PhilRogers34 on 2011-02-15
Not to worry, thanks for trying anyway and thanks for the replies,  i take it no external interface means i don't have to worry too much about things.  pretty much solved, 

cheers!

---

