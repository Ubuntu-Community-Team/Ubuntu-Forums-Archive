---
title: "skype install + ubuntiu 8.04"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by dzinak on 2011-01-02
Hi,
I am really beginner. I use ubuntu 8.04 longer time but finally I decide to by a bit more independent.
I like to install skype. I found this and try with terminal:
sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install skype

reply:attachment

what have I do?
thanks a lot!

---

### Post by Foxheadz on 2011-01-02
Try just downloading the .deb file at [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

### Post by dzinak on 2011-01-02
thanks [Foxheadz]("http://ubuntuforums.org/member.php?u=1152252")
could you write me please how do I reinstall via terminal?Could you write me please, what have I write in terminal exactly in all steps? I do noot know it.

thanks

---

### Post by Foxheadz on 2011-01-02
Well you could just double click on the .deb file i think but you can run ```
dpkg -i "location of .deb file"
```

---

### Post by ingeva on 2011-01-02
> **dzinak said:**
> Hi,I downloaded this file: 
skype-debian_2.1.0.81-1_i386.deb
from skype.com. Then I execute the following file (sudo bash myskype):

```
#!/bin/bash
echo
echo "Installing Skype"
echo
dpkg -i /My/Filebank/LINUX/skype-debian_2.1.0.81-1_i386.deb

```

After installation you'll find Skype in the main menu, under Applications and Internet.
I create a panel icon by adding it to the panel (in Gnome).

Of course, your path to the downloaded file will be different! :)

---

### Post by dzinak on 2011-01-02
well I can not run code,
dpkg: requested operation requires superuser privilege
 
"Try just downloading the .deb file at [http://www.skype.com/intl/en-us/get-...omputer/linux/]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/") "
have I choose debian lenny?

---

### Post by ingeva on 2011-01-02
> **dzinak said:**
> well I can not run code,
dpkg: requested operation requires superuser privilege

That's why I told you to type "sudo bash myskype" - myskype being the name of the file, so you may have to change that. You'll be asked for your user password.

 > **dzinak said:**
> 
"Try just downloading the .deb file at [http://www.skype.com/intl/en-us/get-...omputer/linux/]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/") "
have I choose debian lenny?
Assuming that you're running Ubuntu, I think that version (8.10+) would be better. Try the 32-bit version first. Even if you have a 64-bit system the 32-bit version should run. When you've made THAT work, you can try the 64-bit version, but even if it works you probably won't notice any difference.

---

### Post by dzinak on 2011-01-02
tahanks a lot
pity it looks like I'll have to wait ....[COLOR=Red]**superuser**[/COLOR][COLOR=Red][B]
[/B][/COLOR]
 Thank you both

---

### Post by ingeva on 2011-01-02
> **dzinak said:**
> tahanks a lot
pity it looks like I'll have to wait ....[COLOR=Red]**superuser**[/COLOR][COLOR=Red][/COLOR]
 Thank you bothWe're here to help and be helped! :)

---

### Post by dzinak on 2011-01-02
ok,
I finally understood.
Look at this:

mato@mato-ubuntu:~$ #!/bin/bash
mato@mato-ubuntu:~$ echo

mato@mato-ubuntu:~$ echo "Installing Skype"
Installing Skype
mato@mato-ubuntu:~$ echo

mato@mato-ubuntu:~$ dpkg -i /My/Filebank/LINUX/skype-debian_2.1.0.81-1_i386.deb
dpkg: requested operation requires superuser privilege
mato@mato-ubuntu:~$ sudo bash myskype
bash: myskype: No such file or directory
mato@mato-ubuntu:~$ 

what now?

---

### Post by ingeva on 2011-01-02
> **dzinak said:**
> ok,
I finally understood.
what now?

YOU make the file "myskype", and THEN use the command I gave you.
When you put it in a file, the long command will be there the next time you need it. Saves you time.
Open an editor (I use gedit or geany), and copy/paste the commands into it. Then store the file (myskype).
Of course, you'll have to either change the path or omit it so you can execute the file from the same directory.

Someone also suggested that you double-click the .deb file. I'm not sure if that will work if you're not a superuser, but it's worth a try.

If you TYPE the "dpkg" command, you need to put "sudo" first so you'll enter superuser mode. That's the only command you need actually; the others are just for your information if you run the command as part of a larger batch file.

---

### Post by Foxheadz on 2011-01-03
Run ```
sudo dpkg -i "path to .deb of skype"
``` that's what it means by superuser

---

### Post by dzinak on 2011-01-20
> **ingeva said:**
> YOU make the file "myskype", and THEN use the command I gave you.
When you put it in a file, the long command will be there the next time you need it. Saves you time.
Open an editor (I use gedit or geany), and copy/paste the commands into it. Then store the file (myskype).
Of course, you'll have to either change the path or omit it so you can execute the file from the same directory.

Someone also suggested that you double-click the .deb file. I'm not sure if that will work if you're not a superuser, but it's worth a try.

If you TYPE the "dpkg" command, you need to put "sudo" first so you'll enter superuser mode. That's the only command you need actually; the others are just for your information if you run the command as part of a larger batch file. 
thanks a lot
 it was very complicated for me and my ubuntu does not know skype. me mate Installed it but it does not work properly. I'll have to install a newer version
 Thank you very much

---

### Post by dzinak on 2011-01-20
> **Foxheadz said:**
> Run ```
sudo dpkg -i "path to .deb of skype"
``` that's what it means by superuser

Thank you very much

---

### Post by Foxheadz on 2011-01-20
No problemo

---

