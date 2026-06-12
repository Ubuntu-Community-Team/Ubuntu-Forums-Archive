---
title: "using netsend to interact with windows boxes"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2007-02-04
I have tried a couple things to get ubuntu to send net send messages to the windows machines on the network, but nothing seems to work. 

the first thing I tried was following this syntax:
```

$ smbclient -M <netbiosname>
<message>
ctrl-d

```

I have a windows machine called DESKTOP in the workgroup WGROUP. So I tried smbclient -M DESKTOP, which waited a little before telling me that the 'Connection to DESKTOP failed'. I then noticed it was listed as desktop in the Windows Network. So I tried that, with the same result. 

After that, I tried the same with local IPs instead. I'm on 192.168.0.100, the other machine is on 192.168.0.101. I tried both, just to see the difference. 

results:
```

kulgan@UBUNTU:~$ smbclient -M 192.168.0.100
message start: ERRSRV - ERRmsgoff (Not receiving messages.)
kulgan@UBUNTU:~$ smbclient -M 192.168.0.101
session request failed

```

for all other IPs it was:
```
conrad@UBUNTU:~$ smbclient -M 192.168.0.xxx
Error connecting to 192.168.0.xxx (No route to host)
Connection to 192.168.0.xxx failed

```

obviously... 

there were no changes in the router log.

I can understand the part about not getting the messages to myself, but what about the ones to the windows box? 

Normally netsend is enabled by default (at least, the computer bloke at school had to turn it off after I found out :D ), so there shouldn't be a problem now, right? Unless this is another difference between XP and Home...

I have seen several posts elsewhere on the same topic that have been left unresolved and even unanswered, so I hope this one won't be :D

Thanks for all help
-K

---

### Post by alex.scotton on 2007-12-27
errr... i use the Win Messenger Service all the time, but I cannot do:

smbclient -M (IP_Address)

it won't connect, not sure why, never queried it, as:

smbclient -M (netbios name) works well!.. there is a way to send using IP addresses using -M and then -I however don't seem to be able to get it to work!

Anyways hope you pick this up, and that it helps.

---

