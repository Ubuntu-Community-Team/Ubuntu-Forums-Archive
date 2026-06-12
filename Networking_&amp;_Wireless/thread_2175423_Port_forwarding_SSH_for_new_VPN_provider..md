---
title: "Port forwarding SSH for new VPN provider."
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by Verax on 2013-09-19
I am experiencing trouble setting up port forwarding with Ubuntu 13.04 using OpenVPN to connect to servers through a new VPN provider.  I'm using several files that have been generated through the VPN service provider's setup configuration system.  

When I initiate the login script all is good until it stalls out at the end.  I've tried one or two other port numbers as replacements and the result is the same.   Really would like to resolve this with someone that can take me through step-by-step here and figure out how to port forward on Ubuntu. 

Here's the output I get when trying to connect to the host.   

 Is there something that needs to be included in the /etc/ssh/ssh_config for port forwarding?


SSH Tunnel
OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to XXX.XXX.XX.XXX [XXX.XX.XX.XXX] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: SELinux support disabled
debug1: identity file sshtunnel.key type -1
debug1: identity file sshtunnel.key-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-6+squeeze2
debug1: match: OpenSSH_5.5p1 Debian-6+squeeze2 pat OpenSSH_5*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.1p1 Debian-4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA  ee:ee:eb:ee:ee:ee:ee:ee:ee:ee:ee:ee:ee:ee:ee
The authenticity of host 'XXX.XX.XX.XXX (XXX.XX.XX.XXX)' can't be established.
RSA key fingerprint is ee:ee:eb:ee:ee:ee:ee:ee:ee:ee:ee:ee:eb:ee:ee
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'XXX.XX.XX.XXX' (RSA) to the list of known hosts.
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: sshtunnel.key
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
Authenticated to XXX.XX.XX.XXX([XXX.XX.XX.XXX]:22).
debug1: Local connections to LOCALHOST:1412 forwarded to remote address 127.0.0.1:2018
debug1: Local forwarding listening on ::1 port 1412.
bind: Address already in use
debug1: Local forwarding listening on 127.0.0.1 port 1412.
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 1412
Could not request local forwarding.
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: Remote: Pty allocation disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Forced command.


And I don't see anything listening on 1412 from the output above.  What am I missing here?

@hostname:/etc$ netstat -tulpn | grep :1412
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 127.0.1.1:1412          0.0.0.0:*               LISTEN      6245/ssh        
tcp        0      0 127.0.0.1:1412          0.0.0.0:*               LISTEN      3311/ssh        
tcp6       0      0 ::1:1412                :::*                    LISTEN      3311/ssh

---

