---
title: "How to get Ubuntu Software Centre ?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by ESDEEM on 2011-04-19
I've recently install [Ubuntu 10.04 "Lucid Lynx" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso")  14MB(64-bit)
Now I'm manually installing other softwares(vlc,alsa .etc)....
So I want to install Ubuntu Software Center....
Pls tell me how to install it on terminal...
I need an apt-get command.......

Waiting
thanks !

---

### Post by jtarin on 2011-04-19
You should be able to find the "Software Center" in your Main Menu. It is installed there by default.

---

### Post by ESDEEM on 2011-04-19
> **jtarin said:**
> You should be able to fine the "Software Center" in your Main Menu. It is installed by default.
recently I have only three options on the main menu..I'm manually setting things....

---

### Post by jtarin on 2011-04-19
> **ESDEEM said:**
> recently I have only three options on the main menu..I'm manually setting things....
If you have a main menu you have more than three options....what three options do you see? It should be under Applications.

---

### Post by Joe of loath on 2011-04-19
How about sudo apt-get install ubuntu-software-center? ;)

Or install synaptic and search for it in there.

---

### Post by mörgæs on 2011-04-19
I would recommend Synaptic in stead. Fast and bug-free, unlike Software Centre.

---

### Post by DogMatix on 2011-04-19
If it is pre-installed

```
software-center
```

would launch it.

---

### Post by yetiman64 on 2011-04-19
> **ESDEEM said:**
> I've recently install [Ubuntu 10.04 "Lucid Lynx" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso")  14MB(64-bit)
Now I'm manually installing other softwares(vlc,alsa .etc)....
So I want to install Ubuntu Software Center....
Pls tell me how to install it on terminal...
I need an apt-get command.......

Waiting
thanks !

> **jtarin said:**
> If you have a main menu you have more than three options....what three options do you see? It should be under Applications.

@ jtarin, the OP has used the minimal installer, only 14 MB compared to roughly 690 MB for a normal installer, very likely it is not installed by default.

@ OP, Joe of loath seems to have the good idea with regard to install Synaptic 1st, then use it to search for and install Software center if you still need it (Synaptic will often do a better job than software center, but it takes a bit more to learn it. It is a very powerful tool for what it does).

---

### Post by jtarin on 2011-04-19
> **yetiman64 said:**
> @ jtarin, the OP has used the minimal installer, only 14 MB compared to roughly 690 MB for a normal installer, very likely it is not installed by default.

@ OP, Joe of loath seems to have the good idea with regard to install Synaptic 1st, then use it to search for and install Software center if you still need it (Synaptic will often do a better job than software center, but it takes a bit more to learn it. It is a very powerful tool for what it does).
Your right.....missed the minimal install note.:P Synaptic is the way to go for your software. Gives a graphic frontend to apt and much better for beginners and experts alike.

---

### Post by yetiman64 on 2011-04-19
Don't worry jtarin, Being a bit on the slow side today I just realized the OP may need to install a Desktop Environment to install USC or Synaptic. Don't know for sure from the thread if the OP has yet. Hope so :). Then again if vlc is installed ?
I've never used a minimal install myself but plan to experiment soon.

@ OP, I've heard good reports here on occasion about people using the "perfectminimal" script to build a system from installers like you have used. You may want to have a look at it, if so it is here, [http://www.andyduffell.com/perfectminimal](http://www.andyduffell.com/perfectminimal) hope it helps.

---

### Post by mörgæs on 2011-04-19
And the explanation for Perfectminimal:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

It is not 'perfect', but a really good script. I use it for my installs.

---

### Post by ESDEEM on 2011-04-19
It says.....when I try 
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

---

### Post by ESDEEM on 2011-04-19
> **mörgæs said:**
> And the explanation for Perfectminimal:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

It is not 'perfect', but a really good script. I use it for my installs.
that scrip is really good but I want something like software centre as i am a newbie... :)

Edited :It seems its not that much perfect...I cant see any software it installed (skype.etc )

---

### Post by mörgæs on 2011-04-19
> **ESDEEM said:**
> but I want something like software centre as i am a newbie.

Did you try Synaptic before making that decision, or did you just decide?

Did you reboot the machine after running the script?

---

### Post by ESDEEM on 2011-04-19
> **mörgæs said:**
> Did you try Synaptic before making that decision, or did you just decide?

Did you reboot the machine after running the script?
yea i rebooted but no changes... :(
there's synaptic pakage manager but when I open it,it says.....
[PHP]]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/PHP]Anyway to install synaptic again or fix the "dpkg" thing...
 thanks in advance.......
PS : I like software Centre cuz its simple and easy to  use....

---

### Post by Elfy on 2011-04-19
You need to run the dpkg command.

---

### Post by ESDEEM on 2011-04-20
> **forestpiskie said:**
> You need to run the dpkg command.
Where and how....?
This appears in the terminal.....
:?

---

### Post by ESDEEM on 2011-04-20
I installed Synaptc again...thinks its woks....
thanks everybody for the help and suggestions....
thanks a lot....
[SOLVED]

---

### Post by allinal on 2011-08-18
go to administration instead you'll find synaptic package manager and search directly software centre

---

### Post by scruffyeagle on 2011-08-18
> **ESDEEM said:**
> yea i rebooted but no changes... :(
there's synaptic pakage manager but when I open it,it says.....
[PHP]]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/PHP]Anyway to install synaptic again or fix the "dpkg" thing...
 thanks in advance.......
PS : I like software Centre cuz its simple and easy to  use....

The error message told you exactly what you need to do; i.e., do exactly what it said. After seeing the error message, at the command prompt, type in precisely the recommended command:
```
sudo dpkg --configure -a
```

Is that difficult?

---

