---
title: "Can't use apt-get update at school."
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Jarthur121 on 2010-07-28
Hey everyone, just a quick question.

I've been using Ubuntu 10.04 on my new laptop for a while now and I've recently just started taking it to my school and hooking it up to the school's wireless network. While I've been at school I've tried doing some very simple things such as updating the system using:
```
sudo apt-get update
```When I do this I get the following errors:

```

james@james-laptop:~$ sudo apt-get update
Err http://au.archive.ubuntu.com lucid  Release.gpg                             
  Could not connect to au.archive.ubuntu.com:80 (202.158.214.106). -  connect (110: Connection timed out)
Err http://au.archive.ubuntu.com/ubuntu/ lucid/main  Translation-en_AU          
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid/restricted  Translation-en_AU    
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid/universe  Translation-en_AU      
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid/multiverse  Translation-en_AU    
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates  Release.gpg                     
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/main  Translation-en_AU  
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/restricted  Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/universe  Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse  Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Ign http://au.archive.ubuntu.com lucid Release        
Ign http://au.archive.ubuntu.com lucid-updates Release
Ign http://au.archive.ubuntu.com lucid/main Packages  
Ign http://au.archive.ubuntu.com lucid/restricted Packages
Ign http://au.archive.ubuntu.com lucid/main Sources   
Ign http://au.archive.ubuntu.com lucid/restricted Sources
Ign http://au.archive.ubuntu.com lucid/universe Packages
Ign http://au.archive.ubuntu.com lucid/universe Sources
Ign http://au.archive.ubuntu.com lucid/multiverse Packages
Ign http://au.archive.ubuntu.com lucid/multiverse Sources
Ign http://au.archive.ubuntu.com lucid-updates/main Packages
Ign http://au.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://au.archive.ubuntu.com lucid-updates/main Sources
Ign http://au.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://au.archive.ubuntu.com lucid-updates/universe Packages
Ign http://au.archive.ubuntu.com lucid-updates/universe Sources
Ign http://au.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://au.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://au.archive.ubuntu.com lucid/main Packages   
Ign http://au.archive.ubuntu.com lucid/restricted Packages
Ign http://au.archive.ubuntu.com lucid/main Sources    
Ign http://au.archive.ubuntu.com lucid/restricted Sources
Ign http://au.archive.ubuntu.com lucid/universe Packages
Ign http://au.archive.ubuntu.com lucid/universe Sources
Ign http://au.archive.ubuntu.com lucid/multiverse Packages
Ign http://au.archive.ubuntu.com lucid/multiverse  Sources                      
Ign http://au.archive.ubuntu.com lucid-updates/main  Packages                   
Ign http://au.archive.ubuntu.com lucid-updates/restricted  Packages             
Ign http://au.archive.ubuntu.com lucid-updates/main  Sources                    
Ign http://au.archive.ubuntu.com lucid-updates/restricted  Sources              
Ign http://au.archive.ubuntu.com lucid-updates/universe  Packages               
Ign http://au.archive.ubuntu.com lucid-updates/universe  Sources                
Ign http://au.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://au.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://au.archive.ubuntu.com lucid/main Packages   
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid/restricted Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid/main Sources    
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid/restricted Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid/universe Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid/universe Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid/multiverse Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid/multiverse Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/main Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/restricted Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/main Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/restricted Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/universe Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/universe Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/multiverse Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates/multiverse Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect  (110: Connection timed out) [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main  Translation-en_AU
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted  Translation-en_AU
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe  Translation-en_AU
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse  Translation-en_AU
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Ign http://security.ubuntu.com lucid-security Release
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Err http://security.ubuntu.com lucid-security/main Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/restricted Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/universe Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/multiverse Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not  connect to au.archive.ubuntu.com:80 (202.158.214.106). - connect (110:  Connection timed out)

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_AU.bz2   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg   Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect  (110: Connection timed out) [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_AU.bz2   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_AU.bz2   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_AU.bz2   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_AU.bz2   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz   Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz   Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

E: Some index files failed to download, they have been ignored, or old  ones used instead.


```Or trying to install a program, say cheese for example:

```

james@james-laptop:~$ sudo apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cheese

```Is there a reason for this/is there a workaround that I can use to get my updates to work?

James.

---

### Post by adamjkok on 2010-07-28
Is ubuntu.com blocked? My school has really dumb security people and they block any website that they don't think is educational. Could be your case too.

---

### Post by jerenept on 2010-07-28
proxy proxy proxy

Is the proxy server correctly configured? you may need to ask the IT Admin about this.

Apply the proxy settings systemwide after you set them in System>Preferences>Network Proxy

---

### Post by lisati on 2010-07-28
It's possible that something that the updates need is blocked by your school. 

On a side note, it's **always** a good idea to co-operate with the IT people and work within the rules set by your school/organization instead of trying to circumvent the rules.

---

### Post by alphacrucis2 on 2010-07-28
> **jerenept said:**
> proxy proxy proxy

Is the proxy server correctly configured? you may need to ask the IT Admin about this.

Apply the proxy settings systemwide after you set them in System>Preferences>Network Proxy

You may have to set the proxy in Synaptic Package Manager under Settings - Preferences - Network. IIRC apt ignores the so called "system wide" proxy settings

---

### Post by adamjkok on 2010-07-28
> **jerenept said:**
> proxy proxy proxy

Is the proxy server correctly configured? you may need to ask the IT Admin about this.

Apply the proxy settings systemwide after you set them in System>Preferences>Network Proxy
That's true, but it sounds like OP can get online but can't get access ubuntu.com. He didn't say for sure, but I would assume this just by how the post was worded.

Anyway, my school's security team uses a proxy as our only form of security. Most likely the admin won't give you the proxy settings, but if your school uses Windows, look in the Fx/IE/Chrome (or whatever browser) settings. That's how I got mine. Keep in mind that this may violate school policy, but I truthfully didn't care, because our security people are dumb and didn't have the technical know-how to find my iPod. It was proxy.(district)usa.lan:8888. Why didn't I guess that in the first place? :-P

Here's someone else's blog post on our security software: [http://www.scootinger.net/2007/03/03/twotrees-shelterbelt-worst-filtering-system-ever/](http://www.scootinger.net/2007/03/03/twotrees-shelterbelt-worst-filtering-system-ever/)
I didn't write it but it shows how absolutely absurd our filter is.

---

### Post by dpacmittal on 2010-07-28
Can you browse sites without using a proxy?

---

### Post by Jarthur121 on 2010-07-28
Ahh, thanks for pointing me in the direction of System proxy, I just chucked in the school's proxy details and it worked. Thanks guys :)

---

