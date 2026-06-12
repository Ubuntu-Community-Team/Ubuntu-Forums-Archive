---
title: "Could not download all repositories indexes"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by oaridus on 2009-10-13
Hi, while updating Synaptic I get the following error message and Synaptic stops without updating the list. I am new to Linux, So could someone help me out with this problem.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  407 Proxy Authentication Required
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tchoklat on 2009-10-13
When you attempt to connect to a Web site through proxy server, the following error may appear: 
HTTP/1.1
407 Proxy Authentication Required

You must authenticate with a proxy server before this request can be serviced.
Please logon to your proxy server and then try again.
 
**Are you using a proxy????**

---

### Post by mimor on 2009-10-13
Are you behind a firewall?
It seems like there is a proxy between you and the server.
And you need to get authed to get trough.

[This article]("https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320") on launchpad should help you.

---

### Post by crolanx on 2009-10-13
Hi,

according to the error message ```
407 Proxy Authentication Required
```, it seems that you are using a proxy.

When you try to download the index files, you need to authenticate yourself, but Synaptic does not.

You could take a look at *System* --> *Preferences* --> *Network Proxy* and check that either no Proxy is set or that you use the correct settings.

---

### Post by oaridus on 2009-10-13
I am working in an educational institute where they have set up a proxy. I used the Network Proxy in System -> Preferences to add the details of my proxy. I also entered the username and password in the authetication tab. But for some reason I am not able to connect to update my system. Any help in this regard would be welcome!!

---

### Post by crolanx on 2009-10-13
Maybe the proxy blocks all traffic to some domains and unfortunately, **archive.ubuntu.com** could be one of those domains which are blocked.

---

### Post by rustutzman on 2009-10-13
You are probably going to have to use NTLmaps to authenticate with the proxy. It's pretty easy to setup. You can download it from the repositories with a net enabled connection [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Russ

---

