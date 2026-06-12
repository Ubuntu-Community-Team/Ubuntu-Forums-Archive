---
title: "i changed permissions, and lost my wired connection!!!"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by sakul07 on 2007-09-25
hi everybody...

i was trying to get ownership over some files...and i screwed up my internet connection...

i accidently did "sudo chmod 777 / -R", and i think i was in my home directory...  
...after that i lost the sudo... but i could recover it reading some posts... but my internet connection still down...

please.... tell me there's some hope!!!

info:
Cablemodem internet connection.
auto asign ip (not static)

more info:
```

lucas@lucas-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:36:B7:1D:6E  
          inet6 addr: fe80::216:36ff:feb7:1d6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2392214 (2.2 MiB)  TX bytes:838 (838.0 b)
          Base address:0x5000 Memory:da000000-da020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


lucas@lucas-laptop:~$ cat /etc/resolv.conf 
nameserver 200.42.0.111
nameserver 200.42.97.111
nameserver 200.49.159.68
nameserver 172.20.2.142


lucas@lucas-laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface


lucas@lucas-laptop:~$ ping google.com
ping: unknown host google.com


lucas@lucas-laptop:~$ ping 72.14.207.99
connect: Network is unreachable

lucas@lucas-laptop:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth0/00:16:36:b7:1d:6e
Sending on   LPF/eth0/00:16:36:b7:1d:6e
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 190.188.168.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted
bound to 201.213.61.35 -- renewal in 4724 seconds.
lucas@lucas-laptop:~$

```

---

### Post by Old *ix Geek on 2007-09-26
I'm sorry I can't help with your Internet problem, but I wanted to say something about this:
> i was trying to get ownership over some files
...
i accidently did "sudo chmod 777 / -R", and i think i was in my home directory... 
It doesn't matter WHERE you were, it's the command's content that determines what happens--and, in your case, you gave read, write, and execute permission to all users, for all files and directories in your system.  That "/" in your command refers to your root (main) directory, and the -R tells chmod to act on everything from that directory on down, recursively.  (I'm sorry if you already know all this; I'm not trying to sound patronizing, but from what you posted I got the impression you were NOT aware of this.)  Since many files and directories are not supposed to have 777 permissions...well, you screwed up!  I'm not sure what the solution will involve, but setting all the permissions back the way they're supposed to be is definitely involved. :frown:

---

### Post by sakul07 on 2007-09-26
You're absolutly right!!! i didn't know what i was doing... hehe... but i'm facing the concecuences now ;)

ANYONE CAN HELP ME???

---

### Post by Old *ix Geek on 2007-09-26
Okay, good!  I'm glad you weren't insulted, because I didn't mean it that way, and it's so damn hard to judge how things will be interpreted online! :)

I think you should wait to see who else weighs in on this--someone might have a quick and dirty solution--but if nothing comes up...oh, I HATE saying these words...I think reinstalling Ubuntu might be necessary.  There are thousands and thousands of files and directories, and without manually changing their permissions back to what they're supposed to be, *I* don't see how else to fix it. :confused:  But someone else might.

Oh, a little word of advice for future reference: When you're using a command--even if it's something you've used a lot before and/or think you're completely familiar with--it's ALWAYS a good idea to take a final glance at it before hitting the [enter] key.  Even go to the point of sounding it out; in your case, **chmod 777 / -R**, that would've sounded like this: "Give all users permission to read, write, and execute all files and directories, starting in the root directory."  Do you see how that [probably] would have prevented the mishap?!  (I still do this after 20 years, and I've really only had one major mishap as a result...knock on wood!)

---

### Post by Skitzoid on 2007-10-23
i would like to bump this one since i'm in the exact same situation :lolflag:
and reinstalling is not an option.... seriously

---

