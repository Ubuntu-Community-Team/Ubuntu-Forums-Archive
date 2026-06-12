---
title: "Keyring Manager &amp; Auto Login in Gutsy"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by blakegrover on 2007-10-19
We have a lot of machines that use the auto login feature in gdm and then they are used to show statistics on monitors in our company.  They have wireless cards and connect wireless to download new information to display on the screens.  In gutsy they have it so the keyring never asks you for a password is your keyring and login passwords are the same.  And it does work that way on our boxes.  

But if you do not manually type in your username and password (by using the auto login feature in gdm) it comes up and asks for the keyring password.  We do not normally have keyboards or mouses hooked up to the machines.  We would like it so it works through the auto login.  I am not sure if anyone else has found this issue and might have suggestions but I am open to try anything.

Blake

---

### Post by blakegrover on 2007-10-19
I found out more information.  The autologin feature in gnome creates a seperate file in /etc/pam.d  the main one for gdm is /etc/pam.d/gdm and the autologin is /etc/pam.d/gdm-autologin  I noticed there are two differences in the files.  here they are below:

/etc/pam.d/gdm
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so  auto_start
@include common-password

```

/etc/pam.d/gdm-autologin
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
@include common-account
session required        pam_limits.so
@include common-session
@include common-password

```

I added the missing lines to the gdm-autologin script so it looked like this:
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so  auto_start
@include common-password

```

When I rebooted my computer it started to login and then a window that said Autologin Password came up and asked me for my password, and then after loginning in network-manager picked up the keyring and had the connection setup.  But I don't want to have user input on the login.  I have also tried wicd but I can't get it to automatically connect to the network, I can get it to startup but it wants me to pick a network to connect to.  Let me know if you think you can help

---

### Post by pikespeakhiker on 2007-10-21
Yep, this is a pain.  I had this working fine in feisty, but not in gutsy.

---

### Post by overmark on 2007-10-22
I have tried everything and it still asks for a password in Gutsy. Network manager asks for the WPA password twice now when logging in :(, so the keyring is useless anyway. Hopefully some one will have a solution down the track :)

---

### Post by Schroeder on 2007-10-22
This is really a pain. In feisty there was a way to get rid of this. Hopefully there is a solution in gutsy,too. Anybody know how?

---

### Post by Nephron on 2007-10-23
I have a laptop where I am the only one who uses Linux, so I have an autologin. But it is a pain when I am asked to unlock the keyring twice to connect to my wireless network at home.

I can see why they protect the passphrase for the network, but surely they can provide a function for it to unlock automatically for those that need not be so concerned about security.

I thought they provided this when I upgraded to Gutsy with a checkbox saying "Unlock automatically at login," but it never seems to do anything.

---

### Post by swaaye on 2007-10-23
Most amazing is that the Ubuntu folks don't fix it! People have been asking for a way to get around this for a **long** time. Crazy.

---

### Post by svivian on 2007-10-28
See [http://ubuntuforums.org/showpost.php?p=3625792&postcount=100](http://ubuntuforums.org/showpost.php?p=3625792&postcount=100)

---

### Post by swaaye on 2007-10-30
> **svivian said:**
> See [http://ubuntuforums.org/showpost.php?p=3625792&postcount=100](http://ubuntuforums.org/showpost.php?p=3625792&postcount=100)

Except...........
> 
Everything works for me like it should until I reboot however. After which firefox seems unable to connect to the internet until I go back into network manager's manual config and re-enter the password for my wifi network. The problem is that i have to do this every time I reboot. (Shouldn't Network manager remember my network password? Especially when using manual config?) Hopefully this is just some issue with my personal network though.


---

### Post by svivian on 2007-11-01
Oh, I haven't had that, it all works fine for me. BTW I had to turn off "roaming connection" on both the wireless connection and wired connection for some reason.

---

### Post by blakegrover on 2007-11-01
I've tried setting the connection manually in the gnome network settings but for some reason I can't pick dhcp, I have to pick static ip address for it to connect.  If I pick dhcp it acts like it never gets an ip address.  Which from what I've seen in the forums is another bug or problem.

---

### Post by aperrado on 2007-11-03
hello

i dont speak english

install wicd to fix your problem



[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by blakegrover on 2007-11-03
Wicd works really good, but I could not get it to auto start when the computer boots up, I would but the program it says in the startup programs but it would not connect to the wireless network automatically, even if I checked the box connect automatically.  I was impressed with it but not with it starting up.

Blake

---

### Post by aperrado on 2007-11-03
did you select "use encryption" ?

---

### Post by dante00001 on 2007-11-03
keyring manager won't see my wireless key. It finds the password for a ftp server i login to but not my wireless. I'm very disappointed with the keyring manager in Gutsy.

---

### Post by blakegrover on 2007-11-03
Yes then network is using wpa

---

### Post by aperrado on 2007-11-03
did you disable network manager?
(System > Preferences > Sessions)

i didn't do

and its work  fine to me

---

### Post by blakegrover on 2007-11-03
I'll try that tomorrow and let you know if it works, thanks for your help

---

### Post by blakegrover on 2007-11-08
I actually had to download the latest testing version off of wicd.sourceforge.net and install it.  It seems like there is a bug in 1.3.1 and in 1.3.4 it works great on my desktop.

Thanks
Blake

---

### Post by aperrado on 2007-11-10
great

---

### Post by ctrlf5 on 2007-12-10
> **aperrado said:**
> install wicd to fix your problem

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

This works for me. I have tried the PAM thing without success. FYI: Running Xubuntu Gutsy.

---

