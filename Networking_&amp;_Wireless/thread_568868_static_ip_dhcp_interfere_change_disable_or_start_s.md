---
title: "static ip dhcp interfere change disable or start stop script"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by SpiritIsReality on 2007-10-06
howdy 
(I can't gt this. Can you?
**     Static IP problems - eth1 not in network.config  **
[http://ubuntuforums.org/showthread.php?t=560064  )]("http://ubuntuforums.org/showthread.php?t=560064")

I mean to say..I don't know how to solve a dhcp interfering with a static ip configuration. Could you please help?

how do you keep dhcp from interfering with a static ip setup.
is an ip outdside the allotted dhcp of the router(not set yet) really going to fix this?
every second or third time, the ip gets assigned by the dhcp even though the /etc/network/interfaces is
     Code:
     auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1


iface eth1 inet static
wireless-essid ______
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1


#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
wireless-essid ______
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1




auto eth1 

                                   #[**17**]("http://ubuntuforums.org/showpost.php?p=3477940&postcount=17")                                         [[IMG]http://ubuntuforums.org/images/uf/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=3477940")                                     
                                            [IMG]http://ubuntuforums.org/images/uf/statusicon/post_old.gif[/IMG]                              1 Day Ago                                                
                                                                                                                                                [holdie]("http://ubuntuforums.org/member.php?u=215997")                     [IMG]http://ubuntuforums.org/images/uf/statusicon/user_offline.gif[/IMG]                                                             
                                  Just Give Me the Beans!
                 [IMG]http://ubuntuforums.org/images/rank_2.png[/IMG]
                                                                                                                  Join Date: Dec 2006
                                            Beans: 45
                                                                            
                 
                                                         
  
                                                                                                    **Re: Static IP problems - eth1 not in network.config**             
                                                                                 by the way, I've found that when my computer boots, it automatically uses the DHCP address, however if I use the init.d restart, then it will start using static. I went to admin-sessions-startup processes to see if dhclient was there or something, but it's not...any ideas?
                                                               __________________
                             thanks 
buds
back to rute 
                                          [RIGHT]                                                                        [[IMG]http://ubuntuforums.org/images/uf/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=3477940")[/RIGHT]

---

### Post by SpiritIsReality on 2007-10-06
[choizy]("http://ubuntuforums.org/member.php?u=68026")                     [IMG]http://ubuntuforums.org/images/uf/statusicon/user_offline.gif[/IMG]                                                             
                                  Spilled the Beans
                 [IMG]http://ubuntuforums.org/images/rank_1.png[/IMG]
                                                                                                                  Join Date: Jan 2006
                                            Beans: 13
                                                                            
                 
                                                                                                                                                               **eth1 takes ip from local dhcp while defined as static**    
 				 				**eth1 takes ip from local dhcp while defined as static** 			
                    			 			 		 		 		 		This is my configuration in /etc/network/interfaces. As you can see I want eth1 to have a static IP. What realy happends is that it takes the last IP in the local dhcp server range. Not at once but im guessin at the same time eth0 renews its lease. How can I stop this from happening. (The dhcp server's range is 192.168.50.50 - 192.168.50.200).

iface eth0 inet dhcp
iface eth1 inet static
        address 192.168.50.10
        netmask 255.255.255.0


**EDIT: RESOLVED**

Case was resolved by checking for processes running dhclient and updating the interface

ps ax | grep dhclient

found severeal, used:

kill pid

The I restarted networking

/etc/init.d/networking restart
         
                                                                        [http://ubuntuforums.org/showthread.php?t=324129](http://ubuntuforums.org/showthread.php?t=324129)

---

