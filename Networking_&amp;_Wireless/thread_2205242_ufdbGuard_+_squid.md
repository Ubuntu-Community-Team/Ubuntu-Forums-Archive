---
title: "ufdbGuard + squid"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by markeee on 2014-02-12
Hi - after gettubg stuck with squidGuard I switched to trying out ufdbGuard - compile from source..edited the config, and then blast..got anotyher error!!


root@dimension:/home/mark# /etc/init.d/ufdb start                                                                                                   
Starting URLfilterDB daemons OK                                                                                                                     
root@dimension:/home/mark# 2014-02-12 23:01:09 [25843] dropped privileges and became user 'ufdb
cannot bind daemon socket: Permission denied (protocol=UNIX) *****                                                                                  
check for and kill old daemon processes                                                                                                             
and remove UNIX socket file "/tmp/ufdbguardd-03977"                                                                                                 
                                                                                                                                                    
root@dimension:/home/mark#       

as per the docs on the site I have it running as user ufdb - but theb im getting the above,.there's no other instances of the daemon running and no udgbguard-03977 file in /tmp/

:(

---

### Post by markeee on 2014-02-19
bump..been a while anyone able to lend a hand with this? Ive googled and asked around and got nowhere!

---

