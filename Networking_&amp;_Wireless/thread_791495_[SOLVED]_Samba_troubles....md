---
title: "[SOLVED] Samba troubles..."
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Shiv Prakash on 2008-05-12
Hey,

I have **ubuntu 8.04** installed and **Places->Network** is just not working as it should :confused:

Only a few times did my system detect other systems on the LAN(all others are windows) even though **nbtscan** clearly shows that all other systems are up and running. Moreover a few time i am even able to connect to others using **smb://<system name>/** but not always

What seems to be the problem here...dual booting just so i can access other systems is a headache...

thanks for your help

---

### Post by Shiv Prakash on 2008-05-12
This seems to be a **very common problem with a very uncommon solution**, too many people shifting over from windows with the launch of 8.04 are **facing difficulties accessing systems on LAN in a predominantly windows setup.**

People not facing this difficulty i.e they can easily access other windows computers on LAN should post here. Hopefully its just some small thing that i and lots of others are doing wrong.

---

### Post by SpaceTeddy on 2008-05-12
there are three things i can think of that could go wrong... 
i'll run them in unlikelyness - i.e. the most unlikely first (from my point of view).

1.) you don't have smbclient installed. I think that smbclient is needed to acctually browse the network properly. to check if it is installed, use this command

```
dpkg-query -l smbclient
```
it should produce an output like this:

> ii  smbclient      3.0.28a-1ubunt a LanManager-like simple client for Unix

if this line does not show up, try installing smbclient via this command
```
sudo apt-get install smbclient
```
i have the distinct feeling that this would be installed by default... so this is really a long shot

2.) you have a firewall running that is blocking port 137/139/445 which are the ports that the windows clients communicate with each other. Disable the firewall (firestarter ?) and try again. 
This is not a long shot, just a guess... i don't know if that acctually fixes anything.

to check if you have some paket filter installed, use this command
```
sudo iptables -L
```

it should produce an output that looks like this:
> Chain INPUT (policy **ACCEPT**)
target     prot opt source               destination         

Chain FORWARD (policy **ACCEPT**)
target     prot opt source               destination         

Chain OUTPUT (policy **ACCEPT**)
target     prot opt source               destination   
the bold bits are showing (in my case) that anythig to the machine is accepted - so nothing is blocked. Check that against yours :)

3.) how do i put this - windows name resolution sucks - big time. The names for a windows machine **do not match** and **do not have any relation** to any other name that the computer uses. The names are distributed via broadcasts between the computers. How that exactly works i have yet to figure, but i do know that the name resolution has never been reliable for me - Ever. Not without a WINS server.
i'd suggest, instead of trying smb://<server name> you try smb://ip-address which will not reoly on the windows name resolution and use the basic ip-layer directly. If you still cannot access the other machine then, this gets serious...

These suggestions are guesses - and guesses only. I don't use windows shares or name resoltuion (as you might have figures from point three). Also, i only know about *network* problems - not about configuration problems... by answering this i hope i can rule out any basic trouble with the connectivity so that someone who know more about the whole windows network can jump in and fix the problem if it still exists.

Also, i have not checked for a bug report on this. 
BTW: the places->network does not work for me either - didn't know it untill i tested it, and i really don't care as i don't use it :)

hope this helps in solving the problem

---

### Post by Shiv Prakash on 2008-05-13
Thanks a lot for replying Space,

I followed all the steps you asked me to...but step 2 did not execute as required

**I am getting (policy DROP) in all of them.**

and yes smb://ip/works like a charm. Now all i have to do is to use nbtscan and then smb://ip/

```
:~$ sudo iptables -L
```
> Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  resolver1.opendns.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  resolver1.opendns.com  anywhere            
ACCEPT     tcp  --  resolver2.opendns.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  resolver2.opendns.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.55         resolver1.opendns.com tcp dpt:domain 
ACCEPT     udp  --  192.168.0.55         resolver1.opendns.com udp dpt:domain 
ACCEPT     tcp  --  192.168.0.55         resolver2.opendns.com tcp dpt:domain 
ACCEPT     udp  --  192.168.0.55         resolver2.opendns.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere

---

### Post by bobblehat on 2008-05-13
Hi folks,

I'd had no problems myself under either Hardy or Gutsy but by habit I mount samba shares manually, either via command line, fstab or in Nautilus -> File -> Connect to server. All those methods seem to work reliably under Gutsy for me and still work under Hardy.

I just tried using Places -> Network under Hardy (from what I read this is where most people seem to have a problem) and couldn't see a share I'd just connected to via a manual mount command.

So in summary - it seems browsing to the share seems problematic but actually connecting isn't (at least that's the case for me).

---

### Post by SpaceTeddy on 2008-05-13
if i see that correctly, according your iptables output, your computer does not accept nmb broafcasts - meaning your nmb cannot receive the broadcasts from other computers - an therefore not their names. If i remeber this correctly, you will need to allow an incomming connection on port 137 or 139 with udp.

for the setup, i cannot tell you how to configure your firewall software, but i can tell you the commands to run to make it work. Unforteunatly, you will need to run the commands every time you reboot, as the rules in iptables are temporary and will be completly reloaded by your firewall software.

If you want to know the commands anyway, please provide the output of the following command (it does the same as the one before, just more detailed so i can properly read your configuration - i am better with numbers than words :))
> sudo iptables -L -vnx 

Again - i cannot make the changes permanent. I can only tell you how to manipulate iptables directly !

cheers

---

### Post by Shiv Prakash on 2008-05-13
Ok here goes

```
:~$ sudo iptables -L -vnx
```

> Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       208.67.222.222       0.0.0.0/0           tcp flags:!0x17/0x02 
     948    69830 ACCEPT     udp  --  *      *       208.67.222.222       0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       208.67.220.220       0.0.0.0/0           tcp flags:!0x17/0x02 
     244    17618 ACCEPT     udp  --  *      *       208.67.220.220       0.0.0.0/0           
     325    31942 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
       8     2056 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
    2503   316956 DROP       all  --  *      *       0.0.0.0/0            192.168.0.255       
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
     232    20188 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
 2541302 3726871631 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       192.168.0.55         208.67.222.222      tcp dpt:53 
    1020    72556 ACCEPT     udp  --  *      *       192.168.0.55         208.67.222.222      udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       192.168.0.55         208.67.220.220      tcp dpt:53 
     268    19222 ACCEPT     udp  --  *      *       192.168.0.55         208.67.220.220      udp dpt:53 
     325    31942 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    2590   184824 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
 1328397 60018187 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
 2541288 3726868955 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
      14     2676 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     113    11300 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
 1327829 59973557 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       3      228 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
     452    33102 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0 

Phew!!! SpaceTeddy god knows what you see in the above...:) i can just hope that someday i too can see what you are seeing here....:(

---

### Post by njparton on 2008-05-13
If you're behind a router you can flush iptables to reset all the rules.  I wouldn't do this is you're directly connected to the net though.
 
I can't remember the command to do this, maybe someone else will chime in with it?

---

### Post by njparton on 2008-05-13
Check this out:
 
[http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html](http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html)

---

### Post by SpaceTeddy on 2008-05-13
as njparton suggested - here are the commands to entirely flush your iptables filter and allow anything to/from your machine

```
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT

```

the first will entirely empty out all rules, the second and thrid overwrite the default behaviour so your machine will accept anything that comes in and is send out. Please note that this only applies on paket level - if nothing is running on a specific port, your machine will still reject the connection :)

so - for inserting the proper rules:

if i am not mistaken, nmb broadcasts work on port 137/udp - so we'll only allow that one for now and see how it goes
```
sudo iptables -I INPUT -p udp --dport 137 -j ACCEPT
```

since your OUTBOUND chain is already allowing your machine to send thing anywhere, there is no second rule needed to allow answers.
Remember that you will have to make permanent changes to your firewall software to allow this upon reboot, or you will need to run the above command every time to reboot AFTER the your firewall script has been loaded.

i hope this does the trick - altough, these rules are (for my eyes) all over the place. They're probably smart as hell - but it takes a while to get used to them

---

### Post by Shiv Prakash on 2008-05-13
Ok so il get down to this and post my experience asap...hope this does the trick :)

---

### Post by Shiv Prakash on 2008-05-13
OHHH my freaking god...It worked...man!!! Freaking 6 days of hunting for a answer and finally...phew!!!! :guitar: :)

Ok so i did all the above and now when i go to Places -> Network i get to see WORKGROUP....which i couldnt before...but not the other computers..
Another interesting fact is that i can now resolve network names from terminals itself i.e

```
:~$ ping praful
```

> PING praful (192.168.0.123) 56(84) bytes of data.
64 bytes from PRAFUL.local (192.168.0.123): icmp_seq=1 ttl=128 time=0.237 ms
64 bytes from PRAFUL.local (192.168.0.123): icmp_seq=2 ttl=128 time=0.227 ms
64 bytes from PRAFUL.local (192.168.0.123): icmp_seq=3 ttl=128 time=0.229 ms

--- praful ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.227/0.231/0.237/0.004 ms

This wasnt happening before...

So all thats left is getting the rest of the network to show up in Places->Network...

---

### Post by SpaceTeddy on 2008-05-13
which way did you go ? flush all the rules and set the default to ACCEPT, or did you just insert the rules ?

---

### Post by Shiv Prakash on 2008-05-13
I did the following

```

sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -I INPUT -p udp --dport 137 -j ACCEPT

```

Just tried out the entire thing after a system restart,and this is what i goto do

1.I put up my firewall
2.Run all the above commands
3.I can now access all other computers on LAN through PLaces->Network.If i stop the firewall then i got to run all the above commands again just like SpaceTeddy pointed out.

But keeping that aside the above happen to be atleast some way a user can access other windows comps on LAN. This needs to be looked into.

---

### Post by Shiv Prakash on 2008-05-13
So basically when i crossed over to Ubuntu i was faced with 2 problems 
> 
[http://ubuntuforums.org/showthread.p...21#post4932321](http://ubuntuforums.org/showthread.p...21#post4932321)
[http://ubuntuforums.org/showthread.php?t=790482](http://ubuntuforums.org/showthread.php?t=790482)

 
1.I couldn't access shared internet connection on the LAN

2.Other windows systems weren't visible in Places->Networks

Well the first got sorted out by simply uninstalling network manager and manually setting up static IP in /etc/interfaces. Simple right?? nooo...took me 3 days to get that,finally **chilli555** gave the solution.Well that got rid of my first problem.

Then on to my second,

Well i haven't understood what i did exactly so **SpaceTeddy** is the guy to forward questions too :) he helped me through the second problem and now with a little tweaking i can easily access other window systems on LAN.

In my journey to do the above i also did what was given in the following thread
> [http://ubuntuforums.org/showthread.php?t=789444](http://ubuntuforums.org/showthread.php?t=789444)
I am not sure whether this also contributed in the final solution but i did it anyways.

Ummm so i guess noobs like me shifting over from a Windows LAN should probably do all the above so the transition is as painless as possible :)

---

