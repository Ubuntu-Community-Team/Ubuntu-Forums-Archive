---
title: "problems connecting to cisco anyconnect vpn client"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by dagarshali on 2010-05-16
Hi,
I recently did a fresh install of 9.10, which i upgraded to lucid lynx. I have installed a 64 bit system. When I try to install the vpn client from the school website, it couldn't do it automatically and instead i had to download a .sh file. It said linuxi386.sh

I ran it as a root and it installed.but, when i tried to connect, it gives the following message

connection attempt has failed due to server certificate problem. 

I tried to work this out with the help from the school IT department and they don't support linux:(

Can anybody help me solve this issue.

Regards,
Vishwa

---

### Post by casevh on 2010-05-17
That is the 32-bit version of the AnyConnect client. The following steps should work:

1) Install the ia32-libs package.
2) Install the lib32nss-mdns package.
3) Create the directory "/usr/local/firefox". This directory is searched first by the AnyConnect client and needs to contain symlinks to 32-bit versions of certain files.

```
cd /usr/local
sudo mkdir firefox
cd firefox
sudo ln -s /usr/lib32/libnss3.so
sudo ln -s /usr/lib32/libplc4.so
sudo ln -s /usr/lib32/libnspr4.so
sudo ln -s /usr/lib32/libsmime3.so
sudo ln -s /usr/lib32/nss/libsoftokn3.so
```

There is another option.

Cisco released a native 64-bit Linux client last week. You will need to work with your university's IT group since they will need to download from Cisco both the actual Linux client for you plus the corresponding package that MUST be installed on the remote access server. If they'll do that for you, the new client works well.

casevh

Caveat: If you've already made the 32-bit client work by creating /usr/local/firefox, you will need to remove that directory before the 64-bit client will work.

---

### Post by dagarshali on 2010-05-18
Hi,
Thanks very much..that sure did the trick..

Regards,
Vishwa

---

### Post by volkyl on 2010-06-14
Thanks casevh!  Your instructions worked for me too!

---

