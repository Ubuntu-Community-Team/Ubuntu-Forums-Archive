---
title: "How To Select Session When Logging In?"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-04-29
Title pretty much says it all. How can I select which of my install desktop environments that I want to log into at the login screen? I know you can select the default through System -> Administration -> Login Screen, bu that's not what I want.

---

### Post by Lateralis on 2011-04-29
In 10.10 and 10.04 (I've not tried 11.04 so don't know if the login screen is different), at the bottom of the login screen there's a bar with a few options.  Under the session menu you can select which type of session to use.

---

### Post by scottykal12 on 2011-04-29
> **Lateralis said:**
> In 10.10 and 10.04 (I've not tried 11.04 so don't know if the login screen is different), at the bottom of the login screen there's a bar with a few options.  Under the session menu you can select which type of session to use.

Works the same in 11.04

---

### Post by dniMretsaM on 2011-04-29
I only see a clock, a power menu, and an accessibility menu.

---

### Post by Lateralis on 2011-04-29
> **scottykal12 said:**
> Works the same in 11.04

Thought it would, but can't be sure in these uncertain days of Unity!  

@dniMretsaM

Once you click on your name to bring up the password box, a "Sessions" menu appears to the left of the accessibility menu.

---

### Post by 23dornot23d on 2011-04-29
You can always use the kdm login menu system it to me is far easier to use .... to try it.

[COLOR=Red]**sudo apt-get install kdm**[/COLOR]

choose kdm when it asks you ........ if you do not like it 

then should you want to remove it afterwards at any point do

sudo apt-get remove kdm

choose gdm when it asks ......

---

### Post by Blasphemist on 2011-04-29
The top screen shot in this thread shows where to change the session type at the login screen.

[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

---

### Post by dniMretsaM on 2011-04-29
> **Lateralis said:**
> @dniMretsaM

Once you click on your name to bring up the password box, a "Sessions" menu appears to the left of the accessibility menu.

I have it set to not ask me for my password on login. Maybe I'll try the KDM login. I plan on trying out the KDE desktop anyway.

---

### Post by Blasphemist on 2011-04-29
I really don't understand. It has been described how to choose the session type through the admin option and how to choose at the start of each session.

---

### Post by dniMretsaM on 2011-04-29
I know how to choose the default through the admin settings but I apparently can't change at the start of each session because I don't have Ubuntu ask for my password when I login and the password entry screen is where the session menu appears.

---

### Post by 23dornot23d on 2011-04-29
1 .... You can choose with kdm as it always asks for the password at startup ...... no matter if you have it set to autologin in gdm ...... ( it will not )

____________________________________________

2 .... With it set up as it is to auto-login in using gdm ........

If you just choose to **[COLOR=Red]log out of your sessio[/COLOR]n **...... 

You will get to see the gdm login screen and your choices ....... 
will or should be available to choose too.


Hope this helps

---

### Post by dniMretsaM on 2011-04-29
I don't use auto-login. Anyway, thanks. That's good to know.

---

### Post by Blasphemist on 2011-04-29
> I know how to choose the default through the admin settings but I apparently can't change at the start of each session because I don't have Ubuntu ask for my password when I login and the password entry screen is where the session menu appears.

> **dniMretsaM said:**
> I don't use auto-login. Anyway, thanks. That's good to know.

It seems to me that you do use auto login.

---

### Post by dniMretsaM on 2011-04-29
No, I don't.

---

### Post by Blasphemist on 2011-04-29
I've never tried the using no password option. When you are prompted for user selection, you don't see what we have shown at the bottom of the screen? If not, it seems you might need to file a bug report and for the time being enable password use.

---

### Post by dniMretsaM on 2011-04-29
Ok, I'll file a bug report. I've always thought it was strange that there was no way to choose a session when logging in.

---

