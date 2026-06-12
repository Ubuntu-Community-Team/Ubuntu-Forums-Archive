---
title: "apt-get error"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by c0nrad on 2010-05-12
Hey, 

When I run apt-get I get this error:

```

conrad@conrad-laptop:~$ sudo apt-get update
[sudo] password for conrad: 
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Get:3 http://dl.google.com stable Release [2,540B]                             
Hit http://archive.canonical.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://dl.google.com stable/main Packages [914B]                         
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Err http://us.archive.ubuntu.com lucid Release.gpg                             
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages             
Fetched 3,950B in 11s (358B/s)                                                 
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

If anyone has any idea what that means that'd be great.

thanks,
c0nrad

---

### Post by Sealbhach on 2010-05-12
Something wicked happened, according to the error message. You will need to do some good deeds to restore balance to the universe.

If that doesn't work, go into Software Sources and select a different "Download from" server using "Select best server".

.

---

### Post by skibum3027 on 2010-05-12
Failing to resolve a name to an address is a DNS problem.

---

