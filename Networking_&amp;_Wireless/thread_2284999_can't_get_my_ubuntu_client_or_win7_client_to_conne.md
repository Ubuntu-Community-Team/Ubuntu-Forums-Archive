---
title: "can't get my ubuntu client or win7 client to connect to my ubuntu server"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by Richard_Schwendler on 2015-07-02
I am running   ubuntu  14.04 LTS   server

         Using  DHCP server built into Fios router
              change range to  192.168.1.2  -  192.168.1.200
    BIND9 Complete DNS Server Configuration with hostname step by step

        Complete DNS server in ubuntu server 12.   Aug 10,2013 copied from ubuntuforums   and changed 

       server name = host name   =  muirfield
                    domain name  =  schwendler
                       zone      =   us

        First of all change the ip address of your server form DHCP to STATIC for this use the following command

        Code:

        sudo nano /etc/network/interfaces

       My  Code:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#  Wi-Fi card
auto wlan0
iface  wlan0  inet static 
address   192.168.1.240
netmask   255.255.255.0
gateway   192.168.1.1 

wpa-ssid  FiOS-6RK0G
wpa-psk   f43c3ee508f6f3693d6601018d5708438598f2c88bf0e463ef0f7e72ec
dns-nameservers 192.168.1.240 
       

        *I am leaving dns-nameserver empty and is commented we will come to it later.


        Restart networking daemons

        Code:

        Sudo service networking restart

        Before configuring a DNS server in linux Ubuntu you have to make domain name first and then you will proceed. First you will check your hostname command for this is

        Code:

        Sudo nano /etc/hostname

        My Server has the following name
     My    Code:

        muirfield

        (This is my Ubuntu server hostname yours might be different .You can change this according to your need)

        Now after hostname, you have to make domain name for your server. Say servername.domain.com it is better practice that whenever you are configuring server for home use or so, do not use .com but .hom or .net or whatever you like. Give the below command

        Code:

        Sudo nano /etc/hosts

        My Code:

        127.0.0.1         localhost
        192.168.1.240     muirfield.schwendler.us muirfield
 

        In my file 127.0.0.1 is for localhost and I have changed the second IP address 127.0.1.1 with my server IP that is 192.168.1.240 now I enter my domain name having my hostname muirfield first then my domain name schwendler.us and then alias muirfield. You can select of your own, hostname.abc.net or hostname.home.lan etc. but remember changing to this file need to restart your server and then login. Restart is must
        Now install BIND9

        Code:

        Sudo apt-get install bind9

        After installation just configure the below files step by step


            Named.conf.options
            Named.conf.local
            Named.conf.resolv.conf 


        Now configure file named.conf.options This file is use for DNS IPs It mean that your server must connect to some DNS outside. When you buy domain name from ISP’s they normally gives you their own DNS IPs. You can use open DNS IPs of google or so. In my case I am using my own ISP DNS IPs.

        Code:

        Sudo nano /etc/bind/named.conf.options

       My  Code:

        forwarders {
        # Give here your ISP DNS IP’s
        #192.168.1.1;     # gateway or route
        8.8.8.8;
        8.8.4.4;         #   google
        };

        Save the file and exit using control x press y and overwrite the file

        Now edit the file named.conf.local This is the file in which we define forward zones and reverse zones. It means that when we enter domain name it will translate it into IP address and when we enter IP address it will simply convert it into name.

        Code:

        Sudo nano /etc/bind/named.conf.local

      My  Code:
//
// Do any local configuration here
//

// Foward zone
zone "schwendler.us" {
     type master;
      file "/etc/bind/db.schwendler.us";
};
// reverse zone
zone "1.168.192.in-addr.arpa" {
      type master;
      file  "/etc/bind/db.192" ;
};


        Save the file and exit using control x press y and overwrite the file

        Now we will make these two database files db.schwendler.us and db.192 in zones folder

       
        


        Now in zones directory we will create two files first db.schwendler.us. I am just copying the db.local already present in /etc/bind folder to zones folder by changing its name to db.schwendler.us. I will put these IP’s in my db.schwendler.us file. Let’s start

        Code:

        Sudo cp /etc/bind/db.local /etc/bind/db.schwendler.us

        Now use the command below to edit the file

        Code:

        Sudo nano /etc/bind/db.schwendler.us

       My  Code:
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    muirfield.schwendler.us. mail.schwendler.net. (
                   2         ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
schwendler.us.    IN    NS      muirfield.schwendler.us.
schwendler.us.    IN    A    192.168.1.240
;@    IN    AAAA    ::1
muirfield         IN     A        192.168.1.240
gateway         IN     A        192.168.1.1
WWW             IN      CNAME        192.168.1.240

        Save it and exit

        mail.schwendler.us. is the email who will access name server. You can write any name instead webuser like admin, root or host master etc.
        Schwendler.us. is my NS means name server
        Schwendler.us.changing to IP 192.168.1.240

        @ IN A 127.0.0.1 and AAAA ::1 can be comment out you should not need it because db.local is already present in /etc/bind it is just a copy of that file. So no need you can delete it

        Changing Muirfield to IP 192.168.1.240

        Gateway to IP 192.168.1.1


        Last, I am using CNAME means canonical name it is just an alias to muirfield. Means that you can access your server by entering [www.schwendler.us]("http://www.schwendler.us") instead muirfield.schwendler.us . You can omit this or comment it. It is just up to you.


        Now create reverse lookup zone file

        Code:

        Sudo cp /etc/bind/db.127 /etc/bind/db.192

        Now use the command below to edit the file

        Code:

        Sudo nano /etc/bind/db.192

       My  Code:
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    muirfield.schwendler.us. mail.schwendler.us. (
                  2          ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN      NS      muirfield.    
240    IN    PTR    muirfield.schwendler.us.
240     IN      PTR     [www.schwendler.us]("http://www.schwendler.us").
1       IN      PTR     gateway.schwendler.us.
        ;


        Save it and exit

        Now when you are done with your zone file you have to check it whether it is working correctly or not by entering the command below for forward zone file

       my  Code:

        named-checkzone schwendler.us /etc/bind/db.schwendler.us

        Output
        Code:

        zone schwendler.us /IN: loaded serial 2
        Ok

        Now check the reverse zone file

       my  Code:

        named-checkzone schwendler.us /etc/bind/db.192

        Output
        Code:

        zone schwendler.us /IN: loaded serial 2
        Ok

        If the output of your named-checkzone is same as above then it is working fine otherwise you made some mistake in file.

        Now edit the file resolv.conf

        Code:

        Sudo nano /etc/resolv.conf

        Code:

        Nameserver 192.168.1.240
        domain schwendler.us
        search schwendler.us

        Enter the following lines into to your resolv.conf file and save it

        Now come to dns-nameservers (/etc/networking/interfaces) *check start of the this post
        you will now add the following code to /etc/networking/interfaces
        Code:

        dns-nameservers 192.168.1.240

        reason for this is that whenever you restart server /etc/resolv.conf file wash its contents
        Restart the bind

        Code:

        sudo service bind9 restart

        After bind start check your setting in log file

        Code:

        tail -f /var/log/syslog

        it must not have any error in the log

Jun 29 12:29:06 Muirfield named[5927]: zone 0.in-addr.arpa/IN: loaded serial 1
Jun 29 12:29:06 Muirfield named[5927]: zone 127.in-addr.arpa/IN: loaded serial 20152
Jun 29 12:29:06 Muirfield named[5927]: zone 1.168.192.in-addr.arpa/IN: loaded serial 2
Jun 29 12:29:06 Muirfield named[5927]: zone localhost/IN: loaded serial 2
Jun 29 12:29:06 Muirfield named[5927]: zone 255.in-addr.arpa/IN: loaded serial 1
Jun 29 12:29:06 Muirfield named[5927]: zone schwendler.us/IN: loaded serial 2
Jun 29 12:29:06 Muirfield named[5927]: all zones loaded
Jun 29 12:29:06 Muirfield named[5927]: running





        Checking forward zones

        Code:

        host –l schwendler.us

        Output should like this

        Code:
schwendler.us name server muirfield.schwendler.us.
schwendler.us has address 192.168.1.240
gateway.schwendler.us has address 192.168.1.1
muirfield.schwendler.us has address 192.168.1.240
        

        Now use NSLOOKUP

        Code:

        nslookup schwendler.us

        OUTPUT

        Code:

        Server: 192.168.1.240
        Address: 192.168.1.240#53

        Name: schwendler.us
        Address: 192.168.1.240

        Use DIG

        Code:

        Dig gateway.schwendler.us

        Code:
  ; <<>> DiG 9.9.5-3ubuntu0.2-Ubuntu <<>> gateway.schwendler.us
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10411
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;gateway.schwendler.us.        IN    A

;; ANSWER SECTION:
gateway.schwendler.us.    604800    IN    A    192.168.1.1

;; AUTHORITY SECTION:
schwendler.us.        604800    IN    NS    muirfield.schwendler.us.

;; ADDITIONAL SECTION:
muirfield.schwendler.us.    604800    IN    A    192.168.1.240

;; Query time: 0 msec
;; SERVER: 192.168.1.240#53(192.168.1.240)
;; WHEN: Mon Jun 29 15:36:50 EDT 2015
;; MSG SIZE  rcvd: 99


        Output should similar to the above, check status: NOERROR means it is resolving check ANSWER SECTION: gateway.schwendler.us is resolved into 192.168.1.1
        Checking reverse zone

        Code:

        host 192.168.1.1

        Output

        Code:

        1.1.168.192.in-addr.arpa domain name pointer gateway.schwendler.us

        If it gives you an error like below

        Code:

        host 1.1.168.192.in-addr.arpa. not found: 3(NXDOMAIN)

        This means that you made some mistake in /etc/bind/named.conf.local file in reverse zone If your server IP is 192.168.1.240 then your reverse zone looks like this

        zone "1.168.192.in-addr.arpa" {
        correct ip reversing
        };

        Sometime people made mistake in reversing the ip like (just an example)

        zone "0.168.192.in-addr.arpa" {
        incorrect ip reversing
        };

        Use NSLOOKUP

        Code:

        nslookup 192.168.1.1

        Code:

        Server: 192.168.1.240
        Address: 192.168.1.240#53

        1.1.168.192.in-addr.arpa name=gateway.schwendler.us

        If you get NXDOMAIN or SERVFAIL like errors it means that one of your zone file is not working correctly

        Test Your Server to Outside World
        Now you can ping ubuntu.com or dig ubuntu.com for the first time it will take several miliseconds to resolve the name ubuntu.com but when you run it second time, it will take form 1 to 10 mili seconds, its normal time and it means that your DNS is working properly

         Ping -c3 ubuntu.com
         ok

          dig     ubuntu.com   

            ok

 ******       Configuring clients  *********************

        windows 7  client   name richard-pc

        open network connections
        select change adapter settings
        select properties
        select internet protocol version IPv4


        and here give the IP address (in my case it is 192.168.1.240 have you remember win7pc)

        IP address 192.168.1.240
        Subnet Mask 255.255.255.0
        Default Gateway 192.168.1.1
        primary DNS 192.168.1.240 (my new BIND DNS server ip)
        select Advance (in the same window)
        select DNS tab
        Type in the text box below here In DNS Suffix for this connection:schwendler.us
        click ok
        click on validate setting upon exit
        click ok


        and you are done with it open CMD

        Code:

        ping muirfield

it gives you this  reply

  ping 192.168.1.240 with 32 bytes of data
  packets:  sent =4 received =4  lost =0    time 91 ms

        it must gives you some replies

        similarly

        Code:

        ping 192.168.1.1 or 240

 ping 192.168.1.240 with 32 bytes of data
packets:  sent =4 received =4  lost =0    time 100 ms

  ping 192.168.1.1 with 32 bytes of data
packets:  sent =4 received =4  lost =0    time 1 ms

        it must gives you some replies
        you can use NSLOOKUP

       code: nslookup muirfield

server: Fios_quantum_gateway.fios-router.home
address: 192.168.1.1
Name: muirfield.fios-router.home
address: 192.168.1.240

 ping  ubuntu.com
ok   157ms
 ping  192.168.1.240
ok     77ms
 Ping  schwendler.us  
  schwendler.us (92.242.140.21)  not found                                   ??
Ping  muirfield.schwendler.us  
  muirfield.schwendler.us (92.242.140.21)  not found 

firefox browser
code  192.168.1.240                >>      apache2 it works

code muirfield.fios-router.home    >>       apache2 it works

code [www.fios-router.home]("http://www.fios-router.home")           >>       server not found
     
code   [www.schwendler.us]("http://www.schwendler.us")            >>       server not found

code: nmap.org     schwendler.us      >>     schwendler.us (92.242.140.21)              ??
 

***********************************************
        ubuntu 14.04 CLIENTS     name  cadillac

ping   -c3  schwendler.us
         92.242.140.21                      ??

ping -c3 muirfield
          192.168.1.240

nslookup muirfield
server:  127.0.1.1
address:  127.0.1.1#53
name: muirfield.fios-router.home
address: 192.168.1.240

dig muirfield
question     muirfield    IN  A
answer       muirfield  0  IN  A     92.242.140.21    ??

nslookup   schwendler.us
server:   127.0.1.1
address:   127.0.1.1#53
name:  schwendler.us
address: 92.242.140.21                     ??

nslookup 192.168.1.1
server:  127.0.1.1
address:  127.0.1.1#53
  1.1.168.192.in-addr.arpa  name=Fios_quantum_gateway.fios-router.home

ping -c3 ubuntu.com
ok
ping -c3 192.168.1.240
ok
ping -c3 schwendler.us   
not found

firefox browser
code  192.168.1.240 
apache2 it works
code muirfield.fios-router.home
apache2     it works
code   schwendler.us
       server not found

****************** I  stoped here *************  I am using DHCP server in the Fios router and  dns server
      fios router  system setting
      local domain      fios-router.home                 change to    schwendler.us   ???

         verizon sends you to  92.242.140.21    for invalid  url
   could change Fios router  dns servers    xx.xx.xx.12   to   xx.xx.xx.14


        Code:

        sudo nano /etc/network/interfaces

        type the following lines
        Code:

        auto eth0
        iface eth0 inet dhcp

        Now restart Network Deamons
        Code:

        Sudo service networking restart

        to force client renew IP command
        Code:

        sudo dhclient -r

        Now obtain fresh IP:
        Code:

        sudo dhclient

        If you are running DHCP server on your system then enter the domain name and name server in dhcpd.conf file for example I have DNS server named muirfield and IP address is 192.168.1.240 like as under

        Code:
        option zone       us
        option server-name muirfield
        option domain-name schwendler;
        option domain-name-server  192.168.1.240;

        How to enable query logging in BIND
        To enable query logging execute rndc querylog command:
        Code:

        Sudo rndc querylog

        Check out query logging status by executing command:
        Code:

        Sudo rndc status

        Now you can view queries:
        Code:

        tail -f /var/log/syslog

        To disable it execute command again.
        Code:

        Sudo rndc querylog

        Our own Query Logging in BIND

        Code:

        Sudo nano /etc/bind/named.conf.local

        Add the following lines at the bottom of the file. You can use any channel to produce log file. You can use more than one channel as well.
        Code:

        logging {
            channel mylog_default {
                file "/var/log/mylogs/mylog.log" versions 3 size 12m;
                severity dynamic;
                print-time yes;
            };
        category default { mylog_default; };
        };

        After saving the file go to /var/log/ and make a mylogs folder and give it bind permission so that bind can write to it.
        Code:

        Sudo mkdir /var/log/mylogs

        Code:

        sudo chown bind:bind /var/log/mylogs

        Now after this you can make file mylog.log by using sudo nano mylog.log and save it in the directory mylogs or when you edit Apparmor it create the file automatically after restarting the bind, But at this time when you restart the bind it will not start and show fail. Because before named daemon can write to the new log file the AppArmor profile must be updated. First, edit
        Code:

        Sudo nano /etc/apparmor.d/usr.sbin.named

        And add:
        Code:

        /var/log/mylogs/mylog.log w,

        Next, reload the profile:
        Code:

        sudo cat /etc/apparmor.d/usr.sbin.named | sudo apparmor_parser -r

        It may give you some warnings
        Now restart bind
        Code:

        Sudo /etc/init.d/bind9 restart

        To check logs
        Code:

        Tail –f /var/log/mylogs/mylog.log

        Last edited by Profark; August 10th, 2013 at 03:37 PM.

---

