---
title: "compiz fuzion &quot;reflection&quot; messed up my ubuntu installation"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by faraz_k86 on 2010-04-11
Was messing around with the compiz options and i enabled "reflection" when I did that the system hung up and did not respond.. I had to do a hardware reset.. now the system wont log on.. when i enter my username it just hangs up again :/

help plz

---

### Post by J V on 2010-04-11
Compiz is crapped out: hit ctrl alt f1 at the login screen, login on the text terminal, find your compiz configuration files (No idea where they are) and delete them

The commands you want are cd, ls, rm

---

### Post by Doctor Mike on 2010-04-11
> **J V said:**
> Compiz is crapped out: hit ctrl alt f1 at the login screen, login on the text terminal, find your compiz configuration files (No idea where they are) and delete them

The commands you want are cd, ls, rmAren't you lucky you get 10% sleep. Original OP might want to look at video drivers.

---

### Post by faraz_k86 on 2010-04-11
so... what am i supposed to do again?

---

### Post by tom.swartz07 on 2010-04-11
> **faraz_k86 said:**
> so... what am i supposed to do again?

Ok- I just went through everything to see. 


This is going to be a bit of terminal work but it should fix it.

When you start up, hit CRTL+ALT+F1, it will change the screen to the terminal mode tty1. type in your login credentials. 


now, you should have a prompt.

Type this command:
```
cd $HOME/.gconf/apps/compiz/plugins/
```

now type 
```
ls
```
you should get a list of the folders there. You are looking for one that says "reflex"

If you see it, type
```
sudo rm -r reflex
```
type in your password and you should be all set!

restart the computer and see if it works!

---

### Post by faraz_k86 on 2010-04-12
thx for the detailed reply, Tom but i tried that and its not working..

i did as you said and reached /.gconf/apps/compiz/plugins/

now when i enter "ls" I get a single line response:

> %gconf.xml   [COLOR="Blue"]neg[/COLOR]

im on ubuntu 9.10 btw

---

### Post by tom.swartz07 on 2010-04-12
> **faraz_k86 said:**
> thx for the detailed reply, Tom but i tried that and its not working..

i did as you said and reached /.gconf/apps/compiz/plugins/

now when i enter "ls" I get a single line response:



im on ubuntu 9.10 btw

Try this first: 
```
sudo less %gconf.xml
``` and see what it outputs.
Give a synopsis or picture here



Hopefully we wont have to completely remove Compiz, get rid of the config files and start anew with your window manager, but it is a final step...
DONT DO THIS JUST YET, we might be able to get away without it!!!

Again, boot into your TTY1, as described above. Then use the following command 
```
sudo apt-get purge compizconfig-settings-manager python-compizconfig compiz compiz-plugins compiz-gnome
```
This will go through and remove compiz, CCSM, and your config files. 

Now, reboot your system and see if it is usable. You might be without window borders- to solve that, hit ALT+F2 and type
```
metacity --replace
``` to get the window buttons back.

After you get everything working, you could reinstall CCSM, and get all of the other bling back; just avoid the reflection plugin :P

---

### Post by faraz_k86 on 2010-04-12
Thankx again tom, im back on ubuntu and am glad that its working normally..

I did > sudo less %gconf.xml first but that gave me an output like > ~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~

and it kept on going.. i had to do a hardware reset.. so after that i tried purging compiz vis the command you gave and then reinstalled it with the same command.. 

working perfectly now.

Thanks again :)

---

### Post by tom.swartz07 on 2010-04-12
> **faraz_k86 said:**
> Thankx again tom, im back on ubuntu and am glad that its working normally..

I did  first but that gave me an output like 
and it kept on going.. i had to do a hardware reset.. so after that i tried purging compiz vis the command you gave and then reinstalled it with the same command.. 

working perfectly now.

Thanks again :)

Perfect!

Glad I could help!

Dont forget to mark the thread as SOLVED from the thread tools at the top of the page!


Have an awesome day!

---

