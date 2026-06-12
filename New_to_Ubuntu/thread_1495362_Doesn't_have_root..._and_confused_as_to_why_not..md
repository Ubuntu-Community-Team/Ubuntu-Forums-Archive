---
title: "Doesn't have root... and confused as to why not."
date: 2010-05-28
forum: New to Ubuntu
---

### Post by obsidianangel on 2010-05-28
I downloaded and booted ubuntu. My system had window's XP and it is still there in a partition. I'm use to Unix so I hopped on the terminal and noticed something odd... I don't have superuser....I tried the old 'su' command and typed my password and it says "Authentication failure" so I tried a few different possible  passwords...no luck either.

I'm baffled to why I don't have superuser considering I downloaded it, and set up the id and password... 
My XP split does not have a password on it either. (not sure if that would affect it).
Any ideas on how to resolve this?

---

### Post by Elfy on 2010-05-28
Ubuntu uses sudo 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cariboo on 2010-05-28
The root account is disabled in Ubuntu, the preferred  method for doing administration task is to us sudo. More more info have a look [here]("https://help.ubuntu.com/community/RootSudo").

**Edit:** The peskie piskie beat me to it. :)

---

### Post by Jakiejake on 2010-05-28
Oh and welcome to Ubuntu/Forums

---

### Post by obsidianangel on 2010-05-28
Thanks guys... I feel silly for not noticing a command difference... too use to Unix... LOL! 
Any quick tricks on dealing with new excutable files that are being stubbern as hell? (Just downloaded wireshark and I cannot find its bin file...-_-) Mind you it is 2am here and I've been up since 2pm... lol! Got to love insommnia! 
And thanks for the warm welcome guys!  :biggrin:

---

### Post by Jakiejake on 2010-05-28
> **obsidianangel said:**
> Thanks guys... I feel silly for not noticing a command difference... too use to Unix... LOL! 
Any quick tricks on dealing with new excutable files that are being stubbern as hell? (Just downloaded wireshark and I cannot find its bin file...-_-) Mind you it is 2am here and I've been up since 2pm... lol! Got to love insommnia! 
And thanks for the warm welcome guys!  :biggrin:

Make sure you get it from the 'Ubuntu Package Manager'

---

### Post by louieb on 2010-05-28
> **obsidianangel said:**
> ...Any quick tricks on dealing with new excutable files that are being stubbern as hell? (Just downloaded wireshark and I cannot find its bin file...-_-) ...  :biggrin:

Guess you downloaded it with Firefox - default download dir is ~/Downloads - check edit>preferences>General Tab.

to run - cd to the directory containing the executable - then prefix the command with a ./
the ./ stands for the current directory. 
poor example 

```
cd ~/Downloads
./wireshark.bin   
```
or if root privileges are needed
```
sudo ./wireshark.bin

```

BTW: The easiest way to find and install software is to use the package manager.
Take a look at System>Administration>Synaptic

---

### Post by bredman on 2010-05-28
As a more traditional Unix user, I find the sudo command very annoying. If you prefer a more traditional su experience, try the command
sudo -i
which will place you into a super-user shell.

NOTE: This is not recommended for amateurs, sudo is there to protect you, and sudo -i removes some of this protection.

---

### Post by mkvnmtr on 2010-05-28
If you are not going to use the repositories to download programs for example you want an updated release just make sure you download a deb file. Then you can right click on it and the gdebi package manager will take care of it.

---

