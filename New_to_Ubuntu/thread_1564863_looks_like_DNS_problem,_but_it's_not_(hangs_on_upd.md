---
title: "looks like DNS problem, but it's not? (hangs on updating)"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by walrus! on 2010-08-31
Hi,

When I sudo apt-get update or sudo aptitude update, it will hang on 0% completed for a while before telling me, well, why don't I just paste it:

```


Err http://archive.canonical.com lucid Release.gpg                                                                                                          
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                                                    
  Unable to connect to archive.canonical.com:http:
Ign http://archive.canonical.com lucid Release                                                                                                              
Ign http://archive.canonical.com lucid/partner Packages                                                  
Ign http://archive.canonical.com lucid/partner Sources                                                   
Ign http://archive.canonical.com lucid/partner Packages                                                  
Ign http://archive.canonical.com lucid/partner Sources                                                   
Err http://archive.canonical.com lucid/partner Packages                                                  
  Unable to connect to archive.canonical.com:http:
Err http://archive.canonical.com lucid/partner Sources                                                   
  Unable to connect to archive.canonical.com:http:
8% [Connecting to archive.ubuntu.com (91.189.92.166)] [Connecting to security.ubuntu.com (91.189.92.167)]^C
gatekeeperwalrus@rocky-iceberg:~$ sudo aptitude update
Err http://archive.canonical.com lucid Release.gpg                                                                                                          
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                                                    
  Unable to connect to archive.canonical.com:http:
Ign http://archive.canonical.com lucid Release                                                                                                              
Ign http://archive.canonical.com lucid/partner Packages                                                
Ign http://archive.canonical.com lucid/partner Sources                                                 
Ign http://archive.canonical.com lucid/partner Packages                                                
Ign http://archive.canonical.com lucid/partner Sources                                                 
Err http://archive.canonical.com lucid/partner Packages                                                
  Unable to connect to archive.canonical.com:http:
Err http://archive.canonical.com lucid/partner Sources                                                  
  Unable to connect to archive.canonical.com:http:
Err http://security.ubuntu.com lucid-security Release.gpg                                                
  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (110: Connection timed out) [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Ign http://security.ubuntu.com lucid-security Release                                                    
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Err http://security.ubuntu.com lucid-security/main Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/restricted Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/universe Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/multiverse Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err http://archive.ubuntu.com lucid Release.gpg      
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (110: Connection timed out) [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Ign http://archive.ubuntu.com lucid Release
Ign http://archive.ubuntu.com lucid-updates Release
Ign http://archive.ubuntu.com lucid-backports Release
Ign http://archive.ubuntu.com lucid/main Packages
Ign http://archive.ubuntu.com lucid/restricted Packages
Ign http://archive.ubuntu.com lucid/main Sources
Ign http://archive.ubuntu.com lucid/restricted Sources
Ign http://archive.ubuntu.com lucid/universe Packages
Ign http://archive.ubuntu.com lucid/universe Sources
Ign http://archive.ubuntu.com lucid/multiverse Packages
Ign http://archive.ubuntu.com lucid/multiverse Sources
Ign http://archive.ubuntu.com lucid-updates/main Packages
Ign http://archive.ubuntu.com lucid-updates/restricted Packages
Ign http://archive.ubuntu.com lucid-updates/main Sources
Ign http://archive.ubuntu.com lucid-updates/restricted Sources
Ign http://archive.ubuntu.com lucid-updates/universe Packages
Ign http://archive.ubuntu.com lucid-updates/universe Sources
Ign http://archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://archive.ubuntu.com lucid-backports/main Packages
Ign http://archive.ubuntu.com lucid-backports/restricted Packages
Ign http://archive.ubuntu.com lucid-backports/universe Packages
Ign http://archive.ubuntu.com lucid-backports/multiverse Packages
Ign http://archive.ubuntu.com lucid-backports/main Sources
Ign http://archive.ubuntu.com lucid-backports/restricted Sources
Ign http://archive.ubuntu.com lucid-backports/universe Sources
Ign http://archive.ubuntu.com lucid-backports/multiverse Sources
Ign http://archive.ubuntu.com lucid/main Packages
Ign http://archive.ubuntu.com lucid/restricted Packages
Ign http://archive.ubuntu.com lucid/main Sources
Ign http://archive.ubuntu.com lucid/restricted Sources
Ign http://archive.ubuntu.com lucid/universe Packages
Ign http://archive.ubuntu.com lucid/universe Sources
Ign http://archive.ubuntu.com lucid/multiverse Packages
Ign http://archive.ubuntu.com lucid/multiverse Sources
Ign http://archive.ubuntu.com lucid-updates/main Packages
Ign http://archive.ubuntu.com lucid-updates/restricted Packages
Ign http://archive.ubuntu.com lucid-updates/main Sources
Ign http://archive.ubuntu.com lucid-updates/restricted Sources
Ign http://archive.ubuntu.com lucid-updates/universe Packages
Ign http://archive.ubuntu.com lucid-updates/universe Sources
Ign http://archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://archive.ubuntu.com lucid-backports/main Packages
Ign http://archive.ubuntu.com lucid-backports/restricted Packages
Ign http://archive.ubuntu.com lucid-backports/universe Packages
Ign http://archive.ubuntu.com lucid-backports/multiverse Packages
Ign http://archive.ubuntu.com lucid-backports/main Sources
Ign http://archive.ubuntu.com lucid-backports/restricted Sources
Ign http://archive.ubuntu.com lucid-backports/universe Sources
Ign http://archive.ubuntu.com lucid-backports/multiverse Sources
Err http://archive.ubuntu.com lucid/main Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid/restricted Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid/universe Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/main Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/restricted Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/universe Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-updates/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/main Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/restricted Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/universe Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com lucid-backports/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Reading package lists... Done



```

When I ping anything, including us.archive.ubuntu.com, or just archive.ubuntu.com, it resolves it.  I did take the 'us' out of my /etc/apt/sources.list, because another thread suggested it.  It didn't help.

NetworkManager fills out /etc/resolv.conf with the address of my router every time, and that seems to get the addresses to resolve to an IP (as opposed to filling it out with the DNS addresses that my router uses.)

NetworkManager also causes it to use a static IP (192.168.1.101) with the gateway as my router (192.168.1.1) and netmask (255.255.255.0).  The only thing that I can't account for (don't know what it does) is that it sets the 'broadcast address' to '192.168.1.255'.  

I'm pretty stuck, why can Ubuntu resolve the addresses but I can't install from the repos?  Installing from repos works just fine on this Ubuntu laptop which uses a dynamically assigned IP address.

Thanks for your consideration, I've been reading these forums for a while, but never yet posted!

---

### Post by surfer on 2010-08-31
can you access the repository (e.g. [http://archive.canonical.com/](http://archive.canonical.com/) ) with your browser?

---

### Post by dream_coder on 2010-08-31
Just for arguments sake set static ip to 192.168.1.2 instead of .101 and also go to system > software sources > choose server then select choose best server

---

### Post by walrus! on 2010-08-31
> **surfer said:**
> can you access the repository (e.g. [http://archive.canonical.com/](http://archive.canonical.com/) ) with your browser?

Nope, it times out in w3m and firefox.

---

### Post by walrus! on 2010-08-31
> **dream_coder said:**
> Just for arguments sake set static ip to 192.168.1.2 instead of .101 and also go to system > software sources > choose server then select choose best server

Do you know if there is a way to do this without the GUI?  The first one I can probably manage (though network manager is going to undo my changes later.)

thanks

**edit

By 'without the GUI' I mean without physical access to the machine.  X forwarding is on the menu.

---

### Post by walrus! on 2010-08-31
Very interesting that the browsers can't load anything... does that make any insights jump out at anyone?

Thanks

**EDIT
just to make it explicit, nothing loads on firefox or w3m, not just a certain domain.

---

### Post by walrus! on 2010-08-31
Any interest in this problem?

-ping resolves hostname to IP
-browsers can't open anything
-apt-get / aptitude won't work?

Can't install anything until this is... (wait for it...) resolved!  Really not looking forward to reinstalling the OS.

---

### Post by surfer on 2010-08-31
are you behind a firewall or a proxy? are any other computers in that network so you could check their network configuration?

and: if http (i.e. browsers) do not work, it's no surprise apt-get doesn't either. apt-ger (usually) fetches its files via http as well.

---

### Post by walrus! on 2010-08-31
No firewall, no proxy, all the other computers work just fine with pretty standard configuration... just a home wireless network here.  thanks!

---

### Post by walrus! on 2010-09-08
Here's an update after more testing:

Everything works just fine when it's not a static IP.  Unfortunately, this is not an option, as this computer needs to be my home server.

When it's a static IP, (nameserver 192.168.1.1), it can resolve names but no http traffic *outside* the LAN.  It can navigate to my router's admin page just fine.

Anyone?  Thanks!

---

### Post by sandyd on 2010-09-08
> **walrus! said:**
> Here's an update after more testing:

Everything works just fine when it's not a static IP.  Unfortunately, this is not an option, as this computer needs to be my home server.

When it's a static IP, (nameserver 192.168.1.1), it can resolve names but no http traffic *outside* the LAN.  It can navigate to my router's admin page just fine.

Anyone?  Thanks!
do instructions here (ignore introduction, just leap down to the steps) -> [http://openubuntu.com/index.php/topic,230.0.html7](http://openubuntu.com/index.php/topic,230.0.html7)
make sure you install winbind after, that will allow you to resolve local network computers

---

### Post by hermdog on 2010-09-14
my first guess is that you are taking the address of the router you are connected to. most of the time the router defaults 192.168.1.1 or 192.168.0.1

i usually use 198.168.1.5 or .10 when configuring my servers. 

because sometimes the modem takes an ip address too.


when it is set to dhcp, what ip does it get?
is it also a 192.168.1.* address??

---

