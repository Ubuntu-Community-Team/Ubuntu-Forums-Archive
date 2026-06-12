---
title: "How to shut off system beep"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Terl on 2009-01-16
I have been unable to find the settings in Xubuntu to shut off the system beep.  I have tried all the sound settings I can find.  Is there a way to turn it off?  Thanks.

---

### Post by meatpan on 2009-01-16
> **Terl said:**
> I have been unable to find the settings in Xubuntu to shut off the system beep.  I have tried all the sound settings I can find.  Is there a way to turn it off?  Thanks.

Try using the command 'xset'.  Open a terminal and run 'xset -b off'.

---

### Post by Terl on 2009-01-16
Thank you, that did the trick.  I hate that stupid beep....in the middle of concentrating and <beep!>.  Mostly it is an annoyance as I have my own lappy at work to play with while other things are running/compiling-the beep annoys...

EDIT:  It turns it off for terminal, but not system wide.  Oh well...  I thought there would be a system-wide setting like Ubuntu has...

---

### Post by GenericGuy on 2009-01-16
add the following line to /etc/modprobe.d/blacklist:
```
blacklist pcspkr
```
I probably would ended up killing somebody if I didn't find this out somewhere :)

---

### Post by OrangeCrate on 2009-01-16
> **GenericGuy said:**
> add the following line to /etc/modprobe.d/blacklist:
```
blacklist pcspkr
```
I probably would ended up killing somebody if I didn't find this out somewhere :)

I confirm, that this is the only way I've been able to kill the system beep too.

:(

---

### Post by stchman on 2009-01-16
> **Terl said:**
> I have been unable to find the settings in Xubuntu to shut off the system beep.  I have tried all the sound settings I can find.  Is there a way to turn it off?  Thanks.

I believe under System--->Preferences--->Sounds there is a menu that will allow you to disable the system beep.

---

### Post by Terl on 2009-01-16
> **GenericGuy said:**
> add the following line to /etc/modprobe.d/blacklist:
```
blacklist pcspkr
```
I probably would ended up killing somebody if I didn't find this out somewhere :)

Thank you!!!!   This works like a charm.

---

### Post by OrangeCrate on 2009-01-16
> **stchman said:**
> I believe under System--->Preferences--->Sounds there is a menu that will allow you to disable the system beep.

So that others don't needlessly chase this as a solution, for Ubuntu, you're correct. This thread however, is regarding Xubuntu, and that option doesn't exist (unfortunately).

---

### Post by Clueless163 on 2009-03-31
> **GenericGuy said:**
> add the following line to /etc/modprobe.d/blacklist:
```
blacklist pcspkr
```
I probably would ended up killing somebody if I didn't find this out somewhere :)
 
 
call me stupid, but I added this line to the file but it says "can't open file to write"

---

### Post by Malalo on 2009-03-31
> **Clueless163 said:**
> call me stupid, but I added this line to the file but it says "can't open file to write"

You'll need to open the file with admin priviledges.

Type the following : 

```
gksudo gedit /etc/modprobe.d/blacklist
```

then add the line and save

---

### Post by Clueless163 on 2009-03-31
> **Malalo said:**
> You'll need to open the file with admin priviledges.
 
Type the following : 
 
```
gksudo gedit /etc/modprobe.d/blacklist
```
 
then add the line and save
 
Ok, I got the admin priviledge code in...I'm still not doing something right. Do I need to open the file and add the code or do it via terminal?

---

### Post by Malalo on 2009-03-31
After typing 

```
 gksudo gedit /etc/modprobe.d/blacklist
```

this will open the "gedit" text editor with the "blacklist" file.
At the bottom of the file, add this line :

```
blacklist pcspkr
```

then click "Save" then close.
Remember to leave the terminal window open until you close gedit.

---

### Post by Clueless163 on 2009-03-31
> **Malalo said:**
> After typing 
 
```
 gksudo gedit /etc/modprobe.d/blacklist
```
 
this will open the "gedit" text editor with the "blacklist" file.
At the bottom of the file, add this line :
 
```
blacklist pcspkr
```
 
then click "Save" then close.
Remember to leave the terminal window open until you close gedit.
 
When I typed the first line, nothing happened...I checked and rechecked the code, still nothing

---

### Post by Malalo on 2009-03-31
> **Clueless163 said:**
> When I typed the first line, nothing happened...I checked and rechecked the code, still nothing

Are you typing this in a terminal window ?
Try by removing "gk" :

```
sudo gedit /etc/modprobe.d/blacklist
```

it should then ask for the admin priviledge password within the terminal window.

---

### Post by Clueless163 on 2009-03-31
> **Malalo said:**
> Are you typing this in a terminal window ?
Try by removing "gk" :
 
```
sudo gedit /etc/modprobe.d/blacklist
```
 
it should then ask for the admin priviledge password within the terminal window.
 
 
Yes, I am typing in the terminal window..."sudo: gedit: command not found" is what it says typing that code in

---

### Post by Clueless163 on 2009-03-31
ok, I shut the laptop off and rebooted...it prompts for a password when I enter the code with a gksudo but nothing else comes up

---

### Post by Malalo on 2009-03-31
"gedit : command notfound".... that surprised me...

which version on Ubuntu are you using ?

---

### Post by Clueless163 on 2009-03-31
> **Malalo said:**
> "gedit : command notfound".... that surprised me...
 
which version on Ubuntu are you using ?
 
xubuntu 8.10

---

### Post by Malalo on 2009-03-31
Aha... my mistake, should've asked this first...

xubuntu's "gedit" equivalent is "mousepad" so try everything I suggested but replace "gedit" with "mousepad"

---

### Post by kukibird1 on 2009-03-31
For Xubuntu try gksudo mousepad /etc/modprobe.d/blacklist .

---

### Post by sisco311 on 2009-03-31
> **Clueless163 said:**
> ok, I shut the laptop off and rebooted...it prompts for a password when I enter the code with a gksudo but nothing else comes up

the default GUI text editor in Xubuntu is mousepad:
```
gksu mousepad /etc/modprobe.d/blacklist
```

or you can use a cli text editor (nano)
```
sudo nano /etc/modprobe.d/blacklist
```

press
Ctrl+o, Enter to save the file
Ctrl+x to exit
or Ctrl+x, y. Enter to save and exit

---

### Post by Clueless163 on 2009-03-31
> **Malalo said:**
> Aha... my mistake, should've asked this first...
 
xubuntu's "gedit" equivalent is "mousepad" so try everything I suggested but replace "gedit" with "mousepad"
 
> **kukibird1 said:**
> For Xubuntu try gksudo mousepad /etc/modprobe.d/blacklist .
 
 
wooohooo! Got the editor to pop up, I entered blacklist pcspkr and saved it. It still beeped when I powered it down, that normal that it would need a reboot?
 
Edit: Got the annoying system beeping noise turned off! sweetness! Thanks guys for being patient with me.

---

### Post by sisco311 on 2009-03-31
> **Clueless163 said:**
> wooohooo! Got the editor to pop up, I entered blacklist pcspkr and saved it. It still beeped when I powered it down, that normal that it would need a reboot?

you need to reboot or manually remove the module:
```
sudo modprobe -r pcspkr
```;)

---

### Post by Malalo on 2009-03-31
> Edit: Got the annoying system beeping noise turned off! sweetness! Thanks guys for being patient with me.

No problem, enjoy the silence ;)

---

### Post by Clueless163 on 2009-03-31
> **Malalo said:**
> No problem, enjoy the silence ;)
 
..and I will!  :popcorn:    Time to look into undervolting my laptop...anybody have experience with this?

---

### Post by unutbu on 2009-03-31
I have not tried this myself, but hopefully this will set you on the right path: (for undervolting)
[http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt](http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt)

---

### Post by jose187 on 2009-03-31
> **Clueless163 said:**
> Yes, I am typing in the terminal window..."sudo: gedit: command not found" is what it says typing that code in

copy the code from the browser, and then go to the terminal and paste it there. then press enter.
You should then be asked to type in your password.

---

