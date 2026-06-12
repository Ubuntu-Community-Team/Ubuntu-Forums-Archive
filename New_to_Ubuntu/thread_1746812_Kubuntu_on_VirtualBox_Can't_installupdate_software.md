---
title: "Kubuntu on VirtualBox: Can't install/update software"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2011-05-02
I installed kubuntu 11.04 on an Windows7 PC inside a VirtualBox VM. I have setup the network connections proxy server (didn't accept hostnames btw, had to use the ip) and now i have connection to the internet, and to the UNIX servers that I manage. But I can't use kPackageKit or sudo apt-get update/upgrade/install/etc. Is there something I'm missing?

---

### Post by Abu_Dayya on 2011-05-04
It appears to be something related to proxy. I added a proxy from System Settings -> Network Settings -> Proxy -> Manually specify proxy settings. It still doesn't work. And I can't also add my username and password in Network Settings -> Proxy. The radio button for adding username and password is grayed out. I can only choose "Prompt me". 

I also tried adding the following entry in /etc/PackageKit/PackageKit.conf
```
ProxyHTTP=http://username:password@proxyip:port
```

I also did
```
echo http_proxy=http://username:password@proxyip:port >> $HOME/.bashrc
echo export http_proxy >> $HOME/.bashrc
```

Still can't install software. When hit 'check for new updates' in kpackagekit, it fails and throws an error about proxy authintication. I can still brows the internet through rekonq though.

One more thing, my password as an '@' char in it. could this be why its not working? I tried escaping it with '\' in both PackageKit.conf and .bashrc, and it still doesn't work. this is how it actually looks

```
echo http_proxy=http://yousef:passw\@rd@1.2.3.4:8080 >> $HOME/.bashrc
echo export http_proxy >> $HOME/.bashrc
```

Any help?

---

### Post by gmargo on 2011-05-04
To configure a proxy for the packaging system, edit (or create) **/etc/apt/apt.conf** to add a proxy specification like this, and substitute appropriately:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```
Now **apt-get**, **aptitude**, **synaptic**, (and hopefully PackageKit) should work.

---

### Post by Abu_Dayya on 2011-05-05
Thanks. Will try when get back to work.

What about the '@' char in my password. Do I escape it with '\' or just leave it?

---

### Post by gmargo on 2011-05-05
> **Abu_Dayya said:**
> What about the '@' char in my password. Do I escape it with '\' or just leave it?

I'd be surprised if it worked at all.  Consider changing it.

---

### Post by Abu_Dayya on 2011-05-07
> **gmargo said:**
> I'd be surprised if it worked at all.  Consider changing it.

Yup. Didn't work. Need to contact help desk and change the password

---

### Post by Abu_Dayya on 2011-05-10
Alright, changed the password. Still no go.

This is the error I get in KPackageKit
```
E: Error http://extras.ubuntu.com natty/main Sources
407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied. )
E: Error http://extras.ubuntu.com natty/main i386 Packages
407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied. )

```

I get the same error when I sudo apt-get update

---

