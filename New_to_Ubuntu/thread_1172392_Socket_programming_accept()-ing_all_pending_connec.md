---
title: "Socket programming: accept()-ing all pending connections"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Rij on 2009-05-28
Hello,

I am writing a server which uses edge-triggered epoll. When the server calls accept(), it just extracts the first connection in the pending queue. If there are more connections that are waiting, can we make the server accept all the pending connections? I wrote a loop like the following:

 ```
  do  {  
      client_fd = accept(...); 
      /* Work with the client fd */ 
   } while (client_fd != -1);
```

Doesn't seem to work.

A related question, more a clarification, is as follows. My understanding was that a connect() at the client returns only when accept() in the server returns. Clearly, I was incorrect. Even with no accept() call in the server, my client was able to connect and send data. Am I getting this right?  

Your help will be really appreciated.

---

### Post by Rij on 2009-05-28
Silly me.

The listening socket was set as blocking. Once I made it non blocking, everything seems to work just fine.

---

