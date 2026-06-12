---
title: "basic terminal questions"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-07
1. when you use terminal to launch applications (e.g. typing: firefox listen.grooveshark.com and launching that page) is there a way to use the same terminal without it "freezing?" The only way i can seem to use it is close firefox (or whatever app im using) or open a new terminal window. reset and clear doesn't seem to work.

2. when using a sudo command (what does that stand for anyway?) such as to install something, like sudo apt-get fortune, for example, and you have to enter your password, is there a way to have it show how many characters you are typing without showing the actual characters? something like asterisks or something? I was thinking something similar to the echo command like i used in cmd in windows, which, works in the terminal too, apparently, but not echoing the actual characters. anyway to have asterisks show when you enter a password on terminal?

3. is there a way to have terminal always present (open?) i have it launch at startup, but just wondering

4. unrelated to terminal (i think) - is it possible to set shortcut keys to apps like you can in windows 7. e.g. ctrl+alt+f in windows would launch firefox if you set it to do so.

---

### Post by TeoBigusGeekus on 2011-04-07
1)
```
firefox listen.grooveshark.com &
```
It will launch the app in the background.

2)I don't think it's possible.

3)Having it launch at startup is the only way that I know.

4)Look in Administration>Preferences>Keyboard Shortcuts

---

### Post by jerome1232 on 2011-04-07
> **RememberWhenItRained said:**
> 
2. when using a sudo command (what does that stand for anyway?) such as to install something, like sudo apt-get fortune, for example, and you have to enter your password, is there a way to have it show how many characters you are typing without showing the actual characters? something like asterisks or something? I was thinking something similar to the echo command like i used in cmd in windows, which, works in the terminal too, apparently, but not echoing the actual characters. anyway to have asterisks show when you enter a password on terminal?


Yes you'd have to set the pwfeedback option in your sudoers file, I actually have run an errand like 5 minutes ago but I'll reply with more details about it when I get back. Probably with an edit of this post.

---

### Post by seawolf167 on 2011-04-07
Basically the same answers as TGB already posted above:

[LIST=1]
[*]Add an '&' at the end of the command
[*]SUDO = substitute user do, it doesn't display characters for security reasons, I don't know a way around it
[*]System -> Administration -> Startup Applications -> Add an entry for opening a terminal (or maybe point to a BASH script opening a terminal after a 'wait=5' if it doesn't launch correctly). I just bind open a terminal to a keyboard shortcut (I dislike the default keybinding)
[*]System -> Preferences -> Keyboard Shortcuts
[/LIST]

---

### Post by ~Plue on 2011-04-07
2.

see >> [https://help.ubuntu.com/community/Sudoers#Enabling%20Visual%20Feedback%20when%20Typing%20Passwords]("https://help.ubuntu.com/community/Sudoers#Enabling%20Visual%20Feedback%20when%20Typing%20Passwords")

---

### Post by Paddy Landau on 2011-04-07
Remember to use gksu instead of sudo for any GUI program. In fact, you can always use gksu if you like.

---

### Post by ayenack on 2011-04-07
> **seawolf167 said:**
> Basically the same answers as TGB already posted above:

[LIST=1]

[*]SUDO = substitute user do, it doesn't display characters for security reasons, I don't know a way around it

[/LIST]

Just to clear this up sudo is short for super user do. ;-)

---

### Post by rburkartjo on 2011-04-07
rem when you use the terminal to launch a apply try also adding & exit
this will close the terminal after you launch the app. and you can then open it again. for example to launch firefox type in terminal firefox & exit
not there is a space after ff and before exit

---

### Post by ~Plue on 2011-04-07
> **ayenack said:**
> Just to clear this up sudo is short for super user do. ;-)
actually, its [substitute user do,]("http://en.wikipedia.org/wiki/Sudo") ;) root is just the default
you can run as any user by sudo -u <user> command


edit:// reply to post below..
you have to edit the file. run
*sudo EDITOR=nano visudo*
and find the starting with [FONT=monospace]"[/FONT]Defaults", and add to the end of the line "pwfeedback" ,without quotes (use a comma to separate with other options)
then press ctrl+X  > Y > return to save the file

hope that clears it up

edit2:// jerome1232's replay on the next page..

---

### Post by RememberWhenItRained on 2011-04-07
> **jerome1232 said:**
> Yes you'd have to set the pwfeedback option in your sudoers file, I actually have run an errand like 5 minutes ago but I'll reply with more details about it when I get back. Probably with an edit of this post.
```
collin@collin:~$ /etc/sudoers pwfeedback
bash: /etc/sudoers: Permission denied
```
am i not in /root mode or something?

---

### Post by jerome1232 on 2011-04-07
To change it you do this (had to do some experimenting to figure it out)

```
sudo visudo
```

At the top should be a line that says

```
Defaults         env_reset
```

Add a line below it so that it looks like this

```

Defaults         env_reset
Defaults         pwfeedback
```

---

### Post by seawolf167 on 2011-04-07
> **ayenack said:**
> Just to clear this up sudo is short for super user do. ;-)

It is substitute user do ([wiki]("http://en.wikipedia.org/wiki/Sudo") and from the man page: "execute a command as another user"), I know linking wiki pages aren't authoritative, but as said previously, sudo allows you to become *anyother* user, not just the *root* user

---

### Post by RememberWhenItRained on 2011-04-07
even doing something like
```
 firefox listen.grooveshark.com &
```or ```
skype  &
```will close the program upon closing the terminal? any way  around this or is that just what happens when you launch from the  terminal?


> **jerome1232 said:**
> To change it you do this (had to do some experimenting to figure it out)

```
sudo visudo
```At the top should be a line that says

```
Defaults         env_reset
```Add a line below it so that it looks like this

```

Defaults         env_reset
Defaults         pwfeedback
```

that seems to only yield me this (screenshot attached )
by default terminal sudo commands are run in /root mode correct? which is super mode or admin mode, etc? what am i doing wrong
should i type "man" and see if that'll help?

---

### Post by jerome1232 on 2011-04-07
You just need to arrow down to the line that begins with "Defaults"

Add a line below it that says "Defaults pwfeedback" Then hit ctrl+o to save the file, then ctrl+x to exit.

---

### Post by RememberWhenItRained on 2011-04-08
> **jerome1232 said:**
> You just need to arrow down to the line that begins with "Defaults"

Add a line below it that says "Defaults pwfeedback" Then hit ctrl+o to save the file, then ctrl+x to exit.
works like a charm, thanks. if only that worked for the "away" util that i installed. oh well.

---

### Post by jerome1232 on 2011-04-08
> **RememberWhenItRained said:**
> works like a charm, thanks. if only that worked for the "away" util that i installed. oh well.

You'll notice most command line utilities default to giving no feedback at a password prompt, I personally like this because when I'm copy/pasting terminal output I don't have to worry about even revealing the length of my passwords.

Which btw if I were to do a brute force attempt on someones password, knowing it's exact length is a HUGE help.

I actually saved those changes to my sudoers file when I was showing you and forgot, then did a sudo command and it caught me off guard when I noticed it echo'ing asterisks back. Now I'm removing that change :)

---

### Post by Paddy Landau on 2011-04-08
> **RememberWhenItRained said:**
> even doing something like
```
firefox listen.grooveshark.com &
```or```
skype  &
```will close the program upon closing the terminal? any way  around this or is that just what happens when you launch from the  terminal?
When you run any program, it is a *process*. When you run a terminal, it starts a new process to run it. Then, you run a command from a terminal, so it runs as a *daughter* of the terminal's process. Therefore, if you close the terminal, it also closes the daughter program you started.

You have three different options to get around it.

[LIST=1]
[*]Create a shortcut that you can start from your panel, your menu or your desktop.
[*]Press Alt-F2. This brings up a small dialogue. Enter your command there, and it will start independently.
[*]In the terminal, use the "no hangup" command. This separates the command from the terminal. Use as follows.
```
nohup firefox listen.grooveshark.com &>/dev/null &
```The [FONT=Courier New][SIZE=3]nohup[/SIZE][/FONT] separates the command from the terminal. The [FONT=Courier New][SIZE=3]&>/dev/null[/SIZE][/FONT] discards output intended for the terminal, otherwise it creates a file called [FONT=Courier New][SIZE=3]nohup.out[/SIZE][/FONT] in your home directory. And, of course, the final [FONT=Courier New][SIZE=3]&[/SIZE][/FONT] sends the program to the background so that you can continue using the terminal.
[/LIST]

---

### Post by ayenack on 2011-04-08
@~Plue

You know I was all ready to explain how sudo will always invoke root privileges even when changing user, that it would invoke root privileges to change to that user and then once the user was changed they would run with their own privileges. And how sudo -i and sudo su worked etc. But then I had a little think about things and decided to take a look at man sudo (which I have never done believe it or not) and it quite clearly states that "sudo is used to invoke commands as superuser or another user" which seems to support your and wikipedia's definition of sudo.

Also the sudoers and sudoers.d would also support this.

I've always been told that sudo stands for super user do, every web site, book, tutorial, I've ever read has said that it stands for super user do. Having read man sudo it would seem they're wrong and your definition is correct.

It's amazing I've been using Linux for years, I have servers that I maintain I invoke the sudo command all the time and in all that time I may have been invoking a command I did not fully understand.

I'm intrigued by this and will have to do a little more investigation to completely satisfy myself but for now I am willing to accept your definition.

Well the old saying is true you learn something new every day.

---

