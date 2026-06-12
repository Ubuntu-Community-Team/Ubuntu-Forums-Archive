---
title: "Pidgin Not connecting... period!"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Sugz on 2009-09-03
Im using Gutsy 7.10
And suddenly as if overnight (granted it was 2 months ago now) pidgin has suddenly
decided that it will not connect at all. 
I have checked my credentials, port and connection method, to no success. 

This had better not be another case of..."Oh we have decided to break this app because you have not updated to a more recent version of Ubuntu" 

Again thanks for your support.

---

### Post by dearingj on 2009-09-03
> **Sugz said:**
> Im using Gutsy 7.10
And suddenly as if overnight (granted it was 2 months ago now) pidgin has suddenly
decided that it will not connect at all. 
I have checked my credentials, port and connection method, to no success. 

This had better not be another case of..."Oh we have decided to break this app because you have not updated to a more recent version of Ubuntu" 

Again thanks for your support.

Which services are you trying to connect to? I know that MSN and Yahoo have been known to change their protocols once in a while, possibly to prevent third-party apps like Pidgin from connecting.

The Ubuntu developers never deliberately break apps, but they can't keep supporting old versions forever.

---

### Post by Sugz on 2009-09-25
I am trying to connect to MSN, however I am still as of yet, unable to connect.

---

### Post by jflaker on 2009-09-25
Might be time to upgrade, don't ya think?

---

### Post by cgroza on 2009-09-25
I had the same problem to Yahoo.I just added "cn" at the begining of the page server adress and it worked....I dont know about MSN....

---

### Post by Sugz on 2009-09-30
I tried the above solution but to no avail. 
Aaaaand im still very reluctant to upgrade simply for the fact that I don't trust upgrading Linux yet. 
It is working (almost) perfectly on my laptop, and I want to keep it that way.

---

### Post by ankspo71 on 2009-09-30
If it helps any, Pidgin 2.5.5 in Jaunty uses these advanced options as default for MSN.

Server: messenger.hotmail.com
Port: 1863
Use http method: Disabled
Http Method Server: gateway.messenger.hotmail.com
Proxy Options: Use gnome proxy settings

I don't chat but I looked in the pidgin options anyways. I thought maybe this might help somehow. Btw, give the Jaunty live cd a spin and see if it works out for you, or you could install Jaunty inside virtualbox to chat that way.
James.

---

### Post by mharrison on 2009-09-30
> **ankspo71 said:**
> If it helps any, Pidgin 2.5.5 in Jaunty uses these advanced options as default for MSN.

Server: messenger.hotmail.com
Port: 1863
Use http method: Disabled
Http Method Server: gateway.messenger.hotmail.com
Proxy Options: Use gnome proxy settings

I don't chat but I looked in the pidgin options anyways. I thought maybe this might help somehow. Btw, give the Jaunty live cd a spin and see if it works out for you, or you could install Jaunty inside virtualbox to chat that way.
James.

I think the servers are the issue here.  I did an install of Hardy the other day and Pidgin wouldn't connect to Yahoo or MSN...I did a full update of the system and it still wouldn't connect.  I stole the server settings from my Jaunty box and it connected right away.

I would suggest trying out the server settings listed above and see if you can connect.

---

### Post by nnamdi on 2009-09-30
get a new ubuntu distro 8.04 up gusty has no support again man

---

### Post by LewRockwell on 2009-09-30
[http://www.ubuntugeek.com/fix-for-master-password-expose-for-pidgin.html](http://www.ubuntugeek.com/fix-for-master-password-expose-for-pidgin.html)

.

---

### Post by rajeev1204 on 2009-09-30
> **Sugz said:**
> Im using Gutsy 7.10
And suddenly as if overnight (granted it was 2 months ago now) pidgin has suddenly
decided that it will not connect at all. 
I have checked my credentials, port and connection method, to no success. 

This had better not be another case of..."Oh we have decided to break this app because you have not updated to a more recent version of Ubuntu" 

Again thanks for your support.

Gutsy has reached end of life (eol) ,please upgrade your OS, any new patches will not be available for your OS,including the yahoo connectivity issue which happened 2 months ago.

---

