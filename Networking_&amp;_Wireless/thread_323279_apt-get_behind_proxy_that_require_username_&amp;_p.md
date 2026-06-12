---
title: "apt-get behind proxy that require username &amp; password"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by mooha on 2006-12-21
I am on the way to get upset and I think I am going to give up soon, can any one help please, I am behind a proxy server with authenfication, I did put the user and password thing on the apt.conf but no way, can anyone help ?

I tried all methods that was given by users here in forum.

So why apt-get or Adept or synaptic dont use the proxy system configuration to download pakages?

Do I have to activate Root login in graphic and try it out?

I am confused.

Any help is apreciated, thanks

---

### Post by bapoumba on 2006-12-22
Hi,
first, please give the output to **cat /etc/apt/apt.conf**.
I actually have a laptop, there is a proxy at my university network and I have no proxy at home. Works for me.
Is this a ISA proxy ?

---

### Post by lorenzo on 2006-12-22
try:

$> export http_proxy=http://name:password@proxy: port
$> sudo apt-get....

---

### Post by mooha on 2006-12-22
thanx for reply , in  cat /etc/apt/apt.conf  I have :

> $ cat /etc/apt/apt.conf
Acquire::http::Proxy "True";


I tried export and here's what I see after $sudo apt-get update



s> udo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
26% [Waiting for headers] [Waiting for headers]


Please any help?

---

### Post by bapoumba on 2006-12-22
You should have something like :
```
ACQUIRE { 
http:: proxy "http://myproxy.mydomain:xxxx"
};

```
Without the space between http:: and proxy (: p shows up as a smiley).

---

### Post by mooha on 2006-12-22
unfortunately it gave me the same thing,

M I right here ? :

```
ACQUIRE { 
http::proxy "http://myuser:password@myproxy.mydomain:xxxx"
};
```


there is 1 space between proxy and "http://,

---

### Post by bapoumba on 2006-12-22
Well, I do not need authentication with the proxy, but should be correct :
[http://www.die.net/doc/linux/man/man5/apt.conf.5.html]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html")
See the http section in ACQUIRE GROUP

If you are running GNOME, did you set the proxy also in > System > Prefs > Network proxy ?

---

### Post by mooha on 2006-12-22
thanx for quick reply...

I will read the link and I'll let you know.
Yes I did set up the proxy seting and I am running Gnome

---

### Post by mooha on 2006-12-22
](*,) 
](*,) 
](*,) 

Smileys speeks for them selves

Thanx for your help, I think I will give up

---

### Post by bapoumba on 2006-12-22
Why that ?
It should work, or at list a solution might exist.

Is this a ISA proxy ?

---

### Post by mooha on 2006-12-22
yes it is ISA proxy

---

