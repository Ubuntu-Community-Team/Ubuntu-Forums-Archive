---
title: "need to set up password-less login"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by kmkrause on 2010-02-20
I previously had ubuntu 9.1 installed via a Wubi, and recently did a re-install from a CD. I have everything up and running now, but I can't set up a password-less login like I did before. When I set up new users, there is a checkbox that says "don't ask for password at login" but it is greyed out, and I can't select it. Also, when I try do delete Home directories from failed user setups, I get an error message telling me that I don't have sufficient rights to perform that function. I didn't get anything like that after the previous installation. 

Any insights? 

Thank you!

---

### Post by Enigmapond on 2010-02-20
System -> Administration -> Login Window go to the security tab and set automatic login for your user name. I think this is what you're looking for.

---

### Post by kmkrause on 2010-02-20
That is what I keep reading, but I don't have a SYSTEM -> ADMINISTRATION -> LOGIN WINDOW. I have SYSTEM -> ADMINISTRATION -> LOGIN SCREEN. And there is no security tab (or any tabs at all for that matter) in that window.

---

### Post by Enigmapond on 2010-02-20
Ok you can edit the GDM like this and bypass it.


```
gksu gedit /etc/gdm/custom.conf
```Enter the configuration values  that you want to override:
AutomaticLoginEnable=true
AutomaticLogin=laikexpert

(Save  changes and close custom.conf)

Reboot  your system, and you&#8217;re automatically logged in to Ubuntu.

I would back up the original configuration so you have it. I hope this helps.

---

### Post by skymera on 2010-02-20
> **kmkrause said:**
> That is what I keep reading, but I don't have a SYSTEM -> ADMINISTRATION -> LOGIN WINDOW. I have SYSTEM -> ADMINISTRATION -> LOGIN SCREEN. And there is no security tab (or any tabs at all for that matter) in that window.

Yeah, it's a similar thing.

on LOGIC SCREEN window, click the UNLOCK button on the bottom right.

Choose "Log in As" and pick your username.

Done...

---

### Post by -kg- on 2010-02-20
> **kmkrause said:**
> That is what I keep reading, but I don't have a SYSTEM -> ADMINISTRATION -> LOGIN WINDOW. I have SYSTEM -> ADMINISTRATION -> LOGIN SCREEN. And there is no security tab (or any tabs at all for that matter) in that window.

That's what I have as well.  All is greyed out until you click the "Unlock" button.  It asks for your administrative password, then makes the controls available.

Once it's available, just click on the second radio button, "Log in as <desired user name> automatically" and you should be good to go.  I'll try this, and if it doesn't work as you are wanting it to I'll edit this post.  If I don't edit this post, it worked.

<edit> It worked, but I'm editing this anyway, because if I had read more closely I would have noticed that skymera had already posted much the same thing. :P

Also, Upon reboot it asked for my password anyway for release of the keyring, so if you're on wifi for the internet and have WEP or WPA enabled, you're going to have to insert your password to release the keys.

Personally, I don't mind logging in with the password, because if my laptop ever fell into the wrong hands, they would need to be computer savvy enough to figure out how to boot it! :D

---

### Post by kmkrause on 2010-02-20
Thank you for the quick responses. 

What I really need to do is to set up a user account for another person, and have that account not require a password. (visitors, wife, etc). When I had it setup previously, I created the username "guest" and then entered "double click to login" as the real name. Then it was obvious that all they had to do was double click the login button to log on. At some point I had installed Kubuntu, but then went back to the GNOME interface because the Kubuntu one was too slow on my machine. Do think that the ability to setup users like this was part of Kubuntu? I didn't bother installing it this time around. All it took was a couple of mouse clicks, but I can't find the right locations any more.

---

