---
title: "Cannot connect to Nessus"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by roton on 2010-03-19
I downloaded Nessus and the gui client from their website, and installed it.

I added a user (nessus-adduser) and made certificates (nessus-mkcert).

Using the gui client to connect to 127.0.0.1 on port 1241 with the user created earlier.

SSL settings are: 

path to ca - /opt/nessus/com/nessus/CA/cacert.pem
path to key - /opt/nessus/var/nessus/CA/cakey.pem
path to cert - /opt/nessus/com/nessus/CA/servercert.pem

I keep getting "It was not possible to connect to the remote host - make sure the host IP and port are correct and that the Nessus Server service is running".

"ps -aux | grep nessusd" shows that nessusd is indeed running. 

Also tried "sudo /etc/init.d/nessusd restart".

I don't have any firewall software loaded.

Any ideas what I'm doing wrong?

---

### Post by Gixxy on 2010-03-20
Are you trying to use the client to connect to it or a browser? I could not get the nessus client program to connect to it. (maybe from lack of effort) But [https://localhost:8834](https://localhost:8834) works just fine. Try that hos. Must be new with the new version of nessus.  ;)

---

### Post by roton on 2010-03-20
> **Gixxy said:**
> Are you trying to use the client to connect to it or a browser? I could not get the nessus client program to connect to it. (maybe from lack of effort) But [https://localhost:8834](https://localhost:8834) works just fine. Try that hos. Must be new with the new version of nessus.  ;)

Nothing worked until I added an exception to hosts.allow. Now I can access the web interface using your link but the client says "the remote host does not seem to be a Nessus server (or an SSL error occured)" when trying to connect on port 8834 (which is weird because I thought Nessus default port was 1241).

I've run nmap against localhost and neither 1241 nor 8834 are even open. Ah well I suppose I'm happy to just use the web interface for now.

Thanks for your help Gixxy.

---

### Post by Gixxy on 2010-03-21
Glad to help out... with the old version the client did connect on 1241. I think they have changed they way it works... since they have the security center and what not they are trying to sell. I am actually digging the web interface though... I think its pretty slick and takes some annoying steps out of scanning the client would put you through.

well, happy scanning... ;)

---

