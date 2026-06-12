---
title: "home network problem"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by MintabiePete on 2007-03-19
I have had this wired  home network  for some time , and when I originally set it up I had  no problems  with it .

4 computers, 3 running  Ubuntu edgy 1  running  ubuntu dapper

Linksys AG 241 router,  AAPT  broadband 

I can  go online  with them all , I have no problems  with that .

(A) main  with ubuntu 6.10 edgy 
(B)            "     ubuntu 6.06 dapper 
(C)            "     ubuntu 6.10 edgy
(D)            "     ubuntu 6.10 edgy

On (A) I can  send files to  (B)  but  not  to (C) or (D)
On (B) I can send  files  to  (A) (C) & (D)
On (C) I can send  files  to (B) but not to (A) or (D)
On (D) I can  send files  to (B) but not to (A) or (C)

in All purposes  I have no problems   with (B) that is running  ubuntu 6.06 dapper 

I have tried Filezilla , FireFTP  Konquerer and gFTP , they are all the  same 

I can ping  ok from each   computer , no problems  there . I have  gotten used to this  , and if  I want to send  files from computer to computer I can do it , but not the way I would like to  :)

I am   using normal  network setup eth0 and connecting auto config DHCP  Internet Protocol IPv4 I think I done away with IPv6 

But it seems the only  computer  that is  working  somewhat normal  is (B) running  ubuntu 6.06 dapper that I havn't  touched .

Can  someone help me :)

Thanks

---

### Post by paulmilliken on 2007-03-19
Some more information would be useful to diagnose your problem.  Please try the following:
 
Open a terminal on computer A and type:
"ssh <username_C>@<ipaddress_C>"

where username_C is your user-name on computer C and ipaddress_C is the ip-address for computer C.  (If you don't know the ip address for computer C then type "ifconfig" on computer C and look for the number next to inet addr).

If you aren't able to log in via ssh then please report the output of "ps axu | grep sshd" for each of your computers.

If you are still stuck then please post the output of ifconfig under the heading eth0.

Paul

---

### Post by MintabiePete on 2007-03-19
This is  from (A)

pedro@pedro-desktop:~$ ssh <peter_C>@<192.168.1.65_C>
bash: syntax error near unexpected token `newline'
pedro@pedro-desktop:~$ ps axu | grep sshd
pedro    20706  0.0  0.0   2800   748 pts/0    R+   19:31   0:00 grep sshd
pedro@pedro-desktop:~$

This is from (B)
lita@lita-desktop:~$ ps axu | grep sshd
lita     19718  0.0  0.1   2892   820 pts/0    S+   19:36   0:00 grep sshd
lita@lita-desktop:~$

This is  from (C)
peter@peter-desktop:~$ ps axu | grep sshd
peter    18820  0.0  0.1   2796   748 pts/0    R+   19:40   0:00 grep sshd
peter@peter-desktop:~$

This is from (D)

pedro1@pedro1-desktop:~$ ps axu | grep sshd
pedro1   19147  0.0  0.1   2796   748 pts/0    R+   19:43   0:00 grep sshd
pedro1@pedro1-desktop:~$

---

### Post by dummybert on 2007-03-19
Try switching off IPv6, I think there's some problem in 6.10

in /etc/modprobe.d/aliases 


change line

alias net-pf-10 ipv6 

to

alias net-pf-10 off #ipv6

and restart network (or computer if you like)

---

### Post by MintabiePete on 2007-03-19
Try switching off IPv6, I think there's some problem in 6.10
 Ok I have  done that , will I do the  same  on the other two running  6.10 ?

And  thanks  for  giving  me  a hand , much appreciated  :)

I did it  with them all , even the  6.06 dapper , I remembered on (D) I had a  go previously  to fix it  and had the IPv6 commented  , but I did  what you said on them all . And have  rebooted  all the  computers  , but nothing has  changed , I can only  access (B) with any normality .

---

### Post by MintabiePete on 2007-03-19
this is  what I get  with  ifconfig  on computer  (A)

pedro@pedro-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:E3:FA:D8  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3091988 (2.9 MiB)  TX bytes:622767 (608.1 KiB)
          Interrupt:217 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5448 (5.3 KiB)  TX bytes:5448 (5.3 KiB)

pedro@pedro-desktop:~$

---

### Post by MintabiePete on 2007-03-19
I still cant  get any joy out of this , I will leave it  for a  while  then I may  install ubuntu dapper 6.06 in one of the   computers  running  6.10 edgy , and  see  what happens  :)

---

