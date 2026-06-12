---
title: "Apt timing out on update, all other network connections working normally"
date: 2019-11-22
forum: Networking &amp; Wireless
---

### Post by mboros on 2019-11-22
Fresh install of Ubuntu 18.04LTS, run in a VM on a Windows 7 Host. Network is through a proxy which has been set up through the UI, browser, ping, wget working normally.

I've tried configuring the apt.conf file to use the proxy, makes no difference. Also, network does not seem able to handle IPv6 so I'm forcing apt to use IPv4

When I run: 

```
sudo apt -o Debug::Acquire::http=true -o Acquire::ForceIPv4=true update
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                                 
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.23), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.14), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.26), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.24), connection timed out
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                        
  Unable to connect to us.archive.ubuntu.com:http:
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease                                      
  Unable to connect to us.archive.ubuntu.com:http:
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease                                         
  Could not connect to security.ubuntu.com:80 (91.189.88.173), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.24), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.174), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.31), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.26), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.14), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.162), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.23), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.24), connection timed out
Reading package lists... Done                        
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Could not connect to us.archive.ubuntu.com:80 (91.189.91.23), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.14), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.26), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.24), connection timed out
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Unable to connect to us.archive.ubuntu.com:http:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Unable to connect to us.archive.ubuntu.com:http:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Could not connect to security.ubuntu.com:80 (91.189.88.173), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.24), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.174), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.31), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.26), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.14), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.162), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.23), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.24), connection timed out
W: Some index files failed to download. They have been ignored, or old ones used instead.
```


I can wget this address:
```
wget 91.189.91.23:80
--2019-11-22 11:34:41--  [http://91.189.91.23/](http://91.189.91.23/)
Resolving proxy.myproxy.net (proxy.myproxy.net)... myproxyIP
Connecting to proxy.myproxy.net (proxy.myproxy.net)|myproxyIP|:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: 11321 (11K) [text/html]
Saving to: &#8216;index.html&#8217;

index.html                                         100%[================================================================================================================>]  11.06K  --.-KB/s    in 0.001s  

2019-11-22 11:34:41 (21.2 MB/s) - &#8216;index.html&#8217; saved [11321/11321]
```


Any ideas on how to debug this?

---

### Post by TheFu on 2019-11-25
Does this not work?
[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

