---
title: ":: Lan Connection Proglem ::"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by mohsin on 2005-08-10
hello .. facing a problem which is meaning less 

       got 2 server .. 


 1 is ISA server 2003 its address is 192.168.0.1 8080

 2nd is LINUX base (squid) address is 192.168.0.3 8080


 my ip address is 192.168.0.101 (on window xp and suse i used this before)


 now i login to my UBUNTU account .. i did following .. 

    network proxies i give 192.168.0.1 or .3 
 
    network devices ..  eth0 .. give it manual proxies .. 

                            ip add . 192.168.0.101
                            subnet  255.255.255.0
                            gatway 192.168.0.1               or .3 should also work

   now when i ping to 192.168.0.1 it says destination host unreachable no net works
 when it gives ip to 192.168.0.1 (which is server ip how can i have it )

     then it pings .. ok .. net works for 5 to 10 min then again give error the proxy you have set is not connecting .. (mozilla) give this error .. 

         i think its too long ... now .. if any one is getting what a problem is then how can i solve this .. plz tell me .. but i only know .. my ip should be 101. gateway should be either .1 or .3 and when i ping it should work and when i give any of these 2 .1 or .3 in mozila net should work also but not the case :(  [-X

---

