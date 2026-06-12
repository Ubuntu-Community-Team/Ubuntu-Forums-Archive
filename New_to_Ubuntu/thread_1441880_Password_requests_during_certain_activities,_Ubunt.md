---
title: "Password requests during certain activities, Ubuntu 9.10"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by EARNEST on 2010-03-29
hello guys, i'd like to disable/enable/modify those password requests when i mount a partition or launch the synaptic package manager program etc. i tried to look into user groups, but didn't find a solution. any tips, please?
thanks.

---

### Post by theozzlives on 2010-03-29
Those are security measures, they are good.

---

### Post by EARNEST on 2010-03-29
> **theozzlives said:**
> Those are security measures, they are good.
even tho, i'd like to know how to disable those or modify :) also, i am the only user on my computre, so it's ok

---

### Post by Tony Flury on 2010-03-29
The password requests are part of the security design of Linux - where it deliberately makes you confirm the actions you are about to take, and provide it with admin rights to make those changes.

You can add applications into a list (can't remember where), which modifies when and how often you are prompted but i would be careful - the password prompt is a good protection for you.

Another expert will probably furnish you with details of the application list.

---

### Post by theozzlives on 2010-03-29
It's against forum rules to tell people how to bypass that stuff. Just because you're the only one at home, you have the company of billions when online, at least millions want to mess up your system "just because they can".

---

### Post by r_s on 2010-03-29
but you can surely change the timeout for which it does not prompt you for the password again

---

### Post by EARNEST on 2010-03-29
> **Tony Flury said:**
> The password requests are part of the security design of Linux - where it deliberately makes you confirm the actions you are about to take, and provide it with admin rights to make those changes.

You can add applications into a list (can't remember where), which modifies when and how often you are prompted but i would be careful - the password prompt is a good protection for you.

Another expert will probably furnish you with details of the application list.
thanks for your answer.

---

### Post by EARNEST on 2010-03-29
> **theozzlives said:**
> It's against forum rules to tell people how to bypass that stuff. Just because you're the only one at home, you have the company of billions when online, at least millions want to mess up your system "just because they can".
i don't really think it is against the rules. it is a feature of a system and u modify your own system. if there is a function that can be abused, it doesn't mean that everyone would do such things. thanks for your reply, but i disagree with its strength.

---

### Post by r_s on 2010-03-29
If I write down something over here  it's visible to millions of users outside and who knows what they can do with that information , security can be compromised with a single silly mistake.

---

### Post by theozzlives on 2010-03-29
> **r_s said:**
> If I write down something over here  it's visible to millions of users outside and who knows what they can do with that information , security can be compromised with a single silly mistake.

+1
I find Ubuntu Forums' posts with Google all the time.

---

### Post by sisco311 on 2010-03-29
Check out the following links:

[thread=510812]Ubuntu Security[/thread]
[uhelp]community/RootSudo[/uhelp]
[thread=1132821]HowTO: Sudoers Configuration[/thread]
[thread=716201]Forum policy on log-in-as-root tutorials[/thread]
[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)
[http://hal.freedesktop.org/docs/polkit/polkit.8.html](http://hal.freedesktop.org/docs/polkit/polkit.8.html)

---

### Post by lotharmat on 2010-03-29
> **theozzlives said:**
> 
I find Ubuntu Forums' posts with Google all the time.

That's the *only* way of finding them!!!

[searchterm] site:ubuntuforums.org

---

### Post by EARNEST on 2010-03-29
> **sisco311 said:**
> Check out the following links:

[thread=510812]Ubuntu Security[/thread]
[uhelp]community/RootSudo[/uhelp]
[thread=1132821]HowTO: Sudoers Configuration[/thread]
[thread=716201]Forum policy on log-in-as-root tutorials[/thread]
[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)
[http://hal.freedesktop.org/docs/polkit/polkit.8.html](http://hal.freedesktop.org/docs/polkit/polkit.8.html)
thanks a lot.
that info is available to anyone, so i don't understand why certain users made a hassle about posting such things?

---

