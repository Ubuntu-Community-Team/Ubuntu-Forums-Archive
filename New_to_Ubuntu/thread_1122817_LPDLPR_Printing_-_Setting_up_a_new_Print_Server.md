---
title: "LPD/LPR Printing - Setting up a new Print Server"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by jazzyjam on 2009-04-11
I know nothing about Ubuntu(Linux) and need some hand holding here.  

I am confused on where to begin. Sorry if this post is long.

I want to set up a LPD/LPR Print Server on my ubuntu (8.10) desktop machine and from my XP workstations send print jobs via LPR command to the Ubuntu machine.  I do not want to print the actual jobs I want to "hold" them in their queues and then grab the data from a different windows machine.  I know it sounds silly but I need to set this up for our company.

Most of our customers send their data to us via FTP or Email but this one potential customer which has about 100 branches send all of their data via the LPR commands.  Their data needs to be modified and added to our SQL database so they don't need to be printed yet. 

As of right now they are sending their test print jobs to our Xerox copier and it works, however retrieving their data off the xerox copier (which is also linux based) is a hassle because xerox renames everything to JOB#DAT, if 6 jobs go to the xerox machine and this customer sends their data is is 7DAT. Unfortunately, its not the same job# every time so its impossible to find it via the shared name. We have to physically go to the machine and look on the display and find the job name then go to our server and retrieve the raw data.  
You can imagine if we have over 100 of these a data it will get very tiresome.  So I thought I could setup a Print Server with a queue name of each branch then go to the SQL Server and get the data and modify it and add it to our SQL Database.

I have attached some pix on my progress so far. Ubuntu machine is 192.168.0.59 
I installed CUPS, I must be missing some steps, I have a printer setup as LPD/LPR Host and have a Queue named "dummy" I go to a windows xp machine on the same network and send a test.pdf  file but I keep getting "Error: Print Server unreachable or does not exist
C:\test>lpr -S 192.168.0.59 -P dummy test.pdf
Error: print server unreachable or specified printer does not exist.

Any help is appreciated.
[IMG]http://tinyurl.com/cjbgcj[/IMG]
[IMG]http://tinyurl.com/c3sq5f[/IMG]
[IMG]http://tinyurl.com/clv6ro[/IMG]

---

### Post by jazzyjam on 2009-04-11
more pix:
[IMG]http://tinyurl.com/dlbpd6[/IMG]
[IMG]http://tinyurl.com/d3ps5f[/IMG]
[IMG]http://tinyurl.com/cymcrf[/IMG]

---

### Post by lfaraone on 2009-04-11
Can you ping your system from windowsXP? 

Can you print from the server itself using that command?

---

### Post by jazzyjam on 2009-04-11
I can ping it from any workstation.
No I can't print but it isn't an actual printer. 
I guess that is where I just don't "get it".  I want to send these files to the dummy queue of this "fake" printer but it is not accepting the jobs. It acts like there is no LPD/LPR Host

[IMG]http://tinyurl.com/cawsgn[/IMG]

---

### Post by jazzyjam on 2009-04-11
Is there something I didn't install?

---

