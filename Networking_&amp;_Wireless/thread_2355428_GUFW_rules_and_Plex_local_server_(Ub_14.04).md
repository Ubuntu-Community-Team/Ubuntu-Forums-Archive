---
title: "GUFW rules and Plex local server (Ub 14.04)"
date: 2017-03-12
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2017-03-12
I would really appreciate some help on setting up the GUFW firewall. 

My problems started because programs have been regularly freezing  and then unfreezing  if  I wait long enough. I have to wait a long time for data to populate a web page and sending out pop3 mail via google sometimes fails to engage with google's mail server. My desktop computer is an FM2A88X extreme6+. 

DMESG  showed a very high number of [UFW BLOCK] entries from 192.168.1.254 to 192.168.1.69 PROTO UDP SPT 1900 TTL64 DPT 53069.

Guessing the  problem with the frozen programs is partly to do with my set up of gufw:

[B]*Should I open all the ports that have PID/ Program Names  listed in the  netstat results below?*
[/B]

I referred to  this link:
[http://unix.stackexchange.com/questions/40619/uncomplicated-firewall-ufw-and-upnp](http://unix.stackexchange.com/questions/40619/uncomplicated-firewall-ufw-and-upnp)

Plex's advice as to ports to open is::

[HTML]The most important port to make sure your firewall allows is the main TCP port the Plex Media Server uses for communication:

    TCP: 32400 (for access to the Plex Media Server) [required]

The following ports are also used for different services:

    UDP: 1900 (for access to the Plex DLNA Server)
    TCP: 3005 (for controlling Plex Home Theater via Plex Companion)
    UDP: 5353 (for older Bonjour/Avahi network discovery)
    TCP: 8324 (for controlling Plex for Roku via Plex Companion)
    UDP: 32410, 32412, 32413, 32414 (for current GDM network discovery)
    TCP: 32469 (for access to the Plex DLNA Server)

Note: This article is discussing ports in the local firewall of the computer running Plex Media Server. This is not discussing ports on a router.[/HTML]

As my setup is not the same as the example script in the link,  I obtained these two reports:

**Netstat command**
```
robins@robins-desktop:~$ netstat -lptu --numeric-ports
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:32469           0.0.0.0:*               LISTEN      8806/Plex DLNA Serv
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:5943          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:1753            0.0.0.0:*               LISTEN      8806/Plex DLNA Serv
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:33887         0.0.0.0:*               LISTEN      9113/Plex Plug-in [
tcp        0      0 0.0.0.0:33029           0.0.0.0:*               LISTEN      3078/skype      
tcp        0      0 127.0.0.1:41063         0.0.0.0:*               LISTEN      8747/Plex Plug-in [
tcp        0      0 127.0.0.1:41994         0.0.0.0:*               LISTEN      9089/Plex Plug-in [
tcp        0      0 127.0.0.1:37642         0.0.0.0:*               LISTEN      8930/Plex Plug-in [
tcp        0      0 127.0.0.1:42730         0.0.0.0:*               LISTEN      8850/Plex Plug-in [
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:38255         0.0.0.0:*               LISTEN      8854/Plex Plug-in [
tcp        0      0 0.0.0.0:32400           0.0.0.0:*               LISTEN      8733/Plex Media Ser
tcp        0      0 127.0.0.1:32401         0.0.0.0:*               LISTEN      8733/Plex Media Ser
tcp        0      0 127.0.0.1:45138         0.0.0.0:*               LISTEN      9187/Plex Plug-in [
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
tcp6       0      0 :::445                  :::*                    LISTEN      -               
tcp6       0      0 :::139                  :::*                    LISTEN      -               
udp        0      0 0.0.0.0:631             0.0.0.0:*                           -               
udp        0      0 0.0.0.0:41744           0.0.0.0:*                           8806/Plex DLNA Serv
udp        0      0 0.0.0.0:59237           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           8806/Plex DLNA Serv
udp        0      0 0.0.0.0:1901            0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 127.0.0.1:59617         0.0.0.0:*                           3078/skype      
udp        0      0 192.168.1.69:43263      0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 192.168.1.69:43400      0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 0.0.0.0:36386           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:37112           0.0.0.0:*                           8806/Plex DLNA Serv
udp        0      0 0.0.0.0:53698           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:62074           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:45809           0.0.0.0:*                           -               
udp        0      0 192.168.1.69:54286      0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 127.0.0.1:38176         0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 127.0.0.1:38616         0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 0.0.0.0:47299           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:32410           0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 0.0.0.0:32412           0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 0.0.0.0:32413           0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 0.0.0.0:32414           0.0.0.0:*                           8733/Plex Media Ser
udp        0      0 0.0.0.0:8063            0.0.0.0:*                           8806/Plex DLNA Serv
udp        0      0 127.0.1.1:53            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 192.168.1.255:137       0.0.0.0:*                           -               
udp        0      0 192.168.1.69:137        0.0.0.0:*                           -               
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -               
udp        0      0 192.168.1.255:138       0.0.0.0:*                           -               
udp        0      0 192.168.1.69:138        0.0.0.0:*                           -               
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -               
udp        0      0 0.0.0.0:33029           0.0.0.0:*                           3078/skype      
udp6       0      0 :::33275                :::*                                -               
udp6       0      0 :::5353                 :::*                                -               
udp6       0      0 :::57675                :::*                                -               

```

**Lsof Command**
```
robins@robins-desktop:~$ lsof -i :1025-9999 +c 15
COMMAND  PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
Plex    8733 robins   78u  IPv4 136042      0t0  UDP *:1901 
Plex    8806 robins   12u  IPv4 138246      0t0  UDP *:1900 
Plex    8806 robins   15u  IPv4 137689      0t0  TCP *:1753 (LISTEN)
Plex    8806 robins   18u  IPv4 138253      0t0  UDP *:8063 
Plex    8806 robins   30u  IPv4 224675      0t0  UDP robins-desktop:49130->robins-desktop:8063 

```

To me the netstat output suggests Plex needs more ports open than listed in  plex site quote above.  Have I understood it properly?

***Is  samba essential to all Ubuntu installations however small? Can I safely uninstall it?  *** 

Looking at the sample scrip in the link,  I think I should also include the following although they do  not appearing in the netstats as open files:

[HTML]#  server's IP address
SERVERIP=192.168.1.?

# Local Network
LAN="192.168.1.0/255.255.0.0"

# open port for SSH
ufw allow OpenSSH

# open ports for Samba file sharing (not sure i need this so I have # them out for now)

#ufw allow from $LAN to   $SERVERIP app Samba
# ufw allow to   $LAN from $SERVERIP app Samba

#ufw allow from $LAN to $SERVERIP 137/udp # NetBIOS Name Service
#ufw allow from $LAN to $SERVERIP 138/udp # NetBIOS Datagram Service
#ufw allow from $LAN to $SERVERIP 139/tcp # NetBIOS Session Service
#ufw allow from $LAN to $SERVERIP 445/tcp # Microsoft Directory Service

#plex ports to be listed


# open ports for web services
ufw allow 80
ufw allow 443
ufw allow 8000:9999/tcp
ufw allow 8000:9999/udp

# Deny FTP
ufw deny 21/tcp


# open port for network time protocol (ntpd)
ufw allow ntp[/HTML]


Robin

---

### Post by TheFu on 2017-03-12
I run plex, but only block external stuff at the firewall. I do not use external plex stuff - don't even have a plex account and don't use any official plex clients. I find that DLNA clients work fine or the Kodi/PlexBMC addon for my playback devices.

No, you don't need samba for anything, unless you need it.  If you can, prefer NFS over Samba/CIFS for Plex or Kodi media storage. NFS is faster than CIFS and provides native file/directory permissions. Of course, to use NFS, you'll want the storage to be native linux file systems, not NTFS/FAT-whatever.

Sorry I'm not more help.

---

### Post by Robbyx on 2017-03-13
Thank you. I found it very helpful.  

I was  forced to use the external plex server because that was the only way I could find that worked to access the videos on my computer.  

I am using the Now/ Roku  server to send the videos to the TV and I am using the Plex software (version 1.4.3.3433)  to send the video from the computer to the Roku. 

It would help me greatly if you could refer me to  guidance as to how to set up the plex software so as to avoid going outside the LAN? Alternatively  I would also appreciate if  you could give me an outline here as to how you set up the plex software in your system so as to stay within the LAN.

---

### Post by TheFu on 2017-03-13
[https://support.plex.tv/hc/en-us/articles/201543147-What-network-ports-do-I-need-to-allow-through-my-firewall-](https://support.plex.tv/hc/en-us/articles/201543147-What-network-ports-do-I-need-to-allow-through-my-firewall-) is a list of network ports.  LAN access isn't the same as WAN access. All of these ports can be blocked on the WAN.  On the LAN, the services you want to allow should be open to the client devices you'd like to allow access. It depends on your knowledge to know which services you want/need on the LAN. I have disabled a few of them, since they don't make sense on my network and I'm willing to manually configure things.

I don't run any other programs capable of sharing data with the internet on my plex server.

Feel free to block all outbound connections from your plex server if you like. You can always unblock something if it doesn't work.  I only block the plex infrastructure which runs on Amazon - but I've been blocking amazon EC2 from my subnets for a long time. My plex server is headless, so not a desktop and it doesn't need access to many outside things - just things for ubuntu to be patched.

Most of my viewing is from Kodi (on a different machine) using DLNA that plex provides.  I'm not very impressed with the Plex app on the Roku. Compared to Kodi, it sucks. Also not a fan of the Plex app on any platform. Most of my issues are with their overlay placement. Can't believe they overlay OVER subtitles when paused. Sorta defeats the purpose of pause, IMHO. I pause to read the subtitles.

---

### Post by Robbyx on 2017-03-13
Thanks for responding. You explained that you " run plex, but only block external stuff at the firewall". Seems worth my copying that approach. Do I therefore just set up rules within Gufw  allowing all the ports as mentioned in your referral, to be open?   I have another firewall in the Router  which I assume I leave alone for this purpose, on the assumption that firewall will deal with external ip addresses.. 

Robin

---

### Post by TheFu on 2017-03-13
My WAN gateway blocks outbound connections based on source/target IPs and subnets. It is BSD and uses pf. 
My internal router also runs pf to keep different subnets separate - kids/games are blocked from my business and parent's subnet. The guest subnet is outside all of those.

Don't have any idea how to do that on most home routers. Don't remember seeing any web interface on any that allows this config.

---

### Post by TheFu on 2017-08-19
Beware that Plex corporate has decided to change their privacy policy next month. [https://www.plex.tv/about/privacy-policy-update-notice/](https://www.plex.tv/about/privacy-policy-update-notice/) Each person will need to decide if that change is allowable in their environment.

I've skimmed it. They are interested in file metadata EXCLUDING file names - resolution, codecs, tracks, etc., length of time used, and 3rd party service use.  So if you are using Plex via Alexa, they want to know that.

I don't think it is time for pitch forks.

> This information may include metadata about the media (such as title, duration, author, cover art, dates associated with the media, and other relevant information) and information about the media itself (such as resolution, bit rate, format, location, etc.).

Well, perhaps it is time for pitch forks after all, assuming you don't block your plex machine from internet access.

---

