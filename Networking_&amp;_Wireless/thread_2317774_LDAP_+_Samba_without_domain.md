---
title: "LDAP + Samba without domain?"
date: 2016-03-19
forum: Networking &amp; Wireless
---

### Post by LeNy95 on 2016-03-19
Hello, I've just installed and configured LDAP + Sampa with LAM web account manager. 

I used this tutorial:
```
http://www.linuxsecrets.com/categories/latest-articles/setup-samba-domain-controller-with-ldap-on-debian-ubuntu-scientific-linux-fedora-centos-redhat
```

And I want to connect to my samba public folder across Windows 7 Home Premium (don't have domain controller). Is is possible to do this? Or is it possible to change a verification in LDAP / samba without domain ?

// Edit:
I mean that is it possible to join with workgroup without domain?

---

### Post by bab1 on 2016-03-19
> **LeNy95 said:**
> Hello, I've just installed and configured LDAP + Sampa with LAM web account manager. 

I used this tutorial:
```
http://www.linuxsecrets.com/categories/latest-articles/setup-samba-domain-controller-with-ldap-on-debian-ubuntu-scientific-linux-fedora-centos-redhat
```

And I want to connect to my samba public folder across Windows 7 Home Premium (don't have domain controller). Is is possible to do this? Or is it possible to change a verification in LDAP / samba without domain ?

// Edit:
I mean that is it possible to join with workgroup without domain?
Yes it is possible to share files without a domain (using workgroups).  You don't *"join"* a workgroup at all.  The workgroup is just a way to visually arrange the shares that reside on multiple machines.  The domain is for managing users and groups, not managing sharing.

Why did you install Samba as a AD-DC if you are using the server to serve (share) files in a workgroup situation?  

You can create shares using the /etc/samba/smb.conf file to configure the parameters, but I have heard that this setup has had problems when the server is also a AD-DC.  I believe that Samba.org will resolve this in the future with Samba v4.3.

[**Here**]("http://www.jonathanmoeller.com/screed/?p=3608") is a good basic guide to configuring Samba as a standalone file server.

---

### Post by LeNy95 on 2016-03-20
Thanks for reply. My friend told me that "install LDAP and Samba, that gave you easy users control etc.." so i do this. After installation I have read that only Professional or higher type of Windows can join to domains, so I'm looking for the golden mean

---

### Post by bab1 on 2016-03-20
> **LeNy95 said:**
> Thanks for reply. My friend told me that "install LDAP and Samba, that gave you easy users control etc.." so i do this. After installation I have read that only Professional or higher type of Windows can join to domains, so I'm looking for the golden meanI don't get it.  Are you interested in managing users in a centralized location?  How many users will you have? If you don't have many users you can manage users without the complexity of a LDAP domain setup.   Or, are you interested in managing Samba shares that are available across a simple network?  

There is no "golden mean" between these two different objectives.

---

### Post by LeNy95 on 2016-03-21
I've got more than 50 accounts, so I want to use LDAP as account manager for samba without domain. Is it possible ?

---

### Post by bab1 on 2016-03-21
> **LeNy95 said:**
> I've got more than 50 accounts, so I want to use LDAP as account manager for samba without domain. Is it possible ?
If you use Samba as a AD-DC then a domain is created upon installation.  This can be a local domain only.  There is no need to register this domain name or maintain an ICANN Internet Domain Name for Samba to work.

---

### Post by LeNy95 on 2016-03-21
> **bab1 said:**
> If you use Samba as a AD-DC then a domain is created upon installation.  This can be a local domain only.  There is no need to register this domain name or maintain an ICANN Internet Domain Name for Samba to work.

Yep I know that, but I can't connect to Samba public folder on Windows Home and lower because they aren't support domains. So I have two ideas:
1. disable connect to samba folder via domain (possible), LDAP will be only samba account manager
2. look for another samba web account manager
 
Which way is best?

---

### Post by bab1 on 2016-03-21
> **LeNy95 said:**
> Yep I know that, but I can't connect to Samba public folder on Windows Home and lower because they aren't support domains. 

Have you tried to configure a Samba share and then access it from a Windows machine?  If the Samba share is configured to allow all users (*guest ok = yes*) then there is _no [COLOR="#008000"]**authentication**[/COLOR] of the user_ (who are you?).  All [COLOR="#FF0000"]authorization[/COLOR] (you can do that) is always carried out by the Linux OS file system.

I believe the only thing that Windows Home version can't do is administrate the AD-DC because it can't successfully install the [**Remote Server Administration Tools**]("https://www.microsoft.com/en-us/download/details.aspx?id=45520").
> 


So I have two ideas:
1. disable connect to samba folder via domain (possible), LDAP will be only samba account manager

There is no "connect via domain".  Your options are; authenticate with user data via LDAP database or authenticate using a local Samba and Linux user databases.
> 
2. look for another samba web account manager

I don't think you mean exactly what you said here.  Do you mean an web based app that manages the LDAP database?  Or do you mean another method all together to manage your users; one that takes the place of LDAP?

---

