---
title: "Hamachi Cannot ping"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by boblemur on 2008-06-27
hey all :)

i know a lot have people have brought up this topic, but im still at a loss as to why i cant get any hamachi traffic moving :S

nick@nick-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth1

this is the problem.... the fact that the ham0 is on 0.0.... for the gateway.

however i have deleted that reference and then replaced it with one that has the correct gateway... however it has reverted itself :S back to all 0's

nick@nick-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto ham0
iface ham0 inet static
address 5.17.136.141
netmask 255.0.0.0

i dono if that has something to do with it or not, please help....

i can provide anymore info anyone needs... just im not sure where i should look next...

thanks for any help in advance

---

### Post by kahm007 on 2008-08-23
Bump-

I swear hamachi has me ready to pull my hair out. I have had hamachi for years on windows boxes but I find this installation really frustrating. 

Here's what I have done so far. 

I have installed hamachi from the website.  Had no problems getting it to connect to my network and it works!  ONE TIME!  After that if I reboot the computer I get the same problem I had before, which is hamachi will connect and see my networks but I cannot ping them.  I know it's not a firewall issue because it worked that first time. 

Hamachi process is as such.

Hamachi start

hamachi login

hamachi go-online <network>

hamachi get-nicks

hamachi list

and I cannot ping anything in that list.  Destination Unreachable.


Why does it work just once?  Its just so darn weird.

Tried restarting tuncfg

tried running hamachi-init -f thinking it might of been a key issue (NOT)

Read every post about the same problem with other people and tried the go-online thing obviously.  I just can't get it to work more then once.

I know it works and very well.  Now I just need it to work.. oh .. EVERY TIME!


Sigh.  It has driven me slightly batty.

Any and all suggestions are welcome.

---

### Post by boblemur on 2008-08-24
[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)

is a good howto on install make sure uv done all of those steps first...

u havnt joined a network, but i assume that u just forgot to type that...

make sure also that you can ping the computer without hamachi ie using its 192.168.1.x address or what ever or make sure that if its accross the internet that its not a router problem.

sorry i dont know that much about hamachi so im just guessing really

---

