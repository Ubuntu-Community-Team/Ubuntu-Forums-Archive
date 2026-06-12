---
title: "Problem moving files into home with Ubuntu 10.10"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2011-07-05
I know this is probably a stupid problem to be having, but every time I try and move a file to install a program into my home folder it says "Permission Denied". This is starting to cause some real issues with programs I can't get via synaptic or terminal prompt. Does anyone know a way to gain permission? I mean I'm on the administrator account and its my computer so it should allow me access

---

### Post by dFlyer on 2011-07-05
First off, Synaptic is not for installing programs that are downloaded. If you download a deb file use dpkg -i "packagename" to install the package or just double click on it. Second, Linux requires an administrator password to install a program, regardless if it installed via synaptic, dpkg, apt-get or Ubuntu Software Center. Third what is the name of the program, is it a win program under wine? If so you need to change it to executable before it will install, regardless if your administrator. If it's a bin program it also need to be changed to executable.

Remember, Linux is not windows and there is a learning curve. Go slow and have fun.

---

### Post by Captainflowers91 on 2011-07-05
Thanks. I've been working with it for a little more then a year now. Anyway, its Android SDK. I need it to root my phone. It says theres a linux version and tells you to drag the extracted file into home, but its no dice

---

### Post by candtalan on 2011-07-05
> **Captainflowers91 said:**
> It says theres a linux version and tells you to drag the extracted file into home, but its no dice

Where are you dragging it from?  Ubuntu? From which folder? Presumably into your ubuntu home folder.

With Ubuntu GUI, if you right click onto the file icon or file manager listed filename and choose Properties, then Permissions, you will see the file owner. If it is not your username you will need to manage a change. Not necessarily difficult, but  first, see what owner name is shown.
hth

---

### Post by alphacrucis2 on 2011-07-05
> **Captainflowers91 said:**
> Thanks. I've been working with it for a little more then a year now. Anyway, its Android SDK. I need it to root my phone. It says theres a linux version and tells you to drag the extracted file into home, but its no dice


By home do you mean:

/home

or 

/home/<your usercode>


If you are trying to write the file to /home then that will fail. You need admin rights to do that. The instructions probably mean to move the file to /home/<your usercode> as that is the current directory when you open a terminal.

---

### Post by dFlyer on 2011-07-05
> **Captainflowers91 said:**
> Thanks. I've been working with it for a little more then a year now. Anyway, its Android SDK. I need it to root my phone. It says theres a linux version and tells you to drag the extracted file into home, but its no dice

What is the full file name including it's extension? and home is /home/username what ever that may be when you open a terminal.

---

### Post by Captainflowers91 on 2011-07-05
The file name is android-sdk-linux_x86. I have it in /home/username, how do I install it via terminal?

---

### Post by alphacrucis2 on 2011-07-06
> **Captainflowers91 said:**
> The file name is android-sdk-linux_x86. I have it in /home/username, how do I install it via terminal?

Did the site you downloaded it from not provide instructions?

---

### Post by dFlyer on 2011-07-06
change file to executable with chmod +x filename on a command line then try sh android-sdk-linux_x86. If that doesn't work try ./android-sdk-linux_x86

---

### Post by Captainflowers91 on 2011-07-06
Sadly no, thats part of the problem lol. And neither of those terminal prompts worked :/

---

