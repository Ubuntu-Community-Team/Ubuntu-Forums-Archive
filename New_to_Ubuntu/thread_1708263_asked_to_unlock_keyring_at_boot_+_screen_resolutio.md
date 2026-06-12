---
title: "asked to unlock keyring at boot + screen resolution settings not saved (Ubuntu 10.10)"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by flee0308 on 2011-03-16
Hi, I just installed Ubuntu on my notebook and I have 2 problems. Can someone help me?

1) Whenever I start up Ubuntu, I get this windows named "Unlock Keyring" saying:

Enter password for keyring 'Default' to unlock

An application wants access to keyring 'Default', but it is locked.

Under details, I have 3 options. Either I:

Lock this keyring when I log out (this option is marked)

OR

Lock this keyring after x minutes

OR

Lock this keyring if idle for x minutes

I believe this is due to the wifi, as it connects only after I unlocked the keyring.

2) Screen Resolution can't be saved. 

Using NVIDIA X server settings, I change my screen resolution on my notebook from 800x600 to Auto. But for some reason, it keep reverting back to 800x600 whenever I restart the notebook.

I tried to do the option "Save to X Configuration File". First I pressed save, ticking "merge with existing file", key in my password, but it goes back to 800x600 after I reboot.

Can someone help me solve these two problems?

---

### Post by vivek.pandey on 2011-03-16
for second problem try this system->prerences->monitors and change the resolution from there
for first problem whats your question i mean you wanna stop that keyring from popping or something else

---

### Post by flee0308 on 2011-03-16
> **neo_aryan said:**
> for second problem try this system->prerences->monitors and change the resolution from there
for first problem whats your question i mean you wanna stop that keyring from popping or something else

I want to it to stop asking for the keyring at boot. Maybe auto authentiate or something.

EDIT: Screen resolution problem fixed, after I used Ubuntu's own screen resolution manager.

---

### Post by flee0308 on 2011-03-16
bump.

---

### Post by woodmaster on 2011-03-17
[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

---

### Post by flee0308 on 2011-03-17
> **woodmaster said:**
> [http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

Okay I deleted the file. When I restarted I was prompted to create a new password. Every subsequent restart since then had the same problem.

---

### Post by woodmaster on 2011-03-17
after you delete it & reboot, when it promts you to create a new password : **don't**  It will give you an error about insecure passwod storage, but it's ok.

---

### Post by flee0308 on 2011-03-17
> **woodmaster said:**
> after you delete it & reboot, when it promts you to create a new password : **don't**  It will give you an error about insecure passwod storage, but it's ok.

Umm, no. That still doesn't work. Whenever I restart I need to key in the password to enter the wifi AND press cancel when I am prompted for password.

---

### Post by woodmaster on 2011-03-17
I don't have a wireless PC here, but I think I remember entering the wifi pass and just clicking ok on the keyring with both fields blank. Then it saved the password.

---

### Post by matt_symes on 2011-03-17
Hi

There are a couple of ways to fix it.

You can right click on your network connection and select edit connections, select your wireless connection and select edit and select make available to all users. That assumes it is your wireless pass key that is creating the problem

The other way to fix this is to make sure under "passwords and encryption keys" all your keys appear under login and not default on the passwords page or ensure the password for default is the same as your login. (i forget which exactly) 

Both these 2 fixes have worked more me at different times.

Kind regards

---

### Post by flee0308 on 2011-03-18
thanks, this helped.

---

