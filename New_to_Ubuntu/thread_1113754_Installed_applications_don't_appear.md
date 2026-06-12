---
title: "Installed applications don't appear"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Haruki-kun on 2009-04-02
I downloaded Festival Speech Synthesizer using synaptic, but when it was done installing, it wouldn't show in the menu. It's something that has happened with quite a few applications in the past.

Where did it go? How can I find it?

---

### Post by linuxuser21 on 2009-04-02
This has happened to me.  If I absolutely cannot find it I usually just get rid of it by "sudo apt-get remove WHATEVER".

---

### Post by Haruki-kun on 2009-04-02
> **linuxuser21 said:**
> This has happened to me.  If I absolutely cannot find it I usually just get rid of it by "sudo apt-get remove WHATEVER".

Thanks, but... I sorta really need it to get working...

---

### Post by FlatBlackIan on 2009-04-02
Ive had this problem as well.  What I have done, is open a terminal and type > help /program name
The programs help file can usually tell you how to start the application manually.

Im sure there is a more effective/better way to do it, but I are super noob to linux.

Is there a guru out the willing to school us.....

Please?

---

### Post by lindsay7 on 2009-04-02
Go to Synatics Package manager and find the program that you are looking for.  Right click on it and click on properties, go to the tab "installed files" and open it. You can see where the files are installed. Go there and find the file that starts the program.  You can then right click on applications on the menu bar and click on "edit menu" pick a place where you want to locate the program. click on "new item" and fill in the boxes with the program location and the start file.

---

### Post by linuxuser21 on 2009-04-02
> **FlatBlackIan said:**
> but I are super noob to linux.

That sentence alone made me laugh!  Mine grammer be ungood at sometimes to.  Lolz.  Sorry, had to throw that out there.
I don't know of any easier way than the way you said though.

---

### Post by _Purple_ on 2009-04-02
Type the following in terminal for manual:

```
man festival
```

You can start festival in command line by typing:

```
festival
```

There are many front-end clients which you can use for GUI.

---

### Post by pieisgood4589 on 2009-04-02
You could also simply try to type in and run the program name through terminal, it works more times than not.

---

### Post by egalvan on 2009-04-02
Did you get this working?

I installed this program, 
and it runs from the terminal...

```
festival
```


typing
```
man festival
```
gives some documentation

if you type help while the program is running,
it also gives some help..

The syntax is VERY picky....

you need to type EXACTLY as shown, including the capitalization...
for example, typing :

SayText "hello"

works....
this does not :

saytext "hello"


also, I have yet to get it to quit, or end :)
I just shut down the terminal window

ErnestG

Formerly of Puebla & Cholula

---

