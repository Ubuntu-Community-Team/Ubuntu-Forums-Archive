---
title: "Fixed Alsa sound and LOST wifi Ath5k"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by iamgeniusrnti on 2009-12-06
So I was following this [here]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/") and it worked like a charm!!!  I have sound on alsa again!

BUT.. I am typing this on my thru my ethernet connection because my ath5k stopped working.  Watch this:

root@K-Netbook:/usr/src# ifconfig        
eth0      Link encap:Ethernet  HWaddr 00:23:5a:83:94:6c  
          inet addr:192.168.1.240  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe83:946c/64 Scope:Link              
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1              
          RX packets:20980097 errors:0 dropped:0 overruns:0 frame:0       
          TX packets:387 errors:0 dropped:0 overruns:0 carrier:3          
          collisions:0 txqueuelen:1000                                    
          RX bytes:255418 (255.4 KB)  TX bytes:56180 (56.1 KB)            
          Interrupt:28                                                    

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                            
          RX bytes:2580 (2.5 KB)  TX bytes:2580 (2.5 KB)       

root@K-Netbook:/usr/src# sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132                                                                                                                
root@K-Netbook:/usr/src# rfkill list                                                                                                           
1: phy0: Wireless LAN                                                                                                                          
        Soft blocked: no                                                                                                                       
        Hard blocked: yes                                                                                                                      
root@K-Netbook:/usr/src# rfkill list                                                                                                           
1: phy0: Wireless LAN                                                                                                                          
        Soft blocked: no                                                                                                                       
        Hard blocked: yes                                                                                                                      
root@K-Netbook:/usr/src# rfkill unblock 1                                                                                   
root@K-Netbook:/usr/src# rfkill list                                                                                                      
1: phy0: Wireless LAN                                                                                                                          
        Soft blocked: no                                                                                                                       
        Hard blocked: yes                                                                                                                      
root@K-Netbook:/usr/src# ifconfig                                                                                                              
eth0      Link encap:Ethernet  HWaddr 00:23:5a:83:94:6c                                                                                        
          inet addr:192.168.1.240  Bcast:192.168.1.255  Mask:255.255.255.0                                                                     
          inet6 addr: fe80::223:5aff:fe83:946c/64 Scope:Link                                                                                   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20981097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1156 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000
          RX bytes:1307456 (1.3 MB)  TX bytes:238278 (238.2 KB)
          Interrupt:28

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2580 (2.5 KB)  TX bytes:2580 (2.5 KB)

root@K-Netbook:/usr/src# ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
root@K-Netbook:/usr/src# sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
root@K-Netbook:/usr/src# rfkill list
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
root@K-Netbook:/usr/src# rfkill unblock 1
root@K-Netbook:/usr/src# rfkill list
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
root@K-Netbook:/usr/src# uname -a
Linux K-Netbook 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686 GNU/Linux
root@K-Netbook:/usr/src#
 

WHY?!?!?!?!?!  What does the damn sound card have to do with the price of tea in China?!?!?!

If rfkill won't unblock it, what will???

---

### Post by iamgeniusrnti on 2009-12-06
Ok... update:

I ran this: sudo modprobe -r -f ath5k

Then I ran modprobe ath5k

Then ifconfig wlan0 up--badda bing, badda boom, it's alive.

Not sure what the -f does; who cares.

---

