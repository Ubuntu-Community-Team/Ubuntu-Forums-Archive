---
title: "full disk encryption and home directory encryption"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by nutpants on 2011-05-29
i have recently wanted to dedicate a drive to full disk encryption on my main computer.. i did a install from the alternate x64 11.04 cd and picked full disk encryption and encrypt home directory.. 
sad to say that my main computer would not run Ubuntu 11.04 ( i think it has to do with my ati video card.)

so i pulled out a old p4 3ghz and did full disk encryption on it
but i forgot to encrypt the home directory at install..

now there is no option to encrypt the home directory if i make a new user.

am i missing something?
is it not possible to encrypt the home directory if the disk is fully encrypted? 

is that the reason that the install did not work on my main computer?
because i did pick home directory encryption when installing with the alternate install cd.

is it necessary to encrypt the home directory on top of full disk?
( or is it just a bonus)

thank you for any help..

nuts

---

### Post by wildmanne39 on 2011-05-29
> **nutpants said:**
> i have recently wanted to dedicate a drive to full disk encryption on my main computer.. i did a install from the alternate x64 11.04 cd and picked full disk encryption and encrypt home directory.. 
sad to say that my main computer would not run Ubuntu 11.04 ( i think it has to do with my ati video card.)

so i pulled out a old p4 3ghz and did full disk encryption on it
but i forgot to encrypt the home directory at install..

now there is no option to encrypt the home directory if i make a new user.

am i missing something?
is it not possible to encrypt the home directory if the disk is fully encrypted? 

is that the reason that the install did not work on my main computer?
because i did pick home directory encryption when installing with the alternate install cd.

is it necessary to encrypt the home directory on top of full disk?
( or is it just a bonus)

thank you for any help..

nutsHi, I have this link on encryption.[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

---

### Post by nutpants on 2011-05-29
If the administrator wants to add a new user with an encrypted home directory after the initial installation, use: sudo adduser --encrypt-home. This requires the ecryptfs-utils package. 


you would think that they would make it easier to find what package was required..

thanks for the pointer.

nuts

---

### Post by Thewhistlingwind on 2011-05-29
If your opponent manages to beat the full disk encryption, nothing will save you.

You can go ahead and encrypt your home folder anyway if you feel like it.

Make sure to add your new user to the sudoers file.

---

### Post by wildmanne39 on 2011-05-30
> **nutpants said:**
> If the administrator wants to add a new user with an encrypted home directory after the initial installation, use: sudo adduser --encrypt-home. This requires the ecryptfs-utils package. 


you would think that they would make it easier to find what package was required..

thanks for the pointer.

nuts
Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:)

---

