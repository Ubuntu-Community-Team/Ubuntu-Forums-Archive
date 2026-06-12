---
title: "Help!! I seem to have broken the internet"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by reflexsa on 2008-10-21
Hey people,

So I was busy fiddling around trying to forward a port for warcraft 3 and I came across this [http://ubuntuforums.org/showthread.php?t=480979]("http://ubuntuforums.org/showthread.php?t=480979")

I followed the 4th posts instruction where you edit the firewall file using gedit. After doing all the steps in that post I could no longer use the internet. I also was not able to log onto my router.

I first ran this command: /etc/init.d/firewall stop
And then I removed it from the start list using: update-rc.d firewall remove

As far as I can remember I did use the sudo command infront of all of these. When trying to remove it from the startup I had to use a -f to force it. After doing this still nothing worked, so I deleted the firewall file that I was editing.

Now thats gone and I cant get it back, and it still doesnt work. However I installed firestarter and if I open that then close it then the internet works until I reboot.

Im quite new to linux, as you may have noticed. Im using ubuntu hardy I think

Thanks for any help in advance

---

### Post by SpaceTeddy on 2008-10-21
you have leftover iptables rules somewhere from that script. I am not entirely sure what exactly you did, or what that script did (that's why one should not run things one does not understand - especially when they fiddle in the systems core).

Anyways - post the output of these command when the internet is NOT working to see if you have leftover iptables rules:

```
sudo iptables -L
sudo iptables -L --table nat
```

lets see what we can see :)

---

### Post by reflexsa on 2008-10-21
Okay, here is the result from sudo iptables -L:

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  kenny                10.0.0.255          
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
nicfilt    all  --  anywhere             anywhere            
srcfilt    all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
srcfilt    all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
s1         all  --  anywhere             anywhere            

Chain f0to1 (3 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6112 state NEW 
logdrop    all  --  anywhere             anywhere            

Chain f1to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6112 state NEW 
logdrop    all  --  anywhere             anywhere            

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED ' 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain logdrop (4 references)
target     prot opt source               destination         
logdrop2   all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
DROP       all  --  anywhere             anywhere            

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED ' 
DROP       all  --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       all  --  anywhere             anywhere            

Chain logreject2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       all  --  anywhere             anywhere            

Chain nicfilt (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
logdrop    all  --  anywhere             anywhere            

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      all  --  anywhere             kenny               
f0to1      all  --  anywhere             10.0.0.255          
f0to1      all  --  anywhere             ip6-localhost       
logdrop    all  --  anywhere             anywhere            

Chain s1 (1 references)
target     prot opt source               destination         
f1to0      all  --  anywhere             anywhere            

Chain srcfilt (2 references)
target     prot opt source               destination         
s0         all  --  anywhere             anywhere   



And from the iptables -L --nat:



Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

Hope this helps

---

### Post by SpaceTeddy on 2008-10-21
ok -these are definitely a lot of leftovers... i have no idea where exactly they get loaded (are you sure there is no firewall loaded anywhere, and you really have removed every reference to the file you added earlier ?)

anyways... these commands will fix your problem (they will disable any firewalling and let anything pass to and from your computer):
```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

the last line might not be needed, but is in anyways just to be on the safe side. 

As i said before, it is unlikely that ubuntu loads these kind of rules by itself - you must have leftovers somewhere that load your iptables-configuration... on order to find these, can you (after you have tried the above apporach) post the output of 
```
ls /etc/rc2.d
cat /etc/rc.local
cat /etc/network/interfaces
```

this will show most (not all) information about what you systems starts and loads at boot time... maybe something can be seen in there... 

cheers

---

### Post by reflexsa on 2008-10-21
Ok, I am going to use those commands you have given me. Will this make my computer easy to hack?

Anyway I uninstalled Firestarter and the iptable -L gave this:



Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  login.router         anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  login.router         anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             10.0.0.255          
DROP       all  --  BASE/8               anywhere            
DROP       all  --  anywhere             BASE/8              
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
ACCEPT     tcp  --  kenny                login.router        tcp dpt:domain 
ACCEPT     udp  --  kenny                login.router        udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE/8               anywhere            
DROP       all  --  anywhere             BASE/8              
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
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:x11:6015 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:x11:6015 
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




Thanks for the help so far, I am pretty sure I would be breaking things more without your help

---

### Post by SpaceTeddy on 2008-10-21
mhm - there is still something loading - did you run all the commands from the first block and then produce the output ? you should be looking like this:
```
# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

# sudo iptables -L --table nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ipoese@ipoese-laptop:~$ 
 
```

And this does not neccessarily make your computer "easier" to hack - it just makes it possible to connect to services that are running on your computer from another machine. The real question is - what is running on your computer :) for that i need to know the output of the second block of commands...

---

### Post by reflexsa on 2008-10-21
Ah I did get the same output that you just posted, I am going to try restart quickly and see if it sticks

---

### Post by reflexsa on 2008-10-21
After restarting the iptables -L looks the same as before I did the 5 sudo iptables commands.

Here is the output from the other 3

kevin@kenny:~$ ls /etc/rc2.d
README                       S12dbus           S20winbind     S89cron
S01policykit                 S18avahi-daemon   S24dhcdbd      S90binfmt-support
S05vbesave                   S20apport         S24hal         S98usplash
S10acpid                     S20cupsys         S25bluetooth   S99acpi-support
S10powernowd.early           S20hotkey-setup   S25pulseaudio  S99laptop-mode
S10sysklogd                  S20nvidia-kernel  S30gdm         S99rc.local
S10xserver-xorg-input-wacom  S20powernowd      S89anacron     S99rmnologin
S11klogd                     S20rsync          S89atd         S99stop-readahead

kevin@kenny:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

kevin@kenny:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by SpaceTeddy on 2008-10-21
there is nothing in your boot configuration (that i can see) that would load these iptables settings... 
the rc2.d looks clean, the rc.local is empty (as it should be) and the network card does not force any scripts either... i am (unfortunately) out of ideas... sorry :(

anybody else got any idea why these settings get loaded ?

---

### Post by reflexsa on 2008-10-21
Is there a way I can run those other commands on startup? Its the only thing I can think of

---

### Post by SpaceTeddy on 2008-10-21
yes you can - put them into the /etc/rc.local file - edit it with
> gksu gedit /etc/rc.local

and put the following lines in (BEFORE the *exit 0* - anything after it gets ignored !)

> /sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -P INPUT ACCEPT
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -P FORWARD ACCEPT

then save and reboot - see if it works by rebooting. 

I must stress tho that this is a workaround and might lead to strange behavior if you ever choose to install a firewall again... just so you know. You can, of course, always remove those lines again)

cheers

---

### Post by reflexsa on 2008-10-21
Okay I think I have fixed it. I ran those 5 commands again and then I went into the synaptic package manager. I had also installed one of the other firewalls through the add/remove thing. So I searched for all of them and selected to completely remove them.

I rebooted and it seems to work.
Yay!

Thanks SpaceTeddy, you were a great help. Thanks for responding quickly aswell. Dont fear I will let you know if somethings bombs from my deleting of things :)

---

### Post by reflexsa on 2008-10-21
Oh yes, using these

sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT 

can I be easily hacked, or do you not think it will be much of a problem?

---

### Post by SpaceTeddy on 2008-10-21
i don't think it is much of a problem... to be "hacked" you usually need some open port (ok, there are ways to do it without by attacking the protocol stack itself) but in general, if you know what is running on your computer (i.e. you don't blindly install servers) then your system should be fairly safe. 
Of course, having the packet filter adds another layer of security, as even open ports get blocked... but if you know what your computer does - well - then this is not really a problem.
(i don't usually load a firewall when booting my PC - but then, i made sure i have no open ports either - except ssh)

cheers

---

