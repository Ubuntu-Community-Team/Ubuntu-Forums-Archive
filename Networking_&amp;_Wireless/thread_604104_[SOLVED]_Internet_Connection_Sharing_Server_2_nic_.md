---
title: "[SOLVED] Internet Connection Sharing Server 2 nic cards"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by SpiritIsReality on 2007-11-05
howdy
InternetConnectionSharing

Example of server with 2 nic cards.

All of the following information can be found here
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com](https://help.ubuntu.com)

The router in this setup serves dhcp addresses from 192.168.0.100 to 192.168.0.120 
(see router manual) to a 192.168.0.0 network.
The server is a regular ubuntu desktop with monitor, keyboard, mouse.
sharing it's internet connection with other desktop computers.
The server is one of several computers on the 192.168.0.0 network.
(other computers on the 192.168.0.0 network are not shown in the attachments of post #2)
The server needs a static eth0 address outside the range of the router's dhcp addresses.
The server has a static eth0 address of 192.168.0.140 , the cable going to the router.
The server has a static eth1 address of 192.168.1.1 , the cable leading to the switch -> to the clients.
The clients are two Ubuntu and one xp.
The client addresses are static  192.168.1.2 , 192.168.1.3 , and 192.168.1.4
(In this example , the Ubuntu server is not running dhcp3-server)
This is what I did to get internet connection sharing working.

Preparing the Server
1.
please see attachments of post #2
2 nic cards in server
eth0 connected to router, to internet
eth1 connected to switch, to clients
eth1 closer to the edge of the motherboard, closer to the bottom of case.
(reference: [http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm) )
--------------------
2.
7.10 alternate install cd.
chose eth0 as nic card to use for install.
When the install starts to configure the network dhcp, cancel, or go back, and select
manual configuration.
In this case, I entered the address as 192.168.0.140 , and then accepted the default
netmask, gateway, and dns.
After the install,
I edited the /etc/apt/sources.list file by adding a # in front of the cdrom line.
Press and hold the ALT key, type the F2 key, release all.
Type, or cut and paste, in the run box,
Code:

gksudo gedit /etc/apt/sources.list

#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
-------------
save and close file.(click File -> Save, and click File -> Quit)
System -> Help and Support -> Advanced Topics -> Installing Server Applications
or [https://help.ubuntu.com/](https://help.ubuntu.com/)
--------------
3.
/etc/network/interfaces of server
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.140
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

# The secondary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        # gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
----------------
/etc/resolv.conf of server
nameserver 192.168.0.1
----------------
4.
clients ip addresses would be 192.168.1.2 , 192.168.1.3 , 192.168.1.4 ...
/etc/network/interfaces of client 192.168.1.2
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    #dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.0.1
---------------
/etc/resolv.conf of client
nameserver 192.168.0.1
---------------
xp client configure
Start -> Control Panel -> Network Connections -> right click Local Area Connection ->
Properties -> click on Internet Protocol(TCP/IP) , click on Properties -> 
click Use the following IP address
IP address 192.168.1.4
Subnet mask 255.255.255.0
Default gateway 192.168.1.1
click Use the following DNS server address
Preferred DNS server 192.168.0.1
click OK, click Close

[http://www.okaay.com/windows-xp-tips/how-to-make-your-ip-static/](http://www.okaay.com/windows-xp-tips/how-to-make-your-ip-static/)
[http://www.google.ca/search?hl=en&q=xp+%22static+ip%22&btnG=Google+Search&meta=]("http://www.google.ca/search?hl=en&q=xp+%22static+ip%22&btnG=Google+Search&meta=")
[http://www.google.ca/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=xp+tcp/ip+settings&spell=1](http://www.google.ca/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=xp+tcp/ip+settings&spell=1)
--------------
make sure the clients can ping each other and the eth1 of server.
ping 192.168.1.1
Ctrl-C to stop. (press and hold Ctrl key, tap the c key)
if the pings are unsuccessful, there is something wrong with the configuration done so
far that needs correcting before moving on.
[http://rob.pectol.com/content/view/5/28/](http://rob.pectol.com/content/view/5/28/)
---------------
5.
[https://wiki.edubuntu.org/ThinClientHowtoNAT](https://wiki.edubuntu.org/ThinClientHowtoNAT)
( [https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano) or use gksudo gedit /etc/network/options )
fred@piii:~$ cd /etc/network
fred@piii:/etc/network$ ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces
fred@piii:/etc/network$ sudo touch iptions
[sudo] password for fred:
fred@piii:/etc/network$ ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces  iptions
fred@piii:/etc/network$ cd
fred@piii:~$ sudo nano -w /etc/network/options
fred@piii:~$ cat /etc/network/options
ip_forward=yes
spoofprotect=yes
syncookies=no
fred@piii:~$ cat /proc/sys/net/ipv4/ip_forward
0
fred@piii:~$ sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
fred@piii:~$ cat /proc/sys/net/ipv4/ip_forward
1
fred@piii:~$ sudo iptables --table nat --append POSTROUTING --jump MASQUERADE  --source 192.168.1.0/24
fred@piii:~$ echo 'client can reach internet'
client can reach internet

-----------------
[COLOR=blue]If server is shutdown and restarted[/COLOR], the clients have no internet connection.
I tried pinging, it was ok, between clients and clients to server.
For clients to reach internet, I have to run these 2 commands:
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
sudo iptables --table nat --append POSTROUTING --jump MASQUERADE --source 192.168.1.0/24
then the clients can reach the internet.
---------------------
server restarted, clients have no internet connection.

fred@piii:~$ cat /proc/sys/net/ipv4/ip_forward
0
fred@piii:~$ sudo iptables -t nat -n -L
[sudo] password for fred:
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
fred@piii:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
fred@piii:~$ sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
fred@piii:~$ cat /proc/sys/net/ipv4/ip_forward
1
fred@piii:~$ sudo iptables --table nat --append POSTROUTING --jump MASQUERADE --source 192.168.1.0/24
fred@piii:~$ sudo iptables -t nat -n -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  0    --  192.168.1.0/24       0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
fred@piii:~$ 
----------
clients can reach internet.

-------------------------------------
When installing Ubuntu on a client, check the /etc/network/interfaces and /etc/resolv.conf files.
/etc/network/interfaces for clients eth0
 dns-nameservers 192.168.0.1
(the same as the servers dns-nameservers)

/etc/resolv.conf
 nameserver 192.168.0.1
(the same as the servers nameserver)
-----------------------
Internet Connection Sharing Documentation [http://ubuntuforums.org/showthread.php?t=503287](http://ubuntuforums.org/showthread.php?t=503287)
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring)
[https://wiki.edubuntu.org/ThinClientHowtoNAT](https://wiki.edubuntu.org/ThinClientHowtoNAT)
[https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing](https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing)
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
ubuntuforums.org advanced search, iptables, titles only, tutorials and tips forum.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
If you would like to use Firestarter to manage iptables [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)
How-To set up Internet connection sharing and how to network your xbox
[http://ubuntuforums.org/showthread.php?t=103881](http://ubuntuforums.org/showthread.php?t=103881)
Internet Connection Sharing with only one NIC [http://ubuntuforums.org/showthread.php?t=551826](http://ubuntuforums.org/showthread.php?t=551826)

(correction in step 5
 sudo nano -w /etc/network/options
) tx
 trails

---

### Post by SpiritIsReality on 2007-11-05
howdy
oops!...here's the attachments.
trails

---

### Post by amados on 2007-12-07
Hi, I am trying configure my network with 2 nic.
The command ...:**~$ sudo -w nano /etc/network/options**   bring this error:
sudo: illegal option `-w'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

What can I do?

---

### Post by holepunch on 2007-12-26
I too had the same problem when following the otherwise excellent instructions.  I got round it by using gedit instead of nano.

sudo gedit /etc/network/options

Then I cut and pasted the three following lines into the document that came up,

I'm not sure if that was the right thing to do but it seems to be working fine so far.

---

### Post by kevdog on 2007-12-26
Could someone write a specfic tutorial on how to do this?  Im really glad you got it working.  This feature is a recurring request, and it would be nice if there were one definitive post out there to point to.

---

### Post by bradbase on 2008-02-02
A quick correction:
~$ sudo -w nano /etc/network/options

Creates an error because it was published incorrectly.  It should be;

~$ sudo nano -w /etc/network/options

The -w is a switch for nano, not sudo.  The switch ensures there is no word wrap (so your config file doesn't break if a line rolls over the edge of your screen).

---

