---
title: "[SOLVED] can you make a program prompt for password?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-18
I was wondering If there is a way to make a program prompt for a password before launching without being root.

More specifically Firefox!

I would like it to ask for root password but still run without root privs.

Is this possible?

---

### Post by bruce89 on 2008-12-18
I don't understand why you'd want to do this. If you don't want someone else using the computer, lock your session.

---

### Post by nakama85 on 2008-12-18
> **bruce89 said:**
> I don't understand why you'd want to do this. If you don't want someone else using the computer, lock your session.

It is for a child. I want them to be able to play the games like xmoto but not be able to get to the internet.

---

### Post by pHreaksYcle on 2008-12-18
Then make them a separate user without network manager installed. Or use that firestarter program or something.

---

### Post by nakama85 on 2008-12-18
> **pHreaksYcle said:**
> Then make them a separate user without network manager installed. Or use that firestarter program or something.

Thanks for the tips. 
However I am really hoping to still find a way just to password protect it. I have a unique situation that I would prefer not to explain on the forums (personal).

Would there be a way to do this?

---

### Post by pHreaksYcle on 2008-12-18
remove all the firefox icons. is the kid familiar with the terminal?

---

### Post by RequinB4 on 2008-12-18
try seahorse

```

sudo apt-get install seahorse

```

---

### Post by nakama85 on 2008-12-18
> **pHreaksYcle said:**
> remove all the firefox icons. is the kid familiar with the terminal?

no he is not. However removing icons would be bad because I am setting up this ubuntu box for my father in law and he is not ready for terminal yet

---

### Post by anim on 2008-12-18
[https://addons.mozilla.org/en-US/firefox/addon/9808](https://addons.mozilla.org/en-US/firefox/addon/9808)

Make sure to set the extensions.startupmaster.block option in about:config and set a master password. If your kid knows how to remove extensions with the file manager and firefox safe mode then your probably not going to find an easy solution.

---

### Post by nakama85 on 2008-12-21
> **anim said:**
> [https://addons.mozilla.org/en-US/firefox/addon/9808](https://addons.mozilla.org/en-US/firefox/addon/9808)

Make sure to set the extensions.startupmaster.block option in about:config and set a master password. If your kid knows how to remove extensions with the file manager and firefox safe mode then your probably not going to find an easy solution.

thanks This worked Perfect For Firefox.

And no he has no computer knowledge at all so I am not worried about that.

I do hesitate to mark this thread as solved though.
I will however if someone can tell me password protecting individual programs without root privs is not possible.

Thanks again

---

### Post by baruch60610 on 2008-12-21
I'm thinking this may not work all that well... if this child is older than about 8 or so, he's likely to know more about computers than you may realize.  A solution relying on his ignorance may not be very effective.

I understand your situation is unique, but really the best way of doing this (IMNSHO) is to use a separate user just for the child, and don't give him any Internet-capable programs.

The problem I see is that you may wind up giving the child Internet access, while having the comforting illusion that he is protected from it.  But of course, if your situation doesn't permit a separate user name, then probably what others have said is the best you can hope for.

---

### Post by namdung on 2008-12-21
Go to System ---> Preferences ---> Main Menu

Double click to open the launcher properties of the program. In the **command** field add **gksu**.

---

### Post by ugm6hr on 2008-12-21
> **namdung said:**
> Go to System ---> Preferences ---> Main Menu

Double click to open the launcher properties of the program. In the **command** field add **gksu**.

That would add root privileges to Firefox.

---

### Post by stalkingwolf on 2008-12-21
You might try In firefox going to Edit > Preferences > Security > Use a Master Password.

That might be your solution.

---

### Post by nakama85 on 2008-12-21
Okay, Thanks for your help and input everyone. I am going to go ahead and assume that this is not possible(as far as I know) and mark this thread as solved. 

If I stand to be corrected than please do so.

Thanks again

Nakama

---

