---
title: "egroupware ldap imap"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by syadnom on 2007-08-21
i'm despirately need help on running egroupware and an imap server(courier, cyrus, doesnt matter) and authenticating against LDAP.

i have searched high and low and come up short.  will run any flavor of ubuntu but prefer 7.04.

can anyone help me with a guide or some help getting stuff set up. 

i think i have LDAP working but get 'authentication' errors in the webmin administrative interface, though i can see all ldap users and groups just fine.  i used the smbldapinstaller script from [here]("http://www.vcsvikings.org/docuwiki/cgi-bin/moin.cgi/FrontPage") to get LDAP working but am not sure of how to set it up properly to authenticate the system, webmin, egroupware, or imap against it.

i would like to document every step with someone/anyone that would help and get the information out because the web is sorely lacking in egroupware/ldap setup guides...

---

### Post by syadnom on 2007-08-21
just trying to bump this up a little...

---

### Post by scottie4442 on 2007-08-24
I am in the same boat here, I am trying to get an egroupware server setup  at the college where I work.  I tried to do it with Fedora Directory Server and FC6 but it was way too much trouble, should have stuck with a Debian derivative in the first place.  I am trying to set this up in Ubuntu server and was wondering if Xampp was a good idea or just install each package. Also which IMAP server is the easiest to administer and setup.  Another question is our student data is stored in an Oracle database and will need to be imported, any ideas?

---

### Post by syadnom on 2007-08-24
i have no problem getting egoupware installed with ubuntu 7.04 server LAMP install

apt-get install egroupware

then download egroupware 1.4 from the site as well as the egw-pear stuff.

the i delete the contents of /usr/share/egoupware and replace them with the 1.4 stuff

cd /usr/share
tar -xvjpf /dl_loc/egroupware1.4.tar.bz2
tar -xvjpf /dl_loc/egw_pearstuff.tar.bz2

login to localhost/egroupware/setup and fly through it

problem is, LDAP is kicking my but.  i cant seem to get it setup right unless i use the smbldapinstaller script that is available online but then i can seem to connect to it with egroupware.  i install webmin
download webmin debian package

dpkg -i webmin.deb
get some dep errors, just
apt-get install
and it will correct them.

now [https://localhost:10000](https://localhost:10000) get me webmin

i can configure the ldap client to see the ldap server but i cannot add users because it says authentication failure!! im sure i have all the stuff right! guess im wrong.

---

### Post by syadnom on 2007-10-02
one more bump!

---

