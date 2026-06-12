---
title: "squidGuard - problems building the DBs"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by markeee on 2014-02-08
I've been struggling to get squidGuard to work right for the past 2 days or so-spent a lot of time on squidGuard now and still stuck - hoping someone can help me out

I' firstly tried to install from the source SquidGuard V1.4 - off squidguard.org - compiled/make etc and made a basic config - then when it came ti buildng the DB using the cmd squidGuard -C all

I'd get the following error: DB->put: method not permitted before handle's open method

which seems to be aboue the Berekly DB LIBRARY(But nopt sure what to do really - i read there's problems with  versions over 4.6) 

next up was the repos - which installs squidguard.1.5.1 [http://packages.ubuntu.com/saucy/squidguard](http://packages.ubuntu.com/saucy/squidguard) with libdb5.1

this worked fine eventually (had a few issues where it threw errors that there was no config file) - so i created one and then the setup worked

however with this it gets stuck at making the db files again

squidguard -C all - and it just HANGS , no output nothing


Any suggestions would be massively appreciated

---

### Post by markeee on 2014-02-08
root@dimension:/usr/local/squidGuard/db# nano domains                                                             
root@dimension:/usr/local/squidGuard/db# squidGuard -C all                                                        
DB->put: method not permitted before handle's open method                                                         
          

thats the issue when compiled from source

---

### Post by markeee on 2014-02-08
root@dimension:/usr/local/squidGuard/db# apt-get remove squidguard                                                
Reading package lists... Done                                                                                     
Building dependency tree                                                                                          
Reading state information... Done                                                                                 
The following packages will be REMOVED                                                                            
  squidguard                                                                                                      
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.                                                    
After this operation, 264 kB disk space will be freed.                                                            
Do you want to continue [Y/n]? y                                                                                  
(Reading database ... 214474 files and directories currently installed.)                                          
Removing squidguard ...                                                                                           
Processing triggers for man-db ...                                                                                
root@dimension:/usr/local/squidGuard/db# apt-get install squidguard                                               
Reading package lists... Done                                                                                     
Building dependency tree                                                                                          
Reading state information... Done                                                                                 
Suggested packages:                                                                                               
  ldap-utils squidguard-doc                                                                                       
The following NEW packages will be installed                                                                      
  squidguard                                                                                                      
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.                                                    
Need to get 0 B/107 kB of archives.                                                                               
After this operation, 264 kB of additional disk space will be used.                                               
Preconfiguring packages ...                                                                                       
Selecting previously unselected package squidguard.                                                               
(Reading database ... 214449 files and directories currently installed.)                                          
Unpacking squidguard (from .../squidguard_1.5-1_i386.deb) ...                                                     
Processing triggers for man-db ...                                                                                
Setting up squidguard (1.5-1) ...                                                                                 
Move log file directory to new directory /var/log/squidguard.                                                     
Rebuild SquidGuard database - this can take a while.  

Installing from the repos when there'sd a file containing entries in /usr/local/squidguard/db it just hangs on the above
and it says it can take a while..sure but the test file for the db only has 3 entries
doubleclick.net
flashbannernow.com
addispenser.com

[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)

if i rm -rf the test file squidguard will install and comment that no file is present to buold a db off - and then when I run squidGuard -C all later - hangs there

root@dimension:/home/mark# apt-get install squidguard                                                                                                   
Reading package lists... Done                                                                                                                           
Building dependency tree                                                                                                                                
Reading state information... Done                                                                                                                       
Suggested packages:                                                                                                                                     
  ldap-utils squidguard-doc                                                                                                                             
The following NEW packages will be installed                                                                                                            
  squidguard                                                                                                                                            
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.                                                                                          
Need to get 0 B/107 kB of archives.                                                                                                                     
After this operation, 264 kB of additional disk space will be used.                                                                                     
Preconfiguring packages ...                                                                                                                             
Selecting previously unselected package squidguard.                                                                                                     
(Reading database ... 214449 files and directories currently installed.)                                                                                
Unpacking squidguard (from .../squidguard_1.5-1_i386.deb) ...                                                                                           
Processing triggers for man-db ...                                                                                                                      
Setting up squidguard (1.5-1) ...                                                                                                                       
Move log file directory to new directory /var/log/squidguard.                                                                                           
No data files found in /usr/local/squidGuard/db - exiting update-squidguard.                                                                            
root@dimension:/home/mark#                                                                                                                              
root@dimension:/home/mark#                                                                                                                              
root@dimension:/home/mark#                                                                                                                              
root@dimension:/home/mark#                                                                                                                              
root@dimension:/home/mark# squidGuard -C all                                                                                                            
                                             

thats without a db file the install finished and then when I run squidGard -C all to make a db out of the file I created after install in /usr/local/squidguard/db it just hangs again

not sure what to do now as I've tried both source and repos

if anyone could point me in the right direction or suggest a logfile to read Id appreciate it

---

