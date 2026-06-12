---
title: "can't type password for sudo su"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by altvic on 2009-01-02
I am trying to install wireless dongle and picked up the following advice but I cannot enter my password in the terminal as the last instruction says (nor paste it).  Any advice?  Many thanks but PLEASE write in language I understand as a complete novice.
Thanks


[I]Open a Terminal Window

Open a terminal window (Applications > Accessories > Terminal). From here on you'll be issuing some commands that need super user privileges. To obtain these, use the following command:

sudo su

You'll probably be asked to enter your password.
[/I]

---

### Post by Arylon on 2009-01-02
When you enter your password for sudo, you won't see any typing on the screen, not even the stars (*) that some programs use to hide passwords. Just type your password and press Enter.

---

### Post by Tony Flury on 2009-01-02
You might be confused because the password prompt does not actually display the keys that you press, even though it is actually recognising and using the keys that you press. Have you actually tried to type your password - and then press Enter - Nothing will display (as I say) but it should work - and you will get an error message if you type it wrong.

---

### Post by altvic on 2009-01-02
many thanks Arylon and Tony

---

### Post by AndrewTheArt on 2009-01-02
You're not the only one that has been confused by this. I was helping a friend install Ubuntu a few weeks ago and he had the same problem. I don't see why displaying stars would be such a big deal. My guess, without looking it up to verify, is that it is a security feature against people figuring out your password length, or some malicious program exploiting some security hole in the star implementation so they can copy your password. Regardless, maybe this feature should be added and enabled by default in Ubuntu, but a way to turn it off (for whatever reason) should be offered to experienced users.

---

### Post by bumanie on 2009-01-02
It is a security feature as stated. AFAIK there has never been a visual output from terminal when one inputs their password, this feature goes back to unix security, I believe. Remember unix was always meant as a multi-user system and thus security was built in from the beginning.

---

### Post by handydan918 on 2009-01-02
> **AndrewTheArt said:**
> You're not the only one that has been confused by this. I was helping a friend install Ubuntu a few weeks ago and he had the same problem. I don't see why displaying stars would be such a big deal. My guess, without looking it up to verify, is that it is a security feature against people figuring out your password length, or some malicious program exploiting some security hole in the star implementation so they can copy your password. Regardless, maybe this feature should be added and enabled by default in Ubuntu, but a way to turn it off (for whatever reason) should be offered to experienced users.

Yeah! Same with ALL those pesky security features! Let the advance users secure their machines themselves...



...just like Windows.


:rolleyes:

---

### Post by AndrewTheArt on 2009-01-02
> **handydan918 said:**
> Yeah! Same with ALL those pesky security features! Let the advance users secure their machines themselves...



...just like Windows.


:rolleyes:
Maybe there should be a way to add stars, but a security message would pop up and state the risks? Lol.

---

### Post by handydan918 on 2009-01-02
> **AndrewTheArt said:**
> Maybe there should be a way to add stars, but a security message would pop up and state the risks? Lol.
That, my friend, is the real beauty of Open Source. If you want it, you can code it. No limitations but your own ability.

---

