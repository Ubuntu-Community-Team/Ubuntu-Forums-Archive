---
title: "Please, Help"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by PhilDawg on 2009-09-24
Hello to everyone,

I just recently started using Ubuntu and I am completely lost with mostly everything. First off, when I go to log in, It says my password or username is incorrect, and when I went to make a new one...I found out I have no idea how to. I went into the options menu and I don't see anything of that nature, so I'm lost with that.

Also, I downloaded IcedTea so I could play Java games and Ialso downloaded a few other programs, the only thing is when it seems like I don't know how to install them from the Terminal. Can somebody please help me out? I would greatly appreciate it.

Thanks in advance,

--Phil.

---

### Post by credobyte on 2009-09-24
Recover your password: [http://ubuntuforums.org/showthread.php?t=3609](http://ubuntuforums.org/showthread.php?t=3609)

Install Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by Goveynetcom on 2009-09-24
Well to make a new profile you need to the master password. As for the terminal stuff, I am just as confused as you...

---

### Post by ~sHyLoCk~ on 2009-09-24
Hello and welcome Phil!

Are you sure you are providing the right username and password which you gave during install? Do check for caps lock. Also, there is a package manager called Synaptic which you will find in System->Administration, you can search and browse through that and install whatever you need. 
Hope this helps.

---

### Post by PhilDawg on 2009-09-24
Also, I forgot to tell you guys I'm on a PS3.

---

### Post by nmccrina on 2009-09-24
Yah, 99% of the time you aren't going to download programs to install off teh interwebs. Instead, most stuff you need can be installed from Ubuntu's very own repositories. I would recommend using Synaptic to begin with, it's a GUI kinda sorta like the ADD/REMOVE programs in Windows. You can find it at System->Administration->Synaptic

Oh dear, Shylock beat me to it...

---

### Post by Goveynetcom on 2009-09-24
Does the PS3 Ubuntu run differently than the normal setup?

---

### Post by nmccrina on 2009-09-24
> **PhilDawg said:**
> Also, I forgot to tell you guys I'm on a PS3.

Nice; I've always thought that would be a cool thing to do but didn't have the *shekels* for the hardware...:(

Can you use a mouse and keyboard with that, or is it all controller? That probably shows how little I know about the PS3, lol

---

### Post by QIII on 2009-09-24
If you install Java (which really is the way to go.  Nothing like the real thing.) don't forget  

```
sudo apt-get install sun-java6-bin
```

Then make sure that Sun's Java is the one that will be used

```
sudo update-java-alternatives -s java-6-sun
```

Then, to check to see you are using Sun

```
java -version
```

---

### Post by PhilDawg on 2009-09-25
I'm still lost on the whole password and login thing. Is it different on a pc than a ps3?

---

### Post by credobyte on 2009-09-25
> **PhilDawg said:**
> I'm still lost on the whole password and login thing. Is it different on a pc than a ps3?

Umh, well .. PS3 doesn't have ESC key ? :D

---

### Post by PhilDawg on 2009-09-25
I did it, thanks. No need for the sarcasm though bro.

---

### Post by credobyte on 2009-09-25
> **PhilDawg said:**
> I did it, thanks. No need for the sarcasm though bro.

Simply, you should ask it to yourself, as you are the one who uses it on PS3 :) 
Google told me that they are pretty much the same ( if not even equal ), so .. everything depends on your peripherals ( keyboard, joystick, etc. ).

---

### Post by PhilDawg on 2009-09-25
No harm done man, I'm just frustrated. One more question? It says I'm not on the sudo files or something like that when I go to the terminal, is there any way to fix that?? I'm just frustrated with this thing already...

---

### Post by credobyte on 2009-09-25
> **PhilDawg said:**
> No harm done man, I'm just frustrated. One more question? It says I'm not on the sudo files or something like that when I go to the terminal, is there any way to fix that?? I'm just frustrated with this thing already...

Well, by default, only your main username will be in sudoers file. 
Check this thread ( your questions have been already answered ): [http://ubuntuforums.org/showthread.php?t=9890](http://ubuntuforums.org/showthread.php?t=9890) ;)

---

### Post by PhilDawg on 2009-09-25
I looked at that page and I'm still confused...this is my first time using this program, so I really need things in layman terms. this sudo user file thing is pissing me off..

---

### Post by Terry of Astoria on 2009-09-25
It's a bit of a learning curve, but you will be surprised at how much you can do . . .
The PS3 is an awesome machine. There is a lot of processing power in there. I bet you can do stuff fast with it. . .
   Well, do take a bit of time to figure this out. You'll be glad you did. Thing to do is read those above-linked pages about sudo and stuff. You're forced to. It seems simple to me right now, although it's hard to explain all at once . . . 
   To reset your password, reboot, choose recovery mode from the GRUB menu, and then issue the following command:
```
passwd username
```
where username is your username
After you have your password sorted, you'll be able to move forward.

---

### Post by Terry of Astoria on 2009-09-25
This thread looks promising for fixing the problem of not being on the sudoers list . . .
[http://ubuntuforums.org/showthread.php?t=162867](http://ubuntuforums.org/showthread.php?t=162867)

---

### Post by PhilDawg on 2009-09-25
Thanks. The problem I'm having is, It seems like I am completely shut off from everything. When I go to anything it says I do not have permission..I'm just gonna give up on this.

--Phil.

---

