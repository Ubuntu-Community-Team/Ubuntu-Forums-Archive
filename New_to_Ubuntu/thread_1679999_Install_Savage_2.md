---
title: "Install Savage 2"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Ginger297 on 2011-02-01
I was trying to download Savage 2 and i googled,which never really helps, but savage2 looks pretty badass and i kinda wanna try it out. So, i have no clue on how to use a terminal or what the hell that even is, so if someone could be kind and patient enough I'd love some help. Thanks!

---

### Post by pi3.1415926535... on 2011-02-01
Firstly, terminal, is an application that allows you to enter commands, which can be more efficient than using a graphical environment. For more about the terminal see [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal"). Beyond that, you have not specified what you are trying to accomplish, please post what your objective is.
Edit: I just Googled Savage2, the download appears to be a binary file (.bin).
Edit2: Installation Guide for Ubuntu (requires use of terminal) [http://naiux.wordpress.com/2009/03/29/savage-2-ubuntu-linux-installation-guide/]("http://naiux.wordpress.com/2009/03/29/savage-2-ubuntu-linux-installation-guide/")

---

### Post by Ginger297 on 2011-02-01
Oh, i forgot about that, my bad. What i want to do is install Savage 2, but when i install it all it is a document and i have no idea or clue on how to fix it.

---

### Post by khamil8686 on 2011-02-01
the game savage 2 you mean or did you mean something else?
if you meant the game 
first goto System > Administration > Hardware Drivers
and make sure that you have the recommended graphics driver activated, if not then activate it
then goto savage2.com and goto their downloads section and download either the 32 bit version or the 64 bit version of the game, 64 bit means you have a 64 bit processor, if you dont know then open a terminal by pressing alt+f2 and typing gnome-terminal and hitting enter, then enter the following code
```
cat /proc/cpuinfo
```
once you hit enter it will scroll a bunch of stuff, scroll up to the top and it should show you what processor you have, then goto newegg and look up your processor and the specs should tell you whether 64 bit is supported
once you have the file downloaded, if it downloaded to the desktop then open that gnome-terminal again and type
```
cp ~/Desktop
```
then type
```
sudo chmod +x *name of downloaded file here plus the .bin extension, Example: savage.bin*
```
it will ask for your password, go ahead and type in your password, the characters wont show as youre typing for security reasons, then type
```
sudo ./*name of downloaded file here*
```
and it should install, just look under your Applications menu for the program that installed

here is a link to a tutorial i just found but its for the 64 bit one, so if you have a 32bit processor just replace 64 bit with 32 bit when following that tutorial
[http://gwos.org/doku.php/guides:64bit:savage_2](http://gwos.org/doku.php/guides:64bit:savage_2)

oh and youre not a moron :P everyone starts somewhere, but next time when posting use a more descriptive title to your post :)
post back if problems!

---

### Post by Frogs Hair on 2011-02-01
I went to the Savage 2 website and it looks like the provide a bin file and found these instructions . I have not installed this file type before , but this is looks like a good step by step instruction.

[http://www.ehow.com/how_4578189_install-bin-file-ubuntu-linux.html](http://www.ehow.com/how_4578189_install-bin-file-ubuntu-linux.html)

I don't know anyone named Mo Ron ;)

---

### Post by Vaphell on 2011-02-01
too late :)

---

### Post by _outlawed_ on 2011-02-01
While not relative, I'd just like to say thanks. Was looking to try something new, and S2 does indeed look badass.

---

### Post by Ginger297 on 2011-02-01
the alt+f2 wont open a terminal?

---

### Post by Ginger297 on 2011-02-01
> **_outlawed_ said:**
> While not relative, I'd just like to say thanks. Was looking to try something new, and S2 does indeed look badass.

oh and ya S2 is pretty cool, something now from playing starcraft2 and other games, friend showed me today and i havent been able to find out how to play it D;

---

### Post by Frogs Hair on 2011-02-01
> **Ginger297 said:**
> the alt+f2 wont open a terminal?

Accessories > Terminal

---

### Post by phoenix122 on 2011-02-01
> **Vaphell said:**
> too late :)
agreed :-)

---

### Post by khamil8686 on 2011-02-01
if alt+f2 wont open a terminal goto Applications > System and terminal should be there somewhere, if not in system it should be in the list of files
and i third that it does look badass comment :)

---

### Post by Ginger297 on 2011-02-01
not finding anything...

---

### Post by _outlawed_ on 2011-02-01
> **Ginger297 said:**
> not finding anything...

Applications -> Accessories -> Terminal.

---

### Post by Ginger297 on 2011-02-01
i have vista, im not seeing a applications thing anywhere though...

---

### Post by phoenix122 on 2011-02-01
> **Ginger297 said:**
> i have vista, im not seeing a applications thing anywhere though...

try this....

[http://www.bigdownload.com/games/savage-2-a-tortured-soul/pc/savage-2-a-tortured-soul-client/](http://www.bigdownload.com/games/savage-2-a-tortured-soul/pc/savage-2-a-tortured-soul-client/)

---

### Post by Ginger297 on 2011-02-01
> **phoenix122 said:**
> try this....

[http://www.bigdownload.com/games/savage-2-a-tortured-soul/pc/savage-2-a-tortured-soul-client/](http://www.bigdownload.com/games/savage-2-a-tortured-soul/pc/savage-2-a-tortured-soul-client/)

ya... that's what i downloaded.

---

### Post by _outlawed_ on 2011-02-01
> **Ginger297 said:**
> i have vista, im not seeing a applications thing anywhere though...

Oh, assumed you were on Ubuntu. lol

---

### Post by Ginger297 on 2011-02-01
i kinda said earlier. i have no clue what im doing.

---

