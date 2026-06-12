---
title: "Password!!!!!!!"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by booklover on 2011-07-15
I'm not an EXPERT on computers and all that stuff, as I'm in 6th grade. I've forgotten my password and though I am not asked for my password every time I switch it on, I would like to change it.

Any ideas?
(I've googled this and they tell me to reboot and so on, but I don't understand all those stuff.I would be delighted if you can tell me what to do in plain English):p

---

### Post by haqking on 2011-07-15
> **booklover said:**
> I'm not an EXPERT on computers and all that stuff, as I'm in 6th grade. I've forgotten my password and though I am not asked for my password every time I switch it on, I would like to change it.

Any ideas?
(I've googled this and they tell me to reboot and so on, but I don't understand all those stuff.I would be delighted if you can tell me what to do in plain English):p

you can go to system>preferences>about me 

choose change password

or from terminal you can type

passwd

and follow prompts

Edit: Sorry my bad i just realised it says you have forgotten your password, sorry ;-)

---

### Post by Elfy on 2011-07-15
You do need to reboot. You then need to pick the second line down in your grub menu. If you don't see a menu - use Shift after the POST has finished. Should see it then.

Once you've booted into the recovery menu - pick root terminal. 

Then - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Elfy on 2011-07-15
> **haqking said:**
> ...New one on me - much easier though :)

---

### Post by haqking on 2011-07-15
> **forestpiskie said:**
> You do need to reboot. You then need to pick the second line down in your grub menu. If you don't see a menu - use Shift after the POST has finished. Should see it then.

Once you've booted into the recovery menu - pick root terminal. 

Then - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


yeah just realised he said he had forgotten it.

edited above post ^

---

### Post by booklover on 2011-07-15
> **forestpiskie said:**
> You do need to reboot. You then need to pick the second line down in your grub menu. If you don't see a menu - use Shift after the POST has finished. Should see it then.

Once you've booted into the recovery menu - pick root terminal. 

Then - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


sorry, but what IS reboot? and grub?

---

### Post by haqking on 2011-07-15
> **booklover said:**
> sorry, but what IS reboot? and grub?


so do you mean you cant login at all because you have forgotten password or it is auto login and when it asks you for password for admin tasks you cant remember it ?

if you cant login at all then you need to follow the link provided above by forestpiskie ot reset it.

if you are logged in then you can follow my instructions above to change password

---

### Post by booklover on 2011-07-15
> **haqking said:**
> so do you mean you cant login at all because you have forgotten password or it is auto login and when it asks you for password for admin tasks you cant remember it ?

if you cant login at all then you need to follow the link provided above by forestpiskie ot reset it.

if you are logged in then you can follow my instructions above to change password

"it is auto login and when it asks you for password for admin tasks you cant remember it ?"

that's the one
and it also asks me for my password when it is in sleep or suspend mode

---

### Post by haqking on 2011-07-15
> **booklover said:**
> "it is auto login and when it asks you for password for admin tasks you cant remember it ?"

that's the one
and it also asks me for my password when it is in sleep or suspend mode

ok in which case carry out instructions already provided.

from terminal

passwd

or system>preferences>about me

and choose change password

---

### Post by booklover on 2011-07-15
when i do that it asks me for my old password if i want to change it...

---

### Post by haqking on 2011-07-15
> **booklover said:**
> when i do that it asks me for my new password if i want to change it...


yeah so whats the problem ?

you said you wanted to give yourself a new password ?

so enter a new one and then remember it this time ?

---

### Post by haqking on 2011-07-15
> **booklover said:**
> when i do that it asks me for my new password if i want to change it...


however if it asks you for your current one then you will need to do a reset with the instructions provided before

---

### Post by Wim Sturkenboom on 2011-07-15
And don't be lazy; use the password for login as well. That way you probably have to type it every day and you will not forget :D

---

