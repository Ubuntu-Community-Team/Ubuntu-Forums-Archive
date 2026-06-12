---
title: "Ubuntu-XP home network : etc/network/interfaces file problem"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2007-08-02
I had 2 spare PC lying around one with XP installed and the other was ond old machine on which I decided to use as a Linux server.
What I eventually want to do is to use the linux box as a web/ftp/samba server for the XP machine the physical connection being a crossover patch cable.
Neither of them are connected to the Internet. 

OK here goes !
Installed Ubuntu 7.04 server edition.Everything went ok.
Had to browse the CD to install all the Samba debian files and managed to find the one dependency, libcupsys2, on the net.
Samba was installed with no problems, smb.conf configured and up and running.

I assigned the Ubuntu box an IP of 192.168.0.1 with the command

```


ifconfig eth0 192.168.0.1 netmask 255.255.255.0 up


```


Went into XP,

Network Connection -> TCP/IP -> Add , configured WINS , IP of 192.168.0.1 etc.
Manually assigned the IP 192.168.0.2 to the XP box.
Rebooted.
Pinged from Ubuntu ( 192.168.0.1 ) to XP ( 192.168.0.2) worked fine and visa versa. Excellent I thought, the machines are hooked up.
The fun started when I tried to map the network drive.

On Ubuntu I had edited the /etc/network/interfaces file. Here it is :

```


auto eth0 
iface eth0 net static 
address 192.168.0.1 
netmask 255.255.255.0 
network 192.168.0.0
broadcast 192.168.0.255 
gateway 192.168.0.1 ( also tried leaving this blank )


```


I restarted the network session /etc/init.d/networking restart
and got the following error message:

```


/etc/network/interfaces :6: unknown address type
ifdown : couldn't find interfaces file "etc/network/interfaces
 unknown address type 
ifup : couldn't find interfaces file "etc/network/interfaces" FAIL


```


I assume that this basically states that the network is not up ?
When I came to mapping the drive in windows I tried putting in both name (\\ubuntu\home\samba) and IP address (\\192.168.0.1\home\samba) in the address fields. I made sure that the correct samba user name and password were used but still got the error :

```


Drive cannot be mapped because no network was found .


```


I can still ping successfully between the two machines. Just from first thoughts I fear that my etc/network/interfaces file is not correctly configured. Any pointers ?

Here is my /etc/host file as well :

```


127.0.0.1 local host 
192.168.0.1 ubuntu


```

As I am not going to connect to the net I do not have to configure dhcp / DNS do I ?

Thanks !


Uncle

---

### Post by noob12 on 2007-08-02
typo address family should be **inet**
> 
auto eth0 
iface eth0 [COLOR="Red"]inet[/COLOR] static 
address 192.168.0.1 
netmask 255.255.255.0 
network 192.168.0.0
broadcast 192.168.0.255 
gateway 192.168.0.1 ( also tried leaving this blank )


---

### Post by spd106 on 2007-08-02
Looking over the interfaces file it appears that you have a typo on the second line, 

```
auto eth0 
iface eth0 [COLOR="Red"]i[/COLOR]net static 
address 192.168.0.1 
netmask 255.255.255.0 
network 192.168.0.0
broadcast 192.168.0.255 
gateway 192.168.0.1 ( also tried leaving this blank )
```

As there's no routing going on, you don't need a gateway and in any case it should be the IP address of the interface on the other PC. You don't need the network or broadcast lines either, but they're harmless.

---

### Post by uncle-c on 2007-08-02
Thanks a million guys. It is late night here in London, so will give it a go in the morning and let u know how it went. Thanks a lots for all the help, much appreciated.

uncle

---

### Post by uncle-c on 2007-08-03
Excellent news guys. You solved part of the problem !
I  finally got the two machines linked up. The etc/network/interfaces file needed the missing "i" in inet and I omitted the network/broadcast/gateway lines.  When I restarted networking there were no errors.
I still could not map the drive from Windows UNTIL I edited the smb.conf file and set  the "force group" to =  blank. Then I mapped the drive no problem and could share the files on my Linux with the XP box. I came across the smb.conf file problem  somewhere else and I'm sure the reasoning for this has been well documented. I will read it thoroughly
Thanks for the help ! Next project is to set up an FTP server on this Linux box !

Cheers,
Uncle.

---

