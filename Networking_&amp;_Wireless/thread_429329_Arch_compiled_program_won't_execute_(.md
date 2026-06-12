---
title: "Arch compiled program won't execute? :("
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by scottylans on 2007-05-01
EDIT: whole thing was badly worded.




Hi guys,

I can't 'run' a program I've compiled?
I type the name of it and nothing happens.
If I type the start of the  name and try to tab complete it, it still won't work

I am fairly new to linux but I was under the impression when you download a tar file, you extract it (zxvf or zxcf, I can't recall)
Then once it's extracted you sudo make and sudo make install (or make / make install)

I'm trying to get aircrack-ptw woring and the 'executable' is coming up green in the shell when I do an ls 
WTF have I missed? :( I'm dopey, sorry

Followed the instructions here too!?
[http://www.wirelessdefence.org/Contents/Aircrack-ptw.htm](http://www.wirelessdefence.org/Contents/Aircrack-ptw.htm)[http://www.wirelessdefence.org/Contents/Aircrack-ptw.htm]("http://www.wirelessdefence.org/Contents/Aircrack-ptw.htm")

I didn't receive any errors when following those instructions either.

Any advice would be really appreciated.

---

### Post by scottylans on 2007-05-01
No one? :(

---

### Post by scottylans on 2007-05-02
Sorry to bump again, I've re-written it so it might make some more sense.

---

### Post by scottylans on 2007-05-02
Here is a screenshot of the problem!
[http://members.iinet.net.au/~scottylans/screen01.png](http://members.iinet.net.au/~scottylans/screen01.png)

---

### Post by chili555 on 2007-05-02
The HOWTO you referred us to suggests the command is ```
**./**aircrack-ptw
```See steps 5 and 6. Put that little  ./ in front and see if it works.

---

### Post by scottylans on 2007-05-02
> **chili555 said:**
> The HOWTO you referred us to suggests the command is ```
**./**aircrack-ptw
```See steps 5 and 6. Put that little  ./ in front and see if it works.

I'm surprised to say that works?!
Is there any way that I can make it so it works like a normal executable though? I just type 'airc' and  hit tab?

I can't even type airc(tab) in the same directory that it's located in!?

---

### Post by chili555 on 2007-05-02
> I'm surprised to say that works?!Surprised? Hey, 800+ beans has got to be worth something!

There might be some way to convert it to a "normal" executable, but I don't know it; maybe a 2,000 beaner will jump in!

---

### Post by jfinkels on 2007-05-02
You can create a link to it in your /usr/bin directory. Type this command:
```

sudo ln -s ~/aircrack-ptw /usr/bin/aircrack-ptw

```
Just replace "~/aircrack-ptw" with the actual location of the file on your system :D

EDIT: 

Let me explain what's going on here.

Typing "./commandname" will run a program whose executable is in your current directory.

To run a program without the "./" part, it has to be located in a directory that is in your $PATH environment variable. You can view the contents of your path by typing the following command: ```
echo $PATH
```

You can also put a 'symbolic link' to the actual location of the file in a directory in your path. That's what the command I gave you above does.

---

### Post by scottylans on 2007-05-02
> **jfinkels said:**
> You can create a link to it in your /usr/bin directory. Type this command:
```

sudo ln -s ~/aircrack-ptw /usr/bin/aircrack-ptw

```
Just replace "~/aircrack-ptw" with the actual location of the file on your system :D

EDIT: 

Let me explain what's going on here.

Typing "./commandname" will run a program whose executable is in your current directory.

To run a program without the "./" part, it has to be located in a directory that is in your $PATH environment variable. You can view the contents of your path by typing the following command: ```
echo $PATH
```

You can also put a 'symbolic link' to the actual location of the file in a directory in your path. That's what the command I gave you above does.



Good god I'm shocked confused and dazed!  You must be joking!
I like Ubuntu but that has to be one of the most $!%^ING ridiculous things I've ever heard.

Let me get this straight.......

I'm an old dos guy.
I understand the theory of how a path works and what it does, it lets you run files in select directories even if you're not in them   - makes sense!
HOWEVER if you're in a directory to an application and it's not in the path, you can still run that application because you happen to be in the directory for it, that's totally darn logical to me.

You're saying that Ubuntu won't execture an application I'm _IN_ the directory for, unless i put ./ infront of it or add it to the path?   That is _truely_ bloody stupid!

Disclaimer: I hope I'm wrong, because I happen to like Ubuntu and I happen to like linux, sometimes people bash it for silly things and other times people bash it for things which it really does which is stupid but in this case, if I'm right, good lord is that really really REALLY illogical!

P.S Your help is appreciated, despite my rant!

---

### Post by jfinkels on 2007-05-03
Ummm, I guess that's just the way it is. I can't tell you why or how, because I don't know. Using "./" to represent the current directory is a convention among other systems and languages. Doesn't seem like that much more of a hassle to me. Remember, Linux is not Windows (or DOS)!

I assume you understand the idea behind relative paths? "." means the current directory and ".." means the directory containing the current one. That's why it looks like "./command". To execute a command that is in the directory above the current one, you could run "../command".

I suppose that typing "./command" is more specific, so in case you had an executable in your path with the same name, typing just "command" would execute the one in the path, and typing "./command" would execute the one in the current directory.

---

### Post by scottylans on 2007-05-03
> **jfinkels said:**
> Ummm, I guess that's just the way it is. I can't tell you why or how, because I don't know. Using "./" to represent the current directory is a convention among other systems and languages. Doesn't seem like that much more of a hassle to me. Remember, Linux is not Windows (or DOS)!

I assume you understand the idea behind relative paths? "." means the current directory and ".." means the directory containing the current one. That's why it looks like "./command". To execute a command that is in the directory above the current one, you could run "../command".

I suppose that typing "./command" is more specific, so in case you had an executable in your path with the same name, typing just "command" would execute the one in the path, and typing "./command" would execute the one in the current directory.

I now understand what is happening and yes I understand .. and .   - I see what it means and can now work within these guidelines, I do however find them illogical  - I realise linux does not = dos but, I dunno just seems straight forward to me.

---

### Post by jfinkels on 2007-05-03
> **scottylans said:**
> I now understand what is happening and yes I understand .. and .   - I see what it means and can now work within these guidelines, I do however find them illogical  - I realise linux does not = dos but, I dunno just seems straight forward to me.

Different strokes for different folks :D

---

