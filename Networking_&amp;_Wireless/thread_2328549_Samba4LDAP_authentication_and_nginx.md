---
title: "Samba4/LDAP authentication and nginx"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by ninz0r on 2016-06-22
[COLOR=#242729][FONT=Arial]Before i start with my problem: I've got a website which is protected by a reverse proxy (nginx). So the client is not allowed to connect directly to the website. It must connect to nginx and nginx shows then the content of the website.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now i wanted to add more "security" features. I installed samba4 as it is usable as a AD DC and wanted to use LDAP (which is included in samba4?) to authenticate the clients which are trying to reach the website. So before a client can actually see the website it must connect to nginx and then authenticate itself (with LDAP credentials) and then it can view the websites content.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I configured nginx with the module ldap_http_authentication (see configuration below) and it is working. When the client tries to view the website i need to login with some LDAP credentials, but when i try to authenticate the client it just doesn't work. It says that the LDAP credentials are wrong. How can i add LDAP users when LDAP comes with samba? I just don't know which credentials to use. I added some users to samba like "test" and tried to use their credentials to authenticate, but they don't work as well. So which credentials do i have to use for "binddn" and "binddn_passwd"? Where do I have to create them or get them?

My nginx ldap configuration:
[/FONT][/COLOR]```
ldap_server adds {
    url "ldap://192.168.50.131/dc=test,dc=dom?sAMAccountName?sub?";
    binddn "TEST\\USERNAME";
    binddn_passwd "password";
    connect_timeout 5s;
    bind_timeout 5s;
    request_timeout 5s;
    require valid_user;
    satisfy any;
     }
```[COLOR=#242729][FONT=Arial]
Thanks!
Btw: I've never set an LDAP Password, i just installed samba4. That's all!

[/FONT][/COLOR]

---

