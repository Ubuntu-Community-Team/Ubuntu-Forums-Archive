---
title: "Missing dialog asking what desktop to boot"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Books on 2010-11-22
I installed Ubuntu 10.10 and updated all the packages, and restarted and everything was going fine. 

Then I installed **kubuntu-desktop** and **xubuntu-desktop** to try them out. 

During the installation of kubuntu-desktop it asked me what the default manager would be -- gdm or kdm -- and I chose gdm.

Now it gets weird when I restart.

When it boots it shows:

1. The **Kubuntu** booting screen... Huh?

2. The **Xubuntu** log-in screen.

So I type in the username and password.

3. Then it boots **Ubuntu** every time!

I found the Ubuntu System > Administration > Login Screen and chose the "Show the screen for choosing who will log in" and "User Defined Session" as the default session. Still won't show the dialog.

How can I get a dialog asking me what desktop manager to boot? 

Thanks!

---

### Post by mikewhatever on 2010-11-22
So, there is no 'Session' at the login screen to select the DE?

---

### Post by Books on 2010-11-22
I finally got a log-in screen, but it's the Xubuntu login screen. First it shows the Kubuntu splashscreen and then the Xubuntu login screen.

I figured out how to get it to select a desktop to boot, but I want to get rid of it and get the standard Ubuntu login screen back.

Should I try uninstalling Xubuntu... or could that cause worse problems?

---

### Post by NightwishFan on 2010-11-22
Just remove the package xubuntu-gdm-theme, and reinstall the package gdm.

---

### Post by Books on 2010-11-22
> **NightwishFan said:**
> Just remove the package xubuntu-gdm-theme, and reinstall the package gdm.

It worked! I've got the standard Ubuntu login back.

You are truly a Ubuntu-Jedi Master!

Any ideas on how to get rid of the Kubuntu splash screen?

Thank you.

---

### Post by NightwishFan on 2010-11-22
No, I am sorry. :(

Edit: Wait, go into the KDE (Kubuntu) session at the login screen, and go to the kde system settings and turn it off there, that might work.

---

### Post by bokgeneraal on 2010-11-27
**RE: Missing dialog asking what desktop to boot**
Hi There
I installed Kubuntu-desktop in Ubuntu 10.04 and I too have no dialog to choose desktop manager at the login screen.
Plz share how you got the dialog back
Thanx;)

---

