---
title: "SCP command hanging after completing file transfer"
date: 2021-02-20
forum: Networking &amp; Wireless
---

### Post by violetv16 on 2021-02-20
Hello all! I am trying to SCP a file from a machine running Ubuntu Server 20.04 to a windows 10 machine. My issue is that when SCP finishes transferring the file, it hangs and doesn't return the prompt until I press Ctrl+C. The file is successfully delivered to the destination. I've tried sending a file from the windows machine to the linux machine, and it works fine.

I've tried uninstalling and reinstalling openssh-client on the linux machine - no luck.

Running scp -vvv filename.txt [EMAIL="usr@hostname.com"]usr@hostname.com[/EMAIL]:/file/dest yields:

```

Executing: program /usr/bin/ssh host 192.168.0.213, user reid_, command scp -v -t C:/Users/reid_/Downloads
OpenSSH_8.2p1 Ubuntu-4ubuntu0.1, OpenSSL 1.1.1f  31 Mar 2020
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug2: resolve_canonicalize: hostname 192.168.0.213 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.168.0.213 [192.168.0.213] port 22.
debug1: Connection established.
debug1: identity file /home/eber/.ssh/id_rsa type -1
debug1: identity file /home/eber/.ssh/id_rsa-cert type -1
debug1: identity file /home/eber/.ssh/id_dsa type -1
debug1: identity file /home/eber/.ssh/id_dsa-cert type -1
debug1: identity file /home/eber/.ssh/id_ecdsa type 2
debug1: identity file /home/eber/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/eber/.ssh/id_ecdsa_sk type -1
debug1: identity file /home/eber/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /home/eber/.ssh/id_ed25519 type -1
debug1: identity file /home/eber/.ssh/id_ed25519-cert type -1
debug1: identity file /home/eber/.ssh/id_ed25519_sk type -1
debug1: identity file /home/eber/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /home/eber/.ssh/id_xmss type -1
debug1: identity file /home/eber/.ssh/id_xmss-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_for_Windows_8.1
debug1: match: OpenSSH_for_Windows_8.1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.0.213:22 as 'reid_'
debug3: hostkeys_foreach: reading file "/home/eber/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/eber/.ssh/known_hosts:4
debug3: load_hostkeys: loaded 1 keys from 192.168.0.213
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,sk-ecdsa-sha2-nistp256@openssh.com,ssh-ed25519,sk-ssh-ed25519@openssh.com,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos:
debug2: languages stoc:
debug2: first_kex_follows 0
debug2: reserved 0
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: rsa-sha2-512,rsa-sha2-256,ssh-rsa,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos:
debug2: languages stoc:
debug2: first_kex_follows 0
debug2: reserved 0
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:krsbzotBOrITkQclXuttTiwhQg+3T3uhlPBvzd/z8c4
debug3: hostkeys_foreach: reading file "/home/eber/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/eber/.ssh/known_hosts:4
debug3: load_hostkeys: loaded 1 keys from 192.168.0.213
debug1: Host '192.168.0.213' is known and matches the ECDSA host key.
debug1: Found key in /home/eber/.ssh/known_hosts:4
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey out after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey in after 134217728 blocks
debug1: Will attempt key: /home/eber/.ssh/id_rsa
debug1: Will attempt key: /home/eber/.ssh/id_dsa
debug1: Will attempt key: /home/eber/.ssh/id_ecdsa ECDSA SHA256:1hIbHjir112cziUNICNHOJrQ1dpDk06WUEvppLAyuSM
debug1: Will attempt key: /home/eber/.ssh/id_ecdsa_sk
debug1: Will attempt key: /home/eber/.ssh/id_ed25519
debug1: Will attempt key: /home/eber/.ssh/id_ed25519_sk
debug1: Will attempt key: /home/eber/.ssh/id_xmss
debug2: pubkey_prepare: done
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/eber/.ssh/id_rsa
debug3: no such identity: /home/eber/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/eber/.ssh/id_dsa
debug3: no such identity: /home/eber/.ssh/id_dsa: No such file or directory
debug1: Offering public key: /home/eber/.ssh/id_ecdsa ECDSA SHA256:1hIbHjir112cziUNICNHOJrQ1dpDk06WUEvppLAyuSM
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 60
debug1: Server accepts key: /home/eber/.ssh/id_ecdsa ECDSA SHA256:1hIbHjir112cziUNICNHOJrQ1dpDk06WUEvppLAyuSM
debug3: sign_and_send_pubkey: ECDSA SHA256:1hIbHjir112cziUNICNHOJrQ1dpDk06WUEvppLAyuSM
debug3: sign_and_send_pubkey: signing using ecdsa-sha2-nistp521 SHA256:1hIbHjir112cziUNICNHOJrQ1dpDk06WUEvppLAyuSM
debug3: send packet: type 50
debug3: receive packet: type 52
debug1: Authentication succeeded (publickey).
Authenticated to 192.168.0.213 ([192.168.0.213]:22).
debug2: fd 4 setting O_NONBLOCK
debug2: fd 5 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting no-more-sessions@openssh.com
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: network
debug3: receive packet: type 80
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug3: receive packet: type 91
debug2: channel_input_open_confirmation: channel 0: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: ssh_packet_set_tos: set IP_TOS 0x08
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug3: Ignored env SHELL
debug3: Ignored env PWD
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_SESSION_TYPE
debug3: Ignored env MOTD_SHOWN
debug3: Ignored env HOME
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: send packet: type 98
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_CONNECTION
debug3: Ignored env LESSCLOSE
debug3: Ignored env XDG_SESSION_CLASS
debug3: Ignored env TERM
debug3: Ignored env LESSOPEN
debug3: Ignored env USER
debug3: Ignored env SHLVL
debug3: Ignored env XDG_SESSION_ID
debug3: Ignored env XDG_RUNTIME_DIR
debug3: Ignored env SSH_CLIENT
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env PATH
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env SSH_TTY
debug3: Ignored env _
debug1: Sending command: scp -v -t C:/Users/reid_/Downloads
debug2: channel 0: request exec confirm 1
debug3: send packet: type 98
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: exec request accepted on channel 0
Sending file modes: C0664 10 test.txt
test.txt                                                                              100%   10     5.1KB/s   00:00
debug2: channel 0: read<=0 rfd 4 len 0
debug2: channel 0: read failed
debug2: channel 0: chan_shutdown_read (i0 o0 sock -1 wfd 4 efd 6 [write])
debug2: channel 0: input open -> drain
debug2: channel 0: ibuf empty
debug2: channel 0: send eof
debug3: send packet: type 96
debug2: channel 0: input drain -> closed

```

If more information is required please let me know! Thanks for the help it's greatly appreciated! Also I apologize if this is in the wrong location.

---

### Post by TheFu on 2021-02-20
How does it work between Linux machines?  If no issues, then it is a Windows problem. Check that scp implementation for bugs.
You can use 
```
$ scp -vvv filename.txt usr@localhost:/tmp/file
```

---

### Post by violetv16 on 2021-02-20
Sending a file to a Mac works flawlessly on the linux machine. 
I set my default ssh shell to the bash.exe inside the system32 folder on the Windows machine. Sending a file to the said linux machine with both Powershell and the bash terminal works fine.

---

### Post by violetv16 on 2021-02-20
Found out what was happening. 

I'm not sure why, but setting the bash.exe as my default ssh shell apparently wouldn't let scp disconnect after transferring the file.

Running this fixed my issue:

```
 New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force 
```

Anyone with some insight into why that happened would be much appreciated.

---

