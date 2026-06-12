---
title: "How to avoid having to type wallet password in order for ubuntu to connect by wifi"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by duartemolha on 2007-07-02
Hello

I have a wireless connection in my house using WPA. 

The passphrase to connect to this wireless connection in stored by ubuntu on the wallet system and every time I login to ubuntu it asks me for the wallet password to connect the my wireless network.

I am just wondering if there is anything I can do to make ubuntu not require me to put the password to access the wallet. I already have to log in using a password and it just seems unnecessary to have to type the password twice.


Best regards, 


        Duarte Molha

---

### Post by Mopana on 2007-07-02
Are you talking about the keyring?

[http://ubuntuforums.org/showthread.php?t=349984](http://ubuntuforums.org/showthread.php?t=349984)

This guide might work

---

### Post by vanadium on 2007-07-02
I have a more simple solution, taken from [http://www.digiplace.nl/pivot/entry.php?id=746](http://www.digiplace.nl/pivot/entry.php?id=746) and probably to be found elsewhere

```

sudo apt-get install libpam-keyring
gksudo gedit /etc/pam.d/gdm

```

The last command will open gedit. Add this line to the end of the file
```

@include common-pamkeyring

```

Your keyring password must be the same as your login. If it is not, you need to change your keyring password, and unfortunately, that is to be done the rough way:

```

sudo killall gnome-keyring-daemon

```
to kill the keyring daemon (probably there is also a "softer" way to just stop/start it)
then delete ~/.gnome2/keyrings

```

rm ~/.gnome2/keyrings

```

If you have other "keys" in your keyring, they will be gone as well with that procedure.

---

### Post by drdanield@gmail.com on 2008-01-04
:guitar:  Nice job.  You should also post a link to this method on the other forum subject.  Thanks :)

---

