---
title: "In home folder, is .anyfolder compared to prog files?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by rcayea on 2009-11-05
Basically as the title asks...

In the home folder, is .anyfolder = Program Files in Windows 

and

in my home folder does Anyfolder (not hidden) = My Documents?

Thanks,
Randy

---

### Post by Seti on 2009-11-05
There are a lot of configuration files in your home directory that provide the settings for the way you have personalized any program you use. Lots of times you'll see .program where 'program' is the name of a program you use. Rarely though should the executable (bin) of these programs be found in your home though.
Beyond that, you can make directories in your home for whatever you want... documents, pictures, videos, music, etc etc.

---

### Post by b0b138 on 2009-11-05
no. .anything means its hidden less you check show hidden files/folders

most of (or all?) of the hidden folders in you home store your personal program settings/preferences/profiles.

Your whole home folder is kinda like My Documents but better. Windows stores personal program settings/preferences/profiles and some other stuff in (scratches head and looks at the ceiling) c:/documents and settings/user/Application Data ????

The linux equivilent of program files is /usr/share/ (i think)  ;)

---

### Post by philinux on 2009-11-05
> **rcayea said:**
> Basically as the title asks...
In the home folder, is .anyfolder = Program Files in Windows 
and
in my home folder does Anyfolder (not hidden) = My Documents?
Thanks,
Randy

First question, answer = no, the .folder files are program configuration folders. Like .mozilla is your firefox config folder string bookmarks and addons etc. Also in there are .files which again are config files.

Second question, answer = yes.

---

### Post by cariboo on 2009-11-05
Any file or directory with a dot in front of it is hidden, and usually is a configuration file/directory.

The only directory that is semi comparable to Program Files is the /usr directory. You can put files anywhere you want in your home directory which is more the equivalent to Documents and Setting/user

Edit: when I started my post there were no answers, by the time I had answered the phone and finished, three others had answered already. Good show guys

---

### Post by Kedster on 2009-11-05
In a short answer all that you have said is semi-correct with some exeptions.
all the .anyfolder means is that it is hidden. Not all the hidden folders in your home folder will be program folders, but by default I do believe the hidden folders in home are actually program folders. Another thing is that they are not exactly the same as in windows they do not usually have the actual program in the home folders just the settings and other important things. The actual program is installed somewhere else, do not ask me where I do not know. the rest of the foders and any folders you create do act like "My Documents" from windows.

Ps. You can make any folder in linux hidden with a period in front. but when renaming remember that linux is case sensitive.

---

### Post by b0b138 on 2009-11-05
Here ya go  [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Its a little outdated so some things might have changed. Plus different distros will have there own little difference also.

---

### Post by rcayea on 2009-11-05
thanks for the replies!

---

