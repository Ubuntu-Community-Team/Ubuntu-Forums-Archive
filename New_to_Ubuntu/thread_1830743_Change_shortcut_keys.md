---
title: "Change shortcut keys"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by superg33k on 2011-08-22
Hi,

I would like to change the shortcut keys, such as alt+shift+up gives me the expose style window selector, and I would like to add a shortcut key for the workspace selector. I have checked in "keyboard shortcuts" however it doesn't have these listed. It says I can add command shortcuts there, but then I do not know the commands for these applications. Can you please help?

Also, as a side question. Why is the alt+shift+up shortcut for expose not in the "keyboard shortcuts" list? 

Thanks for your help.

---

### Post by superg33k on 2011-08-22
I am almost there. I got a package xdotool which allows me to enter command line commands for application switcher, and expose thing, but in keyboard shortcuts it doesn't allow me to enter the + symbol cuz it already has a meaning.

---

### Post by superg33k on 2011-08-22
Now I have no idea whats going on. I made a little wrapper script and it should just run 'xdotool key super+s' but instead it runs 'xdotool key super'. The wrapper script by itself runs fine. But when I try it from the "keyboard shortcuts" application it does it differently!

#!/bin/sh 
# This script is a wrapper so that this command can be used by the application
# keyboard shortcuts
/usr/bin/xdotool key super+s

---

### Post by androssofer on 2011-08-22
> **superg33k said:**
> Hi,

I would like to change the shortcut keys, such as alt+shift+up gives me the expose style window selector, and I would like to add a shortcut key for the workspace selector. I have checked in "keyboard shortcuts" however it doesn't have these listed. It says I can add command shortcuts there, but then I do not know the commands for these applications. Can you please help?

Also, as a side question. Why is the alt+shift+up shortcut for expose not in the "keyboard shortcuts" list? 

Thanks for your help.

i wanted to do this a while back, as was surprised how little info ther is for it! forgot to write my how to on it... prob wudda helped u.. alas. 

anyway i digress... install "CompizConfig settings manager" then open it up. then search "expo" then open up the options for expo. this is the workspace switcher.. look for the settings for "bindings" and u should see an option for keyboard, then u can change the keyboard shortcut(s) for opening workspace swticher etc.

then again in the config settings manager, search for "scale" this is the expose style window selecter. again look for "bindings" and select the keyboard shortcut u want. default is super-w (i think)

thats what u wer wanting?

---

### Post by superg33k on 2011-08-22
thanks. Thats exaclty as I wanted! 

Thanks very much! It all works how I want it to now.

---

### Post by androssofer on 2011-08-22
> **superg33k said:**
> thanks. Thats exaclty as I wanted! 

Thanks very much! It all works how I want it to now.

woo! scratch 1 up for the forums!

i'm adding these next random lines in so next time sum1 googles this, hopefully this thread comes up :-).

exposé on ubuntu

window changer shortcuts

expose like window switcher ubuntu

expose shortcuts ubuntu 

workspace switcher keyboard shortcuts

exposé is called scale on ubuntu

workspace switcher is called expo in compiz config

spaces shortcuts ubuntu

---

### Post by androssofer on 2011-08-22
ps: mark as solved. using the "thread tools" near the top of this page :-)

---

