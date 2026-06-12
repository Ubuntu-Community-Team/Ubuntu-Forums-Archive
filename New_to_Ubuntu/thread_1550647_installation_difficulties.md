---
title: "installation difficulties"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by adieunew on 2010-08-11
I find ubuntu sold as a rock once programs are installed, but the installation process is terribly frustrating.

I recently upgraded to 10.04 and tried to install openCPN. When I finally found where it had been installed I tried to launch it. It twirled for a moment then stopped. When I checked permissions I was told I was not the owner.

If anyone can tell me how I become the owner I would be most grateful.

Thanks

---

### Post by Earl_Maroon on 2010-08-11
chown [username] [file]

Hopefully that should do.

---

### Post by adieunew on 2010-08-11
Thanks Earl. Please excuse my ignorance, but I assume you mean type that into the terminal. I tried it and got:

chown: cannot access `opencpn': No such file or directory

Any hints?

---

### Post by Earl_Maroon on 2010-08-11
Yes, in the terminal.

You need to type the full path to the file. If it's on your desktop, for example:

chown username /home/username/Desktop/opencpn

I hope that helps.

---

### Post by brujoquizz on 2010-08-11
chown is to change the owner of a file. You should run it with sudo , because I asume that you have no access to the program so you are not able to change the permissions with your user. The file you have to change permission is possibly in /usr/bin.

Overall:
```
sudo chown user_you_want /usr/bin/Program_you_want
```

Hope you find helpful!

---

### Post by adieunew on 2010-08-11
Many thanks for the help.

I could be accessing it in the wrong place, but as near as I can tell the file I want is in usr/local/share/applications. I tried to access it with "sudo chown username /usr/local/share/applications/opencpn". I was asked for password, then told "no such file or directory exists". 

I know that most of my usual problems with ubuntu have terribly simple solutions, but this has me gobsmacked.

---

### Post by JKyleOKC on 2010-08-11
To find out exactly where the program is located, type this into the terminal: ```
which opencpn
```

I'm assuming that the name you type to open it is "opencpn" so if it's something else, change the "which" argument accordingly. This is always the way to locate an executable program; if it's not in the system, "which" won't return anything at all.

When you have the full path, use it in the "sudo chown" command together with your own user name...

---

### Post by howefield on 2010-08-11
> **adieunew said:**
> I know that most of my usual problems with ubuntu have terribly simple solutions, but this has me gobsmacked.

The problem might lie with the software you are trying to install as opposed to Ubuntu. Have you posted in the OpenCPN forum, seems fairly active and helpful ?

---

### Post by adieunew on 2010-08-11
With "which opencpn" I was shown a file path /usr/local/bin, which was not the location I had previously found. I did the chown command.

But the file, while "executable", won't execute. I double-click and nothing. It could be a problem with the program. I will reinstall if no one has a simple solution.

Thanks for the help.

---

### Post by adieunew on 2010-08-12
Solved. Found a post over at opencpn.org dealing with just my problems. Had to update to libwxgtk2.8-0.

cheers and thanks

---

