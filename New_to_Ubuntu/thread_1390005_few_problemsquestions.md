---
title: "few problems/questions"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by cry8wolf9 on 2010-01-25
Problems


[COLOR=Red]SOLVED[/COLOR]   1) ubuntu software center seems to be stuck in "in progress" (the attached image is what i mean if it helps

[COLOR=Red]SOLVED[/COLOR]   2) cant use apt-get i think its linked to #1 i keep getting this when using apt get 
```

  sudo apt-get install mencoder ffmpeg mplayer vlc
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

[COLOR=YellowGreen]
[COLOR=Lime]STILL NEED HELP[/COLOR]  [/COLOR]3) sound seems weak idk if theres anything i can do for this though the music i ported from windows before i put ubuntu seems much lower in volume and so does online videos (and yes i did turn the sound up in system::preferences::sound)


Questions

 [COLOR=Red]SOLVED[/COLOR] 1) when i had windows because of my video editing/watching i had needed this 
[http://www.free-codecs.com/download/K_Lite_Mega_Codec_Pack.htm](http://www.free-codecs.com/download/K_Lite_Mega_Codec_Pack.htm)
is there a ubuntu equivalent? or is it already installed and not enabled?
[COLOR=YellowGreen]
[COLOR=Lime]STILL NEED HELP[/COLOR][/COLOR]  2) is there a way to disable the use of passwords on certain users?

---

### Post by Cheezespread on 2010-01-25
For the point **2** , are you installing any other apps through another terminal window or Synaptic  alongside the one you put in codes? ( or even an update manager woring maybe - not sure of this )

> **cry8wolf9 said:**
> Problems


1) when i had windows because of my video editing/watching i had needed this 
[http://www.free-codecs.com/download/K_Lite_Mega_Codec_Pack.htm](http://www.free-codecs.com/download/K_Lite_Mega_Codec_Pack.htm)
is there a ubuntu equivalent? or is it already installed and not enabled?



I believe vlc handles most of the codecs effectively. Or else , you will be intimated once you need a specific codec or plugin.

---

### Post by Paqman on 2010-01-25
> **cry8wolf9 said:**
> cant use apt-get i think its linked to #1

It is indeed. You'll need to shut Software Centre before you can access the package manager through another tool. If it won't shut, hit Alt-F2, type ```
xkill
``` and click on it.

---

### Post by theozzlives on 2010-01-25
I believe you need to run ```
sudo dpkg --configure -a
```

As far as codecs, the only thing I've needed is ubuntu-restricted-extras ```
sudo apt-get install ubuntu-restricted-extras
```and the stuff [here]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by cry8wolf9 on 2010-01-25
> **Paqman said:**
> It is indeed. You'll need to shut Software Centre before you can access the package manager through another tool. If it won't shut, hit Alt-F2, type ```
xkill
``` and click on it.
ok did that now im getting 
```

@winterfresh:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


```

---

### Post by Paqman on 2010-01-25
If you've got nothing else that's using the package manager open (eg: gdebi, update manager, etc) then that's probably because it still thinks Software Centre is running. A reboot should sort you out.

---

### Post by cry8wolf9 on 2010-01-25
[COLOR=Red]edit: nvm seems to have fixed it self [/COLOR]

wow this is driving me nutz lol seems i cand use sudo
```

@winterfresh:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for kyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kyle@winterfresh:~$ 


```tried apt-get no go 
```

kyle@winterfresh:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```i have admin privileges and i ever enabled the root and tried that too but still cant use it

---

### Post by Cheezespread on 2010-01-25
> **cry8wolf9 said:**
> [COLOR=Red]edit: nvm seems to have fixed it self [/COLOR]

wow this is driving me nutz lol seems i cand use sudo
```

@winterfresh:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for kyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kyle@winterfresh:~$ 


```tried apt-get no go 
```

kyle@winterfresh:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```i have admin privileges and i ever enabled the root and tried that too but still cant use it


You mean you tried ```
sudo apt-get -f install
``` or that your user has admin privilages on the machine ?.

And , Did you try re-booting as Paqman mentioned ? .That should throw off the lock on Synaptic .

---

### Post by cry8wolf9 on 2010-01-25
> **theozzlives said:**
> I believe you need to run ```
sudo dpkg --configure -a
```As far as codecs, the only thing I've needed is ubuntu-restricted-extras ```
sudo apt-get install ubuntu-restricted-extras
```and the stuff [here]("https://help.ubuntu.com/community/Medibuntu")
thanks that helped
> **Cheezespread said:**
> You mean you tried ```
sudo apt-get -f install
``` or that your user has admin privilages on the machine ?.

And , Did you try re-booting as Paqman mentioned ? .That should throw off the lock on Synaptic .
yea after the second one the update manager picked up some files that were corrupt and asked me if i wanted to reinstall them and java was one of them lol

---

### Post by t0p on 2010-01-25
OP: by going back and editing the thread to mark questions as "SOLVED" you have succeeded in confusing me.  With which issues do you still require help?

You said that you "couldn't use *sudo*", but the output you reproduced is normal - ie I can't see any failure with *sudo*.  Then you said you ran *apt-get -f install* and it didn't work, returning error messages that included the words "Permission denied".  This is because you didn't use *sudo*. You should type in

```
sudo apt-get -f install
```

then type in your password when prompted for it.  You won't be able to see your password as you type it in - that's a security feature and completely normal.  Just type in the password and hit <Enter>.  Post the output here if you have any problem.

---

### Post by Paqman on 2010-01-25
> **cry8wolf9 said:**
> 
2) is there a way to disable the use of passwords on certain users?

What exactly do you want to achieve? 

a) Do you want to be able to log in without a password?
b) Or are you asking if you can skip entering the password for using admin tools like Synaptic?
c) Do you want to disable the use of admin tools altogether?
d) Something else?

a) is doable for one user, b) is not for security reasons, c) is just a matter of setting up their account right. Let us know if it's d).

---

### Post by t0p on 2010-01-25
> **Paqman said:**
> b) is not for security reasons.

Actually b) *is* possible, though perhaps not advisable.  It involves editing your /etc/sudoers file, which is *not* a simple task.  If you want to find out more, search the internet, using search items like "ubuntu edit sudoers" or similar.  Don't embark on editing the file until you understand what you're doing.

---

### Post by Paqman on 2010-01-25
> **t0p said:**
> Actually b) *is* possible, though perhaps not advisable.

I'd go further than "not advisable" and say "genuinely bad idea".

---

### Post by t0p on 2010-01-25
> **Paqman said:**
> I'd go further than "not advisable" and say "genuinely bad idea".

Not necessarily.  It all depends on what you want to do and why you want to do it.

For instance, if anyone wants to search my posting history, they'll eventually find a thread I started about problems with Gnome-PPP.  It turned out I needed to run Gnome-PPP as root; but I didn't fancy having to type in my password every time I clicked the icon.  So I edited /etc/sudoers so *sudo* didn't need a password to run Gnome-PPP, and the problem was solved without (much) risk to security.

Removing entirely the need for passwords with *sudo* probably *is* a bad idea.  But it really does depend on the circumstances.  Though I'll qualify that by pointing out, the fact that the OP knows nothing about *sudo* suggests to me that he should learn about it before he bypasses its security features.  OP: I suggest you start [here]("https://help.ubuntu.com/community/RootSudo") in your quest for knowledge.

---

### Post by cry8wolf9 on 2010-01-25
> **t0p said:**
> OP: by going back and editing the thread to mark questions as "SOLVED" you have succeeded in confusing me.  With which issues do you still require help?

You said that you "couldn't use *sudo*", but the output you reproduced is normal - ie I can't see any failure with *sudo*.  Then you said you ran *apt-get -f install* and it didn't work, returning error messages that included the words "Permission denied".  This is because you didn't use *sudo*. You should type in

```
sudo apt-get -f install
```then type in your password when prompted for it.  You won't be able to see your password as you type it in - that's a security feature and completely normal.  Just type in the password and hit <Enter>.  Post the output here if you have any problem.i marked the questions that had gotten help with as solved the ones i still need help with are the ones with need help in green next to them

> **Paqman said:**
> What exactly do you want to achieve? 

a) Do you want to be able to log in without a password?
b) Or are you asking if you can skip entering the password for using admin tools like Synaptic?
c) Do you want to disable the use of admin tools altogether?
d) Something else?

a) is doable for one user, b) is not for security reasons, c) is just a matter of setting up their account right. Let us know if it's d).
"a" i would like to use for a normal user with out admin controls 
and "b" would be nice once ive loged into my admin account its kinda annoying to keep entering my password over and over again

---

### Post by Paqman on 2010-01-26
> **cry8wolf9 said:**
> 
"a" i would like to use for a normal user with out admin controls 
and "b" would be nice once ive loged into my admin account its kinda annoying to keep entering my password over and over again

a) Is no problem at all. Just set that account to log in automatically in System > Admin > Login Window. By default new accounts you create don't have admin rights, but you can also remove admin rights for any account in System > Admin > Users and Groups.

b) Is not such a good idea. It may be a pain, but authenticating yourself as a human before using admin tools is a Good Thing™. In Linux you only take on admin rights for a single task, you aren't running as admin the rest of the time. That helps keep you safe, but it has the small drawback that you need to authenticate to mess about with the system.

---

