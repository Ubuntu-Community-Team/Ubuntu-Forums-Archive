---
title: "Hebrew support problem"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by eblam137 on 2011-05-24
Hello
we've just installed ubuntu and we cannot use Hebrew eventhough it's installed in Hebrew, and it's chosen in the language support.
Even in openoffice when it's chosen and we start writing it's only in English/
idea anyone?

---

### Post by jtarin on 2011-05-24
H-m-m, that doesn't sound kosher!:)
[HERE]("http://www.oooforum.org/forum/viewtopic.phtml?t=113567")

---

### Post by grahammechanical on 2011-05-24
You may also need to set the keyboard layout to Hebrew. This is in System Settings>Keyboard>Layouts.

The system and Openoffice are using the same type of font. Called unicode. The font package is large enough to hold characters from many languages. The keyboard needs to be set work from the part of the font matrix that contains the characters that you want.

When you are in Openoffice click on Insert>Special Character and you can view all the characters in the font and imagine action the OS has to do get your choice on the screen.

Did you notice that once you have different language support installed you can select the language both for the system and the keyboard at login? Click on the user name and you will see the options in the bottom panel.

P.S. I have just tried to set my copy of Libreoffice to Hebrew in Tools>Options>Language Settings>Languages. It is not possible to set the default language for documents to Hebrew until you tick the check box Enable for Complex Text Layout (CTL) under the Enhanced Language Support section. After that you will find Hebrew in the drop down menu of CTL. So, I ask are you setting Hebrew as the default language for documents in this place? If you have already tried that, then please forgive me.

Regards.    &#1513;&#1500;&#1493;&#1501;

---

