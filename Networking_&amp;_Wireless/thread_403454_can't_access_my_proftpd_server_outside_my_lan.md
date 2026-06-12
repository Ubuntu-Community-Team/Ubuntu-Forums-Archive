---
title: "can't access my proftpd server outside my lan"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by vizenmaster on 2007-04-07
I had read many post how to access proftpd through nat, but it doesn't work for me. this is my proftpd.conf

ServerName			"FTP"
ServerType			standalone
DefaultServer			on
DefaultRoot ~
IdentLookups off
ServerIdent on "FTP Server ready."

Umask				022
MaxInstances			30
User				nobody
Group				nogroup

**MasqueradeAddress**		anything.myftp.org
Port				50000
AllowForeignAddress on
**PassivePorts** 50000 52000

AllowOverwrite off
AllowRetrieveRestart on

ScoreboardFile /var/run/proftpd.scoreboard
SystemLog /var/log/proftpd.sys
TransferLog /var/log/proftpd.xfer
ServerLog /var/log/proftpd.serv

<Limit SITE_CHMOD>
  DenyAll
</Limit>

<Limit LOGIN>
  DenyAll
  AllowUser andy
</Limit>

<Limit ALL>
DenyAll
</Limit>

<Limit CDUP CWD LIST PWD>
  AllowAll
</Limit>

<Directory /share>
  <Limit STOR STOU>
    Allowall
  </Limit>
</Directory>

#<Directory /home/ftp/pub>
#  <Limit READ>
#    AllowAll
#  </Limit>
#</Directory>


### Limit the maximum number of anonymous logins
#MaxClients			10
#
#<Anonymous /home/ftp>
#  <Limit LOGIN>
#    AllowAll
#  </Limit>
#
#  User			ftp
#  Group			ftp
#  RequireValidShell	off
#  UserAlias 		anonymous ftp
#</Anonymous>
I added MasqueradeAddress		anything.myftp.org
Port				50000
AllowForeignAddress on
PassivePorts 50000 52000
and forward this to my router
192.168.1.6     TCP 50000 -> 52000
                        UDP 50000 -> 52000
then i tried to access my server from my friend house as anything.myftp.org with port 50000 but it doesn't work. Please help me. I couldn't find any solution.

---

### Post by eentonig on 2007-04-07
Did you configure your router/ADSL modem to forward the external ftp connections to your ftp server on the LAN?

Do you try to connect to your public address? Or the 192.168.x.x address? (Stupid basic question, but I have to ask)

---

### Post by vizenmaster on 2007-04-07
> **eentonig said:**
> Did you configure your router/ADSL modem to forward the external ftp connections to your ftp server on the LAN?

Do you try to connect to your public address? Or the 192.168.x.x address? (Stupid basic question, but I have to ask)

it's worked now, i forward my external ip to local ip and it works. thanks a lot.

---

