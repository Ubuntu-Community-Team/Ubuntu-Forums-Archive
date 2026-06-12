---
title: "new karmic install"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by DarinB on 2010-03-07
on a new karmic install i have it set to log in automatically for her. 
when she logs out and tries to go back in it does not take the password. 
and now she can not open empathy with out keyring asking for her password. 
I tried to change password in key ring and leave it blank but it does not seem to change anything. she is set to log in auto what do i do?????
if i set her to log in on password,,,,i don't know maybe she won't be able to get back in at all!!!!! at least now she can restart and log in automatically, i did go to users and groups and have her authenticate and reenter her same password as change password it came up old password is same as new i had her click ok but she  is still required to enter password for empathy keyring and to get her gmail account email in thunderbird. 
not sure what to do at this point. 
i did read that it happens when you set to auto log in keyring does not unlock. but i am worried since she can not log in with password after log out. it hangs there. my karmic at home has no problems and i am at auto log in eveything works fine. don't know what to do. 
Problem one. 
if i have to remove auto log in will she be able to get back in
problem two will that resolve the keyring issue? 
problem three what if she can't log back in??? am i messed up?

---

### Post by steindor2 on 2010-03-07
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by DarinB on 2010-03-07
this only tells me how to log on when password is lost. but does not say how to get to the shell or answer my other questions as to why she can not enter with her password.

---

### Post by steindor2 on 2010-03-07
> **DarinB said:**
> this only tells me how to log on when password is lost. but does not say how to get to the shell or answer my other questions as to why she can not enter with her password.

You are misunderstanding something, those instructions are a complete guide to resetting the root password.

---

### Post by steindor2 on 2010-03-07
nevermind what i posted earlyer i found a better way

Durning startup press esc, select recovery mode.
wait while ubuntu boots
when you reach the blue screen select root, this will give you acess to the root shell
type ```
passwd
```
enter your new password twice
reboot and enjoy;)

---

### Post by DarinB on 2010-03-08
cool thank you. i really need to know this 

but it does not explain why she can't log in after log out. or how to fix that.

---

### Post by DarinB on 2010-03-09
> There are couple of things about the keyring manager you should know:

1. If you use login password the keyring will be unlocked automatically at login time as long as keyring password is the same as your login password. So you should never need to type two passwords when you log in.

2. If you enable automatic login, the keyring isn't automatically unlocked so you need to either type the keyring password, or set the keyring password to empty.

3. If you change your login password, you'll want to change your keyring password as well to keep the automatic keyring unlocking working.

To change your keyring password, or remove it, go to Applications/Accessories/Passwords and Encryption Keys. On the Passwords-tab right-click the "Passwords:login"-entry and select "Change Password".

(And the keyring manager is used to store passwords because it's simpler, easier and more secure to have one program to handle this tasks for all your programs. It also allows much better desktop integration (like the signing and encrypting options you have in your right-click menu, and the automatic keyring unlocking)

I am trying to remove password on the keyring in a karmic install.... so she can log on automatically and not be asked for the password on Thunderbird (a gmail account) or empathy. does any one know the exact procedure for this i seem to be missing something and am not doing something correctly and also she can not log in after log out. The password does not seem to work but her admin password does work to unlock the keyring and use synaptic etc....
She is set to auto log in as stated in the quoted piece above.

---

