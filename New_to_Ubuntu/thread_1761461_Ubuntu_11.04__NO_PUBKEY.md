---
title: "Ubuntu 11.04  NO_PUBKEY"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by skey. on 2011-05-18
Hi People 
Could some please help me as I just loaded 11.04 everything looks great but this little problem came up  

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444

So is there anyone could please help me

Thanks 
Mick

---

### Post by skey. on 2011-05-18
thanks for quick reply can you explain what you mean and how can I fix the problem

---

### Post by NormanFLinux on 2011-05-18
Open up a terminal and input this command:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv- keys 


Add your key number at the end of it and enter your sudo password. Hit enter. Then wait until the signed key is added to the Signed Key List in Software Sources.

---

### Post by lindsay7 on 2011-05-18
copy and paste these commands into the terminal



gpg --keyserver keyserver.ubuntu.com --recv 83FBA1751378B444
gpg --export --armor 83FBA1751378B444 | sudo apt-key add -

then run

sudo apt-get update

---

### Post by Frogs Hair on 2011-05-18
Make sure the PPA is compatible , if you have upgraded you need to check if there is an 11.04 package.

---

### Post by skey. on 2011-05-18
Thank Every-one 
All fixed

---

