---
title: "Repositories wont work over school proxy"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by ChickenCow on 2009-09-24
Hi, at my boarding school we have a proxy set up. 
so I went to System -> Preferences -> Network Proxy -> "Direct Internet connection"

 System -> Administration -> Synaptic Package Manager -> Settings -> preferences -> Network -> "Manual proxy config." and filled in the first two lines.

I can get on firefox and use that fine but my repositories cannot download any packages which is really annoying because I need certain software. 

and when I download and install a package manually (from the site, then opening them in .deb package manager) .deb package manager cannot access the files online to make them open. 

so I am thoroughly confused. help please?

(oh I have Jaunty and I have to use my username and password for the network to get online (a little box pops up in firefox and asks for it ever time))

---

### Post by QIII on 2009-09-25
What happens, for instance, when you type in the terminal

```
sudo apt-get update
```Your description of what is going on is a bit too vague.

---

### Post by ChickenCow on 2009-09-25
this is what I get when I type that into the terminal:
```


Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by QIII on 2009-09-26
[FONT=Verdana][SIZE=1]OK.  Try this[/SIZE][/FONT][FONT=Verdana][SIZE=1], but I am not sure if I remember it correctly.  Wait a bit and see if anyone comes up with anything better ...
[/SIZE][/FONT][FONT=Verdana][SIZE=1]
```
gksudo gedit /etc/apt/apt.conf.d/70debconf
```

At the end, add

```
//This is to get me through the proxy
Acquire::http::Proxy "http://yourusername:yourpassword@yourdomain:appropriateport";
```You will have to talk to your network administrator to get the appropriate[/SIZE][/FONT][FONT=Verdana][SIZE=1] domain and the port to use.[/SIZE][/FONT]

---

### Post by unmole on 2009-09-26
Scan all ports using [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) and find an open port and note the number. Then do a

         gksudo gedit /etc/apt/apt.conf

And add these two lines in the end```


Acquire::http::proxy "[http://username:password@proxy]("http://username:password@proxy/"):port";
 Acquire::ftp::proxy "[ftp://username:password@proxy]("ftp://username:password@proxy/"):port";

```Replace username,password and port with the appropriate values and finally run 

```
sudo apt-get update
```

P.S. Scan ports in batches of 500 i.e. 1-500,500-1000 etc.

---

### Post by ChickenCow on 2009-09-26
I just tried both ways and both times I got the same information I got back from the terminal.
do I need to change my proxys through system>network proxys before I do that in the terminal? and I found a few ports that were open (aka ssn is port 22) (https port open on  443)
do I enter those different ports for each category (ssn and https???)

---

### Post by ChickenCow on 2009-09-26
this is what I got when I tried unmole's way

Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ChickenCow on 2009-09-26
so I tried both of your ways then started monkeying around on my proxy's ports etc. and turned out I did something right! 
thanks for giving my a place to start at!

---

### Post by corsino on 2009-10-20
What did you do? I'm with the same problem. I tried ntlmaps and still not working.

---

