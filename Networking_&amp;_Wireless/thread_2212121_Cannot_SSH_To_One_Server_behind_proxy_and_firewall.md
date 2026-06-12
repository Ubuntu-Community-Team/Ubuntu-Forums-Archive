---
title: "Cannot SSH To One Server behind proxy and firewall whereas able to access another one"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by blueelvisrocks on 2014-03-19
Hello there,

I am behind a firewall which restricts access to Internet and the only way we are allowed to access the Internet is via a proxy service via port 8080.
Now, I am using corkscrew and it is allowing me to tunnel to the Amazon EC2 via SSH and using the corkscrew but I am not able to tunnel to the DigitalOcean's server whereas from a non restrictive Internet I am able to access both of the servers. Can anyone help me in solving this?


Here is the log when ssh is running via the `-v` command :-
    
   >  ssh -vvv XXXX@XXXXX -p 443
    OpenSSH_6.5, OpenSSL 1.0.1f 6 Jan 2014
    debug1: Reading configuration data /etc/ssh_config
    debug1: /etc/ssh_config line 49: Applying options for *
    debug1: /etc/ssh_config line 53: Applying options for 128.199.203.97
    debug1: Executing proxy command: exec corkscrew proxy.ac.in 8080 1.199.203.97 443 /bin/.corkscrew-auth
    debug1: permanently_drop_suid: 1001
    debug3: Incorrect RSA1 identifier
    debug3: Could not load "/home/Blueelvis_RoXXX/.ssh/id_rsa" as a RSA1 public key
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_rsa type 1
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_rsa-cert type -1
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_dsa type -1
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_dsa-cert type -1
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_ecdsa type -1
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_ecdsa-cert type -1
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_ed25519 type -1
    debug1: identity file /home/Blueelvis_RoXXX/.ssh/id_ed25519-cert type -1
    debug1: Enabling compatibility mode for protocol 2.0
    debug1: Local version string SSH-2.0-OpenSSH_6.5
    Proxy could not open connnection to 1.99.203.97:  Proxy Authentication Required
    ssh_exchange_identification: Connection closed by remote host



Here is the ssh_config file as well as I am using corkscrew to tunnel through :-
> 
Host XX.199.203.97
User pranav
HostName XX.199.203.97
Port 443
ProxyCommand /bin/corkscrew proxy.ddn.upes.ac.in  8080 %h %p
IdentityFile /home/blueelvis_roxxx/id_rsa



On connecting to the Amazon EC2 via the same parameters, I am able to tunnel through it but not on this one. I do not get any Proxy Authentication Error Required when connecting to the Amazon Instance but I do get the error when I am connecting to the DigitalOcean server. Any idea what is happening and why?


I am running Cygwin on the Client side and the DigitalOcean Server is running Ubuntu 12.04 LTS whereas the Amazon EC2 is using Ubuntu 13.10. I even tried with 13.10 server of digitalocean but no luck :(

---

