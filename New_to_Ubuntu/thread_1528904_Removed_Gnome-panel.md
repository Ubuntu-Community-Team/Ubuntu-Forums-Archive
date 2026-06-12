---
title: "Removed Gnome-panel"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by LittleGyko on 2010-07-11
Hi,

I use ubuntu 10.04 on my Dell Studio laptop, and the panel which appears on top of the screen was not behaving properly, more specifically, some of the icons might appear twice/may not appear/ only half of the icon might appear etc. 

I thought reinstalling the panel might solve the above issues and so i went to synaptic and from there completely removed gnome-panel. Before installing it again, I logged out and now I am not able to login again. The login screen appears and after I type in the password, it tries to login, but then it returns the login screen again.

Ctrl + Alt + F'x' for x a number does not seem to work.

Can someone help me.

Thanks

---

### Post by Naitsirhc Hsem on 2010-07-11
You can hit Crtl + Alt + F6 to get to an emergency terminal from the login screen.  from there you can login to the terminal and ```
sudo apt-get install gnome-panel
```

---

### Post by LittleGyko on 2010-07-11
I use a Dell Studio 14 laptop. Ctrl + Alt + F6 or Ctrl + Alt + F'x', for any number x does not work.

---

### Post by Naitsirhc Hsem on 2010-07-11
have you tried booting in recovery mode in the grub menu?

sorry, I did not read the last part

---

### Post by LittleGyko on 2010-07-11
i edited the message...so my mistake. 

i only had wireless network in my room and there it gave an error that it could not download the file. but now i realise that it might have been so because it could not connect to the net. 

in the recovery mode i shall choose the option root terminal with networking. once here, can you tell me how i can check if my laptop is connected to the internet.

thanks

---

### Post by LittleGyko on 2010-07-11
now i connected to the net using a cable and was successful in sudo apt-get install gnome-panel. 

hopefully things will work now. i'll get back.

---

