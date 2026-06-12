---
title: "Need an expert to check if I have illegal activity on my network please"
date: 2016-05-05
forum: Networking &amp; Wireless
---

### Post by james223 on 2016-05-05
TOTAL linux noob .. but I believe I have some bad stuff going on .. please advise..

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 mynametoo:domain        *:*                     LISTEN     
tcp        0      0 *:8200                  *:*                     LISTEN     
tcp        1      0 mynametoo:52766         ec2-54-214-43-32.:https CLOSE_WAIT 
tcp        1      0 mynametoo:35946         64.91.226.82:http       CLOSE_WAIT 
tcp        0      0 mynametoo:49960         a172-231-56-110.d:https CLOSE_WAIT 
tcp        0      0 mynametoo:35958         64.91.226.82:http       ESTABLISHED
tcp        0      0 mynametoo:51844         198.41.214.162:https    ESTABLISHED
tcp        0      0 mynametoo:43946         198.41.215.67:http      TIME_WAIT  
tcp        0      0 mynametoo:42616         198.70.245.229:https    ESTABLISHED
tcp        0      0 mynametoo:39388         198.70.245.218:http     ESTABLISHED
tcp        0      0 mynametoo:36292         kul06s07-in-f3.1e:https ESTABLISHED
tcp        0      0 mynametoo:43948         198.41.215.67:http      TIME_WAIT  
tcp        1      0 mynametoo:44280         ocsp.comodoca.com:http  CLOSE_WAIT 
tcp        0      0 mynametoo:56074         198.70.245.223:https    ESTABLISHED
tcp        0      0 mynametoo:39372         198.70.245.218:http     TIME_WAIT  
tcp        0      0 mynametoo:56406         93.184.216.116:https    ESTABLISHED
tcp        1      0 mynametoo:38014         ec2-54-245-119-25:https CLOSE_WAIT 
tcp        0      0 mynametoo:35956         64.91.226.82:http       ESTABLISHED
tcp        1      0 mynametoo:35954         64.91.226.82:http       CLOSE_WAIT 
tcp        0      0 mynametoo:33730         72.21.91.8:https        ESTABLISHED
tcp        0      0 mynametoo:56078         198.70.245.223:https    ESTABLISHED
tcp        0      0 mynametoo:46376         server-205-251-21:https ESTABLISHED
tcp        0      0 mynametoo:38770         198.70.67.101:https     ESTABLISHED
tcp        0      0 mynametoo:40232         nuq04s18-in-f2.1e:https ESTABLISHED
tcp        1      0 mynametoo:35952         64.91.226.82:http       CLOSE_WAIT 
tcp        1      0 mynametoo:35950         64.91.226.82:http       CLOSE_WAIT 
tcp        0      0 mynametoo:60106         198.41.215.66:https     ESTABLISHED
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 239.255.255.250:1900    *:*                                
udp        0      0 mynametoo:51742         *:*                                
udp        0      0 *:51849                 *:*                                
udp        0      0 mynametoo:domain        *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:ipp                   *:*                                
udp6       0      0 [::]:mdns               [::]:*                             
udp6       0      0 [::]:44123              [::]:*                             
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7
```

Heres the whole thing...

```
john@mynametoo:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 mynametoo:domain        *:*                     LISTEN     
tcp        0      0 *:8200                  *:*                     LISTEN     
tcp        0      0 mynametoo:38324         198.70.245.218:https    ESTABLISHED
tcp        0      0 mynametoo:57622         198.70.245.249:http     ESTABLISHED
tcp        1      0 mynametoo:36836         feijoa.canonical.c:http CLOSE_WAIT 
tcp        1      0 mynametoo:36832         feijoa.canonical.c:http CLOSE_WAIT 
tcp        1      0 mynametoo:36828         feijoa.canonical.c:http CLOSE_WAIT 
tcp        1      0 mynametoo:36838         feijoa.canonical.c:http CLOSE_WAIT 
tcp        0      0 mynametoo:56158         edge-star-mini-sh:https ESTABLISHED
tcp        0      0 mynametoo:58814         198.70.245.238:https    ESTABLISHED
tcp        0      0 mynametoo:56428         198.70.245.223:https    ESTABLISHED
tcp        0      0 mynametoo:56074         198.70.245.223:https    ESTABLISHED
tcp        1      0 mynametoo:36834         feijoa.canonical.c:http CLOSE_WAIT 
tcp        0      0 mynametoo:56078         198.70.245.223:https    ESTABLISHED
tcp        0      0 mynametoo:54854         198.70.245.245:https    ESTABLISHED
tcp        0      0 mynametoo:56236         xx-fbcdn-shv-01-sj:http ESTABLISHED
tcp        0      0 mynametoo:49866         sfo07s13-in-f5.1e:https ESTABLISHED
tcp        0      0 mynametoo:58912         198.70.245.216:https    ESTABLISHED
tcp        0      0 mynametoo:54880         198.70.245.245:https    TIME_WAIT  
tcp        0      0 mynametoo:36430         xx-fbcdn-shv-01-l:https ESTABLISHED
tcp        0      0 mynametoo:56238         xx-fbcdn-shv-01-sj:http ESTABLISHED
tcp        0      0 mynametoo:56416         198.70.245.223:https    ESTABLISHED
tcp      339      0 mynametoo:42358         xx-fbcdn-shv-01-s:https ESTABLISHED
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 239.255.255.250:1900    *:*                                
udp        0      0 *:51849                 *:*                                
udp        0      0 mynametoo:domain        *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 mynametoo:49545         *:*                                
udp        0      0 mynametoo:33170         pa-in-f189.1e100.:https ESTABLISHED
udp        0      0 *:ipp                   *:*                                
udp6       0      0 [::]:mdns               [::]:*                             
udp6       0      0 [::]:44123              [::]:*                             
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7          
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    266919   /run/user/1000/systemd/notify
unix  2      [ ACC ]     STREAM     LISTENING     266920   /run/user/1000/systemd/private
unix  2      [ ACC ]     SEQPACKET  LISTENING     9962     /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     269495   /run/user/1000/keyring/control
unix  2      [ ACC ]     STREAM     LISTENING     269570   /run/user/1000/keyring/pkcs11
unix  3      [ ]         DGRAM                    8312     /run/systemd/notify
unix  2      [ ACC ]     STREAM     LISTENING     269572   /run/user/1000/keyring/ssh
unix  2      [ ACC ]     STREAM     LISTENING     265151   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     268725   /tmp/.ICE-unix/12268
unix  2      [ ACC ]     STREAM     LISTENING     268895   /run/user/1000/pulse/native
unix  2      [ ACC ]     STREAM     LISTENING     339964   /tmp/.com.google.Chrome.LDvmrU/SingletonSocket
unix  2      [ ACC ]     STREAM     LISTENING     265150   @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     268587   @/tmp/dbus-nmXPmtSCrM
unix  2      [ ACC ]     STREAM     LISTENING     8313     /run/systemd/private
unix  17     [ ]         DGRAM                    8318     /run/systemd/journal/dev-log
unix  2      [ ACC ]     STREAM     LISTENING     8326     /run/systemd/fsck.progress
unix  2      [ ACC ]     STREAM     LISTENING     8327     /run/systemd/journal/stdout
unix  6      [ ]         DGRAM                    8328     /run/systemd/journal/socket
unix  2      [ ACC ]     STREAM     LISTENING     268554   /home/john/.gnupg/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     12976    /run/uuidd/request
unix  2      [ ACC ]     STREAM     LISTENING     12977    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     12978    /run/snapd.socket
unix  2      [ ACC ]     STREAM     LISTENING     12979    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     12980    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     12981    /run/acpid.socket
unix  3      [ ]         SEQPACKET  CONNECTED     339794   @0003d
unix  2      [ ACC ]     STREAM     LISTENING     269654   @/tmp/dbus-JjRaeLDQ
unix  2      [ ]         DGRAM                    339425   /run/wpa_supplicant/wlp6s0
unix  2      [ ]         DGRAM                    355039   /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     269504   @/com/ubuntu/upstart-session/1000/12020
unix  2      [ ACC ]     STREAM     LISTENING     269532   @/tmp/dbus-n8XwjS1uR8
unix  2      [ ACC ]     STREAM     LISTENING     268724   @/tmp/.ICE-unix/12268
unix  2      [ ACC ]     STREAM     LISTENING     20223    /var/run/NetworkManager/private-dhcp
unix  3      [ ]         STREAM     CONNECTED     270296   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     270574   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     21510    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     270802   
unix  3      [ ]         STREAM     CONNECTED     367003   
unix  3      [ ]         STREAM     CONNECTED     268757   
unix  3      [ ]         STREAM     CONNECTED     269776   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     22160    
unix  2      [ ]         DGRAM                    16023    
unix  3      [ ]         STREAM     CONNECTED     270282   /var/run/dbus/system_bus_socket
unix  2      [ ]         DGRAM                    270361   
unix  3      [ ]         STREAM     CONNECTED     270043   
unix  3      [ ]         STREAM     CONNECTED     341868   
unix  3      [ ]         STREAM     CONNECTED     273431   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     268671   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     19417    
unix  3      [ ]         STREAM     CONNECTED     19930    
unix  3      [ ]         STREAM     CONNECTED     341891   
unix  3      [ ]         STREAM     CONNECTED     271427   
unix  3      [ ]         STREAM     CONNECTED     268670   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     339888   
unix  2      [ ]         DGRAM                    269167   
unix  3      [ ]         STREAM     CONNECTED     268238   
unix  3      [ ]         STREAM     CONNECTED     269632   
unix  3      [ ]         STREAM     CONNECTED     269583   
unix  3      [ ]         STREAM     CONNECTED     368798   
unix  3      [ ]         STREAM     CONNECTED     10663    
unix  3      [ ]         STREAM     CONNECTED     272462   
unix  3      [ ]         STREAM     CONNECTED     259885   /run/systemd/journal/stdout
unix  3      [ ]         SEQPACKET  CONNECTED     340652   
unix  3      [ ]         STREAM     CONNECTED     271501   
unix  3      [ ]         STREAM     CONNECTED     16565    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     272385   @/dbus-vfs-daemon/socket-GP9OcGPa
unix  3      [ ]         STREAM     CONNECTED     334856   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     271724   
unix  3      [ ]         STREAM     CONNECTED     267167   
unix  3      [ ]         STREAM     CONNECTED     341848   
unix  3      [ ]         STREAM     CONNECTED     341830   
unix  3      [ ]         STREAM     CONNECTED     269219   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     268625   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20345    
unix  3      [ ]         STREAM     CONNECTED     18648    
unix  3      [ ]         STREAM     CONNECTED     270859   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     16264    
unix  3      [ ]         STREAM     CONNECTED     270591   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     270262   
unix  3      [ ]         STREAM     CONNECTED     269082   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     17828    
unix  3      [ ]         STREAM     CONNECTED     340641   
unix  3      [ ]         STREAM     CONNECTED     270070   
unix  3      [ ]         STREAM     CONNECTED     268743   
unix  3      [ ]         STREAM     CONNECTED     16040    
unix  3      [ ]         DGRAM                    8455     
unix  3      [ ]         STREAM     CONNECTED     269727   
unix  3      [ ]         STREAM     CONNECTED     268631   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     272414   
unix  3      [ ]         STREAM     CONNECTED     270592   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     270566   
unix  3      [ ]         STREAM     CONNECTED     269829   @/tmp/dbus-n8XwjS1uR8
unix  2      [ ]         DGRAM                    269486   
unix  3      [ ]         STREAM     CONNECTED     13181    
unix  3      [ ]         STREAM     CONNECTED     368805   
unix  3      [ ]         SEQPACKET  CONNECTED     339792   
unix  3      [ ]         STREAM     CONNECTED     269680   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     265169   
unix  3      [ ]         STREAM     CONNECTED     333359   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     341869   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18615    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16187    
unix  3      [ ]         STREAM     CONNECTED     370601   
unix  3      [ ]         STREAM     CONNECTED     268197   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     339883   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270218   
unix  3      [ ]         STREAM     CONNECTED     267066   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268608   @/tmp/.X11-unix/X0
unix  2      [ ]         DGRAM                    296891   
unix  3      [ ]         STREAM     CONNECTED     271670   @/dbus-vfs-daemon/socket-mjkVSSLS
unix  3      [ ]         STREAM     CONNECTED     267169   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     269698   
unix  3      [ ]         STREAM     CONNECTED     271454   
unix  3      [ ]         STREAM     CONNECTED     268739   
unix  3      [ ]         STREAM     CONNECTED     268707   
unix  3      [ ]         STREAM     CONNECTED     16022    
unix  3      [ ]         STREAM     CONNECTED     270576   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     23216    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     268729   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20374    
unix  3      [ ]         STREAM     CONNECTED     272459   
unix  3      [ ]         STREAM     CONNECTED     271483   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270338   
unix  3      [ ]         STREAM     CONNECTED     269828   
unix  3      [ ]         STREAM     CONNECTED     369750   
unix  3      [ ]         STREAM     CONNECTED     331323   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     333895   
unix  3      [ ]         STREAM     CONNECTED     267055   
unix  3      [ ]         STREAM     CONNECTED     16807    
unix  3      [ ]         STREAM     CONNECTED     269243   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     340644   /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     268733   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269587   
unix  3      [ ]         STREAM     CONNECTED     271736   
unix  3      [ ]         STREAM     CONNECTED     268695   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268136   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     341825   
unix  3      [ ]         STREAM     CONNECTED     270331   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     270551   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17220    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17201    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     340120   
unix  3      [ ]         STREAM     CONNECTED     369747   
unix  3      [ ]         STREAM     CONNECTED     270340   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     269807   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     259884   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     16041    
unix  3      [ ]         STREAM     CONNECTED     269253   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     269250   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     367618   
unix  3      [ ]         SEQPACKET  CONNECTED     341889   
unix  3      [ ]         STREAM     CONNECTED     269209   /var/run/dbus/system_bus_socket
unix  3      [ ]         SEQPACKET  CONNECTED     341895   
unix  3      [ ]         STREAM     CONNECTED     341863   
unix  3      [ ]         STREAM     CONNECTED     341861   
unix  3      [ ]         STREAM     CONNECTED     269213   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     270076   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         DGRAM                    19169    
unix  3      [ ]         STREAM     CONNECTED     341866   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     269310   
unix  3      [ ]         STREAM     CONNECTED     269830   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     16182    
unix  3      [ ]         STREAM     CONNECTED     339882   
unix  3      [ ]         STREAM     CONNECTED     268124   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     341821   
unix  3      [ ]         STREAM     CONNECTED     335734   
unix  3      [ ]         STREAM     CONNECTED     271388   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     268624   
unix  3      [ ]         STREAM     CONNECTED     17938    
unix  3      [ ]         STREAM     CONNECTED     18609    
unix  3      [ ]         STREAM     CONNECTED     367619   
unix  3      [ ]         STREAM     CONNECTED     272415   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     267063   
unix  3      [ ]         STREAM     CONNECTED     269480   
unix  3      [ ]         STREAM     CONNECTED     366392   
unix  3      [ ]         STREAM     CONNECTED     16560    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269261   
unix  3      [ ]         SEQPACKET  CONNECTED     344988   
unix  3      [ ]         STREAM     CONNECTED     267187   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     13044    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     340625   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     270242   
unix  2      [ ]         STREAM     CONNECTED     271430   
unix  3      [ ]         STREAM     CONNECTED     268669   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     267168   
unix  3      [ ]         STREAM     CONNECTED     368563   
unix  3      [ ]         STREAM     CONNECTED     273423   
unix  3      [ ]         STREAM     CONNECTED     271401   
unix  3      [ ]         STREAM     CONNECTED     269635   
unix  3      [ ]         STREAM     CONNECTED     265157   
unix  3      [ ]         STREAM     CONNECTED     269920   
unix  3      [ ]         STREAM     CONNECTED     268647   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     15122    
unix  3      [ ]         STREAM     CONNECTED     366391   
unix  3      [ ]         STREAM     CONNECTED     270781   
unix  3      [ ]         STREAM     CONNECTED     268898   /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     266997   
unix  3      [ ]         STREAM     CONNECTED     372954   
unix  3      [ ]         STREAM     CONNECTED     18238    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     340628   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18642    
unix  3      [ ]         STREAM     CONNECTED     271603   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269633   
unix  3      [ ]         STREAM     CONNECTED     365463   
unix  3      [ ]         STREAM     CONNECTED     270274   @/tmp/.X11-unix/X0
unix  2      [ ]         DGRAM                    16266    
unix  3      [ ]         STREAM     CONNECTED     16630    
unix  3      [ ]         STREAM     CONNECTED     247472   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269084   
unix  3      [ ]         STREAM     CONNECTED     268189   
unix  3      [ ]         STREAM     CONNECTED     269700   
unix  3      [ ]         STREAM     CONNECTED     339192   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     271628   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269682   
unix  3      [ ]         STREAM     CONNECTED     268607   
unix  3      [ ]         STREAM     CONNECTED     269071   
unix  3      [ ]         STREAM     CONNECTED     267206   
unix  2      [ ]         DGRAM                    23769    
unix  3      [ ]         STREAM     CONNECTED     271737   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     270273   
unix  3      [ ]         STREAM     CONNECTED     270130   @/tmp/.ICE-unix/12268
unix  3      [ ]         STREAM     CONNECTED     268893   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     267051   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     16042    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269278   
unix  3      [ ]         STREAM     CONNECTED     266964   
unix  3      [ ]         STREAM     CONNECTED     340749   
unix  3      [ ]         STREAM     CONNECTED     269923   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     17566    
unix  3      [ ]         STREAM     CONNECTED     341824   
unix  3      [ ]         STREAM     CONNECTED     271555   
unix  3      [ ]         STREAM     CONNECTED     18644    
unix  3      [ ]         STREAM     CONNECTED     333358   
unix  3      [ ]         STREAM     CONNECTED     269697   
unix  3      [ ]         STREAM     CONNECTED     369429   
unix  3      [ ]         STREAM     CONNECTED     343045   
unix  3      [ ]         STREAM     CONNECTED     272412   @/dbus-vfs-daemon/socket-fW0nPtt0
unix  3      [ ]         STREAM     CONNECTED     268654   
unix  3      [ ]         STREAM     CONNECTED     267067   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     268634   
unix  3      [ ]         STREAM     CONNECTED     21520    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     271500   
unix  3      [ ]         STREAM     CONNECTED     269766   
unix  3      [ ]         STREAM     CONNECTED     266992   
unix  3      [ ]         STREAM     CONNECTED     273432   
unix  3      [ ]         STREAM     CONNECTED     270550   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     267183   
unix  3      [ ]         STREAM     CONNECTED     267182   
unix  3      [ ]         STREAM     CONNECTED     271566   
unix  3      [ ]         STREAM     CONNECTED     268591   
unix  2      [ ]         DGRAM                    18643    
unix  3      [ ]         STREAM     CONNECTED     272463   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270585   
unix  3      [ ]         STREAM     CONNECTED     268182   
unix  3      [ ]         STREAM     CONNECTED     269722   
unix  3      [ ]         STREAM     CONNECTED     16808    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269260   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     268267   
unix  3      [ ]         STREAM     CONNECTED     265153   
unix  3      [ ]         STREAM     CONNECTED     13277    
unix  3      [ ]         STREAM     CONNECTED     372064   @/tmp/.X11-unix/X0
unix  3      [ ]         SEQPACKET  CONNECTED     340804   
unix  3      [ ]         STREAM     CONNECTED     341834   
unix  3      [ ]         STREAM     CONNECTED     271428   
unix  3      [ ]         STREAM     CONNECTED     267026   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     341862   
unix  3      [ ]         STREAM     CONNECTED     270046   
unix  3      [ ]         STREAM     CONNECTED     15054    
unix  3      [ ]         STREAM     CONNECTED     370600   
unix  3      [ ]         STREAM     CONNECTED     271439   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     267058   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     268140   
unix  3      [ ]         STREAM     CONNECTED     270342   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     17016    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     17816    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     367057   
unix  3      [ ]         STREAM     CONNECTED     367056   
unix  3      [ ]         STREAM     CONNECTED     270313   
unix  3      [ ]         STREAM     CONNECTED     270499   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     269070   
unix  3      [ ]         STREAM     CONNECTED     266988   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     336933   
unix  3      [ ]         STREAM     CONNECTED     267037   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         SEQPACKET  CONNECTED     341894   
unix  3      [ ]         STREAM     CONNECTED     267205   
unix  3      [ ]         STREAM     CONNECTED     267191   
unix  3      [ ]         STREAM     CONNECTED     270699   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270211   
unix  3      [ ]         STREAM     CONNECTED     267057   
unix  3      [ ]         STREAM     CONNECTED     16181    
unix  3      [ ]         STREAM     CONNECTED     270268   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     271433   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     267219   
unix  3      [ ]         STREAM     CONNECTED     336507   
unix  3      [ ]         STREAM     CONNECTED     273429   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269636   
unix  3      [ ]         STREAM     CONNECTED     266085   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     248251   
unix  3      [ ]         STREAM     CONNECTED     341827   
unix  3      [ ]         STREAM     CONNECTED     270246   
unix  3      [ ]         STREAM     CONNECTED     271405   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     267065   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     372067   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269710   
unix  3      [ ]         STREAM     CONNECTED     267147   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18611    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     270267   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     270583   
unix  3      [ ]         STREAM     CONNECTED     270558   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269627   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268747   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269806   
unix  3      [ ]         STREAM     CONNECTED     17452    
unix  2      [ ]         DGRAM                    355051   
unix  3      [ ]         STREAM     CONNECTED     271453   
unix  3      [ ]         STREAM     CONNECTED     271442   
unix  3      [ ]         STREAM     CONNECTED     269582   
unix  3      [ ]         STREAM     CONNECTED     268520   
unix  3      [ ]         STREAM     CONNECTED     21352    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269659   
unix  3      [ ]         STREAM     CONNECTED     266987   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     337584   
unix  3      [ ]         STREAM     CONNECTED     271458   
unix  3      [ ]         STREAM     CONNECTED     340631   
unix  3      [ ]         STREAM     CONNECTED     269922   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     372951   
unix  3      [ ]         STREAM     CONNECTED     271627   
unix  3      [ ]         STREAM     CONNECTED     332968   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     332967   
unix  3      [ ]         STREAM     CONNECTED     271363   
unix  3      [ ]         STREAM     CONNECTED     268609   
unix  3      [ ]         STREAM     CONNECTED     18534    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     273428   
unix  3      [ ]         STREAM     CONNECTED     271408   
unix  3      [ ]         STREAM     CONNECTED     268522   
unix  3      [ ]         STREAM     CONNECTED     367002   
unix  3      [ ]         STREAM     CONNECTED     268742   
unix  3      [ ]         STREAM     CONNECTED     372069   
unix  3      [ ]         SEQPACKET  CONNECTED     340805   
unix  3      [ ]         STREAM     CONNECTED     331151   
unix  3      [ ]         STREAM     CONNECTED     270503   
unix  3      [ ]         STREAM     CONNECTED     269777   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269244   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269775   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268708   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     268630   
unix  3      [ ]         STREAM     CONNECTED     267060   
unix  3      [ ]         STREAM     CONNECTED     17178    
unix  3      [ ]         STREAM     CONNECTED     341890   
unix  3      [ ]         STREAM     CONNECTED     269774   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269542   
unix  3      [ ]         STREAM     CONNECTED     16494    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269921   
unix  3      [ ]         STREAM     CONNECTED     269590   
unix  3      [ ]         STREAM     CONNECTED     268569   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     16164    
unix  3      [ ]         STREAM     CONNECTED     372063   
unix  3      [ ]         STREAM     CONNECTED     268196   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     16492    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     341831   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     271445   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270255   
unix  3      [ ]         STREAM     CONNECTED     268656   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     268605   
unix  3      [ ]         STREAM     CONNECTED     247474   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16305    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     367623   
unix  3      [ ]         STREAM     CONNECTED     367622   
unix  3      [ ]         STREAM     CONNECTED     19673    
unix  3      [ ]         STREAM     CONNECTED     269567   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270304   
unix  3      [ ]         STREAM     CONNECTED     270066   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     266073   /run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     23326    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18927    
unix  3      [ ]         STREAM     CONNECTED     268186   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16286    
unix  3      [ ]         STREAM     CONNECTED     269085   
unix  3      [ ]         STREAM     CONNECTED     269833   
unix  3      [ ]         STREAM     CONNECTED     267176   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     266998   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269544   @/com/ubuntu/upstart-session/1000/12020
unix  3      [ ]         STREAM     CONNECTED     269257   
unix  3      [ ]         STREAM     CONNECTED     261403   
unix  3      [ ]         STREAM     CONNECTED     20742    
unix  3      [ ]         STREAM     CONNECTED     268123   @/com/ubuntu/upstart-session/1000/12020
unix  3      [ ]         STREAM     CONNECTED     369430   
unix  3      [ ]         STREAM     CONNECTED     270564   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269390   
unix  3      [ ]         STREAM     CONNECTED     267056   @/tmp/dbus-JjRaeLDQ
unix  2      [ ]         DGRAM                    16179    
unix  3      [ ]         STREAM     CONNECTED     246587   
unix  3      [ ]         STREAM     CONNECTED     267209   
unix  3      [ ]         STREAM     CONNECTED     268600   
unix  3      [ ]         STREAM     CONNECTED     266994   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     368789   
unix  3      [ ]         STREAM     CONNECTED     365462   
unix  3      [ ]         STREAM     CONNECTED     335228   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     267184   
unix  3      [ ]         STREAM     CONNECTED     271669   
unix  3      [ ]         STREAM     CONNECTED     268072   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     261404   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     273443   
unix  3      [ ]         STREAM     CONNECTED     17886    
unix  3      [ ]         STREAM     CONNECTED     17840    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16809    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     340630   
unix  3      [ ]         STREAM     CONNECTED     335654   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270664   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     371377   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     367054   
unix  3      [ ]         STREAM     CONNECTED     16255    
unix  3      [ ]         STREAM     CONNECTED     270212   
unix  3      [ ]         STREAM     CONNECTED     268752   
unix  3      [ ]         STREAM     CONNECTED     270266   
unix  3      [ ]         STREAM     CONNECTED     268592   
unix  3      [ ]         STREAM     CONNECTED     266070   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     271429   
unix  3      [ ]         STREAM     CONNECTED     270559   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     267069   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     268108   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269588   
unix  3      [ ]         STREAM     CONNECTED     371373   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     271730   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     271525   
unix  3      [ ]         STREAM     CONNECTED     270501   
unix  3      [ ]         STREAM     CONNECTED     268649   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     266965   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     16631    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     271387   
unix  3      [ ]         SEQPACKET  CONNECTED     339791   
unix  3      [ ]         STREAM     CONNECTED     267008   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     266993   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269543   @/com/ubuntu/upstart-session/1000/12020
unix  3      [ ]         STREAM     CONNECTED     339881   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     271606   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270247   
unix  3      [ ]         STREAM     CONNECTED     267179   
unix  3      [ ]         STREAM     CONNECTED     21066    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     271735   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     270645   
unix  3      [ ]         STREAM     CONNECTED     340640   
unix  3      [ ]         STREAM     CONNECTED     340046   
unix  2      [ ]         DGRAM                    269218   
unix  3      [ ]         STREAM     CONNECTED     333659   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         DGRAM                    8456     
unix  3      [ ]         STREAM     CONNECTED     371372   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269223   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     371044   
unix  3      [ ]         STREAM     CONNECTED     270281   
unix  3      [ ]         STREAM     CONNECTED     270269   
unix  3      [ ]         STREAM     CONNECTED     22161    
unix  3      [ ]         STREAM     CONNECTED     271412   
unix  3      [ ]         STREAM     CONNECTED     267180   
unix  3      [ ]         STREAM     CONNECTED     270067   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269924   
unix  3      [ ]         STREAM     CONNECTED     269805   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268185   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     268723   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     267173   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     272418   
unix  3      [ ]         STREAM     CONNECTED     269249   
unix  3      [ ]         STREAM     CONNECTED     270575   
unix  3      [ ]         STREAM     CONNECTED     267210   
unix  3      [ ]         STREAM     CONNECTED     270275   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     268255   /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     269834   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268183   /var/run/dbus/system_bus_socket
unix  2      [ ]         DGRAM                    10030    
unix  3      [ ]         STREAM     CONNECTED     271611   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269715   
unix  3      [ ]         STREAM     CONNECTED     17165    
unix  3      [ ]         STREAM     CONNECTED     271411   
unix  3      [ ]         STREAM     CONNECTED     267024   
unix  3      [ ]         STREAM     CONNECTED     269566   
unix  3      [ ]         STREAM     CONNECTED     268081   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     273444   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269207   @/tmp/.X11-unix/X0
unix  3      [ ]         DGRAM                    19168    
unix  3      [ ]         STREAM     CONNECTED     343044   
unix  3      [ ]         STREAM     CONNECTED     269205   
unix  3      [ ]         STREAM     CONNECTED     269683   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     268553   
unix  3      [ ]         STREAM     CONNECTED     21390    
unix  3      [ ]         STREAM     CONNECTED     371043   
unix  3      [ ]         STREAM     CONNECTED     267259   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     335736   @/dbus-vfs-daemon/socket-iR33bOPf
unix  3      [ ]         STREAM     CONNECTED     331152   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     267216   
unix  3      [ ]         STREAM     CONNECTED     270584   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     270549   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270858   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     267192   
unix  3      [ ]         STREAM     CONNECTED     267185   
unix  3      [ ]         STREAM     CONNECTED     337901   @/tmp/dbus-n8XwjS1uR8
unix  2      [ ]         DGRAM                    17937    
unix  3      [ ]         SEQPACKET  CONNECTED     339795   
unix  3      [ ]         STREAM     CONNECTED     271407   
unix  3      [ ]         STREAM     CONNECTED     270095   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     21509    
unix  2      [ ]         DGRAM                    340342   
unix  3      [ ]         STREAM     CONNECTED     269248   
unix  3      [ ]         STREAM     CONNECTED     270071   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     268256   /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     270343   
unix  3      [ ]         STREAM     CONNECTED     267061   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270577   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     270214   
unix  3      [ ]         STREAM     CONNECTED     268601   
unix  3      [ ]         STREAM     CONNECTED     271725   
unix  3      [ ]         STREAM     CONNECTED     21083    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19416    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     368788   
unix  3      [ ]         STREAM     CONNECTED     336934   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     267005   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268549   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268512   
unix  3      [ ]         STREAM     CONNECTED     261402   
unix  3      [ ]         STREAM     CONNECTED     246588   
unix  2      [ ]         DGRAM                    8352     
unix  3      [ ]         STREAM     CONNECTED     268201   
unix  3      [ ]         STREAM     CONNECTED     18612    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17826    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10026    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     341860   
unix  3      [ ]         STREAM     CONNECTED     268594   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     334859   
unix  3      [ ]         STREAM     CONNECTED     272457   
unix  3      [ ]         STREAM     CONNECTED     270248   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     15348    
unix  3      [ ]         STREAM     CONNECTED     341835   
unix  3      [ ]         STREAM     CONNECTED     368562   
unix  3      [ ]         STREAM     CONNECTED     267186   
unix  3      [ ]         STREAM     CONNECTED     267068   
unix  3      [ ]         STREAM     CONNECTED     339193   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269591   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     271484   @/dbus-vfs-daemon/socket-IF4HZCVI
unix  3      [ ]         STREAM     CONNECTED     271409   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     19459    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     271431   
unix  3      [ ]         STREAM     CONNECTED     269549   
unix  3      [ ]         STREAM     CONNECTED     269505   
unix  3      [ ]         STREAM     CONNECTED     16569    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     341822   
unix  3      [ ]         STREAM     CONNECTED     270666   @/tmp/dbus-nmXPmtSCrM
unix  2      [ ]         STREAM     CONNECTED     18649    
unix  3      [ ]         STREAM     CONNECTED     271404   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269827   
unix  3      [ ]         STREAM     CONNECTED     268184   
unix  2      [ ]         DGRAM                    22093    
unix  3      [ ]         STREAM     CONNECTED     369751   
unix  3      [ ]         STREAM     CONNECTED     369746   
unix  3      [ ]         STREAM     CONNECTED     270263   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268277   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     268690   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     17813    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     267193   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     247473   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     267025   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     268561   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     268548   
unix  3      [ ]         STREAM     CONNECTED     368806   
unix  3      [ ]         STREAM     CONNECTED     270261   
unix  3      [ ]         STREAM     CONNECTED     270505   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     269747   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     267166   
unix  3      [ ]         STREAM     CONNECTED     267064   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     268606   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     262196   
unix  3      [ ]         STREAM     CONNECTED     341828   
unix  3      [ ]         STREAM     CONNECTED     271434   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     273433   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     270337   
unix  3      [ ]         SEQPACKET  CONNECTED     344989   
unix  3      [ ]         STREAM     CONNECTED     341849   
unix  3      [ ]         STREAM     CONNECTED     18307    /var/run/dbus/system_bus_socket
unix  3      [ ]         SEQPACKET  CONNECTED     340651   
unix  3      [ ]         STREAM     CONNECTED     268798   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     331722   
unix  3      [ ]         STREAM     CONNECTED     21325    
unix  3      [ ]         STREAM     CONNECTED     18645    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     371374   @/tmp/dbus-nmXPmtSCrM
unix  3      [ ]         STREAM     CONNECTED     268628   
unix  3      [ ]         STREAM     CONNECTED     271734   
unix  3      [ ]         STREAM     CONNECTED     269551   @/com/ubuntu/upstart-session/1000/12020
unix  2      [ ]         DGRAM                    20380    
unix  3      [ ]         STREAM     CONNECTED     372062   
unix  3      [ ]         STREAM     CONNECTED     271604   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     269746   
unix  3      [ ]         STREAM     CONNECTED     271755   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     270665   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     270264   /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    267873   
unix  3      [ ]         STREAM     CONNECTED     367055   
unix  3      [ ]         STREAM     CONNECTED     270271   
unix  2      [ ]         STREAM     CONNECTED     16297    
unix  2      [ ]         DGRAM                    16155    
unix  3      [ ]         STREAM     CONNECTED     368799   
unix  3      [ ]         STREAM     CONNECTED     340629   @/tmp/dbus-JjRaeLDQ
unix  3      [ ]         STREAM     CONNECTED     269679   
unix  3      [ ]         STREAM     CONNECTED     268519   
unix  3      [ ]         STREAM     CONNECTED     21353    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     341826   
unix  3      [ ]         STREAM     CONNECTED     16334    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     372952   
unix  3      [ ]         SEQPACKET  CONNECTED     341888   
unix  3      [ ]         STREAM     CONNECTED     269748   /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     269709   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     269753   
unix  2      [ ]         DGRAM                    268089   
unix  3      [ ]         STREAM     CONNECTED     269255   
unix  3      [ ]         STREAM     CONNECTED     269794   @/tmp/dbus-n8XwjS1uR8
unix  3      [ ]         STREAM     CONNECTED     268629   
unix  3      [ ]         STREAM     CONNECTED     267170   @/tmp/.X11-unix/X0
unix  2      [ ]         DGRAM                    16037    
unix  3      [ ]         STREAM     CONNECTED     273430
```

---

### Post by matt_symes on 2016-05-05
Hi

> but I believe I have some bad stuff going on ..

What do you believe is going on ?

Kind regards

---

### Post by james223 on 2016-05-05
wwell.. I switched to linux becuase I was being targeted by hackers on windows BIG TIME...it was so bad that my pc wasnt even mine.. it was simply  a thin client to locon the hackers network.. I just want to be sure im still not being infiltrateed

Another indicator is its failing to download updates any advice??

hers the details on the update failure..

W:The repository 'cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., E:Failed to fetch cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)/dists/xenial/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, E:Failed to fetch cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)/dists/xenial/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by howefield on 2016-05-05
For your last error, try opening Software & Updates and untick the checkbox in the "Installable from CD-ROM/DVD" box.

---

### Post by matt_symes on 2016-05-05
Hi

If that is your only problem then follow howefields advice to fix it. That error is not a compromise. apt is looking for a CD Rom / DVD and can't find one.

Do you have any other problems ?

Kind regards

---

### Post by james223 on 2016-05-05
I suppose Im just super leary cause Windows is SUCH a security nightmare.. gunshy I suppopse.. if you all think its fine Ill trust ya :D thanks for the advice

---

### Post by ian-weisser on 2016-05-06
Security is more that just your OS or a firewall.
Security is also a set of habits.

A default install of Ubuntu includes listeners for clock syncing, printing, DNS and that's about all. Some built-in services handle geolocation, updates from trusted repositories, etc. That's not much attack surface...until you open your web browser (or torrent client) and announce your System and Location to the world, and accept data from the dirty, dirty internet.

Many effective penetrations are social, the OS is irrelevant.

Only safe habits can help you keep your attack surface small, check for common vulnerabilities, check your logs, and refuse social attacks. The OS cannot do any of those for you.

---

### Post by mörgæs on 2016-05-06
> **ian-weisser said:**
> check for common vulnerabilities
The good part is that there are much less vulnerabilities in Buntu than in Windows and that they are fixed and distributed fast if a serious one is discovered. Using Windows one can have to wait for weeks.

---

