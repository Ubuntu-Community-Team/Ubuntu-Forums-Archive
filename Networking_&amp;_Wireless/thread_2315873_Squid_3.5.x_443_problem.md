---
title: "Squid 3.5.x 443 problem"
date: 2016-03-03
forum: Networking &amp; Wireless
---

### Post by secoonder on 2016-03-03
Hello 
i used debian(ubuntu 14.04) 
I read  a lot of articles on the Internet for squid 443 enable redirection. 
As i learned,if port 443 is active from squid,The installed needs by the compiled squid.is it true ? 
am i installed apt-get install squid for 443 redirect?(80.ports redirect wasno problem,it works.the problem is 443 port) 

i installed squid 3.5.8 package from squid-cache.And then i went to squid.3.5.8 folder. 
and then ,  
./configure --with-openssl --enable-ssl-crtd 
make  
make install 
When it was finished, i wanted to go /etc/squid folder. 

But the /etc/squid or /etc/squid3 folder does not exit. 
What can i do? 
am i find step by step squid 3.5.x SSL (80 and 443 port) installation?  ( i read squid mail list .but i can not install successfuly,it doesnt work 443 still.)
Thank you very Much

---

### Post by SeijiSensei on 2016-03-03
If you compile Squid (or most any well-behaved program) from source, "make install" will put the result under /usr/local.  See if you have a /usr/local/squid directory.  The binary will be in /usr/local/squid/sbin/ and the companion files in other directories below /usr/local/squid like /usr/local/squid/etc.

I assume you ran "make install" with root privileges.  If not, go back to the source directory and run "sudo make install".

---

