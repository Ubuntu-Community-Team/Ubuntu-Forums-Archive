---
title: "SSH, KLauncher, X11"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Fahuadai on 2007-05-15
I've successfully logged into my desktop from my laptop using: 

```
ssh -X 192.168.2.8
```

I can run everything as normal, but when i try to run kate, the terminal reports:

"X11 connection rejected because of wrong authentication
kdeinit: Fatal IO Error: client killed
kate: ERROR: couldn't create slave : cannot talk to klauncher
"

Kate then opens, with an error message: "Cannot talk to klauncher."

I can then use kate, but if i try to save a file on the remote computer, it shows a loading bar, which stays at 0%.

I tried manually entering an address and saving but nothing happens except in the terminal complaining again with the same message "kate: ERROR: couldn't create slave : cannot talk to klauncher"

my /etc/ssh/ssh_config: 
```

Host *
#   ForwardAgent no
 ForwardX11 yes
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
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

```

Any help appreciated. thanks in advance.

---

