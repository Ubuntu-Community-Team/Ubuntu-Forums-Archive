---
title: "Problem with Software Centre"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by highflie on 2010-02-07
Hey all,
I have a problem with the Ubuntu Software Centre. I use 9.10 32-bit on windows. When I click the install button, download fails after reaching 50%, and it says check your internet connection. However, my internet connection is fine. And this EXACT thing happens for ALL downloads. What should I do?

Thanks in Advance :)

---

### Post by NCLI on 2010-02-07
Try running "sudo apt-get update" in the terminal, then post the output here.

---

### Post by highflie on 2010-02-08
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Reading package lists... Done                          
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nhasian on 2010-02-08
you must be connected to the internet to run the apt-get update.  if you are connected to the internet and its not working, try changing your server from System->Administration->Software Sources then use the dropdown menu to change the "Download From"

then you should run in a terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

that should have you sorted.

> **highflie said:**
> Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37)...

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by highflie on 2010-02-08
I changed the server from "Server for United States" to "Main Server" and ran the code u said. But still I am facing the problem.

The output got was:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]
Reading package lists... Done                       
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.30). - connect (111: Connection refused) [IP: 91.189.88.30 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by highflie on 2010-02-08
Also I clicked on the "Select best server" option, then it said that "No server could be found for your location. Please check your internet connection."

---

### Post by zeroseven0183 on 2010-02-08
Are you behind a firewall? (I mean, not you literally, but your network)

---

### Post by medphys on 2010-02-08
I am having problems myself.  See posts.  Wonder if there is a problem with servers?

---

### Post by sandyd on 2010-02-08
whats your ISP? they could be blocking the connection.... can you try navigating to [http://archive.ubuntu.com](http://archive.ubuntu.com) w/ your browser?

---

### Post by sandyd on 2010-02-08
> **medphys said:**
> I am having problems myself.  See posts.  Wonder if there is a problem with servers?

one person having a problem? fine. two? definately something wrong here. could be temperory server problems. where do you live? cause right here in L.A. (comcast) Im having no problems other than the usual comcast slowness....

---

### Post by medphys on 2010-02-08
Virginia

---

### Post by highflie on 2010-02-09
Yes, the network I use does have a firewall.And I didnt have any problem going to [http://archive.ubuntu.com/](http://archive.ubuntu.com/). And I am from Kharagpur, India.

---

