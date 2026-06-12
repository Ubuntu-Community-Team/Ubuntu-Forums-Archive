---
title: "Is there a way to use Evolution Email over a SOCKS proxy?"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by diablo75 on 2009-08-28
I'm having some trouble with Evolution as I'm in a different country now.  When I send emails, they sometimes don't make it and I get these failed delivery return emails saying something timed out...  I have had no trouble establishing an SSH tunnel to a PC I have at home and I'd like to be able to use Evolution over this tunnel so I can send and receive emails reliably.

I googled "evolution socks proxy" and the first result lead to this:

[http://www.ubuntux.org/evolution-using-a-socks-proxy](http://www.ubuntux.org/evolution-using-a-socks-proxy)

which mentions a program called "tsocks".  I've never used this program before, and the blog post doesn't go into much detail as to whether or not the program needs any other configuration or bother mentioning how they are establishing their own SOCKS tunnel.  The question that lingers in my head is whether or not the internal port they're setting up to act as the gateway to the ssh tunnel has to be configured anywhere (like what you do when you tell Firefox to connect to "localhost, port number xxxxx" or something like that).

Edit:  Just wanted to add that I've just tried the command "tsocks evolution" from the terminal evolution just sits there attempting to connect but nothing happens.  There's not network activity going on either and the man page for tsocks is pretty slim so I don't know if it's going to work for me at all...

---

### Post by freak42 on 2009-10-03
you need to start your app with
tsocks <appname>

edit /etc/tsocks.conf
to setup your connection

```
sudo gedit /etc/tsocks.conf
```

use this as your default server settings in the tsocks.conf (at the bottom end of the config file):
```
# Default server
# For connections that aren't to the local subnets or to 150.0.0.0/255.255.0.0
# the server at 192.168.0.1 should be used (again, hostnames could be used
# too, see note above)

server = 127.0.0.1
# Server type defaults to 4 so we need to specify it as 5 for this one
server_type = 5
# The port defaults to 1080 but I've stated it here for clarity 
server_port = 9999 
```

and connect to your server and create a port forwarding tunnel (dyncamic from local port 9999):
ssh -f -C -D 9999 [email]yourusername@yourserverorip.com[/email] -N 

this also forks ssh (command line returns) and keeps your tunnel open idefinitely (until your internet craps out or you kill all ssh processes)
if you don't want that omit the -f and -N

hth

---

