---
title: "unwanted root access terminal comes up as root"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by ubume2 on 2011-05-06
I've had to reinstall 10.04. For some reason previously I had always setup a keyboard shortcut for terminal using the F10 key.  I had not seen a default shortcut CTrl Alt t for terminal.

This is a new behavior: When I press F10 I get 

user@desktop:/$
which is root

Running Ctrl Alt t I get

user@desktop:~$ 

which is the way it should be

I would think the behavior using C+A+t and F10 would be the same

Since I have been in the habit of using F10 for so long how do I correct this?

I wonder what kind of problems I have created unknowingly using root for
all my terminal commands and want to avoid further potential problems by correcting this. I have not been able to find a solution for this problem on google or the forum check for related problems.

---

### Post by Bölvaður on 2011-05-06
"gnome-terminal" works, what is the problem?

What is the command you execute when you press f10 ?

It depends on what you are doing if it matters if you are a root or not. The general rule is that you shouldn't run as a root if you can avoid it.

Define what is wrong a little clearer please :)

---

### Post by mtangoo on 2011-05-06
> **ubume2 said:**
> 
Since I have been in the habit of using F10 for so long how do I correct this?
To stay clam and patient until your brain is back at the default key...kinda hard but eventually...

Else Check [this]("https://help.ubuntu.com/community/KeyboardShortcuts") if it helps

---

### Post by josephmills on 2011-05-06
for right now have you tried the command```
exit
``` just for now

---

### Post by ajgreeny on 2011-05-06
> This is a new behavior: When I press F10 I get 

user@desktop:/$
which is root

Running Ctrl Alt t I get

user@desktop:~$ 

which is the way it should beSo what is the problem?  Both those shortcuts do the same thing and take you to a normal gnome-terminal, neither of which is a "root terminal" as you describe it.

EDIT:  Sorry, I missed the ~ in the second one!

---

### Post by matt_symes on 2011-05-06
Hi

> user@desktop:/$
which is root

Running Ctrl Alt t I get

user@desktop:~$ 

which is the way it should be

It's not a terminal with the root user but it is opening with / folder (root folder) instead of ~/ (home folder).

What command are you using to launch the terminal when F10 is pressed ?

You could try something along the lines of

```
gnome-terminal --working-directory=DIRNAME
```

where DIRNAME is the name of the directory to open. If not check your config files ;)

Kind regards

---

### Post by mtangoo on 2011-05-06
Ctrl+Alt+t works fine for me!

---

### Post by mtangoo on 2011-05-06
[URL="http://ubuntuforums.org/showthread.php?t=46539"] Just add "cd /home/your_user_name" at the end of your .bashrc file and it will work perfectly.
It's all you have to do.[/URL]

---

### Post by josephmills on 2011-05-06
this is what root looks like 
```
 root@colleen-Latitude-D610:~# 

``` there is a big difference between that and this 
```
colleen@colleen-Latitude-D610:/$ 

``` as matt pointed out that you are not root you are just in the root dir (/) as ~ is your home dir. I hope that this clears it up further kind regards to go a little bit further 
~ = home dir 
/ = root dir 
$ = signed in as a user 
# = signed in as root 
colleen = user 
colleen-latitude-c610 = computers name 
: = break 
root = root user
so it looks like f10 is signing you on into your root **dir** and ctrl+alt +t is signing the user at the home **dir**

---

### Post by ubume2 on 2011-05-06
> **mtangoo said:**
> Ctrl+Alt+t works fine for me!

Yes, that works.  I just changed the default shortcut to F10.  I don't think 11.04 allows that.

After relaxing and calming down I went with the simplest solution for me.

---

### Post by mtangoo on 2011-05-06
> **ubume2 said:**
> 
After relaxing and calming down I went with the simplest solution for me.
What was that?

---

### Post by matt_symes on 2011-05-06
Hi

> **mtangoo said:**
> What was that?

Changing the key bindings to point to F10.

System->Preferences->Keyboard shortcuts.

Kind regards

---

### Post by mtangoo on 2011-05-07
Cool!:D

---

### Post by ubume2 on 2011-05-17
> **mtangoo said:**
> [URL="http://ubuntuforums.org/showthread.php?t=46539"] Just add "cd /home/your_user_name" at the end of your .bashrc file and it will work perfectly.
It's all you have to do.[/URL]

Yes, finally read this post. That solved it!. Thanks

---

### Post by mtangoo on 2011-05-17
> **ubume2 said:**
> Yes, finally read this post. That solved it!. Thanks
U're welcome :p

---

### Post by satyanash on 2011-06-29
Hi, i have a similar problem, however in my case i never changed the key binding, and pressing up ctrl+alt+T brings up a root terminal, with root access.
Any Help?
Satyajeet

---

