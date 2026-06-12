---
title: "Issue with export http_proxy"
date: 2015-02-03
forum: Networking &amp; Wireless
---

### Post by Laljeev_M on 2015-02-03
Hi

I'm new to Ubuntu server (Ver 14) . We configured the proxy as seen below

export http_proxy=http://mydomain\username:123@pwrd@10.110.10.2:5454 

Later we corrected it as below by adding %40 before special characters

export http_proxy=http://mydomain%40\username:123%40@pwrd@10.110.10.2:5454

While running sudo apt-get update it's saying could not resolve @pwrd@10.110.10.2

Please help us to correct this. We updated the /etc/environment file with http_proxy=http://10.110.10.2:5454, and rebooted the server and still getting the same error. 

Hope some one can help on this

---

### Post by Laljeev_M on 2015-02-03
Later we found we can download files (wget [http://download.beyondtrust.com/PBISO/8.2/linux.deb.x64/pbis-open-8.2.0.2969.linux.x86_64.deb.sh](http://download.beyondtrust.com/PBISO/8.2/linux.deb.x64/pbis-open-8.2.0.2969.linux.x86_64.deb.sh)) and echo $http_proxy showing correct infiormation as [http://10.110.10.2:5454](http://10.110.10.2:5454). The only thing failing is  sudo apt-get update, even we followed [http://askubuntu.com/questions/7470/how-to-run-sudo-apt-get-update-through-proxy-in-commandline](http://askubuntu.com/questions/7470/how-to-run-sudo-apt-get-update-through-proxy-in-commandline) and modified visudo, but still issue persists

---

### Post by SeijiSensei on 2015-02-03
```
http://mydomain\username:123@pwrd@10.110.10.2:5454
```
That's not a valid URL.  Use only forward slashes ("/"), and there can be just one "@" character between the username:password and the hostname or IP address.  What is "@pwrd" supposed to mean?  If it's part of the password, change the password to use a character not found in URLs like "^".

Perhaps you are trying to log into a Windows domain with that "mydomain\username"?  If so, you might need to ask on a Windows board.

---

