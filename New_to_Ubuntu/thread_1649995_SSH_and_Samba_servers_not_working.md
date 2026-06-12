---
title: "SSH and Samba servers not working"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2010-12-20
Hello Ubuntu Forums Community,

I have recently installed SSH and Samba servers on my desktop. I have 2 computers to connect to my good/newer desktop: 2 laptops, all of which have failed to connect to the good desktop. However, they (all except good desktop) can all connect to each other. Strangely, my good desktop can connect to all of the other computers (all computers have samba and ssh servers).

Also (I'm not sure if this is causing the problem), all computers don't have a /etc/init.d/samba file (found that I needed to run it to start the server).

Does anybody know why this is happening?
Thanks in advance.

---

### Post by cariboo on 2010-12-21
What is the output of:

```
ssh -v user@server
```

when trying to connect to the system that doesn't seem to work?

---

### Post by kroq-gar78 on 2010-12-26
sorry for the late response. Here is the output from my Toshiba laptop:

```
kroq-gar78@ubuntu:~$ ssh -v kroq-gar78@192.168.2.98
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.2.98 [192.168.2.98] port 22.
debug1: connect to address 192.168.2.98 port 22: Connection timed out
ssh: connect to host 192.168.2.98 port 22: Connection timed out
kroq-gar78@ubuntu:~$ 

```

---

### Post by Morbius1 on 2010-12-26
On the samba front:

(1) The samba service no longer exists in Ubuntu - it has been replaced but it's constituent daemons: smbd and nmbd.

(2) You'll get a warning if you try to start them from init.d because they're not SystemV jobs anymore they're Upstart jobs:

To reproduce the starting of the old "samba" service you need to do the following:
```
sudo service smbd start
``````
sudo service nmbd start
```

---

### Post by kroq-gar78 on 2010-12-26
it just says its already running for both

---

### Post by kroq-gar78 on 2011-04-24
epicly overdue bump.

this problem still isnt fixed for me...

---

### Post by kroq-gar78 on 2011-04-28
*bump*

---

### Post by crispy_420 on 2011-04-29
Wild shot but have you port scanned the "server" to see if the ports are listening? Or checked if the proper ports are listening?

[http://www.cyberciti.biz/faq/how-do-i-find-out-what-ports-are-listeningopen-on-my-linuxfreebsd-server/](http://www.cyberciti.biz/faq/how-do-i-find-out-what-ports-are-listeningopen-on-my-linuxfreebsd-server/)

---

### Post by kroq-gar78 on 2011-06-16
Sorry, I got a new laptop and kindof forgot about all of this stuff (i haven't been using this desktop for a few months...), but I finally booted up my desktop and ran te command netstat --listen. Sory if wrong command, I just ran the 1st one on the page that looked kinda correct.

Here's the output:
```
kroq-gar78@dell-ubuntu:~$ netstat --listen
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost.localdo:43088 *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 localhost.localdo:64022 *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost.localdo:54391 *:*                     LISTEN     
tcp        0      0 localhost.localdo:12311 *:*                     LISTEN     
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp        0      0 localhost.localdom:6968 *:*                     LISTEN     
tcp        0      0 localhost.localdom:6969 *:*                     LISTEN     
tcp        0      0 localhost.localdom:6970 *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 dell-ubuntu:ipp         [::]:*                  LISTEN     
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN     
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN     
udp        0      0 *:50144                 *:*                                
udp        0      0 dell-ubuntu:ntp         *:*                                
udp        0      0 localhost.localdoma:ntp *:*                                
udp        0      0 *:ntp                   *:*                                
udp        0      0 192.168.255.:netbios-ns *:*                                
udp        0      0 dell-ubuntu:netbios-ns  *:*                                
udp        0      0 192.168.255.:netbios-ns *:*                                
udp        0      0 192.168.255.:netbios-ns *:*                                
udp        0      0 192.168.2.25:netbios-ns *:*                                
udp        0      0 192.168.255.:netbios-ns *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.255:netbios-dgm *:*                                
udp        0      0 dell-ubuntu:netbios-dgm *:*                                
udp        0      0 192.168.255:netbios-dgm *:*                                
udp        0      0 192.168.255:netbios-dgm *:*                                
udp        0      0 192.168.2.2:netbios-dgm *:*                                
udp        0      0 192.168.255:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:mdns                  *:*                                
udp6       0      0 [::]:49780              [::]:*                             
udp6       0      0 dell-ubuntu:ntp         [::]:*                             
udp6       0      0 fe80::216:76ff:fed6:ntp [::]:*                             
udp6       0      0 [::]:ntp                [::]:*                             
udp6       0      0 [::]:mdns               [::]:*                             
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     9748     /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     6573     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     8540     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     8788     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     10150    @/tmp/gdm-greeter-deLmDvpZ
unix  2      [ ACC ]     STREAM     LISTENING     8789     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     9746     /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     9869     /var/run/apache2/cgisock.1699
unix  2      [ ACC ]     STREAM     LISTENING     11583    /tmp/ssh-RAwbKY2111/agent.2111
unix  2      [ ACC ]     STREAM     LISTENING     11587    /tmp/gpg-DaYk2P/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     11629    /tmp/.ICE-unix/2111
unix  2      [ ACC ]     STREAM     LISTENING     8344     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     11670    /tmp/orbit-kroq-gar78/linc-878-0-1a53bb6c71cc8
unix  2      [ ACC ]     STREAM     LISTENING     14344    /tmp/orbit-kroq-gar78/linc-92d-0-2cb1f9b2524ad
unix  2      [ ACC ]     STREAM     LISTENING     11628    @/tmp/.ICE-unix/2111
unix  2      [ ACC ]     STREAM     LISTENING     17666    /tmp/orbit-kroq-gar78/linc-c05-0-661387c73e35
unix  2      [ ACC ]     STREAM     LISTENING     8861     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     11329    /tmp/keyring-QP7fgD/control
unix  2      [ ACC ]     STREAM     LISTENING     12030    /tmp/orbit-kroq-gar78/linc-83f-0-5f44bae47e9db
unix  2      [ ACC ]     STREAM     LISTENING     12263    /tmp/orbit-kroq-gar78/linc-87c-0-70547ad8e133d
unix  2      [ ACC ]     STREAM     LISTENING     14461    /tmp/orbit-kroq-gar78/linc-941-0-582db3d55e3f5
unix  2      [ ACC ]     STREAM     LISTENING     12284    /tmp/keyring-QP7fgD/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     12288    /tmp/keyring-QP7fgD/ssh
unix  2      [ ACC ]     STREAM     LISTENING     12337    /tmp/orbit-kroq-gar78/linc-885-0-74a6870142856
unix  2      [ ACC ]     STREAM     LISTENING     12420    /tmp/orbit-kroq-gar78/linc-893-0-b9d17ea6967
unix  2      [ ACC ]     STREAM     LISTENING     13536    /tmp/orbit-kroq-gar78/linc-8e1-0-19501b986845f
unix  2      [ ACC ]     STREAM     LISTENING     10290    @/tmp/gdm-session-vkWpbHzS
unix  2      [ ACC ]     STREAM     LISTENING     12863    /tmp/orbit-kroq-gar78/linc-8b8-0-72a5907cb067
unix  2      [ ACC ]     STREAM     LISTENING     13009    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     13075    /home/kroq-gar78/.pulse/4d6c7395f47068acb843eaac4c7864ed-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     13130    /tmp/orbit-kroq-gar78/linc-8cd-0-6f9b97ff6da15
unix  2      [ ACC ]     STREAM     LISTENING     13662    /tmp/orbit-kroq-gar78/linc-8c8-0-656fb8b53dec9
unix  2      [ ACC ]     STREAM     LISTENING     13674    /tmp/orbit-kroq-gar78/linc-8c2-0-4f1b1f853ddc
unix  2      [ ACC ]     STREAM     LISTENING     13676    /tmp/orbit-kroq-gar78/linc-8c5-0-3ed0547d53ee8
unix  2      [ ACC ]     STREAM     LISTENING     8887     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     14826    /tmp/orbit-kroq-gar78/linc-938-0-6577500517281
unix  2      [ ACC ]     STREAM     LISTENING     13988    /tmp/orbit-kroq-gar78/linc-895-0-62953ffeb82f7
unix  2      [ ACC ]     STREAM     LISTENING     13992    /tmp/orbit-kroq-gar78/linc-8c7-0-4baa2895e5d0e
unix  2      [ ACC ]     STREAM     LISTENING     14002    /tmp/orbit-kroq-gar78/linc-8e2-0-7db949166c99f
unix  2      [ ACC ]     STREAM     LISTENING     15257    /tmp/orbit-kroq-gar78/linc-98c-0-256d6073a9e3c
unix  2      [ ACC ]     STREAM     LISTENING     15260    /tmp/orbit-kroq-gar78/linc-989-0-372760e4a9efa
unix  2      [ ACC ]     STREAM     LISTENING     15263    /tmp/orbit-kroq-gar78/linc-98b-0-213bf7a9aa048
unix  2      [ ACC ]     STREAM     LISTENING     15269    /tmp/orbit-kroq-gar78/linc-98d-0-5683aa02aa16a
unix  2      [ ACC ]     STREAM     LISTENING     15273    /tmp/orbit-kroq-gar78/linc-982-0-67238e8baa2d0
unix  2      [ ACC ]     STREAM     LISTENING     15279    /tmp/orbit-kroq-gar78/linc-986-0-550e6814aa41f
unix  2      [ ACC ]     STREAM     LISTENING     15381    /tmp/orbit-kroq-gar78/linc-988-0-6b7b3061bb573
unix  2      [ ACC ]     STREAM     LISTENING     15566    /tmp/orbit-kroq-gar78/linc-9ab-0-330cfeacb60d4
unix  2      [ ACC ]     STREAM     LISTENING     15568    /tmp/orbit-kroq-gar78/linc-9ae-0-2c974575b6158
unix  2      [ ACC ]     STREAM     LISTENING     15763    /tmp/orbit-kroq-gar78/linc-9b6-0-78270b359a5a8
unix  2      [ ACC ]     STREAM     LISTENING     16089    /tmp/orbit-kroq-gar78/linc-9bb-0-1ed22e5b5a1f1
unix  2      [ ACC ]     STREAM     LISTENING     16288    /tmp/orbit-kroq-gar78/linc-a29-0-77a3a4a852a47
unix  2      [ ACC ]     STREAM     LISTENING     29030    /tmp/orbit-kroq-gar78/linc-1cc5-0-a94f37532ea3
unix  2      [ ACC ]     STREAM     LISTENING     35111    /tmp/orbit-kroq-gar78/linc-23ce-0-3cf135598491f
unix  2      [ ACC ]     STREAM     LISTENING     35182    /tmp/orbit-kroq-gar78/linc-23d6-0-69bde48aa135
unix  2      [ ACC ]     STREAM     LISTENING     19933    /tmp/orbit-kroq-gar78/linc-dec-0-7e7daf06e83b2
unix  2      [ ACC ]     STREAM     LISTENING     37340    /tmp/orbit-kroq-gar78/linc-259e-0-662f69cd2c7cd
unix  2      [ ACC ]     STREAM     LISTENING     37423    /tmp/gnome-system-monitor.kroq-gar78.3130144881
unix  2      [ ACC ]     STREAM     LISTENING     37439    /tmp/orbit-kroq-gar78/linc-25d6-0-44764ca2ea919
unix  2      [ ACC ]     STREAM     LISTENING     11600    @/tmp/dbus-EgjpkfSFBi
kroq-gar78@dell-ubuntu:~$ 

```

Sorry, I'm not sure what this really means, but there's the output. I ran netstat --listen.

---

