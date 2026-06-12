---
title: "updates install"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by Suan_gr on 2011-08-03
I have been trying ton install updates. I always get this error:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.4.0-0ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.4.0-0ubuntu1.3_i386.deb) Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.30 80]

What could be the problem?

---

### Post by Frogs Hair on 2011-08-03
Open the terminal and run these two commands and try again . 
```
sudo apt-get update 
```
```
sudo apt-get upgrade
```

If that fails open the update manager > settings > Ubuntu Software Tab > Download from . From the drop-down menu select other and then select the best server option . Ubuntu will then search for the best server for your area to receive updates from and lastly try update again .

---

### Post by Suan_gr on 2011-08-03
Error:

  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_IN
  Unable to connect to ppa.launchpad.net:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
  Could not connect to extras.ubuntu.com:80 (91.189.88.33), connection timed out
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
  Unable to connect to extras.ubuntu.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.88.33), connection timed out
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN    
  Unable to connect to archive.canonical.com:http:
0% [Connecting to archive.ubuntu.com (91.189.92.169)] [Connecting to dl.google.
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Could not connect to dl.google.com:80 (209.85.153.91), connection timed out [IP: 209.85.153.91 80]
Err [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
  Unable to connect to dl.google.com:http: [IP: 209.85.153.91 80]


What do I do now?
Please help :confused:

---

### Post by Frogs Hair on 2011-08-03
I'm not sure why you can't connect to the Ubuntu .com . Has this been a long term problem or is it just today ? I suggested changing the sever because that helps some people . If this has been a long term problem , router or isp come to mind. If it is a temporary problem on their end you will have to wait it out.

---

### Post by wildmanne39 on 2011-08-03
Hi, I believe if they have a proxy setup sometimes that conflicts as well.

---

### Post by Suan_gr on 2011-08-04
> **wildmanne39 said:**
> Hi, I believe if they have a proxy setup sometimes that conflicts as well.


O yes, I have a proxy setting. So, how do I get pass the proxy settings so I can update? Is it through the links you provided? It is about 11.04, would it apply to mine which is 10.10?

---

### Post by wildmanne39 on 2011-08-04
Hi, I am not well versed in proxy setups but I found this link that might help it tells how to connect through a proxy.
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Also it might be easiest to not use a proxy unless you have too.

---

### Post by eXe. on 2011-08-04
Just get a hardwired connection, or dont use a proxy unless the FBI or the NHTCU are tailing you or something. Your machine failed to connect to the website. If you are connected through a proxy I would recommend connecting with a direct internet connnection. Just go down to a startbucks or something. After you get that connection do-
sudo apt-get update
sudo apt-get upgrade

Hope it helped

---

### Post by Suan_gr on 2011-08-04
ohk. will do. ty! :cool:

---

