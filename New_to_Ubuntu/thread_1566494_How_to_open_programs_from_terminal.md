---
title: "How to open programs from terminal?"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by malenkylizards on 2010-09-02
My only Linux machine is an EeePC running UNR 10.04.1 LTS.  I just discovered how to open a terminal without using the mouse, and would like to work out how to use this to take my fingers off the mousepad even more.

So how can I use the terminal to start up programs?  I am guessing there's a good bit of knowledge I need to have about my filesystem...I don't know where, for instance, the chromium executable exists in my filespace.  I thought it might work to just type 'open chromium-browser' when in the root directory, but I get the error message 'Couldn't get a file descriptor referring to the console.'

Am I missing an argument, or is this because I'm not opening it from the right location?  Is it none of the above, or all of the above plus other stuff?

---

### Post by Calash on 2010-09-02
For basic applications it is just a matter of typing the name.  If you are not sure of the name you can type the first few letters and press the tab button and it will show a list of commands.

So all you need for your example is 

```

chromium-browser

```

---

### Post by diablo75 on 2010-09-02
Pressing ALT-F2 will bring up a command launcher, which is similar to the "Run" prompt you'd get in Windows if you hit WindowsButton + R, or clicked Start>Run in XP.  Just type your command in and click OK.

---

### Post by oldos2er on 2010-09-02
> **malenkylizards said:**
> So how can I use the terminal to start up programs?  I am guessing there's a good bit of knowledge I need to have about my filesystem...I don't know where, for instance, the chromium executable exists in my filespace.  I thought it might work to just type 'open chromium-browser' when in the root directory, but I get the error message 'Couldn't get a file descriptor referring to the console.'


Leave out the 'open', just type the name of the program you want, i.e. 'chromium-browser'.

---

