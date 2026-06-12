---
title: "cups encryption error"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by UltraMathMan on 2007-03-05
I'm setting up a cups print server in which the lpd protocol is used. I've added printers via the web interface and can print to them from the server. I've then added the printers on the OS X clients so that they point to the server (lpd://server/queue) and opened port 515 (the lpd port) on the server.

When I try to print (test page via cups web interface)on the clients the printer stops and  I get the error: ```
"The process "lpd" stopped unexpectedly with status 1" 
``` and in /var/log/cups/error_log it says ```
D [12/Mar/2007:15:14:48 -0400] cupsdCloseClient: 9
D [12/Mar/2007:15:18:28 -0400] cupsdAcceptClient: 9 from 192.222.19.228:515 (IPv4)
I [12/Mar/2007:15:18:28 -0400] Generating SSL server key...
I [12/Mar/2007:15:18:35 -0400] Created SSL server key file "/etc/cups/ssl/server.key"...
I [12/Mar/2007:15:18:35 -0400] Generating self-signed SSL certificate...
I [12/Mar/2007:15:18:36 -0400] Created SSL server certificate file "/etc/cups/ssl/server.crt"...
E [12/Mar/2007:15:18:36 -0400] encrypt_client: Unable to encrypt connection from 192.222.19.228!
E [12/Mar/2007:15:18:36 -0400] encrypt_client: A record packet with illegal version was received.
E [12/Mar/2007:15:18:36 -0400] Bad request line "chter" from 192.222.19.228!
D [12/Mar/2007:15:18:36 -0400] cupsdSendError: 9 code=400 (Bad Request)


```

Note that 192.222.19.228 is the client IP and "chter" is probably part of the printer name "Schachter-1", so I know the connection is going through. I tried searching and found [**_this thread_**]("http://ubuntuforums.org/showthread.php?t=176958") however cupsys conflicts with lprng (aptitude wants to remove ubuntu-desktop when I try to install it) and I would really rather not manually enter the entire dhcp ip range for the 130+ computers on the network. 

Any help would be apprieciated!

---

### Post by UltraMathMan on 2007-03-12
::bump::

---

### Post by UltraMathMan on 2007-03-13
I'm thinking this might have something to go with ssl, I've specified Encryption Never in the cupsd.conf file, with no success. I also have xinetd running with the cup-lpd mini daemon running, but this hasn't changed anything either. The OS X clients print no problem through ipp, but I'd rather not have to change the config on all of them to go that route. It just seems odd that lpd is giving me so much trouble...:confused:

UPDATE:

Tried adding SSLPort 443 to /etc/cups/cupsd.conf and got the following in error_log ```
D [13/Mar/2007:16:06:13 -0400] cupsdAcceptClient: 11 from localhost:443 (IPv4)
E [13/Mar/2007:16:06:14 -0400] encrypt_client: Unable to encrypt connection from localhost!
E [13/Mar/2007:16:06:14 -0400] encrypt_client: A TLS packet with unexpected length was received.
D [13/Mar/2007:16:06:14 -0400] cupsdCloseClient: 11
D [13/Mar/2007:16:06:14 -0400] cupsdAcceptClient: 11 from localhost:631 (IPv4)
D [13/Mar/2007:16:06:14 -0400] cupsdCloseClient: 11
D [13/Mar/2007:16:06:14 -0400] cupsdAcceptClient: 11 from localhost:515 (IPv4)
D [13/Mar/2007:16:06:14 -0400] cupsdCloseClient: 11
D [13/Mar/2007:16:06:20 -0400] cupsdAcceptClient: 11 from 192.222.19.228:515 (IPv4)
E [13/Mar/2007:16:06:20 -0400] encrypt_client: Unable to encrypt connection from 192.222.19.228!
E [13/Mar/2007:16:06:20 -0400] encrypt_client: A record packet with illegal version was received.
E [13/Mar/2007:16:06:20 -0400] Bad request line "chter" from 192.222.19.228!
D [13/Mar/2007:16:06:20 -0400] cupsdSendError: 11 code=400 (Bad Request)
D [13/Mar/2007:16:06:20 -0400] cupsdCloseClient: 11
```

NOTE: Port 443 is open on the server.

UPDATE 2:
Removed Encryption Never and Authtype None from <location> and readded DefaultAuthType Basic and no longer get errors about localhost encryption problems. Still get same error when I try to print from client. cupsd.conf on first post is most recent changes

---

### Post by UltraMathMan on 2007-03-21
Ok, I think I narrowed down the problem a bit, it seems that cups-lpd isn't running. I have xinetd installed and running with ```
service printer
{
        socket_type = stream
        protocol = tcp
        wait = no
        user = lp
        only_from = 192.222.0.0
        server = /usr/lib/cups/daemon/cups-lpd
}

``` in /etc/xinetd.d/printer as per [CUPS SAM]("http://www.cups.org/doc-1.1/sam.html#8_2"). When I run xinetd -d in the terminal I get ```
Service configuration: printer
        id = printer
        flags = IPv4
        socket_type = stream
        Protocol (name,number) = (tcp,6)
        port = 515
        wait = no
        user = 7
        Groups = no
        PER_SOURCE = -1
        Bind = All addresses.
        Server = /usr/lib/cups/daemon/cups-lpd
        Server argv = cups-lpd
        Only from:  192.222.0.0(NUMERIC)
        No access: No blocked sites
        No logging

07/3/21@14:32:39: ERROR: 15461 {activate_normal} bind failed (Permission denied (errno = 13)). service = printer
07/3/21@14:32:39: ERROR: 15461 {cnf_start_services} Service printer failed to start and is deactivated.
07/3/21@14:32:39: DEBUG: 15461 {cnf_start_services} mask_max = 0, services_started = 0
07/3/21@14:32:39: CRITICAL: 15461 {init_services} no services. Exiting...

``` so any ideas on how to get cups-lpd and xinetd running? Thanks.

---

### Post by UltraMathMan on 2007-03-22
...And here's where I feel silly, I was messing with xinetd and cups-lpd on my laptop (not the print server) and realized I was getting those errors when I ran xinetd -d because I should have been running ***sudo*** xinetd -d. Will try the print server again and report back. :oops:

---

### Post by UltraMathMan on 2007-03-29
I FINALLY got rid of the encryption error. I ended up building the latest versions of openssl and CUPS from source with the ```
./configure --enable-ssl \
        --with-openssl-includes=/path to include \
        --with-openssl-libs=/path to libs
``` directive for CUPS. Now I'm down to ```
Bad request line "^BSchachter" from 192.222.19.178!
cupsdSendError: 12 code=400 (Bad Request)
```

Opened a new thread for this problem see: [here]("http://ubuntuforums.org/showthread.php?t=397368").

---

### Post by UltraMathMan on 2007-05-17
Everything finally resolved see HOWTO I wrote [in this thread]("http://ubuntuforums.org/showthread.php?p=2674183#post2674183") for help.

---

