---
title: "SCIM not working"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Karnex420 on 2009-09-15
I can't seem to get scim working (Jaunty-on an acer laptop with vista). I see the icon on the desktop but "Ctrl and space", doesn't do anything.

---

### Post by Irihapeti on 2009-09-15
Look under System -> Administration -> Language Support and check that the box "Enable support to enter complex characters" is checked.

You will need to reboot after you change that.

If that doesn't work, then:

Open a terminal (Applications -> Accessories -> Terminal)

enter the command:
```
locale|grep 'LANG='
```
and hit enter

You will see your language displayed.
Mine shows:
```
LANG=en_NZ.UTF-8
```
Then type:
```
im-switch -z (your_locale) -s scim-bridge
```
(In my case, it's im-switch -z en_NZ.UTF-8 -s scim-bridge
Yours will probably be different.)

Then log out and log in again.

I'm not sure if the terminal commands are needed for Jaunty - I'm still running Hardy.

---

### Post by expatCM on 2009-09-16
yes, the last response is very good .... check that support for complex characters is enabled ... that really is the first step.

I found one case recently where the user said that scim was not working and of course it was not ..  they were trying to open it up from the desktop with no application (like writer) open and so scim did not do anything.  As soon as writer was opened it started working perfectly ...

---

### Post by Karnex420 on 2009-09-16
That did it &#32481; &#32481; &#26786; &#25968;&#39069;  (Now I just have to learn the characters)  
Can't see where to mark this solved and thanks
You guys are great.

---

### Post by nobswolf on 2009-09-18
I guess I have the same problem.

> **Irihapeti said:**
> Look under System -> Administration -> Language Support and check that the box "Enable support to enter complex characters" is checked.


And now the stupid question:  Where do I find this setting? I am using KDE4 and can't find any "Administration" in the "System" section of the KDE-Menu.

But I know I have seen this dialog box. How do I start it again?

edit:

guess I found it it 

 sudo qt-language-selector --mode select

I selected the checkbox and saved... but that doesn't change anything :-/ 

any more hints for me?

---

### Post by Irihapeti on 2009-09-18
> **nobswolf said:**
> I guess I have the same problem.



And now the stupid question:  Where do I find this setting? I am using KDE4 and can't find any "Administration" in the "System" section of the KDE-Menu.

But I know I have seen this dialog box. How do I start it again?

edit:

guess I found it it 

 sudo qt-language-selector --mode select

I selected the checkbox and saved... but that doesn't change anything :-/ 

any more hints for me?

You're right - my instructions were for Gnome; I've never used KDE and so I don't know my way around it at all. That means I can't tell you very much. I think that KDE's version is called skim. I've found a documentation page with some hints here: [https://help.ubuntu.com/community/SCIM/Kubuntu](https://help.ubuntu.com/community/SCIM/Kubuntu)

I hope it will be of some use.

---

### Post by guriinii on 2009-10-09
I originally used SCIM in GNOME, fancied a change and went to KDE. I tried to reinstall SCIM for ages, searched the forums, used the how-to, but all failed. So I converted back to GNOME, plus GNOME doesn't look like Duplo Lego.

---

### Post by expatCM on 2009-10-09
With KDE I think you need to install Skim, not Scim.

---

