---
title: "[SOLVED] SSH into 8.04 Server from Mac OS X Leopard"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by LarryB90 on 2008-07-31
Hello everyone. First Post! :)

Here's the situation. I have the following setup:

[LIST]
[*]An Ubuntu 8.05 server box
[*]Macs running OS X Leopard
[*]An Apple Airport Extreme
[/LIST]

The Ubuntu box is wired to the Airport Extreme, the other computers are networking wirelessly.

I have been following the steps of that blog post [[LINK]]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") to setup an ftp server. However, I'm having problems with step 11.

I tried to establish an SSH connection by using the following command:

```
ssh -l LarryB 10.0.1.XXX
```

I got the XXX number from an inet number of en0 using ```
ifconfig
```

Unfortunately I got the following error:
```
ssh: connect to host 10.0.1.XXX port 22: Connection refused
```

Therefore I had to map port 22 of my apple airport extreme. I did so using  this guide [[LINK]]("http://portforward.com/english/routers/port_forwarding/Apple/AirPortExtreme/SSH.htm").

I did so, however I still get the ```
ssh: connect to host 10.0.1.XXX port 22: Connection refused
``` error.

---

### Post by kevdog on 2008-07-31
If the ssh daemon or server running?  By default if there is a listening process on port 22, there should be no firewall blocking access unless you are running firestarter or configured a firewall.

---

### Post by LarryB90 on 2008-07-31
The server is running. However, nobody is logged in at the momment.

The firewall on my mac seems to be disabled.[IMG]http://img176.imageshack.us/img176/7695/firewallac1.png[/IMG]

Here is a screenshot of my SSH port mapping in my Airport Extreme:
[IMG]http://img329.imageshack.us/img329/5837/sshairporthc6.png[/IMG]

---

### Post by kevdog on 2008-07-31
Which computer is running the server?  I was under the impression that ubuntu was running the daemon and the MAC the client?

---

### Post by LarryB90 on 2008-07-31
The Ubuntu Server is installed on an old pc made out of spare parts. I'm trying to ssh into it using the terminal of a macintosh computer. I'm sorry for the confusion.

---

### Post by kevdog on 2008-07-31
So from the MAC machine if you use the nmap utility (may need to install it) and you do

nmap -p 22 <server ip address> 

What output do you get?

Can you verify that the server is actually running on the old machine using the netstat command?

---

### Post by LarryB90 on 2008-07-31
Okay. I'm installing nmap, however I can't seem to configure the build system. 

I can't configure it since it doesn't find gcc in my $PATH.

EDIT: As for Netstat:

Active Internet connections
Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
tcp4       0      0  10.0.1.197.50117       yw-in-f18.google.https ESTABLISHED
tcp4       0      0  10.0.1.197.50116       yw-in-f18.google.https ESTABLISHED
tcp6       0      0  Laurent-Boileaus.49964 CPE001ff340e4e7-.winfs ESTABLISHED
tcp6       0      0  Laurent-Boileaus.49963 CPE001ff340e4e7-.winfs ESTABLISHED
tcp4       0      0  10.0.1.197.49702       clarke.freenode..6667  ESTABLISHED
udp4       0      0  10.0.1.197.kerberos    *.*                    
udp6       0      0  Laurent-Boileaus.kerbe *.*                    
udp6       0      0  localhost.kerberos     *.*                    
udp4       0      0  10.0.1.197.ntp         *.*                    
udp6       0      0  Laurent-Boileaus.ntp   *.*                    
udp4       0      0  *.*                    *.*                    
udp6       0      0  localhost.ntp          *.*                    
udp4       0      0  localhost.ntp          *.*                    
udp6       0      0  localhost.ntp          *.*                    
udp6       0      0  *.ntp                  *.*                    
udp4       0      0  *.ntp                  *.*                    
udp6       0      0  *.mdns                 *.*                    
udp4       0      0  *.mdns                 *.*                    
udp4       0      0  *.*                    *.*                    
icm6       0      0  *.*                    *.*                    
Active LOCAL (UNIX) domain sockets
Address  Type   Recv-Q Send-Q    Inode     Conn     Refs  Nextref Addr
 31eca18 stream      0      0        0  32c0bb0        0        0 /var/run/mDNSResponder
 32c0bb0 stream      0      0        0  31eca18        0        0
 31eccc0 stream      0      0        0  32c0cc0        0        0 /var/run/mDNSResponder
 32c0cc0 stream      0      0        0  31eccc0        0        0
 31ecc38 stream      0      0        0  31ec990        0        0 /var/run/mDNSResponder
 31ec990 stream      0      0        0  31ecc38        0        0
 31ecd48 stream      0      0        0  31ec908        0        0
 31ec908 stream      0      0        0  31ecd48        0        0
 3b8f990 stream      0      0        0  3b8fa18        0        0 /var/run/mDNSResponder
 3b8fa18 stream      0      0        0  3b8f990        0        0
 32c0a18 stream      0      0        0  32c0908        0        0 /var/run/mDNSResponder
 32c0908 stream      0      0        0  32c0a18        0        0
 32c0330 stream      0      0        0  32c03b8        0        0 /var/run/mDNSResponder
 32c03b8 stream      0      0        0  32c0330        0        0
 32c0110 stream      0      0        0  32c0198        0        0
 32c0198 stream      0      0        0  32c0110        0        0
 32c02a8 stream      0      0        0  32c0220        0        0 /var/run/usbmuxd
 32c0220 stream      0      0        0  32c02a8        0        0
 32c05d8 stream      0      0        0  32a6220        0        0 /var/run/mDNSResponder
 32a6220 stream      0      0        0  32c05d8        0        0
 32a6dd0 stream      0      0        0  32a6550        0        0 /var/run/mDNSResponder
 32a6550 stream      0      0        0  32a6dd0        0        0
 32a67f8 stream      0      0        0  31ec220        0        0
 31ec220 stream      0      0        0  32a67f8        0        0
 31ec550 stream      0      0        0  32a6880        0        0
 32a6880 stream      0      0        0  31ec550        0        0
 32a6110 stream      0      0        0  31ec110        0        0
 31ec110 stream      0      0        0  32a6110        0        0
 32a6e58 stream      0      0  38bf6c0        0        0        0 /tmp/launch-4PlmZx/:0
 32c0770 stream      0      0  38bf7e0        0        0        0 /tmp/launch-DckKMW/Listeners
 32c0f68 stream      0      0  38bf900        0        0        0 /tmp/launch-Cpkpoj/Render
 32a6908 stream      0      0        0  32a66e8        0        0
 32a66e8 stream      0      0        0  32a6908        0        0
 31ecbb0 stream      0      0        0  31ec7f8        0        0
 31ec7f8 stream      0      0        0  31ecbb0        0        0
 32c0d48 stream      0      0        0  31ec000        0        0
 31ec000 stream      0      0        0  32c0d48        0        0
 32c0dd0 stream      0      0  357ad00        0        0        0 /tmp/launchd-63.GvsSGL/sock
 32c0990 stream      0      0        0  32c0880        0        0
 32c0880 stream      0      0        0  32c0990        0        0
 32a6088 stream      0      0        0  32a62a8        0        0 /var/run/mDNSResponder
 32a62a8 stream      0      0        0  32a6088        0        0
 32a6d48 stream      0      0        0  32c07f8        0        0 /var/run/mDNSResponder
 32c07f8 stream      0      0        0  32a6d48        0        0
 32c0e58 stream      0      0        0  32c0ee0        0        0
 32c0ee0 stream      0      0        0  32c0e58        0        0
 32a63b8 stream      0      0        0  32a6440        0        0
 32a6440 stream      0      0        0  32a63b8        0        0
 32a65d8 stream      0      0        0  32a6660        0        0
 32a6660 stream      0      0        0  32a65d8        0        0
 32a6c38 stream      0      0        0  32a6cc0        0        0
 32a6cc0 stream      0      0        0  32a6c38        0        0
 31ec5d8 stream      0      0        0  31ec660        0        0 /var/run/mDNSResponder
 31ec660 stream      0      0        0  31ec5d8        0        0
 31ec770 stream      0      0        0  31ec6e8        0        0 /var/run/mDNSResponder
 31ec6e8 stream      0      0        0  31ec770        0        0
 31ecaa0 stream      0      0        0  31ecb28        0        0
 31ecb28 stream      0      0        0  31ecaa0        0        0
 31ece58 stream      0      0  31be290        0        0        0 /var/run/pppconfd
 31ecee0 stream      0      0        0  2cef000        0        0
 2cef000 stream      0      0        0  31ecee0        0        0
 2cef110 stream      0      0        0  2cef198        0        0
 2cef198 stream      0      0        0  2cef110        0        0
 2cef2a8 stream      0      0        0  2cef220        0        0 /var/run/mDNSResponder
 2cef220 stream      0      0        0  2cef2a8        0        0
 2cef330 stream      0      0        0  2cef440        0        0
 2cef440 stream      0      0        0  2cef330        0        0
 2cef550 stream      0      0        0  2cef4c8        0        0
 2cef4c8 stream      0      0        0  2cef550        0        0
 2cef5d8 stream      0      0        0  2cef6e8        0        0
 2cef6e8 stream      0      0        0  2cef5d8        0        0
 2cef770 stream      0      0        0  2cef880        0        0
 2cef880 stream      0      0        0  2cef770        0        0
 2cef990 stream      0      0        0  2cef908        0        0
 2cef908 stream      0      0        0  2cef990        0        0
 2cefa18 stream      0      0        0  2cefaa0        0        0
 2cefaa0 stream      0      0        0  2cefa18        0        0
 2cefc38 stream      0      0  2e1b370        0        0        0 /var/tmp/launchd/sock
 2cefcc0 stream      0      0  2e1b490        0        0        0 /private/var/run/cupsd
 2cefd48 stream      0      0  2e1b5b0        0        0        0 /var/run/usbmuxd
 2cefe58 stream      0      0  2e1b6d0        0        0        0 /var/run/asl_input
 2ceff68 stream      0      0  2e1b760        0        0        0 /var/run/portmap.socket
 2cefee0 stream      0      0  2e1b7f0        0        0        0 /var/run/mDNSResponder
 3b8fbb0 dgram       0      0        0  31ecdd0  31ecdd0        0
 31ecdd0 dgram       0      0        0  3b8fbb0  3b8fbb0        0
 3b8fd48 dgram       0      0        0  32c0550  32c0550        0
 32c0550 dgram       0      0        0  3b8fd48  3b8fd48        0
 31ec3b8 dgram       0      0        0  3b8fc38  3b8fc38        0
 3b8fc38 dgram       0      0        0  31ec3b8  31ec3b8        0
 3b8faa0 dgram       0      0        0  3b8fb28  3b8fb28        0
 3b8fb28 dgram       0      0        0  3b8faa0  3b8faa0        0
 3b8fcc0 dgram       0      0        0  32c04c8  32c04c8        0
 32c04c8 dgram       0      0        0  3b8fcc0  3b8fcc0        0
 3b8fdd0 dgram       0      0        0  3b8fe58  3b8fe58        0
 3b8fe58 dgram       0      0        0  3b8fdd0  3b8fdd0        0
 3b8fee0 dgram       0      0        0  3b8ff68  3b8ff68        0
 3b8ff68 dgram       0      0        0  3b8fee0  3b8fee0        0
 32c0088 dgram       0      0        0  32c0000  32c0000        0
 32c0000 dgram       0      0        0  32c0088  32c0088        0
 32c0440 dgram       0      0        0  2cefdd0        0  32a6770
 32a6990 dgram       0      0        0  32a6aa0  32a6aa0        0
 32a6aa0 dgram       0      0        0  32a6990  32a6990        0
 32a6770 dgram       0      0        0  2cefdd0        0  32a6000
 31ec440 dgram       0      0        0  32a6ee0  32a6ee0        0
 32a6ee0 dgram       0      0        0  31ec440  31ec440        0
 32a6000 dgram       0      0        0  2cefdd0        0  32a6198
 32a6198 dgram       0      0        0  2cefdd0        0  32a6a18
 32a6a18 dgram       0      0        0  2cefdd0        0  32a6f68
 32a6f68 dgram       0      0        0  2cefdd0        0  32a6b28
 32c0c38 dgram       0      0        0  32c0aa0  32c0aa0        0
 32c0aa0 dgram       0      0        0  32c0c38  32c0c38        0
 32a6b28 dgram       0      0        0  2cefdd0        0  31ec198
 31ec198 dgram       0      0        0  2cefdd0        0  31ec880
 32c06e8 dgram       0      0        0  32a64c8  32a64c8        0
 32a64c8 dgram       0      0        0  32c06e8  32c06e8        0
 31ec4c8 dgram       0      0        0  31ec088  31ec088        0
 31ec088 dgram       0      0        0  31ec4c8  31ec4c8        0
 31ec880 dgram       0      0        0  2cefdd0        0  2cef3b8
 31ecf68 dgram       0      0        0  2cef088  2cef088        0
 2cef088 dgram       0      0        0  31ecf68  31ecf68        0
 2cef3b8 dgram       0      0        0  2cefdd0        0  2cef660
 2cef660 dgram       0      0        0  2cefdd0        0  2cef7f8
 2cef7f8 dgram       0      0        0  2cefdd0        0        0
 2cefdd0 dgram       0      0  2e1b640        0  32c0440        0 /var/run/syslog

10.0.1.196 Doesn't seem to be there... However it does show up in my finder as a PC Server.

---

### Post by kevdog on 2008-07-31
Sorry I got you into that mess.  Ive never run a MAC OS X.  Im not sure how to tell you to compile.  Have you seen this page:

[http://nmap.org/book/inst-macosx.html](http://nmap.org/book/inst-macosx.html)

For ubuntu systems nmap is in the archive so its as easy as
sudo aptitude install nmap

---

### Post by kevdog on 2008-07-31
netstat -an ??

---

### Post by LarryB90 on 2008-07-31
Yeah, I was on that page following the instructions, but I didn't get my dragon. ;)

If only there were an apt-get for mac os x. Sigh. haha!

I found something interesting though, I found that I can ssh into my own computer... The purpose eludes me for now though.

---

### Post by LarryB90 on 2008-07-31
Net Stat -an output

```
Active Internet connections (including servers)
Proto Recv-Q Send-Q  Local Address          Foreign Address        (state)
tcp4       0      0  10.0.1.197.22          10.0.1.197.50134       ESTABLISHED
tcp4       0      0  10.0.1.197.50134       10.0.1.197.22          ESTABLISHED
tcp4       0      0  *.88                   *.*                    LISTEN
tcp6       0      0  *.88                   *.*                    LISTEN
tcp6       0      0  fe80::21e:52ff:f.50133 fe80::21f:f3ff:f.5009  ESTABLISHED
tcp6       0      0  fe80::21e:52ff:f.50132 fe80::21f:f3ff:f.5009  ESTABLISHED
tcp46      0      0  *.5900                 *.*                    LISTEN
tcp4       0      0  *.22                   *.*                    LISTEN
tcp6       0      0  *.22                   *.*                    LISTEN
tcp4       0      0  *.548                  *.*                    LISTEN
tcp6       0      0  *.548                  *.*                    LISTEN
tcp4       0      0  127.0.0.1.631          *.*                    LISTEN
tcp6       0      0  ::1.631                *.*                    LISTEN
udp4       0      0  10.0.1.197.123         *.*                    
udp6       0      0  fe80::21e:52ff:f.123   *.*                    
udp4       0      0  10.0.1.197.88          *.*                    
udp6       0      0  fe80::21e:52ff:f.88    *.*                    
udp6       0      0  fe80::1%lo0.88         *.*                    
udp4       0      0  *.*                    *.*                    
udp6       0      0  ::1.123                *.*                    
udp4       0      0  127.0.0.1.123          *.*                    
udp6       0      0  fe80::1%lo0.123        *.*                    
udp6       0      0  *.123                  *.*                    
udp4       0      0  *.123                  *.*                    
udp6       0      0  *.5353                 *.*                    
udp4       0      0  *.5353                 *.*                    
udp4       0      0  *.*                    *.*                    
icm6       0      0  *.*                    *.*                    
Active LOCAL (UNIX) domain sockets
Address  Type   Recv-Q Send-Q    Inode     Conn     Refs  Nextref Addr
 3b8f908 stream      0      0        0  3b8fd48        0        0
 3b8fd48 stream      0      0        0  3b8f908        0        0
 31eca18 stream      0      0        0  32c0bb0        0        0 /var/run/mDNSResponder
 32c0bb0 stream      0      0        0  31eca18        0        0
 31eccc0 stream      0      0        0  32c0cc0        0        0 /var/run/mDNSResponder
 32c0cc0 stream      0      0        0  31eccc0        0        0
 31ecd48 stream      0      0        0  31ec908        0        0
 31ec908 stream      0      0        0  31ecd48        0        0
 3b8f990 stream      0      0        0  3b8fa18        0        0 /var/run/mDNSResponder
 3b8fa18 stream      0      0        0  3b8f990        0        0
 32c0a18 stream      0      0        0  32c0908        0        0 /var/run/mDNSResponder
 32c0908 stream      0      0        0  32c0a18        0        0
 32c0330 stream      0      0        0  32c03b8        0        0 /var/run/mDNSResponder
 32c03b8 stream      0      0        0  32c0330        0        0
 32c0110 stream      0      0        0  32c0198        0        0
 32c0198 stream      0      0        0  32c0110        0        0
 32c02a8 stream      0      0        0  32c0220        0        0 /var/run/usbmuxd
 32c0220 stream      0      0        0  32c02a8        0        0
 32c05d8 stream      0      0        0  32a6220        0        0 /var/run/mDNSResponder
 32a6220 stream      0      0        0  32c05d8        0        0
 32a6dd0 stream      0      0        0  32a6550        0        0 /var/run/mDNSResponder
 32a6550 stream      0      0        0  32a6dd0        0        0
 32a67f8 stream      0      0        0  31ec220        0        0
 31ec220 stream      0      0        0  32a67f8        0        0
 31ec550 stream      0      0        0  32a6880        0        0
 32a6880 stream      0      0        0  31ec550        0        0
 32a6110 stream      0      0        0  31ec110        0        0
 31ec110 stream      0      0        0  32a6110        0        0
 32a6e58 stream      0      0  38bf6c0        0        0        0 /tmp/launch-4PlmZx/:0
 32c0770 stream      0      0  38bf7e0        0        0        0 /tmp/launch-DckKMW/Listeners
 32c0f68 stream      0      0  38bf900        0        0        0 /tmp/launch-Cpkpoj/Render
 32a6908 stream      0      0        0  32a66e8        0        0
 32a66e8 stream      0      0        0  32a6908        0        0
 31ecbb0 stream      0      0        0  31ec7f8        0        0
 31ec7f8 stream      0      0        0  31ecbb0        0        0
 32c0d48 stream      0      0        0  31ec000        0        0
 31ec000 stream      0      0        0  32c0d48        0        0
 32c0dd0 stream      0      0  357ad00        0        0        0 /tmp/launchd-63.GvsSGL/sock
 32c0990 stream      0      0        0  32c0880        0        0
 32c0880 stream      0      0        0  32c0990        0        0
 32a6088 stream      0      0        0  32a62a8        0        0 /var/run/mDNSResponder
 32a62a8 stream      0      0        0  32a6088        0        0
 32a6d48 stream      0      0        0  32c07f8        0        0 /var/run/mDNSResponder
 32c07f8 stream      0      0        0  32a6d48        0        0
 32c0e58 stream      0      0        0  32c0ee0        0        0
 32c0ee0 stream      0      0        0  32c0e58        0        0
 32a63b8 stream      0      0        0  32a6440        0        0
 32a6440 stream      0      0        0  32a63b8        0        0
 32a65d8 stream      0      0        0  32a6660        0        0
 32a6660 stream      0      0        0  32a65d8        0        0
 32a6c38 stream      0      0        0  32a6cc0        0        0
 32a6cc0 stream      0      0        0  32a6c38        0        0
 31ec5d8 stream      0      0        0  31ec660        0        0 /var/run/mDNSResponder
 31ec660 stream      0      0        0  31ec5d8        0        0
 31ec770 stream      0      0        0  31ec6e8        0        0 /var/run/mDNSResponder
 31ec6e8 stream      0      0        0  31ec770        0        0
 31ecaa0 stream      0      0        0  31ecb28        0        0
 31ecb28 stream      0      0        0  31ecaa0        0        0
 31ece58 stream      0      0  31be290        0        0        0 /var/run/pppconfd
 31ecee0 stream      0      0        0  2cef000        0        0
 2cef000 stream      0      0        0  31ecee0        0        0
 2cef110 stream      0      0        0  2cef198        0        0
 2cef198 stream      0      0        0  2cef110        0        0
 2cef2a8 stream      0      0        0  2cef220        0        0 /var/run/mDNSResponder
 2cef220 stream      0      0        0  2cef2a8        0        0
 2cef330 stream      0      0        0  2cef440        0        0
 2cef440 stream      0      0        0  2cef330        0        0
 2cef550 stream      0      0        0  2cef4c8        0        0
 2cef4c8 stream      0      0        0  2cef550        0        0
 2cef5d8 stream      0      0        0  2cef6e8        0        0
 2cef6e8 stream      0      0        0  2cef5d8        0        0
 2cef770 stream      0      0        0  2cef880        0        0
 2cef880 stream      0      0        0  2cef770        0        0
 2cef990 stream      0      0        0  2cef908        0        0
 2cef908 stream      0      0        0  2cef990        0        0
 2cefa18 stream      0      0        0  2cefaa0        0        0
 2cefaa0 stream      0      0        0  2cefa18        0        0
 2cefc38 stream      0      0  2e1b370        0        0        0 /var/tmp/launchd/sock
 2cefcc0 stream      0      0  2e1b490        0        0        0 /private/var/run/cupsd
 2cefd48 stream      0      0  2e1b5b0        0        0        0 /var/run/usbmuxd
 2cefe58 stream      0      0  2e1b6d0        0        0        0 /var/run/asl_input
 2ceff68 stream      0      0  2e1b760        0        0        0 /var/run/portmap.socket
 2cefee0 stream      0      0  2e1b7f0        0        0        0 /var/run/mDNSResponder
 32c0550 dgram       0      0        0  2cefdd0        0  32c0440
 3b8fbb0 dgram       0      0        0  31ecdd0  31ecdd0        0
 31ecdd0 dgram       0      0        0  3b8fbb0  3b8fbb0        0
 3b8faa0 dgram       0      0        0  3b8fb28  3b8fb28        0
 3b8fb28 dgram       0      0        0  3b8faa0  3b8faa0        0
 3b8fcc0 dgram       0      0        0  32c04c8  32c04c8        0
 32c04c8 dgram       0      0        0  3b8fcc0  3b8fcc0        0
 3b8fdd0 dgram       0      0        0  3b8fe58  3b8fe58        0
 3b8fe58 dgram       0      0        0  3b8fdd0  3b8fdd0        0
 3b8fee0 dgram       0      0        0  3b8ff68  3b8ff68        0
 3b8ff68 dgram       0      0        0  3b8fee0  3b8fee0        0
 32c0088 dgram       0      0        0  32c0000  32c0000        0
 32c0000 dgram       0      0        0  32c0088  32c0088        0
 32c0440 dgram       0      0        0  2cefdd0        0  32a6770
 32a6990 dgram       0      0        0  32a6aa0  32a6aa0        0
 32a6aa0 dgram       0      0        0  32a6990  32a6990        0
 32a6770 dgram       0      0        0  2cefdd0        0  32a6000
 31ec440 dgram       0      0        0  32a6ee0  32a6ee0        0
 32a6ee0 dgram       0      0        0  31ec440  31ec440        0
 32a6000 dgram       0      0        0  2cefdd0        0  32a6198
 32a6198 dgram       0      0        0  2cefdd0        0  32a6a18
 32a6a18 dgram       0      0        0  2cefdd0        0  32a6f68
 32a6f68 dgram       0      0        0  2cefdd0        0  32a6b28
 32c0c38 dgram       0      0        0  32c0aa0  32c0aa0        0
 32c0aa0 dgram       0      0        0  32c0c38  32c0c38        0
 32a6b28 dgram       0      0        0  2cefdd0        0  31ec198
 31ec198 dgram       0      0        0  2cefdd0        0  31ec880
 32c06e8 dgram       0      0        0  32a64c8  32a64c8        0
 32a64c8 dgram       0      0        0  32c06e8  32c06e8        0
 31ec4c8 dgram       0      0        0  31ec088  31ec088        0
 31ec088 dgram       0      0        0  31ec4c8  31ec4c8        0
 31ec880 dgram       0      0        0  2cefdd0        0  2cef3b8
 31ecf68 dgram       0      0        0  2cef088  2cef088        0
 2cef088 dgram       0      0        0  31ecf68  31ecf68        0
 2cef3b8 dgram       0      0        0  2cefdd0        0  2cef660
 2cef660 dgram       0      0        0  2cefdd0        0  2cef7f8
 2cef7f8 dgram       0      0        0  2cefdd0        0        0
 2cefdd0 dgram       0      0  2e1b640        0  32c0550        0 /var/run/syslog

```

---

### Post by kevdog on 2008-07-31
netstat --tcp --listening --programs

---

### Post by kevdog on 2008-07-31
Ok so it looks like it is listening:

tcp4       0      0  *.22                   *.*                    LISTEN
tcp6       0      0  *.22                   *.*                    LISTEN


Can you confirm on the server you can do a 

ssh localhost 

and connect?

---

### Post by dmizer on 2008-07-31
Just a word of caution, the portmaping in your airport extreme has been configured to allow connections from the internet on port 22, and forward them to 10.0.1.196.

This configuration will have no effect on your local network, it only effects how your airport handles traffic coming from the internet.  The airport will assume that all local traffic is trusted.

---

### Post by LarryB90 on 2008-07-31
> **kevdog said:**
> netstat --tcp --listening --programs

That command doesn't work in os x.

After a bit of research I found a similar command:

```
sudo lsof -i -P
```

with the following output:
```
COMMAND   PID           USER   FD   TYPE    DEVICE SIZE/OFF   NODE NAME
launchd     1           root   13u  IPv6 0x2b3dbe8      0t0    TCP localhost:631 (LISTEN)
launchd     1           root   14u  IPv4 0x2e26e64      0t0    TCP localhost:631 (LISTEN)
launchd     1           root   53u  IPv6 0x2b3d984      0t0    TCP *:548 (LISTEN)
launchd     1           root   55u  IPv4 0x2e26a68      0t0    TCP *:548 (LISTEN)
launchd     1           root   60u  IPv6 0x2b3d720      0t0    TCP *:22 (LISTEN)
launchd     1           root   61u  IPv4 0x2e2666c      0t0    TCP *:22 (LISTEN)
configd    14           root    8u  IPv4 0x2b3ada0      0t0    UDP *:*
configd    14           root   12u  IPv6 0x3256e78      0t0 ICMPV6 *:*
mDNSRespo  16 _mdnsresponder    7u  IPv4 0x2b3abf0      0t0    UDP *:5353
mDNSRespo  16 _mdnsresponder    8u  IPv6 0x2b3ab18      0t0    UDP *:5353
ntpd       25           root   20u  IPv4 0x2b3aa40      0t0    UDP *:123
ntpd       25           root   21u  IPv6 0x2b3a968      0t0    UDP *:123
ntpd       25           root   22u  IPv6 0x2b3a890      0t0    UDP localhost:123
ntpd       25           root   23u  IPv4 0x2b3a608      0t0    UDP localhost:123
ntpd       25           root   24u  IPv6 0x2b3a530      0t0    UDP localhost:123
ntpd       25           root   25u  IPv6 0x2b39450      0t0    UDP Laurent-Boileaus-MacBook.local:123
ntpd       25           root   26u  IPv4 0x2b3a1d0      0t0    UDP 10.0.1.197:123
krb5kdc    52           root    9u  IPv6 0x2b38d90      0t0    UDP localhost:88
krb5kdc    52           root   10u  IPv6 0x2b37f38      0t0    UDP Laurent-Boileaus-MacBook.local:88
krb5kdc    52           root   11u  IPv4 0x2b39d98      0t0    UDP 10.0.1.197:88
krb5kdc    52           root   12u  IPv6 0x2b3cd90      0t0    TCP *:88 (LISTEN)
krb5kdc    52           root   13u  IPv4 0x3d02270      0t0    TCP *:88 (LISTEN)
AppleVNCS  95 laurentboileau    4u  IPv6 0x2b3d258      0t0    TCP *:5900 (LISTEN)
SystemUIS 102 laurentboileau   10u  IPv4 0x2b39f48      0t0    UDP *:*
Camino    118 laurentboileau   25u  IPv4 0x4453270      0t0    TCP 10.0.1.197:50167->yo-in-f147.google.com:80 (ESTABLISHED)
Camino    118 laurentboileau   32u  IPv4 0x4445e64      0t0    TCP 10.0.1.197:50165->64.111.215.214:80 (ESTABLISHED)
AirPort   420 laurentboileau   10u  IPv6 0x2b3c8c8      0t0    TCP Laurent-Boileaus-MacBook.local:50132->CPE001ff340e4e7-CM0012c90b2a3a.local:5009 (ESTABLISHED)
AirPort   420 laurentboileau   13u  IPv6 0x2b3cb2c      0t0    TCP Laurent-Boileaus-MacBook.local:50133->CPE001ff340e4e7-CM0012c90b2a3a.local:5009 (ESTABLISHED)

```

---

### Post by kevdog on 2008-07-31
Im confused.  You only need port 22 or the ssh daemon running on the server, not on the client, unless you want both computers to be both clients and servers.  It does seem however that the ssh servers are setup on both machines.

You need user accounts on both machines also.

---

### Post by LarryB90 on 2008-07-31
> **kevdog said:**
> Ok so it looks like it is listening:

tcp4       0      0  *.22                   *.*                    LISTEN
tcp6       0      0  *.22                   *.*                    LISTEN


Can you confirm on the server you can do a 

ssh localhost 

and connect?

Oh! I still get the port 22 connection refused error on the ubuntu server.

> **dmizer said:**
> Just a word of caution, the portmaping in your airport extreme has been configured to allow connections from the internet on port 22, and forward them to 10.0.1.196.

This configuration will have no effect on your local network, it only effects how your airport handles traffic coming from the internet.  The airport will assume that all local traffic is trusted.

That may explain the problem. I mapped the port for incoming traffic instead of opening it for local traffic. Could it be that I have to open port 22 on the ubuntu box?

---

### Post by LarryB90 on 2008-07-31
> **kevdog said:**
> Im confused.  You only need port 22 or the ssh daemon running on the server, not on the client, unless you want both computers to be both clients and servers.  It does seem however that the ssh servers are setup on both machines.

You need user accounts on both machines also.

I want the following configuration:

Server: Ubuntu box
Client: Mac Computer

---

### Post by kevdog on 2008-07-31
If you are on the server, can you ssh to the box itself:

ssh localhost?

On the server, install nmap, and do
nmap localhost

---

### Post by LarryB90 on 2008-07-31
> **kevdog said:**
> If you are on the server, can you ssh to the box itself:

ssh localhost?


No I get:

```
ssh: connect to host localhost port 22: Connection refused
```

> **kevdog said:**
> 
 On the server, install nmap, and do
nmap localhost

Output of nmap:

```
Interesting ports on localhost (127.0.0.1)
not shown: 1709 closed ports
PORT     STATE    SERVICE
80/tcp   open     http
139/tcp  open     netbios-ssn
445/tcp  open     microsoft-ds
901/tcp  open     samba-swat
3306/tcp open     mysql
```

---

### Post by kevdog on 2008-07-31
Wierd -- nmap would suggest on the server that port 22 is closed.

Can you do the following (all from the server):

sudo /etc/init.d/ssh restart

sudo iptables -L

nmap -p 22 localhost

---

### Post by LarryB90 on 2008-07-31
> **kevdog said:**
> Wierd -- nmap would suggest on the server that port 22 is closed.

Can you do the following (all from the server):

sudo /etc/init.d/ssh restart


No. 

```
sudo: /etc/init.d/ssh: command not found
```

> **kevdog said:**
> sudo iptables -L


Yes.
```

Chain INPUT (policy ACCEPT)
target     prot opt source           destination

Chain FORWARD (policy ACCEPT)
target     prot opt source           destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source           destination

```

> **kevdog said:**
> nmap -p 22 localhost
[/QUOTE]

Yes. and I think we have the culprit.

```
Interesting ports on localhost (127.0.0.1):
PORT     STATE    SERVICE
22/tcp   closed   ssh
```

---

### Post by kevdog on 2008-07-31
Ok -- install the server

sudo aptitude install openssh-server

---

### Post by LarryB90 on 2008-07-31
Done. Port is now open according to nmap -p 22 localhost

---

### Post by kevdog on 2008-07-31
Ok

now try

sudo /etc/init.d/ssh restart

nmap -p 22 localhost

ssh localhost

---

### Post by LarryB90 on 2008-07-31
> It worked!!! It actually worked! They thought I was mad but it worked!!!

:guitar: Thank you guys!!! It works.

I can now log into the server using an ssh connection from any local machine.

Great! Exactly what I wanted. I'll try to hook it up with dyndns.org once I get some time to.

Thanks guys! Thanks are being sent.

---

### Post by kevdog on 2008-07-31
You might want to harden you ssh server by doing one or combo of the following before opening it up to the big bad world:

change port 22 to something else
disallow passwords and only allow keys
Restrict users/groups/etc from inside server configuration file
Configure iptables/fail2ban/denyhosts to limit access to those who will use the ssh server
Configure iptables/fail2ban/denyhosts to deny specific ip access for a period of time if more than x number of failed access attempts are performed
Use PortKnocker for "ultimate security" 

Just some ideas.  It seems like some of these ideas are either well supported or hated by other users in these forums.

---

### Post by LarryB90 on 2008-07-31
Ok thank you for the links. I'll look into that during the weekend. I'll be sure to secure it down before putting it out for all the world to see. Thank you again for your help.

---

