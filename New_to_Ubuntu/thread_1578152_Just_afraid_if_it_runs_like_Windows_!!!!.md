---
title: "Just afraid if it runs like Windows !!?!!"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by mohammedhosen on 2010-09-20
i am a complete ubuntu " fresh meat " , migrating from windows
so...in windows i was afraid of using CMD " command line "...now in ubuntu " like i said above a new user " COMPLETELY TERRIFIED  of using the terminal  :(
MY ISSUE IS ... i entered this command in the terminal to update  " empathy " as stated in a forum ..." sudo apt-get update && sudo apt-get upgrade " ... so.. is it SAFE to close the terminal while upgrading ???  i know its a silly question but its importtant to me 
THANKS ...

---

### Post by syntek on 2010-09-20
NO. DONT CLOSE THE TERMINAL WINDOW!

The updates will run in the terminal, if you close the terminal window while it is processing the updates, you could potentially run into some problems, and you will most certainly not complete the updates.

However, if you prefer to run updates without using the terminal, simply go to System > Administration > Update Manager, it accomplishes the exact same thing through a GUI. You will find that many of the commands that are ran through the terminal can also be ran graphically, however it is usually much quicker to just run a command then point-n-click.. It's also a lot easier when trying to help someone on these forums to have them run a command or few through the terminal then to try to explain click here, select this, click on that, etc.. 

Oh yeah, and welcome to the community!

---

### Post by jarrah-95 on 2010-09-20
i completly get what you are saying about usind the terminal, but its something that when you learn, you wont want to be without. im not sure if you ran empathy or sudo apt-get update && sudo apt-get upgrade. but if it was empathy then you may as well open it from the applications menu in the top left. if it was sudo apt-get update && sudo apt-get upgrade then while it is running (text coming up on the screen ans you cant see the user@name:$ prompt at the bottum) then no do not close it as it is still running, if in dought hit the close button and it will tell you if it is still running.

FYI there are a few more commands to watch out for but the main one is sudo rm -rf / **_[SIZE="5"]never run this command[/SIZE]_** it will delete everything. but other than that all with the terminal is good.
hope this helped

---

### Post by Rasa1111 on 2010-09-20
not a silly question.
but dont close the terminal while it is working. 
Minimizing it is fine. 

also, 
You'll find that you hardly ever have to use the terminal if you dont want to.
 It is good to know and to learn...
but many people use ubuntu daily, without touching terminal. 

 but i always thought it was something to be feared..
then learned it is actually really cool, and not really anything to fear. lol

 good luck. 

 p.s.. it runs nothing like windows!
(if your windows experience was anything like my ten year stint) :lol:

 for me, it's like comparing apples and... well... rotten apples. :lol: sorry, had to.  <3

---

### Post by sikander3786 on 2010-09-20
> **mohammedhosen said:**
> i am a complete ubuntu " fresh meat " , migrating from windows
so...in windows i was afraid of using CMD " command line "...now in ubuntu " like i said above a new user " COMPLETELY TERRIFIED  of using the terminal  :(
MY ISSUE IS ... i entered this command in the terminal to update  " empathy " as stated in a forum ..." sudo apt-get update && sudo apt-get upgrade " ... so.. is it SAFE to close the terminal while upgrading ???  i know its a silly question but its importtant to me 
THANKS ...
Terminal has got the learning curve. You might start liking it and actually want to learn the command-line, but not now at least. Go with the GUIs for now. For updates use the Update Manager under System >>> Administration menu. For installation of other software, use Software Center under the Applications menu or Synaptic Package Manager under System >>> Administraion menu.

Never close a terminal until it returns to yourname@computername. Closing before that will actually cancel all the tasks going on in the terminal.

There are GUIs for most apps. You can use them for now. Later on when you start feeling comfortable, you can switch to the terminal and that also, if you want to.

If you mean by "Will it run like windows" that it will get infected and slow down as the time goes on, it will never. Safety assured.

Regards.

---

### Post by k33bz on 2010-09-20
> **jarrah-95 said:**
> 

FYI there are a few more commands to watch out for but the main one is sudo rm -rf / **_[SIZE="5"]never run this command[/SIZE]_** it will delete everything. but other than that all with the terminal is good.
hope this helped

I also want to add that if you encrypted your home file, DO NOT START DELETING THE CONTENTS OF YOUR ENCRYPTED FILE. Doing so will result in the same thing as sudo rm -rf. I made that mistake once. :|

---

### Post by mohammedhosen on 2010-09-20
thanks alot every one for answering me ...
about the terminal ... well..i started to use ubuntu  just to learn... i just want to learn it ... i am crazy a bout this...but all what iam afraid of is to " burn the machine as happens in windows for any tiny mistake " .. but ... i dont hate the terminal ... i just dont like to do things " like writing down commands " that i am not FULLY  aware of its consiquences...
THANKS ALOT ...REALLY APPRECIATE THIS... :)

---

### Post by k33bz on 2010-09-20
anytime you are not aware of what a certain command will do just type in command -h or man command 

Examples:
```
netstat -h
```
or
```
man netstat
```

Both will give you an idea of what the netstat command will do. man netstat will give you an in-depth idea though.

---

### Post by chewearn on 2010-09-20
As long as your computer don't have important data (priceless like pictures of your grandson, or the project report you need to submit tomorrow), don't be afraid to experiment with Ubuntu.

Really, if you mess up Ubuntu till unfixable, a reinstall is only about half an hour away.

And even if you have priceless data, please practice safe computing; back-up those data.

It is not like in Windows, where a reinstall is impossible unless you have a recovery partition or disc.  And even after reinstall, you might have to spend hours being annoyed because you need to re-activate Windows and all those proprietary software.

---

### Post by CaptainMark on 2010-09-20
+1 

my favourite ubuntu theory is "if it aint broke, you aint push it hard enough."

---

