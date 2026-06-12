---
title: "OpenVPN Server - Need help with the pam authentication plugin configuration"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by leroy5 on 2014-08-11
Hi,

I just install sucessfully a OpenVPN server on Ubuntu Server 14.04 LTS

Everything is working perfectly except for the username/password authentication with the pam plugin.

I currently only authenticate with the certificates and keys on the clients (ca.crt, ta.key, client.crt and client.key) but I would like to add the server's username and password into the authentication process as well to get a real two factor authentication process.

This is 2 things that I already tried  and did not work:


**1-**add this line to my /etc/openvpn/server.conf file:

plugin /usr/share/openvpn/plugin/lib/openvpn-auth-pam.so login

(as suggested on the official openvpn doc)



**2-**follow these steps that I found on a blog:

For Ubuntu 14.04

cp /usr/lib/openvpn/openvpn-plugin-auth-pam.so /etc/openvpn/

Now edit the /etc/openvpn/server.conf file and add the following:

username-as-common-name 
tmp-dir "/etc/openvpn/tmp/"                      
plugin /etc/openvpn/openvpn-plugin-auth-pam.so /etc/pam.d/login 

Create the temp directory mentioned above and allow all writes to it:

mkdir /etc/openvpn/tmp
chmod 777 /etc/openvpn/tmp

Restart OpenVPN

/etc/init.d/openvpn restart


I only want the pam plugin to authenticate with the local server users in etc/passwd or /etc/shadow

What is the official way to do that safely?

Thank you! :)

---

### Post by leroy5 on 2014-08-12
nevermind I found the solution. [IMG]https://forums.openvpn.net/images/smilies/icon_e_smile.gif[/IMG]

This line finally did the trick for me:

plugin /etc/openvpn/openvpn-plugin-auth-pam.so login

---

