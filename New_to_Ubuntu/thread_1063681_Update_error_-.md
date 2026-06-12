---
title: "Update error -"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by longtom on 2009-02-08
sudo apt-get update
Ign file:  Release.gpg
Ign file:  Translation-en_ZA                                                                                 
Ign file:  Release                                                                                            
Ign file:  Packages                                                                                           
Err file:  Packages                                                                                           
  File not found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) intrepid Release.gpg                                                         
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) intrepid/main Translation-en_ZA                                                    
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) intrepid-security Release.gpg                                                      
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) intrepid-security/main Translation-en_ZA                                                          
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                                                                                 
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) intrepid-updates Release.gpg                                          
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                                                      
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) intrepid-updates/main Translation-en_ZA                               
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_ZA                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_ZA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_ZA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Reading package lists... Done
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.229). - connect (111 Connection refused)

W: Failed to fetch file:/tmp/setupsdeb/Packages.gz  File not found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


And with that I can't update anything.  Followed a way to upgrade to Office 3.01.  which I found on the i-net.  That was a mistake - and I am sitting with above trouble.

Can somebody help me to get out of here?

regards

longtom

---

### Post by Kevbert on 2009-02-08
It looks like the server may be temporarily down. Please close terminal and select another server (under Administration-Software Sources).
Then reopen a terminal and try again.

---

### Post by Lunx on 2009-02-08
> **Kevbert said:**
> It looks like the server may be temporarily down. Please close terminal and select another server (under Administration-Software Sources).
Then reopen a terminal and try again.

I'm in Australia and had same problem for most of the day, but tried again just before and was finally able to connect to server, so perhaps try again soon and see how you go.

---

### Post by longtom on 2009-02-08
> **Kevbert said:**
> It looks like the server may be temporarily down. Please close terminal and select another server (under Administration-Software Sources).
Then reopen a terminal and try again.


That was it.  Thank you very much!!

longtom

@Lunx:  SA server didn't respond so I switched to the main server - that did it.

lt

---

