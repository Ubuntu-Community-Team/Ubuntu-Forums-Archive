---
title: "SSH keepalive"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by nephlim on 2007-11-26
Hey guys. I'm running Gutsy, with open ssh 1:4.6p1-5build1 installed. I like to use gnome-terminal to ssh to a bbs, but no matter how I configure the ssh_config in /home/user/.ssh or in /etc/ssh/ it still times out. I'm behind a netgeart wireless router (WTG624 v 3) that i'm CAT-5'd into. 

Here's a pasting of the configs:

/home/user/.ssh/ssh_config: 

"KeepAlive yes
ServerAliveInterval 5"

/etc/ssh/ssh_config:

"Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
    KeepAlive yes    
    ServerAliveInterval 5	"

Any help would be greatly appreciated. 

-Nephlim

---

### Post by nephlim on 2007-11-26
So, uh, yeah, I figured it out myself. Trick was that it needed *TCP*KeepAlive, not just KeepAlive by itself.

---

