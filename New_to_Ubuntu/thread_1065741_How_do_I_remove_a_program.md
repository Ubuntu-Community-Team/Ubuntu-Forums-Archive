---
title: "How do I remove a program?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Jingle on 2009-02-10
Waaa this is starting to do my head in.  I installed thunderbird, and the webmail & hotmail add-ons but it still wouldn't connect to hotmail for me.  Fair enough, I want to remove thunderbird and possibly try again.

When I use the add/remove programs from the main menu it says something is dependant on Thunderbird and to use synaptic. When I use synaptic and search for thunderbird it doesn't find it, only two or three support packages !

grumble grumble...

So how can I remove thunderbird, I don't want to have to reinstall ubuntu or anything stupid.

---

### Post by SunnyRabbiera on 2009-02-10
strange that synaptic wont find it, what version of ubuntu are you running?

---

### Post by Jingle on 2009-02-10
I'm running 8.10 which i have just installed. The add/remove finds thunderbird no problems.

Here's a screen shot of synaptic in case I'm not using it properly.

I installed thunderbird buy using ```
sudo apt-get install mozilla-thunderbird
```
the terminal then suggested I add two others so I did ```
sudo apt-get install thunderbird-gnome-support latex-xft-fonts
```

Thunderbird then appeared nicely in my main menu (this is SO much better than farting about in windows). I messed about with it, probably entered the wrong settings and now I'd like to remove it and start again. 

Since I installed from the terminal instead of synaptic would that make a difference?

---

### Post by girishsasikumar on 2009-02-10
I suggest u take a look of this website before doing anything else
[http://webmail.mozdev.org/installation.html]("http://webmail.mozdev.org/installation.html")

I dont see any reason why Hotmail would not work with thunderbird
anyway if u want to uninstall
```
sudo apt-get *remove* mozilla-thunderbird
```

---

### Post by kostkon on 2009-02-10
Also use the search facility in *Synaptic* for an thorough search and not the quick-search one.

---

### Post by JK3mp on 2009-02-10
Are you sure your set to show all the repository's in synaptic?

---

### Post by stumbleUpon on 2009-02-10
> **Jingle said:**
> I messed about with it, probably entered the wrong settings and now I'd like to remove it and start again. 


If all you want to do is to change the settings in thunderbird, then delete the .mozilla-thunderbird/ folder in your home directory and then start thunderbird again. 

You will be asked to enter the settings again. No need to reinstall.

---

### Post by geirha on 2009-02-10
The search in synaptic may be case sensitive (not sure). Try searching with all lowercase letters "thunderbird".

---

### Post by mkvnmtr on 2009-02-10
I messed up trying to get connected to my accounts also the first time. Al you need to do to start over is delete the hidden file in home like the other poster said. This folder is also the one you want to save to move your addresses and settings to another machine.

---

### Post by Jingle on 2009-02-10
Thank you all, I've had a (careful) poke about in Synaptic and found it!  I think I'd unchecked some repositories for some silly reason, and using the full search makes a massive difference.

stumbleUpon:
I've uninstalled simply because I'm trying to get familiar with synaptic and the terminal.. I also really wanted to make sure I'm keeping my system clean and free of random bits of config and programs like windows gets!

I presume that .mozilla-thunderbird/ is the config folder for thunderbird? and is stored in my user directory rather than the program directory? (sorry I'm still used to the c:\program files from windows)

---

### Post by geirha on 2009-02-10
I believe it actually is .mozilla/thunderbird/, but yes, applications in ubuntu will store configuration in your home folder. The applications generally don't have permissions to store anything anywhere other than your home-folder and /tmp (for temporary files).

The package managers will never remove configuration (or any files at all) from your home folder. You'll need clean up your home-folder yourself.

---

