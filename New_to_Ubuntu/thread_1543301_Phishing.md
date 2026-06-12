---
title: "Phishing"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by tim_ex on 2010-07-31
some one is sending Spam from my facebook account  and i want to know if there is any softwear that i can install to detect some phishing software.  I also dont know how to install softwear 

running 

8.10 intrepid
kernel linux 2.6.27.7-generic
GNOME 2.24.1

thanks

---

### Post by jrothwell97 on 2010-07-31
Change your Facebook password and [contact their security division]("http://www.facebook.com/help/?page=420").

It's that simple.

(Also, Ubuntu 8.10 is no longer supported. Consider upgrading.)

---

### Post by tim_ex on 2010-07-31
i did that but is there anyway  to scan my computer for any virus of stuff like that

---

### Post by Windows Nerd on 2010-07-31
Perhaps you should consider changing your Facebook password for one. If someone is sending stuff from your account, they have your password. 

Ubuntu generally won't get simple viruses like that, the security model just doesn't work that way. Even then, you can install clamav, a free antivirus:

From Menu>Accessories>Terminal, type (or simply copy and paste)

```
sudo apt-get install clamav clamtk
```

Scott

---

### Post by soldier1st on 2010-08-03
change your password and change your privacy settings to be more secure. also update to a supported ubuntu version.

---

### Post by corrytonapple on 2010-08-03
> **tim_ex said:**
> i did that but is there anyway  to scan my computer for any virus of stuff like that
Ubuntu is free of viruses. In fact, the Facebook phishing issue probably doesn't have anything to do with Ubuntu.

---

### Post by neonl on 2010-08-03
> **tim_ex said:**
> I also dont know how to install softwear
In general terms it's typing
```
sudo apt-get intall application-name
```
in a Terminal window.

If want a more graphical thing go to "System -> Administration -> Synaptic".

---

