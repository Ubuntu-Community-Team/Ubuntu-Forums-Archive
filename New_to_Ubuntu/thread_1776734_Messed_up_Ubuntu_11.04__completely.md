---
title: "Messed up Ubuntu 11.04  completely"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Super-Dan on 2011-06-06
Hi Everyone I am a very new user to Ubuntu ditching Windows 7 for a bit of a cooler system!

Well after upgrading to 11.04 I have decided that I didnt like the Bar to the left so I went to Unity Utility and disabled it, I enabled desktop cube whilst I was there!

Well now, I have lost the top panel, the minimise exit panel on all windows. I cant open ALT + F2

If I do CTRL ALT F1 I put my User name in but when I come to type my password in I type but nothing comes up!

Please please help me, in beginners speak if possible!!

:(

---

### Post by lavinog on 2011-06-06
> **Super-Dan said:**
> Hi Everyone I am a very new user to Ubuntu ditching Windows 7 for a bit of a cooler system!

Well after upgrading to 11.04 I have decided that I didnt like the Bar to the left so I went to Unity Utility and disabled it, I enabled desktop cube whilst I was there!

Well now, I have lost the top panel, the minimise exit panel on all windows. I cant open ALT + F2
Can you do CTRL-ALT-T

> 
If I do CTRL ALT F1 I put my User name in but when I come to type my password in I type but nothing comes up!

This is normal behavior for the password prompt...it is for security purpose that it does not show anything when you type.

> 
Please please help me, in beginners speak if possible!!

:(
I believe what you want is to use ubuntu classic.
This can be configured with gdmsetup. If you can use CTRL-ALT-T to open a terminal you can just type gdmsetup.

If that doesn't work, there is a config file you can edit.  Give me a sec and I can get the instructions.

---

### Post by Super-Dan on 2011-06-06
Nope I can not even do CTRL+T

I was happy with 10 version! 

I will not give up though, I feel a steep learning curve coming on!!

---

### Post by Jamie_Dolan on 2011-06-06
I had to reboot and go into classic view to get to my terminal then I did 

unity --reset

to reset the settings in Compiz for unity then I did

unity --reset-icons

to reset the launcher icons towards the left
I hope you found this helpful in anyway

---

### Post by charliewhizbeez on 2011-06-06
> **Jamie_Dolan said:**
> I had to reboot and go into classic view to get to my terminal then I did 

unity --reset

to reset the settings in Compiz for unity then I did

unity --reset-icons

to reset the launcher icons towards the left
I hope you found this helpful in anyway


That's exactly what I did when unity wasn't working for me.  Trust me, it works.

---

### Post by Super-Dan on 2011-06-06
Ok

So restart, then how do I get into Classic View?

Sorry and thankyou.

---

### Post by lavinog on 2011-06-06
> **Super-Dan said:**
> Nope I can not even do CTRL+T

I was happy with 10 version! 

I will not give up though, I feel a steep learning curve coming on!!

Did you try CTRL-ALT-T?

> 
So restart, then how do I get into Classic View?


If you have your system to not automatically log you in, there is a dropdown on the login screen.

However, switching to classic ubuntu can be done from the command line with the following steps:
Do CTRL-ALT-F1 to go to the command line.
Login
use the following command to edit the config file:
```

sudo nano /etc/gdm/custom.conf

```

You should see something like this:
```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=username
TimedLoginEnable=false
TimedLogin=greg
TimedLoginDelay=10
DefaultSession=gnome

```

Go to the last line and change it to read:
```

DefaultSession=gnome-classic

```

Press CTRL-X then it should ask if you want to save, press Y then Enter
Then reboot, and it should log you in in classic mode.

---

### Post by Super-Dan on 2011-06-06
Hmm, It wont recognise my login details!!

---

### Post by lavinog on 2011-06-06
> **Super-Dan said:**
> Hmm, It wont recognise my login details!!

What won't?
Sudo or the login?

---

### Post by Super-Dan on 2011-06-06
It doesnt recognise my login details

BUT!!!!

I created a Launcher on the desktop with the following code
gnome-session-save --logout-dialog

I then used this to logout and into Classic! Boom sorted!!

Thankyou very much guys!!

---

