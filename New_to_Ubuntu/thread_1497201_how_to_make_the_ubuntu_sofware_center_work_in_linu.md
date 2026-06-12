---
title: "how to make the ubuntu sofware center work in linux mint 9"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-05-30
okay if i open a terminal and type


sudo gedit /etc/lsb-release

i get
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=9
DISTRIB_CODENAME=isadora
DISTRIB_DESCRIPTION="Linux Mint 9 Isadora"

then if i change the first line after = to Ubuntu and save i can acccess the ubuntu software center no problem

however if i reboot lsb goes back to the aforementioned and i again have to change the first line. how can i make this change permanent/tks

---

### Post by nerdtron on 2010-05-30
You mean you can't use the software center if you don't change 'LinuxMint' to 'Ubuntu'?

---

### Post by rburkartjo on 2010-05-30
thats right nerd

---

### Post by nerdtron on 2010-05-30
I'm using mint 9 and without any modifications, the new software center works fine.
I suggest that yot post a thread about this on the linux mint forums.

---

### Post by rburkartjo on 2010-05-30
nerd does the linux  mint software manger work fine and can you get the ubuntu software center to work. the mint works okay but just trying to get the ubuntu software center to work also in mint could do it in version 8 but not in 9

---

### Post by rburkartjo on 2010-05-30
i like the new software manager that was rebuild from scratch for linux mint 9 but it still has some bugs and can be slow the ubuntu is better in my opinion

---

### Post by nerdtron on 2010-05-30
> **rburkartjo said:**
> i like the new software manager that was rebuild from scratch for linux mint 9 but it still has some bugs and can be slow the ubuntu is better in my opinion

i like the new software center too. It's good that you can see the review of the app before installing it and that installation happens in the background. It works fine on my machine

Do you get an error message in the software manager if you don't change 'LinuxMint' to 'Ubuntu'?

---

### Post by rburkartjo on 2010-05-31
nerd no i just cant use the ubuntu software center unless i do the change. cant even load it from the command line just weird thats all. just throwing this out for a fix could find one on the net.

---

### Post by beastrace91 on 2010-06-28
Solution in case anyone else is wondering can be found here - [http://jeffhoogland.blogspot.com/2010/06/howto-use-ubuntu-software-center-in.html](http://jeffhoogland.blogspot.com/2010/06/howto-use-ubuntu-software-center-in.html)

~Jeff

---

### Post by rburkartjo on 2010-07-03
beast thanks for the link worked great now i can access both the ubuntu and mint software center

---

### Post by WarrenL on 2010-09-14
Jeff's instructions at his link worked really well EXCEPT that when I rebooted my machine I lost the software manager icon from the Mint menu, and it's not in the menu preferences ("System" tab) to reinstate. In fact, I couldn't find a launcher in "All Applications" anymore, and had to make up a new one with the command "software-center". What's happened?

---

