---
title: "how to use gdm ???"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by ashhab2010 on 2011-08-22
i installd gdm from the maveric backport updates but i have no clue on how to use it 
typing gdm in the terminal gives me this error

** (gdm-binary:4245): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.60" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:4245): WARNING **: Could not acquire name; bailing out


what do i do??

---

### Post by mikewhatever on 2011-08-22
You didn't have to install GDM from backports because it's pre-installed. What do you want to use it for.

---

### Post by ashhab2010 on 2011-08-22
i wanted to change my boot splash screen thats why i installd it

---

### Post by mcduck on 2011-08-22
> **ashhab2010 said:**
> i wanted to change my boot splash screen thats why i installd it

GDM won't help you there, the boot animation is handled by Plymouth while GDM is the one responsible of the login screen and starting desktop sessions for users.

(the command to start GDM would be "sudo service gdm start")

These articles should help you with changing the boot animation:
[http://www.techdrivein.com/2011/05/5-stunning-plymouth-screen-themes-for.html]("http://www.techdrivein.com/2011/05/5-stunning-plymouth-screen-themes-for.html")
[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13]("http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13")

---

### Post by garvinrick4 on 2011-08-22
Select your different plymouth themes in Synaptic package manager.
There is maybe 5 or 6 or theme, like solar,  and some others.
install them.
and then run this below:
                          ```
sudo update-alternatives --config default.plymouth 
```Now choose which one you want to install by number and run update-initramfs below:
```
sudo update-initramfs -u
```

#Is this not the second thread you ran on this subject. One will do I believe, enjoy your Ubuntu.

---

### Post by ashhab2010 on 2011-08-22
> **mcduck said:**
> GDM won't help you there, the boot animation is handled by Plymouth while GDM is the one responsible of the login screen and starting desktop sessions for users.


sorry for not mentioning i even wanted to change the login screen.
i want to know how to do that... a gui would greatly help

---

