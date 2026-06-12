---
title: "Cannot open jpg image"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by suikerbos on 2010-05-20
Ubuntu Firefox:  I have inadvertently altered a preference/setting.  :redface:  Result: I cannot open a jpg image.  Please help me correct this? Grateful thanks in anticipation:)
I'm really sorry to be so dumb - I would like to start again:
[SIZE=+1][FONT=Comic Sans MS][COLOR=#ff0000]
[COLOR=Black]I  received an email into my Mozilla Thunderbird inbox which had a jpg attachment.  Previously I have opened these attachments without any problems, now I cannot. I get an error message,[/COLOR]
 "/tmp/image001.jpg cld not be opened cos the associated helper application does  not exist. Change the association in your preferences" 
[COLOR=Black]How do I change this back to the default setting so I can open jpg attachments from Thunderbird?
Tku kindly for previous answers and sorry to be .... Ultra Absolute Beg..!!
[/COLOR]
[/COLOR][/FONT][/SIZE]

---

### Post by ubunterooster on 2010-05-20
preferences>content>load images automatically

---

### Post by Rushyang on 2010-05-20
> **ubunterooster said:**
> preferences>content>load images automatically
I believe that is ON by default. There must be some sort of another problem. Because he mentioned .JPG especially.

---

### Post by ubunterooster on 2010-05-20
> **Rushyang said:**
> I believe that is ON by default. There must be some sort of another problem. Because he mentioned .JPG especially.
by default, yes.

but [quote=suikerbos]I...altered a preference/setting[/quote]


[color=blue]Does it load other image types?[/color]

---

### Post by lovinglinux on 2010-05-20
Close Firefox, open your Firefox profile folder (i.e. ~/.mozilla/firefox/<profilename>) and delete the file **prefs.js**. Restart Firefox.

This will revert all your Firefox settings to default, including the ones used by extensions.

---

