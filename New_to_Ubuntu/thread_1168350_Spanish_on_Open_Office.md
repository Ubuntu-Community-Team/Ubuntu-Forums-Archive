---
title: "Spanish on Open Office"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by rlj399 on 2009-05-24
I tried setting the language on open office to spanish, but it won't detect grammar errors, is there any extension or package i can install to make it so that open office automatically places accents on words and detects mistakes?

---

### Post by Didius Falco on 2009-05-24
> **rlj399 said:**
> I tried setting the language on open office to spanish, but it won't detect grammar errors, is there any extension or package i can install to make it so that open office automatically places accents on words and detects mistakes?

Here are a couple of resources for you:

[http://www.oooforum.org/forum/viewtopic.phtml?t=63638](http://www.oooforum.org/forum/viewtopic.phtml?t=63638)

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512)

[http://wiki.services.openoffice.org/wiki/Dictionaries#Spanish_.28Spain.2C_....29](http://wiki.services.openoffice.org/wiki/Dictionaries#Spanish_.28Spain.2C_....29)

If that doesn't solve it, you can search around anf/or ask in the OO forums.

I hope this helps...

Regards,

Didius

---

### Post by fballem on 2009-05-24
> **rlj399 said:**
> I tried setting the language on open office to spanish, but it won't detect grammar errors, is there any extension or package i can install to make it so that open office automatically places accents on words and detects mistakes?

You will need to install the dictionaries. I'm assuming that you are using OpenOffice 3.0.

There are two ways to do this, depending on whether it is just yourself on your computer or whether you wish to make the dictionaries available to all users.

For yourself:
[LIST=1]
[*]Start OpenOffice Writer (the Word processor) and start a new text document.
[*]From the menu, select Tools > Extension Manager. You will see a window similar to Screenshot-Extension Manager attached.
[*]Select the Add Extension hyperlink (lower left-hand part of the screen). This will open your web browser and display a page similar to the Screenshot-OpenOffice.org-Extending Your Product.
[*]On the upper left of this screen, you will see a list of the types of extensions, including Dictionaries. If you select Dictionaries you will get a screen list of the dictionaries - as shown in Screenshot-OpenOffice.org repository for Extensions ...
[*]Select the dictionary and follow the instructions.
[/LIST]

The only difference if you want to make the dictionary available for all users of your computer is how you start open office. To do this, open a terminal and execute the following command ```
gksudo soffice
``` This starts open office with root privileges. When you install the dictionary, you will be given the option to make this available to all users of the computer.

By the way, do you have the correct keyboard setup that will allow you to type the accents? If not, then the instructions in the following post may be helpful if you have a US Keyboard: [http://ubuntuforums.org/showthread.php?t=1157474](http://ubuntuforums.org/showthread.php?t=1157474)

Hope this helps,

---

### Post by rlj399 on 2009-05-24
thanks guys, that was really helpful.
I added keyboard indicator to my panel so switching should be easy now thanks again

---

