---
title: "&quot;evolution-alarm-notify&quot;, go away!"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by 311005901 on 2009-08-01
I want Evolution to boot up and to have the alarm notifier do its thing, but I HATE having to type in my password when I log in.

Is there a way to have this process added to my keyring? I just don't want to see it again, ever.

[IMG]http://img27.imageshack.us/img27/5078/97239042.png[/IMG]

---

### Post by Dark Aspect on 2009-08-01
I am not sure but it *could* be under System --> Preferences --> Encryption and Keyrings

---

### Post by 311005901 on 2009-08-01
@Dark Aspect: There's really nothing there. I don't see anything contextually relating to programs that can access the keyring...

---

### Post by Dark Aspect on 2009-08-01
My bad, try Applications --> Accessories --> Password and Encryption Keys. Under that click on the password tab and add evolution-alarm-notify to the program list. I believe that will work as it has worked for me in the past with mm-applet. 

A quick Google search reveled [this]("http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14"), however I remember having a similar dialog box with mm-applet and that application is already in Password and Encryption keys. Hope that helps a little more.

---

### Post by 311005901 on 2009-08-04
Hmmm... Still nothing.
Any suggestions?

---

### Post by 311005901 on 2009-08-15
Sorry...
Bump?

---

### Post by wojox on 2009-08-15
Applications --> Accessories --> Password and Encryption Keys
You have to create the key first.
My Personal Keys > File > New > Password Keyring.

---

