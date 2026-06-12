---
title: "I give Up"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by tropdoug on 2008-08-14
I am not happy jan -- for the first time with linux, I am stumped. 

I have been trying for a week or more to connect two linux computers for simple file sharing and despite some great help cannot get it done. So I gave up and installed nfs

however I am still confused. From what I gather nfs is a true server application for thin clients. Thats not exactly what I want, and I certainly do not want to leave my desktop machine running all day just to serve files to my laptop. Its environmentally wasteful.

What I want is a linux solution to the equivalent of a "home office" network in that other system (shhhh windows) attached is a diagram with IP addresses and home file names exactly as they actually are. 

Could someone help me by 

a) explaining what application I want, and why. 
b) writing the exact commands to use to configure the application using the actual ip addresses and names rather than 'user/mnt/filesystem .... which I find very confusing

Hope someone can assist 

Douglas

---

### Post by lisati on 2008-08-14
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) might be of some help.

---

### Post by tropdoug on 2008-08-14
Thanks for the suggestion Lisati, I should have said I would rather not use samba as predominately it is for networking a linux to windows box, and this is two linux dedicated boxes. I managed to get a one way connection with sshfs but couldnt get it the other way. Nfs is the next thought except for what I wrote above, so here I am --- annoyed (sort of lol)

---

### Post by SpaceTeddy on 2008-08-14
[EDIT]
i guess this is obsolete if you have already tried ssh - didn't see your post as i was still typing my answer - just ignore this :)
[/EDIT]

as a different approach i usually suggest ssh in this case. I think it is just easier to setup than samba - but that is me (maybe i just don't like the idea of a windows protocol being use between two ubuntu machines).

On both machines, install the openssh-server packages:
```
sudo apt-get install openssh-server
```

after that is done, open your filebrowser and type the following in the adressbar:
```
ssh://user@ip
```

where user is the user of the other machine and ip is the ip of the other machine... so from, your exmpale, i would say on Desktop you would type:
> ssh://kim@10.1.1.4
you should first get a complaint that the host is unkown (yes - you want to connect) and then it should ask you for a username and password (the username is already filled in)

once that is supplied you can browse the other computer as if you were on it logged in as kim.

As i said, this is my solution (as i think it is easier than samba). I personally always use sshf for the job, but that is another story.
Also - i used the IP - not the name of the computer. Why ? because i do not know if the name resolution works proberly at your place - so i just chose the safe way. If the names work, you can use them aswell)

hope it helps :)

---

### Post by tropdoug on 2008-08-14
Space Teddy your a genius --- I have been fighting with sshfs for the last week, your the first person that told me I could use my file browser, I was trying the terminal. Anyway I have 50% success. I can connect using nautilus with the command as written from the laptop to the desktop and browse to what I need. Great. However if I try the other way, from the desktop to the laptop using ssh://douglas@10.1.1.4  - access is denied the same if I try ssh://kim@10.1.1.4 

I checked and do have openssh-server on the desktop as well. any ideas what would cause this? Would it be because my connection from desktop to router is via ethernet, whereas the connection from laptop to router is wireless?

---

### Post by SpaceTeddy on 2008-08-14
mhm sice the network connectivity is given i would say that this is a ssh problem (i.e. the reverse connection works) - what happens if yo ssh from the laptop to the desktop (from the console). Does it time out ? Does it reject ? Does it give you any other error message ?

And i don't think it has anything to do with your router (or it shouldn't) as you are in the same subnet segment... The router could technically prevent it - but for some reason i doubt that. Nonetheless, check the config - and check if you can ping from the laptop to the desktop.

As a sidenote - there is a bug in gvfs which reduces the speed of the network connection by about 2/3 - so where as you would be copying with 5 Mbyte/sec with sftp/sshfs you will only get about 1.6Mbyte/sec with gvfs (via the filebrowser). This does not make a whole lot of difference on small files, but it you move large amounts you might want to consider this.

hope we can figure this out.

---

### Post by tropdoug on 2008-08-14
Ok, from the terminal no problem from laptop to desktop, but same access denied when I go the other way. 

I really apreciate the progress, but I have to log off now - get some sleep before work tomorrow, I will check tomorrow evening. 

Thanks for getting me this far :-)

Doug

---

### Post by SpaceTeddy on 2008-08-15
mhm - can ssh to the machine on itself ? i.e. on the laptop try ssh://localhost ? is there any firewall installed there ? have you made sure that the openssh-server is really running ?

i am just guessing here :(

---

### Post by tropdoug on 2008-08-15
Hmmm  veryyy interesting. 

The desktop will not connect to the laptop, I get an "Access Denied" message 
The laptop WILL connect to the desktop just fine.

The desktop WILL connect to itself using ssh://localhost just fine
The laptop will not connect to itself using ssh://localhost I get the "access denied" message

So Its weird to say the least

---

### Post by SpaceTeddy on 2008-08-15
can you please check if the openssh-server is running properly ?
what does
> sudo netstat -lnp
ps aux |grep ssh

say ? is there an ssh server listed there ?
if so, what IP is it bound to ?

i am just guessing now...

---

### Post by tropdoug on 2008-08-20
Sorry its been a while I have been away working :(

Ok here is the output from the commands 

```
 douglas@desktop:~$ sudo netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4597/portmap        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5410/cupsd          
tcp6       0      0 :::22                   :::*                    LISTEN     5685/sshd           
udp        0      0 0.0.0.0:32769           0.0.0.0:*                          5380/avahi-daemon:  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          5380/avahi-daemon:  
udp        0      0 0.0.0.0:111             0.0.0.0:*                          4597/portmap        
udp        0      0 10.1.1.3:123            0.0.0.0:*                          5664/ntpd           
udp        0      0 127.0.0.1:123           0.0.0.0:*                          5664/ntpd           
udp        0      0 0.0.0.0:123             0.0.0.0:*                          5664/ntpd           
udp6       0      0 ::1:123                 :::*                               5664/ntpd           
udp6       0      0 fe80::20f:eaff:fe85:123 :::*                               5664/ntpd           
udp6       0      0 :::123                  :::*                               5664/ntpd           
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     17200    5024/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     20069    5879/dbus-daemon    @/tmp/dbus-ytLnnA8Fk8
unix  2      [ ACC ]     STREAM     LISTENING     17475    5216/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     20837    6033/mapping-daemon /tmp/mapping-douglas
unix  2      [ ACC ]     STREAM     LISTENING     19329    5593/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     19091    5380/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     17587    5287/hald           @/var/run/hald/dbus-DlDUtaf1jM
unix  2      [ ACC ]     STREAM     LISTENING     17584    5287/hald           @/var/run/hald/dbus-URjgbV1Nku
unix  2      [ ACC ]     STREAM     LISTENING     19373    5638/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     19726    5828/gnome-keyring- /tmp/keyring-N7VVVF/socket
unix  2      [ ACC ]     STREAM     LISTENING     19811    5873/ssh-agent      /tmp/ssh-rDzUrG5831/agent.5831
unix  2      [ ACC ]     STREAM     LISTENING     19827    5875/gconfd-2       /tmp/orbit-douglas/linc-16f3-0-4883dff61adcf
unix  2      [ ACC ]     STREAM     LISTENING     19837    5831/x-session-mana /tmp/orbit-douglas/linc-16c7-0-727196172bead
unix  2      [ ACC ]     STREAM     LISTENING     20055    5831/x-session-mana /tmp/.ICE-unix/5831
unix  2      [ ACC ]     STREAM     LISTENING     19152    5410/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     20089    5881/gnome-settings /tmp/orbit-douglas/linc-16f9-0-be312fa36451
unix  2      [ ACC ]     STREAM     LISTENING     20143    5895/gnome-volume-m /tmp/orbit-douglas/linc-1704-0-be312faa9c4c
unix  2      [ ACC ]     STREAM     LISTENING     20161    5889/gnome-panel    /tmp/orbit-douglas/linc-1701-0-be312fab7a15
unix  2      [ ACC ]     STREAM     LISTENING     20248    5891/nautilus       /tmp/orbit-douglas/linc-1703-0-793b14ae283f9
unix  2      [ ACC ]     STREAM     LISTENING     20331    5934/gnome-vfs-daem /tmp/orbit-douglas/linc-172e-0-325c38a370ea7
unix  2      [ ACC ]     STREAM     LISTENING     20348    5897/bonobo-activat /tmp/orbit-douglas/linc-1709-0-e9e8c4814e77
unix  2      [ ACC ]     STREAM     LISTENING     20405    5987/gnome-screensa /tmp/orbit-douglas/linc-174f-0-75c9ed3974ac3
unix  2      [ ACC ]     STREAM     LISTENING     20471    5998/bluetooth-appl /tmp/orbit-douglas/linc-176e-0-7f4e6090b5c29
unix  2      [ ACC ]     STREAM     LISTENING     20581    6019/gnome-power-ma /tmp/orbit-douglas/linc-177a-0-72ee0d0568404
unix  2      [ ACC ]     STREAM     LISTENING     20585    6000/update-notifie /tmp/orbit-douglas/linc-1770-0-45ad064a6a9b8
unix  2      [ ACC ]     STREAM     LISTENING     20589    5997/vino-session   /tmp/orbit-douglas/linc-176d-0-45ad064a6b384
unix  2      [ ACC ]     STREAM     LISTENING     20601    5995/gtk-window-dec /tmp/orbit-douglas/linc-176b-0-8089a4772a39
unix  2      [ ACC ]     STREAM     LISTENING     20635    6017/nm-applet      /tmp/orbit-douglas/linc-1781-0-72ee0d05a1e82
unix  2      [ ACC ]     STREAM     LISTENING     20658    5996/compiz.real    /tmp/orbit-douglas/linc-176c-0-2e045e60445a2
unix  2      [ ACC ]     STREAM     LISTENING     20812    6003/drapes         /tmp/orbit-douglas/linc-1773-0-46aedfd7691a0
unix  2      [ ACC ]     STREAM     LISTENING     20878    6036/trashapplet    /tmp/orbit-douglas/linc-1794-0-7322492379d5f
unix  2      [ ACC ]     STREAM     LISTENING     22150    6067/python         /tmp/orbit-douglas/linc-17b3-0-1f34597b2d05e
unix  2      [ ACC ]     STREAM     LISTENING     22190    6073/mixer_applet2  /tmp/orbit-douglas/linc-17b9-0-2273bda5b99fd
unix  2      [ ACC ]     STREAM     LISTENING     22374    6085/fast-user-swit /tmp/orbit-douglas/linc-17c5-0-2aa1c5cf137cd
unix  2      [ ACC ]     STREAM     LISTENING     22422    6094/firefox-bin    /tmp/orbit-douglas/linc-17ce-0-66eb6277b056a
unix  2      [ ACC ]     STREAM     LISTENING     22736    6112/gnome-terminal /tmp/orbit-douglas/linc-17e0-0-1e5c2223132e
unix  2      [ ACC ]     STREAM     LISTENING     17567    5266/dbus-daemon    @/tmp/dbus-KmDjD0s5Zw
douglas@desktop:~$ ps aux |grep ssh
root      5685  0.0  0.0   5280   964 ?        Ss   17:40   0:00 /usr/sbin/sshd
douglas   5873  0.0  0.0   4432   540 ?        Ss   17:42   0:00 /usr/bin/ssh-agent x-session-manager
douglas   6135  0.0  0.0   2988   764 pts/0    R+   17:48   0:00 grep ssh
douglas@desktop:~$ 

```

---

