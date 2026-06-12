---
title: "My Ubuntu turned into Kubuntu by itself"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by Bennot on 2010-12-09
[SIZE=3]I´ve bought a computer for my daughter and installed Ubuntu 10.10. Then I started installing many education programs from Ubuntu Software Center, many of them starting with K. Next thing I know, the computer now says kubuntu when I boot or turn it off. Is this normal? I tried to see if I can go to ubuntu by logging off and back on into ubuntu, but there are no options to do that in the log on window. I don´t understand how it turned into kubuntu. Am I really using kubuntu or ubuntu? [/SIZE]

---

### Post by bhishan on 2010-12-09
> **Bennot said:**
> [SIZE=3]I´ve bought a computer for my daughter and installed Ubuntu 10.10. Then I started installing many education programs from Ubuntu Software Center, many of them starting with K. Next thing I know, the computer now says kubuntu when I boot or turn it off. Is this normal? I tried to see if I can go to ubuntu by logging off and back on into ubuntu, but there are no options to do that in the log on window. I don´t understand how it turned into kubuntu. Am I really using kubuntu or ubuntu? [/SIZE]

At the login screen you can choose between KDE and GNOME desktop environments. Try choosing GNOME. Hope it helps.

---

### Post by Bennot on 2010-12-09
> **bhishan said:**
> At the login screen you can choose between KDE and GNOME desktop environments. Try choosing GNOME. Hope it helps.

[SIZE=3]The login screen configuration (System->Administration->Login Screen, is set to start the Ubuntu Desktop Edition as the default session, and there appear no options for  any other kind of desktop. So it must be be starting on the ubuntu desktop.

However, when I turn off or start the computer, the screen that appears while it is booting says kubuntu,  not ubuntu. This was not the case before I installed all those education programs. Up until then, the screen said ubuntu.  What I installed was Ubuntu, and as far as I know I never changed it. It´s confusing.[/SIZE]

---

### Post by sikander3786 on 2010-12-09
Welcome to the forums :-)

I think the Kubuntu plymouth theme and might be KDM (Kubuntu Login Manager) got installed with some KDE specific programs.

To switch your plymouth theme back to Ubuntu,

Applications > Accessories > Terminal:

```
sudo update-alternatives --config default.plymouth
```

And to switch back to GDM (Ubuntu Login Manager),

```
sudo dpkg-reconfigure gdm
```

---

### Post by tajiknomi on 2010-12-09
> **Bennot said:**
> [SIZE=3]The login screen configuration (System->Administration->Login Screen, is set to start the Ubuntu Desktop Edition as the default session, and there appear no options for  any other kind of desktop. So it must be be starting on the ubuntu desktop.

However, when I turn off or start the computer, the screen that appears while it is booting says kubuntu,  not ubuntu. This was not the case before I installed all those education programs. Up until then, the screen said ubuntu.  What I installed was Ubuntu, and as far as I know I never changed it. It´s confusing.[/SIZE]

[SIZE=2]Open up Login-Screen and their you will see an option[/SIZE] "[SIZE=2]***Show the screen for chossing who is log in"  ***tick that***,*** and now whenever ,you will login inn. their will be an option below to choose the Enviroment, Gnome & KDE[/SIZE],

---

### Post by tajiknomi on 2010-12-09
[SIZE=2]<not belongs to topic> @sikander:- Can you explain a little-bit these commands,which you has Suggested :p <Closed>[/SIZE]

---

### Post by Bennot on 2010-12-09
[SIZE=3]Thanks all for the suggestions.
I guess it is nothing important. It is logging in to the Ubuntu Desktop Edition as chosen in the login screen. I switched to the KDE to see how it looks like and that sure looks very different.

For some reason it just shows the kubuntu graphics when booting and turning off, after I installed those education programs.[/SIZE]

---

### Post by toasterboy1 on 2010-12-09
You could try this code
```
sudo update-alternatives --list usplash-artwork.so
```
I only have kubuntu installed so it just gave me any error but that is what is said to do in every other post about the boot splash being changed. There is also reference to reconfiguring the kernel with
```
dpkg-reconfigure linux-image`uname -r` 
```

---

