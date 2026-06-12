---
title: "Trouble Seeding torrents...is my port properly forwarded?"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by DarrylLicke on 2010-12-25
Forgive me if this is in the wrong place but after some searching of the forum I'm effectively stuck.

I've tried 3 different clients (Vuze, ktorrent, rtorrent) and they all get the same result: I'm able to download the torrent but that's it. I am not seeding, even when downloading, and when done the torrent effectively goes dead. Even on torrents that should be very busy.

While I have ktorrent running this is what a netstat -plntu looks like:

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::65234                :::*                    LISTEN      23730/ktorrent  
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           23730/ktorrent  
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:40059           0.0.0.0:*                           -               
udp6       0      0 :::5353                 :::*                                -               
udp6       0      0 :::57089                :::*                                -               

```And my iptables look like this: 


```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       

```I've got my port forwarded on my 2WIRE901: 

> Device                         Allowed Applications                         Application Type                         Protocol                         Port Number(s)                         Public IP                                                                       
                                                                      Desktop                         ktorrent                         -                         UDP                         4444
                        **.***.***.***                                                                       
                        
                        
                        TCP                         65234
                        **.***.***.***
And both of those ports match the settings in ktorrent.

I haven't the foggiest idea why I'm not able to seed. And I'd rather not be a jerk when it comes to torrents.

Thanks for any help.

---

### Post by kryptic_mind on 2011-01-03
I am having the same problem. All was working fine on previous gnome installation, now on a fresh KDE install, I have perfect download speed etc, but no uploading whatsoever.

---

### Post by DarrylLicke on 2011-01-03
I wanted to update this thread since it just got a reply. 

I just fixed this last night and the issue was my router. I had correctly incorrectly set the port forwarding on the router for a different computer instead of the seeding box. 

So while the ports were correctly set for both TDP and UDP for ktorrent, the application was authorized for a different computer on the network. 

In the end outgoing was fine because I think the router will allow all outgoing traffic but since the OK was for a different computer nothing was allowed incoming to my seeding computer.

As soon as I switched that setting I checked the port at utorrent port checker and got a green check box.

---

