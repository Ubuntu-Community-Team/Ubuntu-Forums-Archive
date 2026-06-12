---
title: "SCP hanging up after entering password"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by kevin59 on 2014-02-12
Hey guys!

I am new to linux. 


I have been able to access a server using SSH.
However, I have been having problems with the scp command, when I enter my password for the server, it gets stuck and the file never gets transferred. 

The funny thing is I was just able to transfer files using the scp command yesterday just fine.

Any ideas on how I can troubleshoot this and get the scp command working again?

- Kevin

---

### Post by sudodus on 2014-02-12
Welcome to the Ubuntu Forums :-)

Please describe your operating system: Ubuntu version and flavour or some other system?

Are you still able to connect (log in) with ssh or sftp (using the ssh and sftp programs)?

Do you know if you have a connection to the server (can you ping)?

---

### Post by kevin59 on 2014-02-12
Hey Sudodus, 

I am running Ubuntu 13.10

I am still able to connect with ssh however sftp is having issues also (I tried some sftp commands and also FileZilla is having trouble connecting also). 

I am not sure of the server's ip address.

---

### Post by sudodus on 2014-02-13
If you can connect with ssh, you should be able to connect with sftp too, unless the server uses some special port (another number **[COLOR=#ff0000]xxx[/COLOR]** than the standard one  for sftp)

For example if

```
ssh kevin@192.168.0.2
```
works, then
```
sftp kevin@192.168.0.2
``` and
```
sftp -P 22 kevin@192.168.0.2
```
should work too, but if another port is configured at the server, use that port instead
```
sftp -P [COLOR=#ff0000]**xxx**[/COLOR] kevin@192.168.0.2
```

You need to check the address of the server as well as the port number for sftp.

---

### Post by kevin59 on 2014-02-13
Hmm, I just tried again today, and ssh works fine but the sftp commands provided don't work. 

I checked with the server's support people and their ports for sftp/ssh is 22.

---

### Post by kevin59 on 2014-02-13
okay, so i had an instance of bash running on top of csh on the account located on the server. 

exiting the extra bash instance resolved this issue.

Thanks for your help, I really appreciate it!

---

### Post by sudodus on 2014-02-13
You are welcome :-)

Please click on Thread Tools at the top of this page and mark this thread as SOLVED

---

