---
title: "Forgot Authorisation password"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by bwallis5 on 2009-10-29
I have Ubuntu  9.04 installed on my daughters computer and upon trying to install some new software it asked for an authorisation for which she has lost and forgotten. how can we cancel or generate a new authorisation. The same happened with her computer password but help on the forum got us over that hurdle.
Thanks in anticipation.

---

### Post by KoffeeKup on 2009-10-29
I may be wrong but is the authorization password the same as the password you use to login to the computer? Try that.

If not, try changing the account via root.

---

### Post by sisco311 on 2009-10-29
> **KoffeeKup said:**
> I may be wrong but is the authorization password the same as the password you use to login to the computer? Try that.


+1


if she forgot her password:
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by bwallis5 on 2009-11-05
> **KoffeeKup said:**
> I may be wrong but is the authorization password the same as the password you use to login to the computer? Try that.

If not, try changing the account via root.


OK being a beginner how does one change or identify the authorisation in the root. I did change the password OK but it is not the authorisation . It comes up each time you try to change the access in the adim/authorisation menu or if you try to install new updates.

---

### Post by glarphash on 2009-11-06
I hear that Windows 8 will have password spellchecking.  That way if you just type something similar to your password it will be automatically corrected!  In fact, you can log in by typing any random crap in for the password and the paperclip will pop up to help out.  This is a *slight* security flaw but I hear they will fix this in Windows 9.  More seriously you should be able to fix it by doing the following:  
[LIST=1]
[*]Boot off of a live CD
[*]Mount your root partition for the install you are trying to fix
[*]Open a terminal
[*]type: sudo chroot /path/to/mountpoint
[*]type: sudo passwd nameofaccount
[*]reboot
[/LIST]

---

### Post by jrothwell97 on 2009-11-06
Follow the instructions posted in the link above, they'll serve you well. Booting a Live CD to do it will work, but IMHO it's using a sledgehammer to crack a nut.

---

