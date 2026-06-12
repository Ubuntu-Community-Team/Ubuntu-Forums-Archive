---
title: "I've messed up my Public Keys"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by held7over on 2009-12-08
I am getting the following error message, plus a warning I can not trust any update, when I try to update. 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271

How do I fix this?

Thanks! :D

---

### Post by sandyd on 2009-12-08
```

gpg --no-default-keyring --keyring /tmp/empathy.keyring --keyserver keyserver.ubuntu.com --recv 71ADF3D49D6DB68769CC6C0B638ABCA0FA3A1271 && gpg --no-default-keyring --keyring /tmp/empathy.keyring --export --armor 71ADF3D49D6DB68769CC6C0B638ABCA0FA3A1271 | sudo apt-key add - && rm /tmp/empathy.keyring

```

---

### Post by sisco311 on 2009-12-08
Open a terminal and run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FA3A1271
```
to add the key to the list of trusted keys.

then:
```
sudo apt-get update
``` 


[https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

---

### Post by held7over on 2009-12-08
Thanks!  

Everything is happy again.

And thanks for the URL, I will study it and make some notes.

---

### Post by Purple Mouse on 2009-12-11
What does the "empathy" refer to in your  code. I'm struggling to get a public key. So far the server keeps timing out, I've tried to down load the same key from other servers mentioned in other posts however the same result. Server timed out. Have tried over 5 days now. Has anyone got a suggestion other than 
 	Code:
 	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FA3A1271 
 to add the key to the list of trusted keys.
 
 then:
  	Code:
 	sudo apt-get update

---

### Post by MelDJ on 2009-12-11
perhaps you are using a different program than the one the op is using. different sources have different gpg keys.
try the link in my sig

---

### Post by Purple Mouse on 2009-12-12
Ok thanks for the link. I cut and paste the key into the code at the appropriate place. Here is the error message:
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D

---

