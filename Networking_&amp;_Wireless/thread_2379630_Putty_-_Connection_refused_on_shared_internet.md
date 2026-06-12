---
title: "Putty - Connection refused on shared internet"
date: 2017-12-07
forum: Networking &amp; Wireless
---

### Post by makem2 on 2017-12-07
I am using xubuntu  16.04 and a raspberry pi running raspbian.

I have connected the pi the the linix pc with a cat5 cable, made a new ethernet connection  in Network Connections and set the IPv4 setting to Shared to other computers. The pi MAC address appears against the  Ethernet interface enp8so.

The pi is given an IP of 10.42.0.1, Broadcast Address: 10.42.0.255 and Subnet mask: 255.255.255.0

```

makem@ssdTOSH:~$ ifconfig
enp8s0    Link encap:Ethernet  HWaddr 2c:60:0c:8a:6e:27  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::57bb:f783:1f20:9441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29045 (29.0 KB)  TX bytes:172230 (172.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1554505 (1.5 MB)  TX bytes:1554505 (1.5 MB)


wlp7s0    Link encap:Ethernet  HWaddr 34:e6:ad:ba:1f:d0  
          inet addr:192.168.2.33  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c41e:abe2:6bb2:f9fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:335851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166795136 (166.7 MB)  TX bytes:104892755 (104.8 MB)


makem@ssdTOSH:~$

```

I can ping the pi from the pc but putty has a 'Connection Refused' error.

I think the cause is on the linux side.

I have uninstalled putty and removed .putty, reinstalled putty but get the same result. I have also re-flashed the sd card and tried with the newly installed putty - same result. The session log just repeats the error message.

Any pointers as to where to look for the reason this occurs would be appreciated.

EDIT: Installing [COLOR=#555555][FONT=Roboto]openssh-server has allowed putty to access the pi but now the pi will not accept the correct password![/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2017-12-07
Two ideas:
1) Your password might be correct, but is it for the right user ? I don't know about putty, but the command line ssh-client I use will try to connect with your current user name if you don't tell it as what user to connect, which will lead to the situation you describe if the user names are different on the two machines ,,,
2) Are you using login with passwords and are you trying to log in as root ? I recall openssh not liking that combination, you might have to login as a normal user or change the configuration of the ssh server or set up login with cryptographic keys.

Holger

---

### Post by makem2 on 2017-12-07
> **Holger_Gehrke said:**
> Two ideas:
1) Your password might be correct, but is it for the right user ? I don't know about putty, but the command line ssh-client I use will try to connect with your current user name if you don't tell it as what user to connect, which will lead to the situation you describe if the user names are different on the two machines ,,,
2) Are you using login with passwords and are you trying to log in as root ? I recall openssh not liking that combination, you might have to login as a normal user or change the configuration of the ssh server or set up login with cryptographic keys.

Holger

Thank you for your thoughts.

I am logging in as pi with putty when connected to the pi via my router. I also log in as pi to the pi vnc. Login name is pi@192.168.2.33 password accepted

I log in to the pic direct from my pc with putty as pi@10.42.0 1. password not accepted

I log in direct from the pc as ssh pi@10.42.0.1 password not accepted

Same user, same password.

I never log in as root.

I feel there is something silly which I am missing but can't see the wood for trees.

The domain name cannot be changed so pi it must be from wherever.

---

### Post by Holger_Gehrke on 2017-12-07
Check the ssh server configuration on the pi in'/etc/ssh/sshd_config'. It might be something stupid like an automatically set "ListenAddress" line. There should be a manual page 'man 5 sshd_config' on the pi.

Holger

---

### Post by makem2 on 2017-12-07
> **Holger_Gehrke said:**
> Check the ssh server configuration on the pi in'/etc/ssh/sshd_config'. It might be something stupid like an automatically set "ListenAddress" line. There should be a manual page 'man 5 sshd_config' on the pi.

Holger

I have checked that file and the only things not # out are:

ChallengeResponseAuthentification no
UsePAM yes
X11Forwarding yes
PrintMotd no
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server

Nothing related to listening.

I have read somewhere about a key file and I see an 'AuthorizedKeysFile .ssh/authorized_keys .ssh/authorized_keys2'  entry, again #. I was going to see what I can find about that.

There is a /etc/ssh/ssh_config which contains:

SendEnv LANG LC_*
HashKnownHosts yes
GSSAPIAuthentification yes

That looks promising. Nothing about listening. I found the man file for sshd_config but having seen the man for ssh_config I am now wondering which is being used.

The man file for ssh_config says that the default setting for HashKnownHosts is no

EDIT: I also read that GSSAPIAuthentification should not be allowed unless needed (creates attack surface)

---

### Post by makem2 on 2017-12-07
Created a public key for the pi, put it on the pi but still fails when asked for the pi@10.42.0.1's password.

Really stuck now :-(

---

### Post by makem2 on 2017-12-09
Corrected the key method and can log in.Thanks for the assistance.

---

