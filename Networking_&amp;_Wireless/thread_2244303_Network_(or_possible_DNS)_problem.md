---
title: "Network (or possible DNS) problem"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by zaazz on 2014-09-15
I've been procrastinating dealing with this for awhile, almost gave up and built out a new image but for the sake of learning something I thought i'd come here and see if anyone can help. I don't know if I need to rebuild the networking aspect of this box but I'm open to suggestions and appreciate any help. This started after I did command line update from 12 to version 14.

Couple of side notes: I tried to setup Dan's guardian awhile ago and I don't know if that has anything to do with it. (see bottom uninstall)

Version:
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty



~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:32:36:df  
          inet addr:192.168.88.146  Bcast:192.168.88.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21137876 (21.1 MB)  TX bytes:5134879 (5.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:41028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7067797 (7.0 MB)  TX bytes:7067797 (7.0 MB)


Contents of /etc/network/interfaces

auto lo
iface lo inet loopback

*******************************

$ ping -c 5 [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (173.194.46.113) 56(84) bytes of data.
64 bytes from ord08s13-in-f17.1e100.net (173.194.46.113): icmp_seq=1 ttl=51 time=43.5 ms
64 bytes from ord08s13-in-f17.1e100.net (173.194.46.113): icmp_seq=2 ttl=51 time=37.8 ms
64 bytes from ord08s13-in-f17.1e100.net (173.194.46.113): icmp_seq=3 ttl=51 time=37.6 ms
64 bytes from ord08s13-in-f17.1e100.net (173.194.46.113): icmp_seq=4 ttl=51 time=37.0 ms
64 bytes from ord08s13-in-f17.1e100.net (173.194.46.113): icmp_seq=5 ttl=51 time=37.8 ms


--- [www.google.com]("http://www.google.com") ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4009ms
rtt min/avg/max/mdev = 37.076/38.807/43.560/2.400 ms
********************************

$ ping -c 5 archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.149) 56(84) bytes of data.
64 bytes from danava.canonical.com (91.189.88.149): icmp_seq=1 ttl=46 time=132 ms
64 bytes from danava.canonical.com (91.189.88.149): icmp_seq=2 ttl=46 time=125 ms
64 bytes from danava.canonical.com (91.189.88.149): icmp_seq=3 ttl=46 time=126 ms
64 bytes from danava.canonical.com (91.189.88.149): icmp_seq=4 ttl=46 time=126 ms
64 bytes from danava.canonical.com (91.189.88.149): icmp_seq=5 ttl=46 time=126 ms


--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4009ms
rtt min/avg/max/mdev = 125.138/127.354/132.006/2.434 ms

********************************

$ sudo netstat -pt
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        1      0 localhost:33291         localhost:49912         CLOSE_WAIT  1889/Plex DLNA Serv
tcp        1      0 localhost:33292         localhost:49912         CLOSE_WAIT  1889/Plex DLNA Serv
tcp        0      0 lowball-ub-vm.local:50716 chromecast2.local:8008     ESTABLISHED 1889/Plex DLNA Serv
tcp        0      0 lowball-ub-vm.local:53675 chromecast.local:8008   ESTABLISHED 1889/Plex DLNA Serv
tcp        0    288 lowball-ub-vm.local:ssh   240.100.59.10.st:42480 ESTABLISHED 308/24




*********************



$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid Release.gpg                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg                    
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Err [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main i386 Packages                        
  401  Unauthorized
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main Translation-en_US                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  401  Unauthorized
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main Translation-en                       
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
  401  Unauthorized
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
  401  Unauthorized
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en              
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources             
  401  Unauthorized [IP: 91.189.92.150 80]
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages       
  401  Unauthorized [IP: 91.189.92.150 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
  401  Unauthorized [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  401  Unauthorized


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  401  Unauthorized


W: Failed to fetch [http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-i386/Packages](http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-i386/Packages)  401  Unauthorized


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  401  Unauthorized [IP: 91.189.92.150 80]


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  401  Unauthorized [IP: 91.189.92.150 80]


W: Failed to fetch [http://ppa.launchpad.net/jcfp/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/jcfp/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  401  Unauthorized


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages)  401  Unauthorized [IP: 91.189.91.15 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
/$ 



$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo apt-get remove dansguardian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'dansguardian' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



$ sudo apt-get --purge remove --assume-yes "dansguardian"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dansguardian*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 475073 files and directories currently installed.)
Removing dansguardian (2.10.1.1-4) ...
Purging configuration files for dansguardian (2.10.1.1-4) ...
W: Can not find PkgVer for 'dansguardian'
$ sudo apt-get --purge remove --assume-yes "tinyproxy"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tinyproxy
$ sudo apt-get --purge remove --assume-yes "clamav"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'clamav' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get --purge remove --assume-yes "firehol"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firehol
$ sudo apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dansguardian-gui-ubuntu

---

### Post by praseodym on 2014-09-15
Did you activate a system-wide proxy?

---

### Post by zaazz on 2014-09-15
> **praseodym said:**
> Did you activate a system-wide proxy?

I can't answer that question because I am not sure. Would you be able to provide instructions on how to check? I can post the results.

---

### Post by praseodym on 2014-09-15
Go to "System settings -> Network proxy" (in GNOME and Unity) and deactivate it systemwide. Reboot after that.

---

### Post by zaazz on 2014-09-15
> **praseodym said:**
> Go to "System settings -> Network proxy" (in GNOME and Unity) and deactivate it systemwide. Reboot after that.

Here are the settings that were set when I opened it up. Looks like it wasn't enabled systemwide.[ATTACH=CONFIG]256466[/ATTACH]

---

### Post by zaazz on 2014-09-15
> **praseodym said:**
> Go to "System settings -> Network proxy" (in GNOME and Unity) and deactivate it systemwide. Reboot after that.

Actually I think that worked. After a reboot I'm able to do apt-get update successfully! Thanks!

---

