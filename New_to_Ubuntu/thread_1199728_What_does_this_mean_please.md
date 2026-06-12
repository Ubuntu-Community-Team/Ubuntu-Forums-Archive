---
title: "What does this mean please?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by listerdl on 2009-06-29
Hi I am trying to follow a tutorial and it reads: 

While still in the vuze (name of the programme) directory in the terminal type:

sudo mv "azureus" "/usr/bin/azureus"
sudo mv "vuze" "/usr/bin/vuze"
cd ..
sudo mv "vuze" "/usr/share/vuze/"

Does this mean that I type the above in the terminal? Otherwise it refers to me having to type in the directory - but where is that?

Thanks - !

---

### Post by halitech on 2009-06-29
yes you would do it in the terminal but why not install the version in the repo?

---

### Post by listerdl on 2009-06-29
> **halitech said:**
> yes you would do it in the terminal but why not install the version in the repo? 

You know the odd thing is that I did write this code in the terminal and absolutely nothing happened.....no confirmation no nothing....

The situation I am now in is that it keeps telling me that:

Vuze wouldn't update, it always said that "The folder /usr/share/vuze" is not writable.

Then suddenly the programme updates itself and I have to restart Vuze and the process repeats itself in a loop!

Should I install and do the repo?

Thanks for all advice!!

---

### Post by halitech on 2009-06-29
unless there was an error you wouldn't see any output.

I would install from the repo. Either open Synaptic and search for vuze or in the terminal, do
```
sudo apt-get install vuze
```
enter your password (you won't see it) and it will install and you should have an item in the menu

---

### Post by listerdl on 2009-06-29
Thanks for the help....but do you think I ought to uninstall my previous attempts and if so what is the best way to do that? Thanks!!!

---

### Post by halitech on 2009-06-29
might be a good idea. I can't remember the way to do it from the command line but you can open nautilus as sudo and delete just that folder

```
gksudo nautilus
```

---

### Post by listerdl on 2009-06-29
Thanks I really appreciate your help. So I need to open Nautilius and delete anythig that says Vuze I guess.....thanks.

Gosh - why dont people tell you to simply just install like you did - there are lots of tutorials that seem to confuse rather than help!!

---

### Post by halitech on 2009-06-29
just go to "/usr/bin/" and delete the vuze folder

the only downside to the versions of apps in the repo is they could be a version or 2 behind the latest release that the developer has released but this way, it will stay updated and has been tested to work with the version of Ubuntu you have installed.

---

### Post by listerdl on 2009-06-29
ah - and I think that you have hit the problem there. The issue is that the program is unable to update itself as per this advice:

"To install Vuze 4.0.0.4 to Ubuntu Intrepid, I had to change the ownership of /usr/share/vuze to username, using

sudo chown yourusername:yourusername /usr/share/vuze

Vuze wouldn't update, it always said that "The folder /usr/share/vuze" is not writable.

Thing is that when I tried to do this in the terminal "sudo chown yourusername:yourusername /usr/share/vuze" - it just gave me a bad command - did i do wrong there?

THANKS I REALLY APPRECIATE YOUR TIME

---

### Post by halitech on 2009-06-29
when you tried that, did you change yourusername:yourusername to your actual username?

---

### Post by jerome1232 on 2009-06-29
Either actually type your username or you can use this

```
sudo chown $USER:$USER /usr/share/vuze
```

---

### Post by listerdl on 2009-06-29
yes i used my username - thanks for advice jerome1232 - does that act as a sort of generic username that applies to all programes?

---

### Post by halitech on 2009-06-29
if you changed it to your proper username then I'm not sure why it would have failed

---

### Post by listerdl on 2009-06-29
AH - I just realised - I never added the dollar sign - that must have been the problem - do I need to add the $ sign - (I would try now but am not near the computer in questions!!)

---

### Post by halitech on 2009-06-29
$USER will read what user you are currently logged in as and replace $USER with your username

---

### Post by jerome1232 on 2009-06-29
> **listerdl said:**
> yes i used my username - thanks for advice jerome1232 - does that act as a sort of generic username that applies to all programes?

It's a system variable that represents the current user's name.

ie if you typed "echo $USER" it would return your user's name.

You only need the dollar sign if your using a variable as in my example.

---

### Post by listerdl on 2009-06-29
ok great thanks for the tip I will try that later. Thanks again. Appreciate it.

---

