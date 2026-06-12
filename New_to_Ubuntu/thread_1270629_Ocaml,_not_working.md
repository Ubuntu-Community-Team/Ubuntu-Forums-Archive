---
title: "Ocaml, not working"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Kuberr on 2009-09-19
Greetings everyone,

I just got Ubuntu today and am very pleased with it though I'm am not yet very adept with Linux and am still getting used to installing programs. 

I went about trying to install Ocaml [this way]("http://ubuntuforums.org/showthread.php?t=248225"), due to not being as confident with Package Manager. At first everything went well, it went missing though, as in, it didn't register in the list of Applications. I managed to find it and used Main Menu and adding it as a New Item to organize it among the list there. Now for my problem... it doesn't run. I press the icon for Ocaml, but nothing happens. I have Ubuntu dual booting with Vista, Ocaml runs fine with Windows. I am pretty sure I installed it properly. I also think I added it in the Applications list right, as when I typed in ocaml in the command of create launcher, the Ocaml icon appeared automatically. Any suggestions? If it's any help, the version I managed to install is 3.10.2.

---

### Post by sandyd on 2009-09-19
> **Kuberr said:**
> Greetings everyone,

I just got Ubuntu today and am very pleased with it though I'm am not yet very adept with Linux and am still getting used to installing programs. 

I went about trying to install Ocaml [this way]("http://ubuntuforums.org/showthread.php?t=248225"), due to not being as confident with Package Manager. At first everything went well, it went missing though, as in, it didn't register in the list of Applications. I managed to find it and used Main Menu and adding it as a New Item to organize it among the list there. Now for my problem... it doesn't run. I press the icon for Ocaml, but nothing happens. I have Ubuntu dual booting with Vista, Ocaml runs fine with Windows. I am pretty sure I installed it properly. I also think I added it in the Applications list right, as when I typed in ocaml in the command of create launcher, the Ocaml icon appeared automatically. Any suggestions? If it's any help, the version I managed to install is 3.10.2.
not confident with package manager?

maybe Applications -> Accessories -> Terminal
and pasting this in
```

sudo apt-get install ocaml

```

should work.
don't panic if nothing shows up while typing your password - its normal.

---

### Post by Kuberr on 2009-09-19
You seem to have misread my post...

Ocaml is *already* installed, version  3.10.2 specifically. At least, I am quite sure of it. I installed it the way you just recommended, as I stated that I already followed [this user's method]("http://ubuntuforums.org/showthread.php?t=248225"). My problem lies in that it's not working, and I am wondering as to why and how to fix it.

---

### Post by sandyd on 2009-09-19
then perhaps just
```

ocaml

```
in the terminal?
what does that show?

---

### Post by Kuberr on 2009-09-19
This is pretty much all that appears.

```

kub@Kub-Laptop:~$ ocaml
        Objective Caml version 3.10.2

# 

```Help is very much appreciated.

---

### Post by sandyd on 2009-09-19
heheheheh
that IS ocaml. ocaml does not have a GUI in linux that comes along with it.
you will need to install a theird party gui for ocaml.

---

### Post by Kuberr on 2009-09-19
Lol, I had the feeling that it was the case. Just wasn't quite sure.

In any case, to prevent more wasting of my time with me going in circles, how would I go about with the third party GUI? If you don't mind answering again? :)

---

### Post by adamogardner on 2009-09-19
I just installed and tried to start it up by typing it in my terminal.  It didn't work so perhaps a restart should do it.

---

### Post by adamogardner on 2009-09-19
restart did not work.  this is what I get:

adamogardner@CRONUS:~$ ocaml
        Objective Caml version 3.10.0

#

---

### Post by sandyd on 2009-09-19
THAT IS what your supposed to get

im about to go into an extremely important terrirory right now, so listen up.

There is a program in Linux called WINE. It is a reimplementation of windows that allows windows programs to be run on linux.

I just tried, and Ocaml runs on WINE.

so...
```

sudo apt-get install wine cabextract
[LEFT]wget http://winezeug.googlecode.com/svn/trunk/winetricks[FONT=monospace]
[/FONT]chmod +x winetricks[FONT=monospace]
[/FONT]sudo mv winetricks /usr/local/bin[FONT=monospace]
[/FONT]winetricks vcrun2005 vb6run cygwin allfonts fontfix [/LEFT]

```[LEFT]
now assuming you downloaded the Ocaml for Windows installer to the desktop,
[/LEFT]
 ```

cd ~/Desktop
wine ocaml*

```it will then show up in your menu under WINE

HOWEVER, for obvious reasons, WINE is not complete yet, so not all apps work under WINE.
Also, it is prefered to run linux apps instead of windows apps through wine.

---

### Post by Kuberr on 2009-09-20
There's much I have to learn. Anyways, thank you very much carlee!

---

