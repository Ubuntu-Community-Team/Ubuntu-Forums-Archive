---
title: "V9 32bit vs 64bit"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by mike67 on 2009-07-23
I have a new servre that I want to install the V9 server on. Quad-Core processor with 4Gig of RAM, I have an additional 4Gig that I can put in it.
What I am doing with it is the following. I currently have 2 - 6 year old redhat servers that are running
1. static HTML pages
2. E-mail server
3. JSP pages that are backend to a 32-bit MS-SQL database using the jTDS JDBC driver
 
I am going to combine this all to my new server and possibly add MailArchiva to it also. So I would really rather go up to the full 8Gig of Ram that I can put in the server.
 
I don't want to go thru installing 64-bit and find out I need to back out and re-install 32-bit. I guess my main concern are all of my jsp pages that are pulling data from SQL2005 32-bit, these are important. Does anyone see an issue with this? Am I worring about something that I don't need to worry about? I know that they work fine on my old 32-bit servers..
 
I know that SQL could be 64-bit, but it cannot be because other software I am using is not currently compatible with 64-bit due to the base programming language.
Thanks,
Mike

---

### Post by keplerspeed on 2009-07-25
ubuntu server edition uses the PAE kernel, so you can address more than 4 gig of ram with a 32bit system.

---

