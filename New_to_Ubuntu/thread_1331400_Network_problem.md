---
title: "Network problem"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2009-11-19
hi,
could someone please help me to connect ubuntu 9.10 to my network.

i need it to auto detect network settings kind of like what firefox does under preferences,network then settings.then i tick auto detect network settings for this network.

with this i can access the internet through firefox but i cannot access update manager etc.

EDIT:i am using a wired connection!

could someone please help me with this problem.

thanks in advanced 

Daniel

---

### Post by ukripper on 2009-11-19
go to System-->Preferences-->Network connections and check whether is is set to auto eth0 under the wired tab? select auto eth0 and then Edit check "automatically connect"

---

### Post by Bon Dup on 2009-11-19
hey man
 have you had a look in your "edit connections"?

if its a wired connection then it should be something pretty obvious

---

### Post by betterthanjordan79 on 2009-11-19
no i have internet but its because its running from a lan i think.i need it to auto detect these settings.like i said firefox auto detect the settings,i need to do the same for ubuntu.

thanks for replyin btw

---

### Post by ukripper on 2009-11-19
> **betterthanjordan79 said:**
> no i have internet but its because its running from a lan i think.i need it to auto detect these settings.like i said firefox auto detect the settings,i need to do the same for ubuntu.

thanks for replyin btw

follow my post #2 above.

---

### Post by betterthanjordan79 on 2009-11-19
> **ukripper said:**
> follow my post #2 above.

yh i have and this is already done...

---

### Post by ukripper on 2009-11-19
ok in that case network manager is auto detecting your settings, so what is your question?

---

### Post by betterthanjordan79 on 2009-11-19
> **ukripper said:**
> ok in that case network manager is auto detecting your settings, so what is your question?

update manager,add/remove etc is not detecting network settings...

---

### Post by ukripper on 2009-11-19
in terminal can you run this command and see if you can find packages in add/remove after this:
```
sudo apt-get update
```

any errors post here

---

### Post by betterthanjordan79 on 2009-11-19
> ubuntu@ubuntu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]
Reading package lists... Done                        
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111: Connection refused) [IP: 91.189.88.46 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


thats what i get...

---

### Post by bwzz on 2009-11-19
It's obvious that there is a network proxy.
You have to manually add it in the Network Proxy settings.
It seems that it's IP is: 91.189.88.46 and port 80

---

### Post by betterthanjordan79 on 2009-11-19
na it still didnt work-i included an image just incase i set up the proxy wrong

[IMG]http://i49.tinypic.com/id8uiq.png[/IMG]

---

### Post by bwzz on 2009-11-19
First, make sure of the proxy IP. It might not the one I gave you.
THEN:
You need to "Apply System-wide" and put the password.
You may also need to put int network proxy credentials. (by clicking on "Details")

---

### Post by bwzz on 2009-11-19
Silly of me, the 91.189.88.46 IP is the Ubuntu server.
are you connected directly to Internet? are you in a business network?

---

### Post by betterthanjordan79 on 2009-11-19
im at college using a usb setup. im on a college network. this is my results after ipconfig
> ubuntu@ubuntu:~$ ifconfig
eth3      Link encap:Ethernet  HWaddr 00:21:9b:35:0e:78  
          inet addr:10.6.16.206  Bcast:10.6.16.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fe35:e78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:8178533 (8.1 MB)  TX bytes:1821999 (1.8 MB)
          Memory:fe9e0000-fea00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ /sbin/ifconfig
eth3      Link encap:Ethernet  HWaddr 00:21:9b:35:0e:78  
          inet addr:10.6.16.206  Bcast:10.6.16.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fe35:e78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:8233516 (8.2 MB)  TX bytes:1830896 (1.8 MB)
          Memory:fe9e0000-fea00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

ubuntu@ubuntu:~$ 


---

### Post by bwzz on 2009-11-19
How is FireFox configured?
Please include a screen shot if possible.

---

### Post by betterthanjordan79 on 2009-11-19
im using a windows machine now at the minute but its set up the same way as im on the same network.

[IMG]http://i45.tinypic.com/ixe3nn.jpg[/IMG]

---

### Post by bwzz on 2009-11-19
I would suggest trying to find out what is the proxy address is.
If you could  paste the output of trace route to [www.ubuntu.com](www.ubuntu.com)
the command is tracert in Win XP.

---

### Post by betterthanjordan79 on 2009-11-19
this is what i got

> [IMG]http://i48.tinypic.com/35lfcpk.jpg[/IMG]

is there a way to find this out through ubuntu as i am running it on a computer beside me now

---

### Post by bwzz on 2009-11-19
It appears to me that your proxy or gateway IP is: 10.3.3.2
try it out.
I don't know the Linux command for tracert, sorry

---

