---
title: "constant inbound traffic"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by dentarthurdent on 2008-04-23
Hi,

just curious... I just installed conky and noticed that there is steady inbound traffic ~75Kb/sec. system monitor shows the same thing. i have no programs open... is this just ubuntu maintaining a connection to check for updates or something? i'm currently connected via wired connection, but could this be ubuntu scanning wireless connections?

---

### Post by Seti on 2008-04-23
open up a terminal and do a ```
netstat
```
that should show you all your connections and where they're going.

---

### Post by dentarthurdent on 2008-04-23
oh, thanks. i did that, but i'm not sure what i'm looking at, nor what i should be looking for? pardon my ignorance. should i post the result of the netstat?

---

### Post by Crafty Kisses on 2008-04-23
> **dentarthurdent said:**
> oh, thanks. i did that, but i'm not sure what i'm looking at, nor what i should be looking for? pardon my ignorance. should i post the result of the netstat?

Yes please. :)

---

### Post by dentarthurdent on 2008-04-23
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    6054     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    6267     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    13012    @/org/freedesktop/hal/udev_event
unix  11     [ ]         DGRAM                    12771    /dev/log
unix  3      [ ]         STREAM     CONNECTED     80945    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     80944    
unix  3      [ ]         STREAM     CONNECTED     80914    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     80913    
unix  3      [ ]         STREAM     CONNECTED     80906    /tmp/orbit-colin/linc-3497-0-6af37f4e7ef13
unix  3      [ ]         STREAM     CONNECTED     80905    
unix  3      [ ]         STREAM     CONNECTED     80902    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     80901    
unix  3      [ ]         STREAM     CONNECTED     80899    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     80898    
unix  3      [ ]         STREAM     CONNECTED     80894    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     80893    
unix  3      [ ]         STREAM     CONNECTED     52121    
unix  3      [ ]         STREAM     CONNECTED     52120    
unix  3      [ ]         STREAM     CONNECTED     52119    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     52118    
unix  3      [ ]         STREAM     CONNECTED     52115    /tmp/orbit-colin/linc-24dc-0-6beb7f522826a
unix  3      [ ]         STREAM     CONNECTED     52113    
unix  3      [ ]         STREAM     CONNECTED     52112    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     52111    
unix  3      [ ]         STREAM     CONNECTED     52110    /tmp/orbit-colin/linc-24dc-0-6beb7f522826a
unix  3      [ ]         STREAM     CONNECTED     52109    
unix  3      [ ]         STREAM     CONNECTED     52106    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     52105    
unix  3      [ ]         STREAM     CONNECTED     52103    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     52102    
unix  3      [ ]         STREAM     CONNECTED     52098    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     52097    
unix  3      [ ]         STREAM     CONNECTED     44285    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     44284    
unix  3      [ ]         STREAM     CONNECTED     22387    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22386    
unix  3      [ ]         STREAM     CONNECTED     21352    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21351    
unix  3      [ ]         STREAM     CONNECTED     21350    /tmp/orbit-colin/linc-1899-0-6c151d855c421
unix  3      [ ]         STREAM     CONNECTED     21349    
unix  3      [ ]         STREAM     CONNECTED     21346    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     21345    
unix  3      [ ]         STREAM     CONNECTED     21342    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     21341    
unix  3      [ ]         STREAM     CONNECTED     21231    @/dbus-vfs-daemon/socket-5m3obUXA
unix  3      [ ]         STREAM     CONNECTED     21230    
unix  3      [ ]         STREAM     CONNECTED     21232    @/dbus-vfs-daemon/socket-AH7i3Ek3
unix  3      [ ]         STREAM     CONNECTED     21229    
unix  3      [ ]         STREAM     CONNECTED     21225    /tmp/orbit-colin/linc-188f-0-4572658884b23
unix  3      [ ]         STREAM     CONNECTED     21224    
unix  3      [ ]         STREAM     CONNECTED     21221    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     21220    
unix  3      [ ]         STREAM     CONNECTED     21214    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     21213    
unix  3      [ ]         STREAM     CONNECTED     21194    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     21193    
unix  3      [ ]         STREAM     CONNECTED     21175    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21174    
unix  3      [ ]         STREAM     CONNECTED     20674    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     20673    
unix  3      [ ]         STREAM     CONNECTED     20644    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     20643    
unix  3      [ ]         STREAM     CONNECTED     20642    /tmp/orbit-colin/linc-17d1-0-22f2287c24046
unix  3      [ ]         STREAM     CONNECTED     20641    
unix  3      [ ]         STREAM     CONNECTED     20640    /tmp/orbit-colin/linc-185a-0-36224c37bdd59
unix  3      [ ]         STREAM     CONNECTED     20639    
unix  3      [ ]         STREAM     CONNECTED     20637    /tmp/orbit-colin/linc-185a-0-36224c37bdd59
unix  3      [ ]         STREAM     CONNECTED     20636    
unix  3      [ ]         STREAM     CONNECTED     20635    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     20634    
unix  3      [ ]         STREAM     CONNECTED     20633    /tmp/orbit-colin/linc-185a-0-36224c37bdd59
unix  3      [ ]         STREAM     CONNECTED     20632    
unix  3      [ ]         STREAM     CONNECTED     20629    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     20628    
unix  3      [ ]         STREAM     CONNECTED     20624    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20623    
unix  3      [ ]         STREAM     CONNECTED     20554    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20553    
unix  3      [ ]         STREAM     CONNECTED     20551    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20550    
unix  3      [ ]         STREAM     CONNECTED     20540    /tmp/orbit-colin/linc-17e6-0-75665079de07a
unix  3      [ ]         STREAM     CONNECTED     20539    
unix  3      [ ]         STREAM     CONNECTED     20538    /tmp/orbit-colin/linc-1827-0-4f7887b26dbc7
unix  3      [ ]         STREAM     CONNECTED     20537    
unix  3      [ ]         STREAM     CONNECTED     20532    @/dbus-vfs-daemon/socket-Qg0rfofg
unix  3      [ ]         STREAM     CONNECTED     20531    
unix  3      [ ]         STREAM     CONNECTED     20530    @/dbus-vfs-daemon/socket-4YmZP8g3
unix  3      [ ]         STREAM     CONNECTED     20529    
unix  3      [ ]         STREAM     CONNECTED     20525    @/dbus-vfs-daemon/socket-Ucq0yHU9
unix  3      [ ]         STREAM     CONNECTED     20524    
unix  3      [ ]         STREAM     CONNECTED     20526    @/dbus-vfs-daemon/socket-f44A7tD9
unix  3      [ ]         STREAM     CONNECTED     20523    
unix  3      [ ]         STREAM     CONNECTED     20516    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20515    
unix  3      [ ]         STREAM     CONNECTED     20511    /tmp/orbit-colin/linc-1833-0-6b05f92fdc678
unix  3      [ ]         STREAM     CONNECTED     20510    
unix  3      [ ]         STREAM     CONNECTED     20509    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     20508    
unix  3      [ ]         STREAM     CONNECTED     20505    /tmp/orbit-colin/linc-1833-0-6b05f92fdc678
unix  3      [ ]         STREAM     CONNECTED     20504    
unix  3      [ ]         STREAM     CONNECTED     20501    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     20500    
unix  3      [ ]         STREAM     CONNECTED     20498    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     20497    
unix  3      [ ]         STREAM     CONNECTED     20493    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20492    
unix  3      [ ]         STREAM     CONNECTED     20491    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     20490    
unix  3      [ ]         STREAM     CONNECTED     20469    /tmp/orbit-colin/linc-17d1-0-22f2287c24046
unix  3      [ ]         STREAM     CONNECTED     20468    
unix  3      [ ]         STREAM     CONNECTED     20467    /tmp/orbit-colin/linc-1835-0-6b05f92f2f470
unix  3      [ ]         STREAM     CONNECTED     20466    
unix  3      [ ]         STREAM     CONNECTED     20464    @/dbus-vfs-daemon/socket-On5hsYl9
unix  3      [ ]         STREAM     CONNECTED     20463    
unix  3      [ ]         STREAM     CONNECTED     20465    @/dbus-vfs-daemon/socket-abYknxpZ
unix  3      [ ]         STREAM     CONNECTED     20462    
unix  3      [ ]         STREAM     CONNECTED     20458    @/dbus-vfs-daemon/socket-dX7oqCNh
unix  3      [ ]         STREAM     CONNECTED     20457    
unix  3      [ ]         STREAM     CONNECTED     20459    @/dbus-vfs-daemon/socket-wHfxcGPa
unix  3      [ ]         STREAM     CONNECTED     20456    
unix  3      [ ]         STREAM     CONNECTED     20445    @/dbus-vfs-daemon/socket-6XB356wY
unix  3      [ ]         STREAM     CONNECTED     20444    
unix  3      [ ]         STREAM     CONNECTED     20446    @/dbus-vfs-daemon/socket-mIoTEeZx
unix  3      [ ]         STREAM     CONNECTED     20443    
unix  3      [ ]         STREAM     CONNECTED     20413    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20412    
unix  3      [ ]         STREAM     CONNECTED     20411    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20410    
unix  3      [ ]         STREAM     CONNECTED     20409    /tmp/orbit-colin/linc-1835-0-6b05f92f2f470
unix  3      [ ]         STREAM     CONNECTED     20408    
unix  3      [ ]         STREAM     CONNECTED     20407    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     20406    
unix  3      [ ]         STREAM     CONNECTED     20405    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20404    
unix  3      [ ]         STREAM     CONNECTED     20403    /tmp/orbit-colin/linc-1835-0-6b05f92f2f470
unix  3      [ ]         STREAM     CONNECTED     20402    
unix  3      [ ]         STREAM     CONNECTED     20399    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     20398    
unix  3      [ ]         STREAM     CONNECTED     20394    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20393    
unix  3      [ ]         STREAM     CONNECTED     20365    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20364    
unix  3      [ ]         STREAM     CONNECTED     20345    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20344    
unix  3      [ ]         STREAM     CONNECTED     20267    /tmp/orbit-colin/linc-1827-0-4f7887b26dbc7
unix  3      [ ]         STREAM     CONNECTED     20266    
unix  3      [ ]         STREAM     CONNECTED     20265    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     20264    
unix  3      [ ]         STREAM     CONNECTED     20241    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20240    
unix  3      [ ]         STREAM     CONNECTED     20239    /tmp/orbit-colin/linc-1827-0-4f7887b26dbc7
unix  3      [ ]         STREAM     CONNECTED     20238    
unix  3      [ ]         STREAM     CONNECTED     20235    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     20234    
unix  3      [ ]         STREAM     CONNECTED     20225    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20224    
unix  3      [ ]         STREAM     CONNECTED     20223    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     20222    
unix  3      [ ]         STREAM     CONNECTED     20184    /tmp/orbit-colin/linc-17e6-0-75665079de07a
unix  3      [ ]         STREAM     CONNECTED     20183    
unix  3      [ ]         STREAM     CONNECTED     20182    /tmp/orbit-colin/linc-17d2-0-22f2287c66c84
unix  3      [ ]         STREAM     CONNECTED     20181    
unix  3      [ ]         STREAM     CONNECTED     20179    /tmp/orbit-colin/linc-17d1-0-22f2287c24046
unix  3      [ ]         STREAM     CONNECTED     20178    
unix  3      [ ]         STREAM     CONNECTED     20180    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     20177    
unix  3      [ ]         STREAM     CONNECTED     20176    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     20174    
unix  3      [ ]         STREAM     CONNECTED     20175    /tmp/orbit-colin/linc-17d9-0-704a2b805db06
unix  3      [ ]         STREAM     CONNECTED     20173    
unix  3      [ ]         STREAM     CONNECTED     20169    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20168    
unix  3      [ ]         STREAM     CONNECTED     20131    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20130    
unix  3      [ ]         STREAM     CONNECTED     20129    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20128    
unix  3      [ ]         STREAM     CONNECTED     20127    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     20126    
unix  3      [ ]         STREAM     CONNECTED     20125    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20124    
unix  3      [ ]         STREAM     CONNECTED     20086    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     20085    
unix  3      [ ]         STREAM     CONNECTED     20100    /tmp/orbit-colin/linc-17e6-0-75665079de07a
unix  3      [ ]         STREAM     CONNECTED     20067    
unix  3      [ ]         STREAM     CONNECTED     20042    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20041    
unix  3      [ ]         STREAM     CONNECTED     20036    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     20035    
unix  3      [ ]         STREAM     CONNECTED     20033    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     20032    
unix  3      [ ]         STREAM     CONNECTED     20028    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20027    
unix  3      [ ]         STREAM     CONNECTED     20006    /tmp/orbit-colin/linc-17f3-0-6dced27e6c9e4
unix  3      [ ]         STREAM     CONNECTED     20005    
unix  3      [ ]         STREAM     CONNECTED     20002    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     19995    
unix  3      [ ]         STREAM     CONNECTED     19879    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     19878    
unix  3      [ ]         STREAM     CONNECTED     19877    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19876    
unix  2      [ ]         DGRAM                    19875    
unix  3      [ ]         STREAM     CONNECTED     19874    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19873    
unix  3      [ ]         STREAM     CONNECTED     19871    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     19870    
unix  3      [ ]         STREAM     CONNECTED     19869    /tmp/orbit-colin/linc-17e9-0-d6b87914464e
unix  3      [ ]         STREAM     CONNECTED     19868    
unix  3      [ ]         STREAM     CONNECTED     19865    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     19864    
unix  3      [ ]         STREAM     CONNECTED     19821    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19820    
unix  3      [ ]         STREAM     CONNECTED     19775    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     19774    
unix  3      [ ]         STREAM     CONNECTED     19768    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     19767    
unix  3      [ ]         STREAM     CONNECTED     19762    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19761    
unix  3      [ ]         STREAM     CONNECTED     19760    /tmp/orbit-colin/linc-17f0-0-d6b879ebe787
unix  3      [ ]         STREAM     CONNECTED     19759    
unix  3      [ ]         STREAM     CONNECTED     19756    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     19755    
unix  3      [ ]         STREAM     CONNECTED     19749    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19748    
unix  3      [ ]         STREAM     CONNECTED     19824    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     19666    
unix  3      [ ]         STREAM     CONNECTED     19662    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19661    
unix  3      [ ]         STREAM     CONNECTED     19574    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     19573    
unix  3      [ ]         STREAM     CONNECTED     19571    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19570    
unix  3      [ ]         STREAM     CONNECTED     19392    /tmp/orbit-colin/linc-17dc-0-273540cc43c2c
unix  3      [ ]         STREAM     CONNECTED     19391    
unix  3      [ ]         STREAM     CONNECTED     19388    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     19387    
unix  3      [ ]         STREAM     CONNECTED     19385    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     19384    
unix  3      [ ]         STREAM     CONNECTED     19263    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     19262    
unix  3      [ ]         STREAM     CONNECTED     19258    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19257    
unix  3      [ ]         STREAM     CONNECTED     19256    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     19255    
unix  3      [ ]         STREAM     CONNECTED     19254    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19253    
unix  3      [ ]         STREAM     CONNECTED     19143    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     19142    
unix  3      [ ]         STREAM     CONNECTED     19140    /tmp/orbit-colin/linc-17cf-0-382cd4097ada2
unix  3      [ ]         STREAM     CONNECTED     19139    
unix  3      [ ]         STREAM     CONNECTED     19136    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     19135    
unix  3      [ ]         STREAM     CONNECTED     19131    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19130    
unix  3      [ ]         STREAM     CONNECTED     19127    /tmp/orbit-colin/linc-17d2-0-22f2287c66c84
unix  3      [ ]         STREAM     CONNECTED     19126    
unix  3      [ ]         STREAM     CONNECTED     19123    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     19122    
unix  3      [ ]         STREAM     CONNECTED     19120    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     19119    
unix  3      [ ]         STREAM     CONNECTED     19106    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19105    
unix  3      [ ]         STREAM     CONNECTED     19043    /tmp/orbit-colin/linc-17d1-0-22f2287c24046
unix  3      [ ]         STREAM     CONNECTED     19042    
unix  3      [ ]         STREAM     CONNECTED     19032    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     19031    
unix  3      [ ]         STREAM     CONNECTED     19027    /tmp/.ICE-unix/5945
unix  3      [ ]         STREAM     CONNECTED     19026    
unix  3      [ ]         STREAM     CONNECTED     19018    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19017    
unix  3      [ ]         STREAM     CONNECTED     19013    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19012    
unix  3      [ ]         STREAM     CONNECTED     18873    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18872    
unix  3      [ ]         STREAM     CONNECTED     18871    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     18870    
unix  3      [ ]         STREAM     CONNECTED     18869    /tmp/orbit-colin/linc-17c9-0-4451f9299cdf
unix  3      [ ]         STREAM     CONNECTED     18868    
unix  3      [ ]         STREAM     CONNECTED     18865    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     18864    
unix  3      [ ]         STREAM     CONNECTED     18860    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18859    
unix  3      [ ]         STREAM     CONNECTED     18733    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18732    
unix  3      [ ]         STREAM     CONNECTED     18731    /tmp/orbit-colin/linc-17be-0-4035b0ba2378a
unix  3      [ ]         STREAM     CONNECTED     18730    
unix  3      [ ]         STREAM     CONNECTED     18727    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     18726    
unix  3      [ ]         STREAM     CONNECTED     18737    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18687    
unix  3      [ ]         STREAM     CONNECTED     17802    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17801    
unix  3      [ ]         STREAM     CONNECTED     16188    /tmp/orbit-colin/linc-17b7-0-1f5b5b5abb8a7
unix  3      [ ]         STREAM     CONNECTED     16187    
unix  3      [ ]         STREAM     CONNECTED     16184    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     16183    
unix  3      [ ]         STREAM     CONNECTED     16179    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     16178    
unix  3      [ ]         STREAM     CONNECTED     16177    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16176    
unix  3      [ ]         STREAM     CONNECTED     16142    @/tmp/dbus-3HN7PgWDjN
unix  3      [ ]         STREAM     CONNECTED     16141    
unix  3      [ ]         STREAM     CONNECTED     16140    
unix  3      [ ]         STREAM     CONNECTED     16139    
unix  2      [ ]         STREAM     CONNECTED     16125    /tmp/keyring-Ufg4al/socket
unix  3      [ ]         STREAM     CONNECTED     16117    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16116    
unix  3      [ ]         STREAM     CONNECTED     16115    /tmp/orbit-colin/linc-1739-0-5a0b28c66f809
unix  3      [ ]         STREAM     CONNECTED     16114    
unix  3      [ ]         STREAM     CONNECTED     16111    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     16110    
unix  3      [ ]         STREAM     CONNECTED     16074    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16073    
unix  3      [ ]         STREAM     CONNECTED     16040    /tmp/orbit-colin/linc-1739-0-611bc5a2cb664
unix  3      [ ]         STREAM     CONNECTED     16039    
unix  3      [ ]         STREAM     CONNECTED     16036    /tmp/orbit-colin/linc-1734-0-3d51be68eb730
unix  3      [ ]         STREAM     CONNECTED     16035    
unix  3      [ ]         STREAM     CONNECTED     16031    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16030    
unix  3      [ ]         STREAM     CONNECTED     15447    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15446    
unix  3      [ ]         STREAM     CONNECTED     15434    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15433    
unix  3      [ ]         STREAM     CONNECTED     15121    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15120    
unix  2      [ ]         DGRAM                    14530    
unix  3      [ ]         STREAM     CONNECTED     14342    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     14341    
unix  4      [ ]         STREAM     CONNECTED     15122    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14337    
unix  3      [ ]         STREAM     CONNECTED     14025    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14024    
unix  2      [ ]         DGRAM                    14023    
unix  3      [ ]         STREAM     CONNECTED     14019    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14018    
unix  2      [ ]         DGRAM                    14017    
unix  3      [ ]         STREAM     CONNECTED     13959    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13958    
unix  2      [ ]         DGRAM                    13951    
unix  3      [ ]         STREAM     CONNECTED     13909    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13908    
unix  2      [ ]         DGRAM                    13907    
unix  3      [ ]         STREAM     CONNECTED     13618    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13617    
unix  3      [ ]         STREAM     CONNECTED     13612    
unix  3      [ ]         STREAM     CONNECTED     13611    
unix  2      [ ]         DGRAM                    13609    
unix  3      [ ]         STREAM     CONNECTED     13578    @/var/run/hald/dbus-KtpseBAJBw
unix  3      [ ]         STREAM     CONNECTED     13564    
unix  3      [ ]         STREAM     CONNECTED     13563    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13562    
unix  3      [ ]         STREAM     CONNECTED     13254    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13253    
unix  3      [ ]         STREAM     CONNECTED     13241    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     13240    
unix  3      [ ]         STREAM     CONNECTED     13233    @/var/run/hald/dbus-KtpseBAJBw
unix  3      [ ]         STREAM     CONNECTED     13231    
unix  3      [ ]         STREAM     CONNECTED     13232    @/var/run/hald/dbus-KtpseBAJBw
unix  3      [ ]         STREAM     CONNECTED     13221    
unix  3      [ ]         STREAM     CONNECTED     13172    @/var/run/hald/dbus-KtpseBAJBw
unix  3      [ ]         STREAM     CONNECTED     13144    
unix  3      [ ]         STREAM     CONNECTED     13171    @/var/run/hald/dbus-KtpseBAJBw
unix  3      [ ]         STREAM     CONNECTED     13142    
unix  3      [ ]         STREAM     CONNECTED     12996    @/var/run/hald/dbus-pqXmt2YEwF
unix  3      [ ]         STREAM     CONNECTED     12995    
unix  3      [ ]         STREAM     CONNECTED     12976    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12975    
unix  3      [ ]         STREAM     CONNECTED     12962    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12961    
unix  3      [ ]         STREAM     CONNECTED     12937    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12936    
unix  3      [ ]         STREAM     CONNECTED     12928    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12927    
unix  3      [ ]         STREAM     CONNECTED     12898    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12897    
unix  2      [ ]         DGRAM                    12893    
unix  3      [ ]         STREAM     CONNECTED     12872    
unix  3      [ ]         STREAM     CONNECTED     12871    
unix  2      [ ]         DGRAM                    12846

---

### Post by dentarthurdent on 2008-04-23
any ideas from the above netstat, or other things i should check? would a trojan on the LAN i'm on be trying to send me packets non-stop?

---

### Post by Monicker on 2008-04-23
> **dentarthurdent said:**
> any ideas from the above netstat, or other things i should check? would a trojan on the LAN i'm on be trying to send me packets non-stop?

I'm suprised nothing was listed as LISTENING in your netsttat. To verify try netstat -anltp.

You could also install bmon, to see if there is traffic to and from any particular ip addresses.

---

### Post by dentarthurdent on 2008-04-23
ok, here is netstat -anltp

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5205/cupsd      
```

---

### Post by Monicker on 2008-04-23
> **dentarthurdent said:**
> ok, here is netstat -anltp

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5205/cupsd      
```

Hrmm.  Cups is for printing services.  I can't imagine that creating a steady stream of inbound traffic, even if you were using it to share a printer.

---

