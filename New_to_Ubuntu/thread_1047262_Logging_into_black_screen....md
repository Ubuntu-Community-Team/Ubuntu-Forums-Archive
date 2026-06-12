---
title: "Logging into black screen...?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by ubalderdash on 2009-01-22
Today I turned on my computer and instead of loading normally it went to a black screen with plain text asking for my log-in and then my password. This completed successfully I am left with the terminal type message "user@user-desktop:~$" followed by a flashing cursor.
Can anyone tell me the magic code that might get me back to my normal world of ubuntu?

---

### Post by jarbo on 2009-01-22
I am not THE expert  on this, but try the command "exit"...

---

### Post by ET! on 2009-01-22
try the gdm command as the root....it is the graphical desktop manager

---

### Post by ubalderdash on 2009-01-22
Thanks guys, but "exit" only takes me back to the login command and the "gdm as root" command is not recognised.

---

### Post by ET! on 2009-01-22
gdm as root is not a command....it means you have to type "gdm" as the root...here is how

type 

sudo su

type the password when asked

then type

gdm

---

### Post by XanTrax on 2009-01-22
> **ET! said:**
> gdm as root is not a command....it means you have to type "gdm" as the root...here is how

type 

sudo su

type the password when asked

then type

gdm

This is more or less correct.  Instead, type this:

```

sudo su -
gdm &

```

with the & at the end of gdm it will load the gdm, run it as a daemon, and go right to the tty running the gdm (usually ctrl+alt+f7 or f8)

---

### Post by ubalderdash on 2009-01-22
After following your instructions the screen tells me that gdm is already running and gives me a unique option of abandonning

---

### Post by ubalderdash on 2009-01-22
I've run the command again with the "&" symbol and the result is a black screen with a cursor but no text..

---

### Post by XanTrax on 2009-01-22
Ok, first try typing these at the :

```
user@user-desktop:~$
```

screen

```

sudo su -
killall gdm
gdm &

```

Please post the output of the command.

If that does not work then please type these commands where you see the

```
user@user-desktop:~$
```

as you stated above.


Type these in order and copy and paste the output of EACH of the commands:

```

sudo apt-get install gdm
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure ubuntu-desktop

```

Remember, type one command and then copy and paste the output.  Do that for each command.

Ultimately, if all of this does not work, finally try pressing

control+alt+f7

and see what happens.

---

### Post by ubalderdash on 2009-01-22
Please be patient ! I'm having to retransmit these commandes by phone as without the computer I cannot communicate with the forum. 

In your commands you use multiple lines but as the only way for me to return to a new line is to hit "Enter" I am thus activating each line command in turn. Is this correct? Please note also that I have no way of copying and pasting these commands.

I'll get back to you soon as your instructions have been accomplished.

---

### Post by DM was on fire! on 2009-01-22
> **ubalderdash said:**
> In your commands you use multiple lines but as the only way for me to return to a new line is to hit "Enter" I am thus activating each line command in turn. Is this correct? Please note also that I have no way of copying and pasting these commands.

It is.
For instance, you would type *sudo apt-get install gdm*, and then wait for the GDM to completely install. Then ubuntu-desktop, et cetera. :)
It's going to take some patience to do it all, but it might be the only fix right now.

---

### Post by XanTrax on 2009-01-22
> **ubalderdash said:**
> Please be patient ! I'm having to retransmit these commandes by phone as without the computer I cannot communicate with the forum. 

In your commands you use multiple lines but as the only way for me to return to a new line is to hit "Enter" I am thus activating each line command in turn. Is this correct? Please note also that I have no way of copying and pasting these commands.

I'll get back to you soon as your instructions have been accomplished.

Alright, my apologies.  If you can not copy and paste it then please be as specific as you can describing what happens after each command issue.  Read what is on the screen after you issue the command and try to put it in your own words.


If the 

```

sudo apt-get install gdm
sudo apt-get install ubuntu-desktop

```

Says, in short terminology, that it is already installed and newest and does NOTHING then issue these commands...


```

sudo apt-get install --reinstall gdm
sudo apt-get install --reinstall ubuntu-desktop

```

---

### Post by ubalderdash on 2009-01-22
Thanks guys, I'm having to leave for work now and won't be back before Saturday. I will then try your latest suggestions and let you know how I get on. 

I did work through Xantrax's advice and the messages that came back all seemed to be positve suggesting that all was already installed, up to date and, curiously, working correctly. But I still have my black screen with the terminal screen type prompt.

---

