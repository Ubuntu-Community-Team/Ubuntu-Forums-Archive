---
title: "Update Manager&gt; Downloading Packages&gt; Download Speed Problem"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by noluftu on 2009-02-15
I formatted my laptop & install ubuntu. But i cannot update my system. Download speed is unknown.. I can download everything at maximum speed of my connection..

What can i do?

---

### Post by 2hot6ft2 on 2009-02-15
Have you had it find the best server for getting your updates and packages? It can make a big difference.
System>Administration>Software Sources
click on the "Download From" choose "Other" then choose
"Select Best Server"
when it's done testing the servers click on "Choose Server" then Close and then Reload.

Now your updates and packages will come from the best server for you and where you're located.

---

### Post by noluftu on 2009-02-17
Thank you very much... I will try..

---

### Post by noluftu on 2009-03-05
I did. But i get "No suitable download server was found. Please check your Internet Connection"

But i have internet connection.. :(

---

### Post by skymera on 2009-03-05
> **noluftu said:**
> I did. But i get "No suitable download server was found. Please check your Internet Connection"

But i have internet connection.. :(

Great :D

But are you connected?

Try pinging a website.

---

### Post by billgoldberg on 2009-03-05
> **skymera said:**
> Great :D

But are you connected?

Try pinging a website.


Open up your terminal (applications -> accessories -> terminal) and enter this command
```

ping google.com

```

What output does it give?

------

You could try a different mirror, pick one that's in your country or a neighbouring one.

---

### Post by noluftu on 2009-03-05
> **noluftu said:**
> I did. But i get "No suitable download server was found. Please check your Internet Connection"

But i have internet connection.. :(

I fixed. My internet connection does not allow ubuntu update.. I tried another connection and successful..

---

### Post by LiaGalanodel on 2009-10-14
I'm sorry but I have the same problem and I'm new in linux...I try to do: ping google.com
```

PING google.com (74.125.45.100) 56(84) bytes of data.
```I wait a long time and I stop this command:

```
--- google.com ping statistics ---
335 packets transmitted, 0 received, 100% packet loss, time 335477ms
```


Can you help me.

I believe that I have a problem with GPG Key

---

### Post by 3rdalbum on 2009-10-14
If you can't ping Google, and you can't hit the repositories, then you either don't have Internet connectivity or your DNS entries are incorrect.

Try going into Network Manager and changing the IPv4 settings to Automatic (Addresses only) and putting in the following DNS: 208.67.222.222

This is the OpenDNS service. If your internet connection doesn't work after you put the OpenDNS address in, then you don't have any connectivity.

---

### Post by LiaGalanodel on 2009-10-14
Thank you for your answer!

I try and when I put the DNS I have no connection.

---

### Post by CharlesA on 2009-10-14
Post the result of ifconfig.

---

### Post by LiaGalanodel on 2009-10-14
```
amelieathanassiadis@SorinLinux:~/Arm/GCCarm/binutils-2.17/arm-linux$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:92:4e:3c  
          inet addr:10.135.9.113  Bcast:10.135.15.255  Mask:255.255.248.0
          inet6 addr: fe80::208:74ff:fe92:4e3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:496241 errors:0 dropped:0 overruns:1 frame:0
          TX packets:113420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:199577812 (199.5 MB)  TX bytes:22417840 (22.4 MB)
          Interrupt:18 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:968 (968.0 B)  TX bytes:968 (968.0 B)

```

Thank you,

---

### Post by LiaGalanodel on 2009-10-15
I try to find a solution and it's a GPG key problem.
When I write : 

```
apt-get update
``````
Fetched 570B in 1s (399B/s)                               
W: GPG error: http://us.archive.ubuntu.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```Here that's whath I have when I do your solution:

```
amelieathanassiadis@SorinLinux:~$ gpg --keyserver keyserver.ubuntu.com --recv 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpgkeys: key 437D05B5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
amelieathanassiadis@SorinLinux:~$ gpg --export --armor 437D05B5 | sudo apt-key add -
[sudo] password for amelieathanassiadis: gpg: WARNING: nothing exported

gpg: no valid OpenPGP data found.

```Thanks,

Best regards.

---

