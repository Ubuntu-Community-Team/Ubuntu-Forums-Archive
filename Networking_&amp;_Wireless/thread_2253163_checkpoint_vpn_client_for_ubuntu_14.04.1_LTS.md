---
title: "checkpoint vpn client for ubuntu 14.04.1 LTS"
date: 2014-11-17
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2014-11-17
Hi all, 

Does someone use checkpoint client for ubuntu 14.04.1 LTS ? 

[I]$ snx -s xxx.yyy.zzz.jjj -u user1 
Check Point's Linux SNX
build 800005013
Please enter your password:

SNX: Connection aborted.[/I]

My password is correct, because I use it also with checkpoint vpn client for windows and it works fine. 

Please help me to find way to connect via linux command line. 
Thanks ahead.

---

### Post by SeijiSensei on 2014-11-17
Can you have it log the connection attempt?  Is there a verbose mode ("-v")?

Perhaps the server's logs have some useful information?

---

### Post by marchello_lippi2 on 2014-11-18
> **SeijiSensei said:**
> Can you have it log the connection attempt?  Is there a verbose mode ("-v")?

That's all we've got: 

$ snx --help
Check Point's Linux SNX
build 800005013
usage: snx -s <server> {-u <user>|-c <certfile>} [-l <ca dir>] [-p <port>] [-r] [-g] [-e <cipher>]
                                run SNX using given arguments
       snx -f <cf>              run the snx using configuration file
       snx                      run the snx using the ~/.snxrc

       snx -d                   disconnect a running SNX daemon

        -s <server>           connect to server <server>
        -u <user>             use the username <user>
        -c <certfile>         use the certificate file <certfile>
        -l <ca dir>           get trusted ca's from <ca dir>
        -p <port>             connect using port <port>
        -g                    enable debugging
        -e <cipher>           SSL cipher to use: RC4 or 3DES


Tried with -g, but it didn't help much. 

> Perhaps the server's logs have some useful information? 

Unfortunately, I don't have an access to server's logs. 

Any other ideas?

---

