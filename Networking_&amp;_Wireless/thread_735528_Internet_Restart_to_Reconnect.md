---
title: "Internet: Restart to Reconnect"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by Zeotronic on 2008-03-25
Ever since I first managed to connect to the internet, in 7.04 (of course I am in 7.10 now) I have noticed that I cannot reconnect without restarting my computer. Oh sure, if I get disconnected I reconnect no problem, but if I disconnect myself, by any means, then I cannot reconnect. I connect through a Conexant modem, and I use the Conexant Modem Engine, restricted driver to use it. I'm pretty sure I got it from Dell somewhere. I suspect this problem is not because of that though, but I'm not experienced enough to make that call.

Anyways, its a pain to restart every time I want to connect to the internet... and a pain to connect to the internet every time I start-up... so can anyone help me with this?

---

### Post by SpaceTeddy on 2008-03-26
how exactly are you connecting to the internet ? which programm do you use for it ?
also, i suspect that you might be using an ADSL line. in that case, have you tried figuring out if the pppd process is stopped properly ? is dmesg telling you anything after a disconnect ?

lots of questions... please answer any you can, and provide the output of the following commands to further debug the problem

right before you disconnect, please run
```
ifconfig
route -n
```
then disconnect and run
```
ifconfig 
dmesg|tail
ps aux |grep ppp
```

the first/third command shows the network interfaces on your computer, the second will print your routing table, and the fourth will show any failures with the moden upon disconnect (if any). The last one will show if pppd got terminanted properly (that only works if you have adsl...

---

### Post by Zeotronic on 2008-03-26
> how exactly are you connecting to the internet ?
Bright.net dial-up service.
> which programm do you use for it ?
Erm, Network-Admin? I know thats probably not right, but its probably the same thing Ubuntu uses... after all, its *only Xubuntu*.
> also, i suspect that you might be using an ADSL line.
I take it thats a form of DSL? No... I wish DSL was available in my area! I have dial-up! If I had DSL I would have mentioned it... because DSL involves special hardware doesn't it? *I would have had to have mentioned it.*

This is what I got from the code you gave me:
> dusk@zeomatrix:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:1E:4B:3A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:06:5B:1E:4B:3A  
          inet addr:169.254.3.101  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:728 (728.0 b)  TX bytes:728 (728.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:209.143.54.213  P-t-P:209.173.174.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:636845 (621.9 KB)  TX bytes:82493 (80.5 KB)

dusk@zeomatrix:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
209.173.174.129 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
dusk@zeomatrix:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:1E:4B:3A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:06:5B:1E:4B:3A  
          inet addr:169.254.3.101  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:728 (728.0 b)  TX bytes:728 (728.0 b)

dusk@zeomatrix:~$ dmesg|tail
[   97.566440] PPP Deflate Compression module registered
[  263.999151] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.198 DST=209.143.54.213 LEN=485 TOS=0x00 PREC=0x00 TTL=41 ID=0 DF PROTO=UDP SPT=36112 DPT=1026 LEN=465 
[  333.251115] Inbound IN=ppp0 OUT= MAC= SRC=216.155.193.176 DST=209.143.54.213 LEN=226 TOS=0x00 PREC=0x00 TTL=47 ID=25121 DF PROTO=TCP SPT=5050 DPT=47606 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
[  336.367670] Inbound IN=ppp0 OUT= MAC= SRC=216.155.193.176 DST=209.143.54.213 LEN=293 TOS=0x00 PREC=0x00 TTL=47 ID=41789 DF PROTO=TCP SPT=5050 DPT=47606 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
[  340.527125] Inbound IN=ppp0 OUT= MAC= SRC=216.155.193.176 DST=209.143.54.213 LEN=293 TOS=0x00 PREC=0x00 TTL=47 ID=8583 DF PROTO=TCP SPT=5050 DPT=47606 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
[  347.801408] Inbound IN=ppp0 OUT= MAC= SRC=216.155.193.176 DST=209.143.54.213 LEN=293 TOS=0x00 PREC=0x00 TTL=47 ID=5321 DF PROTO=TCP SPT=5050 DPT=47606 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
[  358.926994] Inbound IN=ppp0 OUT= MAC= SRC=216.155.193.176 DST=209.143.54.213 LEN=293 TOS=0x00 PREC=0x00 TTL=47 ID=61351 DF PROTO=TCP SPT=5050 DPT=47606 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
[  368.444598] Inbound IN=ppp0 OUT= MAC= SRC=24.64.239.78 DST=209.143.54.213 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=38353 PROTO=UDP SPT=10461 DPT=1028 LEN=492 
[  368.444633] Inbound IN=ppp0 OUT= MAC= SRC=24.64.239.78 DST=209.143.54.213 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=38351 PROTO=UDP SPT=10461 DPT=1026 LEN=492 
[  368.444654] Inbound IN=ppp0 OUT= MAC= SRC=24.64.239.78 DST=209.143.54.213 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=38352 PROTO=UDP SPT=10461 DPT=1027 LEN=492 
dusk@zeomatrix:~$ ps aux |grep ppp
dusk      6526  0.0  0.1   2976   752 pts/0    R+   09:15   0:00 grep ppp
dusk@zeomatrix:~$ 

While I don't understand all of it... looking at it, I plainly see that ppp0 dissappears in the first command, after disconnecting... though what that means is beyond my understanding.

---

### Post by SpaceTeddy on 2008-03-26
first off, adsl and dialup are (from the linux point of view) the same thing. Both create a ppp device (in your case ppp0) which then acts as the network card connected to the internet. 
In fact, i would say there is little to no difference in how these devices are handled.

in general, your output looks fairly normal, there are no errors in your dmesg (which means the device does not "crash" and cannot be used again) and the ppp process exits normally....

what caught my eye tho was this output
> dusk@zeomatrix:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
209.173.174.129 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 0.0.0.0 0.0.0.0 U 0 0 0 ppp0
0.0.0.0 0.0.0.0 0.0.0.0 U 1000 0 0 eth0

this does not seem to make any sense at all - at least not to me. I am not sure, but it might be that the last two lines of this output is what is getting your modem confused. 
To verify this, try the following.

connect to the internet, and print the output of
> route -n

then disconnect, run it again and also paste the output...

then try to reconnect (i guess the modem connects but you now cannot "use" the internet) and get the output again...

ok. that was the debugging for me (there should be three outputs now) which i would like you to paste here

as for fixing it, after disconnecting the modem, try running this command
```
sudo route del -net 0.0.0.0 netmask 0.0.0.0
```
to remove the 0.0.0.0 entries from your routing table (these changes are only temporary, so you do not break anything permantly). run this command multiple times until ```
route -n
```
does not give you any more lines with 0.0.0.0 in the first row.
then try and see if a reconnect to the internet works...

i might sound a little confusing here, but i have no other ideas... at the moment at least :)

---

### Post by Zeotronic on 2008-03-26
Here is the output you requested:
> dusk@zeomatrix:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
209.173.174.129 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
dusk@zeomatrix:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
dusk@zeomatrix:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
dusk@zeomatrix:~$
And removing the empty lines didn't help... my investigations suggested that that occurs automatically on reconnect.

It has occured to me that it may be useful to know that when I try to reconnect, my modem turns on, as I can hear the tone, and then clicks off... for the record this doesn't happen in Windows... not that I'll ever go back.

---

### Post by SpaceTeddy on 2008-03-27
ok, as you can see, the routing table did not get modified on the third output, which should have been the same as the first (from your last post). this indicates that either your modem does not connect properly anymore, or that (for some reason) the routes are not getting set properly...

those entries that get deleted/added tell your computer where to find the internet.
when you run the command
```
ifconfig ppp0
```
while you are connected, you should see something like this:
> ppp0      Protokoll:Punkt-zu-Punkt Verbindung  
          inet Adresse:242.129.15.93  P-z-P:242.129.15.1  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4785 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3 
          RX bytes:2361644 (2.2 MiB)  TX bytes:516630 (504.5 KiB)


when you then disconnect and reconnect, does the output of that command change into something like
> 
ppp0: Fehler beim Auslesen der Schnittstelleninformation: Gerät nicht gefunden

(sorry for the german - but i do not have a linux at hand at the moment that would give me english errors :) )

if so, your problem lies within the modem itself - or rather, when you disconnect the modem does not cleanly shut down (for some reason) and refuses to connect the next time. If this is really a hardware issue, or a driver thing that ubuntu cannot access the modem properly, i don't know. 
I have never worked with modems that closely to be able to debug this... so you will most likely hope that someone answers this thread that knows more about modem issue than i do...
sorry to disappoint...

---

### Post by Zeotronic on 2008-03-27
So, as it turns out I *do* get that error (though in English of course)... I'm not particularly suprised... but surely there is a command I could use to forcably terminate my modem in a way that would allow me to reconnect without restarting?

---

