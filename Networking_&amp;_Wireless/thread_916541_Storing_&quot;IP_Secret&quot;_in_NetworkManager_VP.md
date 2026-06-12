---
title: "Storing &quot;IP Secret&quot; in NetworkManager VPNC plugin"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by rajeev1982 on 2008-09-11
Hi,

I use NetworkManager vpnc plugin to connect to my office vpn network. When I connect to vpn using network manager, I have to type my password followed by RSA pin in one box and "IP Secret" in another box. This sucks, I have to enter 3 different passwords to connect to VPN. In Mac and Windows I can store the IP Secret and can enter mypasword+RSA when I connect. This reduces the effort of connecting (You know what? Its really difficult to remember the IP Secret, I remember my password and RSA pin can be simply taken from the RSA Token.

Can anybody tell me a way to store only the IP Secret but not my user password for vpn. If I store the password, vpnc stores my password+rsa pin and IP Secret all. RSA ping changes every 60 seconds so I can't store it, I have to manually enter it. But IP Secret can be stored, it doesn't change.

Regards,
Rajeev

---

### Post by pir on 2008-09-11
How did you manage to get openssl installed? PM please :)

---

### Post by kwatson512 on 2008-12-21
I need to do exactly what Rajeev1982 is asking for.  In Hardy, vpnc allowed separate storage of the IP secret and password, so I was able to store the IP secret (group password), and leave the user password field blank.  That is no longer true in Intrepid.  Can the network-manager-vpnc be customized to allow separate storage of a static IP secret?  This would greatly simplify authenticating into my corporate network.

---

### Post by kwatson512 on 2009-01-10
BTW, Fedora 10 implements nm0.7 with the ability to independently store group and user passwords.  This is very nice for corporate users.  Unfortunately, the implementation in Ubuntu doesn't have that flexibility.

---

### Post by jammindice on 2009-02-03
according to this link:
[https://launchpad.net/bugs/91964]("https://launchpad.net/bugs/91964")

this is a regression problem.  it was fixed in hardy but not upstream, it is january now so the fix will probably come out in jaunty, either downgrade to hardy or have to suffer till jaunty, maybe this will be patched before but i would doubt it

---

