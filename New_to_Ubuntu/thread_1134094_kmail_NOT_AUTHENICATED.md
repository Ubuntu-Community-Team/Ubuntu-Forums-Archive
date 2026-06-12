---
title: "kmail NOT AUTHENICATED"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by BertP on 2009-04-23
I am an Ubuntu 7.10 user (using gnome) but I want to install  Kmail because that seems to be the only email package that can import Microsoft Outlook Express databases. 

  When I go to install Kmail, I get a warning about it being not authenticated

Why is this happening?  Has the support for 7.10 ran out and every application I install from now on going to be unauthenticated?


See for yourself,  I have attached a screen shot

---

### Post by unutbu on 2009-04-23
Open a terminal (Applications>Accessories>Terminal) and type
```

sudo apt-get update
```

Repositories use GPG public/private keys to sign their packages. 
The keys change from time to time, and you have to run the above command to get the new keys. Having the current public keys allows your machine to verify that the packages it downloads are authentic.

---

### Post by BertP on 2009-04-23
> **unutbu said:**
> Open a terminal (Applications>Accessories>Terminal) and type
```

sudo apt-get update
```

Repositories use GPG public/private keys to sign their packages. 
The keys change from time to time, and you have to run the above command to get the new keys. Having the current public keys allows your machine to verify that the packages it downloads are authentic.

 
Thanks for the help but if that were true, it would seem logical that the new keys that I need  would be distributed through the update manager, right?

I got a lot of 404 errors during the 'apt-get update' and Kmail is still marked as unauthenticated.  Are the servers down today?

---

### Post by oldos2er on 2009-04-23
"Has the support for 7.10 ran out"

 Yes.

---

### Post by BertP on 2009-04-23
> **oldos2er said:**
> "Has the support for 7.10 ran out"

 Yes.

and is that the reason for my authentication errors?  are they going to take the repositories anytime soon (or have they already? :icon_frown:))

My computer is relatively powerful yet when I repeatedly  tried to upgrade to version 8 the install died every time.  I don't feel like fighting like that with 9 if it is  just not going to work eventually.....  I guess it might be time to go back to Windows ](*,)

---

### Post by oldos2er on 2009-04-23
"and is that the reason for my authentication errors?"

 Yes. See [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

