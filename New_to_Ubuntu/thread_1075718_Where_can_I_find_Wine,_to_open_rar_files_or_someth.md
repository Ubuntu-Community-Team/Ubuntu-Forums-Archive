---
title: "Where can I find Wine, to open rar files or something?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Sherbertlemon on 2009-02-20
I have a few .rar files that I need to open. And people have said that Wine is good but i'm so thick that I dont understand.
So were would I be able to get it?

---

### Post by howefield on 2009-02-20
Ubuntu built in file-roller will handle rar files if you install rar and unrar.

Add the medibuntu repository :

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then in terminal, type :
```

sudo apt-get install lzma unrar rar p7zip p7zip-full p7zip-rar

```

This will add more files types to file-roller including rar.

---

### Post by donkyhotay on 2009-02-20
Umm... you don't need wine to open .rar files. Wine actually has nothing to do with .rar files. The best way to install the software that allows you to open a .rar is to open the terminal and type
```
sudo apt-get install unrar
```
It's in multiverse so you don't actually need medibuntu (though medibuntu is great for other things and I would recommend it)
now if you really do want wine in order to try and run windows programs you install it with
```
sudo apt-get install wine
```

---

### Post by Sherbertlemon on 2009-02-20
> **donkyhotay said:**
> Umm... you don't need wine to open .rar files. Wine actually has nothing to do with .rar files. The best way to install the software that allows you to open a .rar is to open the terminal and type
```
sudo apt-get install unrar
```
now if you really do want wine in order to try and run windows programs you install it with
```
sudo apt-get install wine
```


Umm... What is a terminal?

---

### Post by howefield on 2009-02-20
A command line tool, go to Applications > Accessories > Terminal

---

### Post by Sherbertlemon on 2009-02-20
> **howefield said:**
> A command line tool, go to Applications > Accessories > Terminal

ooohhh... Thank you! Sorry for my stupidity.. But I'm only 12 so I guess I can get away with it xP

---

### Post by donkyhotay on 2009-02-20
From the menu at the top of the screen go to
Applications > Accessories > terminal
This will bring up the terminal program, it is a CLI (command line interface) similar to the old DOS prompt. Although there are ways of installing the software you want from the GUI it's much easier for us to give you a command you can copy and paste into the terminal rather then trying to give directions on which buttons to push in the GUI.

---

### Post by Sherbertlemon on 2009-02-20
> **donkyhotay said:**
> From the menu at the top of the screen go to
Applications > Accessories > terminal
This will bring up the terminal program, it is a CLI (command line interface) similar to the old DOS prompt. Although there are ways of installing the software you want from the GUI it's much easier for us to give you a command you can copy and paste into the terminal rather then trying to give directions on which buttons to push in the GUI.



Okay, thanks!

---

### Post by donkyhotay on 2009-02-20
> **Sherbertlemon said:**
> ooohhh... Thank you! Sorry for my stupidity.. But I'm only 12 so I guess I can get away with it xP

We were all beginners once ourselves. Learn as much as you can and pass it along to the next person. (c:

---

### Post by dolman25 on 2009-02-23
Dont install p7zip it conflicts with unrar when extracting. if im guessing right it will be the unrar that you will be needing.

---

