---
title: "Cant access apache webserver outside/inside local network"
date: 2015-03-15
forum: Networking &amp; Wireless
---

### Post by onemic on 2015-03-15
I apologize in advance if I use any technical words in the wrong way. I'm still a newbie to Linux/networking

Ive been trying to figure out this problem for over a week and none of the related questions others have asked have helped me. I recently built a webserver running on apache2 to host my own website. I also intended to use it for SSH, FTP, and VNC. I registered a domain at GoDaddy, cokongwu.com. A static ip (192.168.0.105) has been setup for the server and I have setup portforwarding as well for port 80, 21, 23, 53 and 443 to the static ip. reading the guides on how to setup a publicly accessible webserver, I thought this was all that was needed, as it was working perfectly at first, but of course I found out that once I  tried to access the webserver using the domain name outside the network, I couldnt connect. After some more searching I found out that I needed to change my A record in my zone file at GoDaddy to my public ip. Once I did that I found that I was no longer able to connect to my webserver at all, either inside the network, where I would instead be redirecred to the router page, as well as outside the network where the connection would simply time out. I later figured out that since my public ip couldnt be set to static I had to use a service, specifically dyndns so that it would be able to constantly update the ip when it changes. I setup the dyndns updater from the software update center and setup my dyndns account, cokongwu.com, with an A record that points to my public ip and an alias [www.cokongwu.com](www.cokongwu.com) that points to cokongwu.com. I also setup a hostname, cokongwu.dyndns.org which also points to my public ip and added the dyndns nameservers to Godaddy's nameservers. The A record I have for cokongwu.com at godaddy still points to my internal ip and the CName records (www and cokongwu.com) both point to cokongwu.dyndns.org.(however, since I replaced godaddys nameserves with dyndns nameservers, I can no longer manage the zone file for the domain) 

After all this, trying to access hostname.com still provides the same problems as before. Accessing it points to my public ip instead of my internal ip, but within the network I just get forwarded to my routers setting page and outside the network it just times out. I'm out of ideas as to how to fix this, so any ideas are welcome. Shouldnt it(the public ip) be redirected to my internal ip?

Once again sorry if I'm using any of these technical words in the wrong way, I'm still very new to this whole thing.

I know a lot of questions related to issues like this post certain commands so I'll do the same:  

```
    Active Internet connections (only servers)
    Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
    tcp        0      0 127.0.0.1:5556          0.0.0.0:*               LISTEN      3387/dyn_updater
    tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      -               
    tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
    tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
    tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      -               
    tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      2729/vino-server
    tcp6       0      0 :::80                   :::*                    LISTEN      -               
    tcp6       0      0 :::21                   :::*                    LISTEN      -               
    tcp6       0      0 :::22                   :::*                    LISTEN      -               
    tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
    tcp6       0      0 :::5800                 :::*                    LISTEN      2729/vino-server
    tcp6       0      0 :::5900                 :::*                    LISTEN      2729/vino-server
    udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
    udp        0      0 127.0.1.1:53            0.0.0.0:*                           -               
    udp        0      0 0.0.0.0:39124           0.0.0.0:*                           -               
    udp        0      0 0.0.0.0:631             0.0.0.0:*                           -               
    udp6       0      0 :::5353                 :::*                                -               
    udp6       0      0 :::53973                :::*                                -     
```  

 
ufw:

```


    sudo ufw status
    [sudo] password for fender: 
    Status: inactive
```



000-default.conf:


```
    <VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
            ServerName cokongwu.com
            ServerAlias [www.cokongwu.com](www.cokongwu.com)
    
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
    
        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn
    
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    
        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
    </VirtualHost>
    
    # vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

---

### Post by divestoclimb on 2015-03-15
A quick check of public DNS suggests things are fine there. I cannot access your server either on HTTP port 80 or by SSH, so it's not being caused by apache.

What happens when you try to visit [http://192.168.0.105/](http://192.168.0.105/) from your internal network? If that works, there must be a misconfiguration with your router's port forwarding.

Be warned that some residential ISPs may block incoming traffic on port 80 to prevent you from doing exactly what you're trying, so I'd focus on getting other protocols working first--SSH and VNC--before worrying too much about the web server. You might also be getting a conflict with your router's web administration GUI.

---

### Post by onemic on 2015-03-15
Trying to access 192.168.0.105 gives me my website. What else needs to be changed by my portforwarding?  Do I need to portforward on my modem as well?

I have the same problem with SSH. using my internal ip works, but using cokongwu.com makes it timeout. VNC just doesnt work at all as I always get some error talking about non matching security types or something whenever I try to connect through a VNC viewer on Windows.

Heres a pic for my portforwading:

[IMG]http://i3.minus.com/ibi7uP8lZi5B41.jpg[/IMG]

---

