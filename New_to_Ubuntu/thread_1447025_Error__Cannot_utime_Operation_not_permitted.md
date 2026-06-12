---
title: "Error?  Cannot utime: Operation not permitted"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by cwfrad on 2010-04-04
I was trying to install a .sh file and it got over halfway thru the installation and then I received the following errors:

  	 	 	 	 	 	  usr/local/bin/  
 tar: usr/local/share: Cannot utime: Operation not permitted  
 usr/local/bin/Budget  
 tar: usr/local/bin/Budget: Cannot open: File exists  
 usr/share/  
 tar: usr/local/bin: Cannot utime: Operation not permitted  
 tar: usr/local: Cannot utime: Operation not permitted  
 usr/share/applications/  
 usr/share/applications/budget-calendar.desktop 
 tar: usr/share/applications/budget-calendar.desktop: Cannot open: File exists  
 tar: usr/share/applications: Cannot utime: Operation not permitted  
 tar: usr/share: Cannot utime: Operation not permitted  
 tar: usr: Cannot utime: Operation not permitted  
 tar: Exiting with failure status due to previous errors  
 

 Error: Installation may be incomplete:  
   -- check permissions  
   -- check available space  
 curtis@CET-Home:~/Downloads$

---

### Post by NightwishFan on 2010-04-04
You probably need to run the script as root. Make sure you know what the script does before you execute it.

```
sudo sh scriptname
```

---

