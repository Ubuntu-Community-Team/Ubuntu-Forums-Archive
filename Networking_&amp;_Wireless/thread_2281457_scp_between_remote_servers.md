---
title: "scp between remote servers"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by zkab on 2015-06-07
I want to make a 'scp' from my workstation to remote transfer from server 'tv-server' -> 'farbaute'.
I give the password - when asked - but get 'exit 1' at the end.
Also an error message 'read_passphrase: can't open /dev/tty: No such device or address'
My /dev/tty looks like:
raivo@zkab:~$ ls -la /dev/tty
crw-rw-rw- 1 root tty 5, 0 jun  7 12:26 /dev/tty
Where is the problem?

raivo@zkab:~/my_scripts$ sudo scp -rv  rajan@tv-server:/etc/oscam-svn/*          jurka@farbaute:/home/jurka/my_data/BackUp/TV/Oscam
Executing: /usr/bin/ssh '-x' '-oClearAllForwardings=yes' '-n' '-v' '-l' 'rajan' '--' 'tv-server' 'scp -v -r' '/etc/oscam-svn/*' 'jurka@farbaute:/home/jurka/my_data/BackUp/TV/Oscam'
OpenSSH_6.7p1 Ubuntu-5ubuntu1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to tv-server [192.168.0.15] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: match: OpenSSH_6.7p1 Ubuntu-5ubuntu1 pat OpenSSH* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: kex: client->server aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 4a:df:19:b0:cf:75:cc:e7:5a:86:63:19:9b:d3:17:83
debug1: Host 'tv-server' is known and matches the ECDSA host key.
debug1: Found key in /root/.ssh/known_hosts:3
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Trying private key: /root/.ssh/id_ed25519
debug1: Next authentication method: password
rajan@tv-server's password: 
debug1: Authentication succeeded (password).
Authenticated to tv-server ([192.168.0.15]:22).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LC_PAPER = sv_SE.UTF-8
debug1: Sending env LC_ADDRESS = sv_SE.UTF-8
debug1: Sending env LC_MONETARY = sv_SE.UTF-8
debug1: Sending env LC_NUMERIC = sv_SE.UTF-8
debug1: Sending env LC_TELEPHONE = sv_SE.UTF-8
debug1: Sending env LC_IDENTIFICATION = sv_SE.UTF-8
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending env LC_MEASUREMENT = sv_SE.UTF-8
debug1: Sending env LC_TIME = sv_SE.UTF-8
debug1: Sending env LC_NAME = sv_SE.UTF-8
debug1: Sending command: scp -v -r /etc/oscam-svn/* jurka@farbaute:/home/jurka/my_data/BackUp/TV/Oscam
Executing: program /usr/bin/ssh host farbaute, user jurka, command scp -v -r -d -t /home/jurka/my_data/BackUp/TV/Oscam
OpenSSH_6.7p1 Ubuntu-5ubuntu1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to farbaute [192.168.0.32] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: kex: client->server aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: Server host key: ECDSA 76:ec:52:16:6e:bb:bb:35:31:c2:67:45:75:4e:67:18
debug1: read_passphrase: can't open /dev/tty: No such device or address
Host key verification failed.
lost connection
debug1: channel 0: free: client-session, nchannels 1
Transferred: sent 3116, received 4148 bytes, in 0.2 seconds
Bytes per second: sent 12550.6, received 16707.3
debug1: Exit status 1
raivo@zkab:~/my_scripts$

---

### Post by Lars Noodén on 2015-06-07
sudo is not needed for scp.  So it should be avoided because it is run as root.  In addition to all the other reasons, running as root will prevent scp from accessing your own account's keys and agent.  Can you get the same error when copying without sudo?

If the two remote hosts cannot connect to each other directly, then you might need to go via the local host using the [-3 option](http://manpages.ubuntu.com/manpages/trusty/en/man1/scp.1.html).  Though that will slow things down.

---

### Post by zkab on 2015-06-07
Get the same 'exit 1' without sudo.
The remote hosts are on the same LAN and I can connect via ssh & passwd ... 'tv-server -> farbaute' and 'farbaute -> tv-server'

raivo@zkab:~/my_scripts$ scp -rv  rajan@tv-server:/etc/oscam-svn/*          jurka@farbaute:/home/jurka/my_data/BackUp/TV/Oscam
Executing: /usr/bin/ssh '-x' '-oClearAllForwardings=yes' '-n' '-v' '-l' 'rajan' '--' 'tv-server' 'scp -v -r' '/etc/oscam-svn/*' 'jurka@farbaute:/home/jurka/my_data/BackUp/TV/Oscam'
OpenSSH_6.7p1 Ubuntu-5ubuntu1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to tv-server [192.168.0.15] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/raivo/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: match: OpenSSH_6.7p1 Ubuntu-5ubuntu1 pat OpenSSH* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: kex: client->server aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 4a:df:19:b0:cf:75:cc:e7:5a:86:63:19:9b:d3:17:83
debug1: Host 'tv-server' is known and matches the ECDSA host key.
debug1: Found key in /home/raivo/.ssh/known_hosts:4
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/raivo/.ssh/id_rsa
debug1: Trying private key: /home/raivo/.ssh/id_dsa
debug1: Trying private key: /home/raivo/.ssh/id_ecdsa
debug1: Trying private key: /home/raivo/.ssh/id_ed25519
debug1: Next authentication method: password
rajan@tv-server's password: 
debug1: Authentication succeeded (password).
Authenticated to tv-server ([192.168.0.15]:22).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LC_PAPER = sv_SE.UTF-8
debug1: Sending env LC_ADDRESS = sv_SE.UTF-8
debug1: Sending env LC_MONETARY = sv_SE.UTF-8
debug1: Sending env LC_NUMERIC = sv_SE.UTF-8
debug1: Sending env LC_TELEPHONE = sv_SE.UTF-8
debug1: Sending env LC_IDENTIFICATION = sv_SE.UTF-8
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending env LC_MEASUREMENT = sv_SE.UTF-8
debug1: Sending env LC_TIME = sv_SE.UTF-8
debug1: Sending env LC_NAME = sv_SE.UTF-8
debug1: Sending command: scp -v -r /etc/oscam-svn/* jurka@farbaute:/home/jurka/my_data/BackUp/TV/Oscam
Executing: program /usr/bin/ssh host farbaute, user jurka, command scp -v -r -d -t /home/jurka/my_data/BackUp/TV/Oscam
OpenSSH_6.7p1 Ubuntu-5ubuntu1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to farbaute [192.168.0.32] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rajan/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: kex: client->server aes128-ctr [email]umac-64-etm@openssh.com[/email] none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: Server host key: ECDSA 76:ec:52:16:6e:bb:bb:35:31:c2:67:45:75:4e:67:18
debug1: read_passphrase: can't open /dev/tty: No such device or address
Host key verification failed.
lost connection
debug1: channel 0: free: client-session, nchannels 1
Transferred: sent 3116, received 4108 bytes, in 0.2 seconds
Bytes per second: sent 13499.6, received 17797.3
debug1: Exit status 1

---

### Post by SeijiSensei on 2015-06-07
Why not just open a shell on one machine with SSH and use scp to copy to the other one?

---

### Post by Lars Noodén on 2015-06-07
> **zkab said:**
> Get the same 'exit 1' without sudo.
The remote hosts are on the same LAN and I can connect via ssh & passwd ... 'tv-server -> farbaute' and 'farbaute -> tv-server'

raivo@zkab:~/my_scripts$ scp -rv  rajan@tv-server:/etc/oscam-svn/*          jurka@farbaute:/home/jurka/my_data/BackUp/TV/Oscam
...

I'm able to get the same kind of error here trying to transfer between two other machines.

```

scp lars@host2:file.csv lars@host3:.
lars@host2's password: 
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password,keyboard-interactive).
lost connection


```

The error occurs whether I am trying to use keys or not.  It also occurs on a more recent version of OpenSSH (OpenSSH_6.8, LibreSSL 2.2), not just the one in 14.04 LTS, for all three machines.  If you file a bug report, post the link and I can add "me, too" to it.

---

### Post by zkab on 2015-06-08
> **SeijiSensei said:**
> Why not just open a shell on one machine with SSH and use scp to copy to the other one?

I have a bunch of remote server.
My idea was to create a script that took care of the copy for all of them - instead of SSH to every machine.

---

### Post by SeijiSensei on 2015-06-08
Something like this maybe:
```

#!/bin/sh

SERVERS="server1 server2 ..."
DEST="destination"

for S in $SERVERS
do
    ssh $S "rsync -av / $DEST:/path/to/backup/$S"
done

```
That uses SSH to run the remote command on each server and back up the files to a server-specific directory on $DEST.  You'd need keys to make this work automatically of course, and probably some options to rsync like --exclude-from listing directories like /proc and /sys.

---

### Post by zkab on 2015-06-14
I made a script according to your recommendation and I tested with only one server "fe-sovis"
My script looks like this:

raivo@zkab:~/my_scripts$ cat test.sh 
#!/bin/sh

#SERVERS="fe-sovis fe-lisanne fe-ilmar fe-guest fe-gille"
SERVERS="fe-sovis"
DEST="jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi"
FROM_SUB_1="/home/rajan/.kodi"
FROM_SUB_2="/home/rajan/my_scripts"

for S in $SERVERS
do
#    ssh $L "rsync -av / $DEST/$S"
echo "rajan@$S rsync -av $FROM_SUB_1   $DEST/$S"
#ssh "rajan@$S rsync -av $FROM_SUB_1   $DEST/$S"
#ssh "rajan@$S rsync -av $FROM_SUB_2   $DEST/$S"
done

1) It gave me correct parameters:
raivo@zkab:~/my_scripts$ ./test.sh
rajan@fe-sovis rsync -av /home/rajan/.kodi   jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi/fe-sovis

2) When I uncommented the first ssh line (ssh "rajan@$S rsync -av $FROM_SUB_1   $DEST/$S") I got:
raivo@zkab:~/my_scripts$ ./test.sh 
rajan@fe-sovis rsync -av /home/rajan/.kodi   jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi/fe-sovis
ssh: Could not resolve hostname 192.168.0.32:/home/jurka/my_data/backup/tv/kodi/fe-sovis: Name or service not known

3) When I entered the command that the scripts was supposed to give me in a command window ... then I got this:
raivo@zkab:~/my_scripts$ ssh rajan@fe-sovis rsync -av /home/rajan/.kodi   jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi/fe-sovis
rajan@fe-sovis's password: 
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(226) [sender=3.1.1]


Don't see what is wrong ...

---

### Post by Lars Noodén on 2015-06-14
Have you tried [forcing pseudo-tty allocation](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html) for the initial connection?

```

ssh **-t** rajan@fe-sovis rsync -av /home/rajan/.kodi/ jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi/fe-sovis/

```

Also, directories usually need to be followed with a slash to get the right effect.

---

### Post by zkab on 2015-06-15
> **Lars Noodén said:**
> 
```

ssh **-t** rajan@fe-sovis rsync -av /home/rajan/.kodi/ jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi/fe-sovis/

```


The forcing pseudo-tty allocation worked OK but running the script gives me a resolve error:

raivo@zkab:~$ test.sh 
ssh: Could not resolve hostname 192.168.0.32:/home/jurka/my_data/backup/tv/kodi/fe-sovis: Name or service not known

raivo@zkab:~$ cat my_scripts/test.sh 
#!/bin/sh

#SERVERS="fe-sovis fe-lisanne fe-ilmar fe-guest fe-gille"
SERVERS="fe-sovis"
DEST="jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi"
FROM_SUB_1="/home/rajan/.kodi"
FROM_SUB_2="/home/rajan/my_scripts"

for S in $SERVERS
do
#echo "rajan@$S rsync -av $FROM_SUB_1   $DEST/$S"
ssh " -t rajan@$S rsync -av $FROM_SUB_1   $DEST/$S"
#ssh "rajan@$S rsync -av $FROM_SUB_2   $DEST/$S"
done

---

### Post by Lars Noodén on 2015-06-15
It may be that the quotation marks are in the wrong places in the script above, the following should work:

```

#!/bin/sh

#SERVERS="fe-sovis fe-lisanne fe-ilmar fe-guest fe-gille"
SERVERS="fe-sovis"
DEST="jurka@192.168.0.32:/home/jurka/my_data/BackUp/TV/Kodi"
FROM_SUB_1="/home/rajan/.kodi"
FROM_SUB_2="/home/rajan/my_scripts"

for S in $SERVERS
do
 ssh -t "rajan@$S" rsync -av "$FROM_SUB_1"  "$DEST/$S"
done
```

---

### Post by zkab on 2015-06-15
Thanks - now it works OK

---

### Post by Lars Noodén on 2015-06-15
Great.  Just to tidy up loose ends, if you can still reproduce the bug with scp you described at first, then you might add your "me, too" for this bug:

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1462758](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1462758)

I wasn't able to get scp to copy between two hosts either, either directly or with the -3 option.

---

