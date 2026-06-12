---
title: "gnome-keyring-manager broken by pam_keyring ?"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by csoler on 2007-07-11
I recently installed pam_keyring to get rid of the annoying keyring password prompt at login time. However, since then, my gnome-keyring-manager does not show password anymore. Besides, when I click on "default keyring" it complains that I don't have the right to access it. 

The keyring manager looks completely blank (see screenshot below), although it's oviously working fine. How could I get my passwords to show again ?

[IMG]http://artis.imag.fr/~Cyril.Soler/keyring.png[/IMG]

Thanks
Cyril

---

### Post by LoSt180 on 2007-07-11
See if this works; (taken from [here.]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"))

> 
Automatic Keyring

To bypass having to enter the keyring password at every login when your keyring password is the same as your login password, follow the following instructions:

```
naaman@freddo:~$ sudo apt-get install libpam-keyring
naaman@freddo:~$ echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm
```

To change keyring password, install libpam-keyring as above then run:

```
naaman@freddo:~$ /usr/lib/libpam-keyring/pam-keyring-tool -c
```



I can still access my keyring via GUI, so I'm not sure what's making yours inaccessible.. Hopefully the command above with help.

---

### Post by eode on 2007-12-20
I have the same problem.

You can apparently delete the keyring file, and it will create a new one.  It is in

/home/(user)/.gnome2/keyrings/default.keyring

..this deletes the keyring and all of its data.  A new one will be generated automatically.

---

