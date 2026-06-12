---
title: "Straange certificates problem"
date: 2019-06-17
forum: Networking &amp; Wireless
---

### Post by kahlenberg on 2019-06-17
Hi,
I have very strange certificate problem.
I tried all of the suggested solution in internet, but nothing worked for me.
I try to install sublime-text but get certificate problem:

```

>sudo aptitude install sublime-text

The following NEW packages will be installed:
  sublime-text 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9.846 kB of archives. After unpacking 34,8 MB will be used.
Err https://download.sublimetext.com apt/stable/ sublime-text 3207
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.236.0.104 443]
0% [Working]W: https://download.sublimetext.com/files/sublime-text_build-3207_amd64.deb: No system certificates available. Try installing ca-certificates.
E: Failed to fetch https://download.sublimetext.com/files/sublime-text_build-3207_amd64.deb: Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.236.0.104 443]
E: Unable to fetch some packages; try '-o APT::Get::Fix-Missing=true' to continue with missing packages


```

I try curl:

```

>curl https://www.google.com

curl: (77) error setting certificate verify locations:
  CAfile: /etc/ssl/certs/ca-certificates.crt
  CApath: /etc/ssl/certs

```


I try wget, it works:

```

>wget https://www.google.com

--2019-06-17 14:55:26--  https://www.google.com/
Resolving www.google.com (www.google.com)... 172.217.16.100, 2a00:1450:400d:808::2004
Connecting to www.google.com (www.google.com)|172.217.16.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;index.html&#8217;

index.html                                           [ <=>            ]  11,11K  --.-KB/s    in 0,009s  

2019-06-17 14:55:26 (1,17 MB/s) - &#8216;index.html&#8217; saved [11381]



```

I tried following suggested solution already but nothing worked for me:
>sudo apt-get install --reinstall ca-certificates
>sudo update-ca-certificates
>sudo aptitude update
>sudo apt-get install --reinstall openssl libssl1.0.0 libssl1.1 libssl-dev

---

