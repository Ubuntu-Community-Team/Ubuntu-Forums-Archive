---
title: "xampp php problem"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by marmoushai on 2009-12-04
This is actually my first thread ever and i hope i'm asking the right questions 
been using ubuntu x64  Ubuntu 9.10 - the Karmic Koala for a while now .. 

goal 
===
i wanted to make php website using netbeans
and i downloaded XAMPP on the localhost 

strange: (plz explain )
======
when i installed it to /opt/lampp   it didn't ask for installing lib32 
but when i tried to install in somewhere else  ( home/ sources ) it did ask for lib32 and when i tried to install the lib32  it gave me some packages to be removed .. so i went back to     /opt/lampp  

Error  My  main Question 
====================
1- i created a php project  in /home/workspace/netbeansproj
2- then wrote  " echo "bla bla hello "  in the editor 
3- when i run the project    it gives me next error 

[COLOR=Red]Object not found!

The requested URL was not found on this server. If you entered the URL manually please check your spelling and try again. 

If you think this is a server error, please contact the webmaster. 
Error 404
localhost

Apache/2.2.12 (Unix) DAV/2 mod_ssl/2.2.12 OpenSSL/0.9.8k PHP/5.3.0 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0[/COLOR]

so wht do you think is wrong ? do i have to put the website in the opt directory ? or wht

---

### Post by marmoushai on 2009-12-04
actually it worked when i did put the project in      
/opt/lamp/htdocs/phpproj

but now i need root access everytime i run netbeans ! 

which brings me to the strange thing which happened when i installed xampp in other directory and it asked for lib32 stuff !!

---

### Post by marmoushai on 2009-12-04
well after allllllllllll i found some way around in this link:
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

i removed everything start new:
1- installed xampp in  /opt directory because i found out tht the localhost points to it donno how or why 
2- i made another folder for my projects in  home directory ( no sudo stuff )
3- i made a link of that folder and put that link in  (/opt/lampp/htdocs/phpfolder)  
p.s :)  be aware to rename the link to same as folder name cause to ease the process 

[http://localhost/phpfolder/firstproject/index.php](http://localhost/phpfolder/firstproject/index.php) 

and hurrayyyyy it worked

---

