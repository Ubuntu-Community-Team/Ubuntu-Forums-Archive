---
title: "SU Password?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by LoneWolf08 on 2009-03-04
So I installed Ubuntu without issue and set up my login name & password, but now I need my SU password to install something.  But I don't recall ever setting a password for this.  I've tried my login password and tried just leaving it blank but neither work.  

Did I totally miss something during install?!?!

---

### Post by SuperSonic4 on 2009-03-04
Ubuntu uses sudo for root access so if you need to be root just do ```
sudo command
``` or [gksu command] for terminal and gui respectively.

```
sudo -i
``` gives you a root shell

---

### Post by LoneWolf08 on 2009-03-04
Well I'm not too sure how to use that.

I entered in 'sudo command' and hit ENTER and it prompted me for my password.  Then it told me "command not found".

So then I tried it again and now it won't even prompt me for a password it just goes to 'command not found'.

<scratches head>

---

### Post by PermNoob on 2009-03-04
the su or sudo password is the same as the password for the first account you setup, as you seem to have figured out already.  It will only ask you for it the first time each session, after that it remembers that you know the password and doesn't ask again.
when he said
sudo command
he meant it as an example, when you want to run a command, say apt-get or something that requires sudo privelages, you type 
```
sudo apt-get blahblah blah
```

make sense now?

---

### Post by mlentink on 2009-03-04
> **LoneWolf08 said:**
> Well I'm not too sure how to use that.

I entered in 'sudo command' and hit ENTER and it prompted me for my password.  Then it told me "command not found".

So then I tried it again and now it won't even prompt me for a password it just goes to 'command not found'.

<scratches head>



ehhh 'command' stands for any valid linux command line command.

so, e.g.

```
sudo mkdir /home/dude/party
```

Would mean: As SUperuser DO make an new directory called ....

---

### Post by LoneWolf08 on 2009-03-04
Yes it totally does now!  <slaps forehead>

I actually got it going by using the "sudo -i" right after I posted that last one.  But I didn't realize it threw me all the way back down to the root.  haha.  Once I figured that out I could run the 'sh' command as needed!

You guys RULE!!!!!!!!!!!!

---

### Post by LoneWolf08 on 2009-03-04
> **PermNoob said:**
> the su or sudo password is the same as the password for the first account you setup, as you seem to have figured out already.  It will only ask you for it the first time each session, after that it remembers that you know the password and doesn't ask again.

And by "session" does that count towards a new terminal(s) I might open?  Session meaning as long as I'm logged into ubuntu yea?  Or is it just for that terminal window?

---

### Post by SuperSonic4 on 2009-03-04
Just for that terminal tab/window

---

### Post by hockeyhead019 on 2009-03-04
umm you sure because i'm on 8.10 intrepid and it doesn't prompt for the password again untill you log out or shutdown ect... so it will only prompt you once during your session for the password for sudo

---

### Post by Keith_Beef on 2009-03-04
I believe there's a time limit, but I don't remember what it is.

Certainly, I've used sudo to execute a command and then sudo again a couple of minutes later, and I didn't need to enter my password again.

But then, after a couple of hours, when I've used sudo I've been prompted for my password again.

K.

---

### Post by PermNoob on 2009-03-04
honestly, that is the first time I posted with an answer instead of a question.  On my machine it seems a little haphazard as to exactly when it holds onto the password and when it doesn't.  Session is probably the wrong word, sorry if that leads to any confusion.
However I have figured out that typing 
exit
will release the password and return you to your normal user, and exit again will obviously close the terminal.  

enjoy ubuntu, I know I am.

---

### Post by sisco311 on 2009-03-04
> **PermNoob said:**
> honestly, that is the first time I posted with an answer instead of a question.  On my machine it seems a little haphazard as to exactly when it holds onto the password and when it doesn't.  Session is probably the wrong word, sorry if that leads to any confusion.
However I have figured out that typing 
exit
will release the password and return you to your normal user, and exit again will obviously close the terminal.  

enjoy ubuntu, I know I am.

and if you are lazy (like me), just press Ctrl+d to log out from the root shell. :)


[uhelp]community/RootSudo[/uhelp]

---

### Post by presence1960 on 2009-03-04
> **hockeyhead019 said:**
> umm you sure because i'm on 8.10 intrepid and it doesn't prompt for the password again untill you log out or shutdown ect... so it will only prompt you once during your session for the password for sudo

Hi hockeyhead. Where you at in philly? I live in south philly.

---

### Post by LoneWolf08 on 2009-03-04
Awesome help here guys.  That all makes sense now..........and yes PermNoob I'm totally enjoying it.  This is my 4th try at Ubuntu, as I've only been trying it on laptop and had issues with NO wireless support, then NO WPA support, but now I'm 100% working!  Thanks to the ubuntu folks!

---

### Post by LoneWolf08 on 2009-03-05
BTW, there is indeed a 'time-out' for sudo.  For a while I could open and close Terminal windows at will and still be able to run "sudo -i", but I left my machine on overnight and when I tried again this morning, I had to re-enter my password.

Just FYI.

---

### Post by kanikilu on 2009-03-05
You can edit your /etc/sudoers file if you feel like changing the timeout. Add the statement *Defaults timestamp_timeout=60* to change the timeout from the default (15) to an hour (60), or whatever time you choose.

From the sudoers man page: > timestamp_timeout
Number of minutes that can elapse before sudo will ask for a passwd again.  The default is 15.  Set this to 0 to always prompt for a password.  If set to a value less than 0 the user&#8217;s timestamp will never expire.  This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.

---

