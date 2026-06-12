---
title: "SSH Key-Based Authentication"
date: 2016-04-24
forum: Networking &amp; Wireless
---

### Post by zergling on 2016-04-24
Hello everyone,

I am opening this thread because I would like to set up my Ubuntu server (if possible) to give different privileges based on X pairing keys.

*_These are my current settings_*

[INDENT]```
**Local Debian Machine 1**
user: zerg
ssh key named: Italy (private key)

```[/INDENT]

[INDENT]```
**Remote Debian Machine 2**
user: overlord
ssh key named: Japan (private key)

```[/INDENT]

[INDENT]```
**Remote Server Ubuntu Machine** 

both public keys (Italy and Japan) are stored in .ssh/authorized_keys 

```[/INDENT]

Currently, to access the Ubuntu server, I do the following:

[INDENT]```
ssh -i Italy server@x.x.x.x

ssh -i Japan server@x.x.x.x
```[/INDENT]

Right now, both machines (Debian 1 and Debian 2) have full access (privileges) on my Ubuntu server.

So my question is, how do I restrict Debian 2 privileges in a way that is only able to create/modify/delete  within a particular directory?

Bye and thank you in advantage ^_^

---

### Post by bab1 on 2016-04-24
> **zergling said:**
> Hello everyone,

I am opening this thread because I would like to set up my Ubuntu server (if possible) to give different privileges based on X pairing keys.

*_These are my current settings_*

[INDENT]```
**Local Debian Machine 1**
user: zerg
ssh key named: Italy (private key)

```[/INDENT]

[INDENT]```
**Remote Debian Machine 2**
user: overlord
ssh key named: Japan (private key)

```[/INDENT]

[INDENT]```
**Remote Server Ubuntu Machine** 

both public keys (Italy and Japan) are stored in .ssh/authorized_keys 

```[/INDENT]

Currently, to access the Ubuntu server, I do the following:

[INDENT]```
ssh -i Italy server@x.x.x.x

ssh -i Japan server@x.x.x.x
```[/INDENT]

Right now, both machines (Debian 1 and Debian 2) have full access (privileges) on my Ubuntu server.

What do you mean by *full access*?  Do these users have sudo rights?
> 

So my question is, how do I restrict Debian 2 privileges in a way that is only able to create/modify/delete  within a particular directory?
This question is really about directory and file ownership and permissions.  SSH only provides the remote login access.  

If the directory structure is reasonable and the users do not have sudo rights you can grant or limit access by user and user-group ownership and permissions.  By default on an Ubuntu system any file that is created is owned by the user that created (user:usergorup).  The user has read and write permissions and all others can read the file (if the directory the file is in allows that).  If you remove the read permission then only the user that created the file has access.  Of course the root user always has access except for a few rare cases.

---

### Post by ian-weisser on 2016-04-25
bab1 to completely right.
It's not about client ssh settings. It's about server login account settings, permissions, ownerships, and group memberships.

---

