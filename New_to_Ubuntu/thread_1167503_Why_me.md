---
title: "Why me????????????????"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Kayrosh on 2009-05-22
I am on my ubuntu account and i try to use add/remove apps but it said it failed. I go to users and groups to makeit to  a new account but it says i cant go there. I think my account is not admin so i cant use it or use add/remove but since it is the only account i have no idea how to change to administrative.
THANKS FOR REPLYING

---

### Post by Locutus_of_Borg on 2009-05-22
Applications > Accessories > Terminal
Enter:
sudo -i

Enter your user's password

Enter:
synaptics

---

### Post by SunnyRabbiera on 2009-05-22
Strange, maybe there is an issue with the package manager.

> **Locutus_of_Borg said:**
> Applications > Accessories > Terminal
Enter:
sudo -i

Enter your user's password

Enter:
synaptics

thats synaptic, not synaptics.
synaptics is touch pad support, synaptic is the package manager.

---

### Post by Alias1407 on 2009-05-22
> **Locutus_of_Borg said:**
> Applications > Accessories > Terminal
Enter:
sudo -i

Enter your user's password

Enter:
synaptics

Also if this doesn't work try...

```
sudo passwd
```

---

### Post by SunnyRabbiera on 2009-05-22
aghain its synaptic, not synaptics... huge difference between the two.

---

### Post by Kayrosh on 2009-05-22
it says i am not in the sudoers file so now what do i do???

---

### Post by theozzlives on 2009-05-22
if you can't use sudo boot recovery mode and select root prompt, then try:
```
passwd <username>
```

---

### Post by egalvan on 2009-05-23
> **Kayrosh said:**
> I am on my ubuntu account and i try to use add/remove apps but **it said it failed.**
 I go to users and groups to makeit to  a new account but it says i cant go there. I think **my account is not admin** so i cant use it or use add/remove but since it is the only account i have no idea how to change to administrative.
THANKS FOR REPLYING

So what is the error code? How did the add/remove fail?

When you try to add or remove with the "add/remove" app,
all you need is your log-in password.
You don't need to be "root", and you don't need to be "admin".

Same with Syaptic... all you need is your log-in password...


I just added a game to my other machine, using "add/remove",
giving only my log-on password...
no "root" needed.

---

### Post by theozzlives on 2009-05-23
> **egalvan said:**
> So what is the error code? How did the add/remove fail?

When you try to add or remove with the "add/remove" app,
all you need is your log-in password.
You don't need to be "root", and you don't need to be "admin".

Same with Syaptic... all you need is your log-in password...


I just added a game to my other machine, using "add/remove",
giving only my log-on password...
no "root" needed.

If you're admin and you provide your password, you become root for a second. You need permissions to install software.

---

### Post by Locutus_of_Borg on 2009-05-23
> **SunnyRabbiera said:**
> Strange, maybe there is an issue with the package manager.



thats synaptic, not synaptics.
synaptics is touch pad support, synaptic is the package manager.
oh yeah

same thing... \\:D/

---

### Post by pspsampsp on 2009-05-23
first of all try running the command "su" and entering your root password , after that run "adduser existing_username_to_add_to_admin_group admin" and hopefully that should fix it.

---

