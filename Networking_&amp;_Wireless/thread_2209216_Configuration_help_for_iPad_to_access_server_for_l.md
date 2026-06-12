---
title: "Configuration help for iPad to access server for local webpage development testing"
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by Thomas_Sprich on 2014-03-04
Hello to the forum,

I am new to HTML and servers but have started a project to develop a webpage. I am using Apache2.  I can test it with the virtual host name in the address bar of firefox from my computer. I however want to test the webpage on my iPad which is connected to Ubuntu through the WiFi hotspot. On searching the internet (links below) I have seen that it can be done by using proxies on the iPad but I am unable to make it work and am looking for help as to what I should do.

I am going to explain the steps that I followed so that you understand what my setup looks like.

Firstly:
I am testing it on a virtual host on ubuntu 13.10 (not server edition) that I set up using this guide.

Consequently my "/etc/hosts" file looks as follows:

```
127.0.0.1    localhost
127.0.0.1    test.local
127.0.1.1    thomas-TravelMate-5720

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

The *.conf file for my file in /etc/apache2/sites-available is as follows:

```
Listen *:8080
<VirtualHost *:8080>

 # Admin email, Server Name (domain name) and any aliases
 ServerAdmin webmaster@test.local
 ServerName  test.local
 ServerAlias www.test.local
                      
                
 # Index file and Document Root (where the public files are located)
 DirectoryIndex index.php index.html
 DocumentRoot /var/www/Project2/htdocs
                                    
                                    
 # Custom log file locations
 LogLevel warn
 ErrorLog  /var/www/Project2/logs/error.log
 CustomLog /var/www/Project2/logs/access.log combined

<Directory /var/www/Project2/htdocs>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
#    Order allow, deny
    Allow from all    

</Directory>

    ProxyRequests On

    <Proxy *>
        Order Deny,Allow
        Deny from all
        Allow from 10
    </Proxy>
</VirtualHost>
```

I have enabled this file with:
sudo a2ensite my-proxy.conf
sudo services apache2 restart

Secondly:
Now I am trying to use the information by Manuel Razzari from this forum to make the iPad talk to the server using proxies. This is the reason I inserted the following code into my "my-proxy.conf" file above in what I think is the right place:
```
Listen *:8080
<VirtualHost *:8080>
    ProxyRequests On

    <Proxy *>
        Order Deny,Allow
        Deny from all
        Allow from 10
    </Proxy>
</VirtualHost>
```

Thirdly:
According to the internet, I should now be able to put proxy information for the server (i.e 127.0.0.1 in my case) with the port information (8080)
My iPad's IP address is 10.42.0.49. Also the WiFi hotspot network doesn't have access to the internet.

The results of ifconfig when the iPad is connected is in case this helps:

```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:1a:a2:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:79657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6123200 (6.1 MB)  TX bytes:6123200 (6.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:ac:28:01  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:feac:2801/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:94912866 (94.9 MB)  TX bytes:21676937 (21.6 MB)
```

The above outlines my setup. With this setup, according to what I have read should allow me to access my webpage on my local host by typing "test.local" in Safari's address bar. This however does not work.

So my question is how do I configure my computer so that I can access my webpage from my iPad? I am open to other suggestions as to what to do if someone has a better answer. Is it possible to do what I want to do?

Please let me know if there is any other information that you need.

Thanks for the help in advance!

---

### Post by Thomas_Sprich on 2014-03-09
Bump

---

