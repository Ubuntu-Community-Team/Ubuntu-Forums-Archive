---
title: "Shell Scripting and SU permission???"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by MrStill on 2008-12-18
Hi,

I am fairly new to Linux and I am trying to write my first shell script. I have been working on a Java application that will call for the system to shut down. I am using Java to call the command "shutdown -h now". I want this process to gain its own root permission -Note I have a thread about this on the Java support forums:
( [http://forums.sun.com/thread.jspa?threadID=5355684&tstart=0](http://forums.sun.com/thread.jspa?threadID=5355684&tstart=0) ). I have not been able to get Java the permission.

So, I want to write a shell script that will receive the password as a command line argument, use the SU command, provide the password given and call for shut down; if it is do-able. I can figure out everything but the providing the password to get super user permission.

If I can write this shell script, I can add it to the process. Java can call the script and provide the password as an argument...

So my question is, is this do-able? Also, any hints would be nice as well.

thanks
Joseph

---

### Post by unutbu on 2008-12-18
Tell java to execute this command:
```
gksu "shutdown -h now"
```

---

### Post by Titan8990 on 2008-12-18
You can't sudo or su shell scripts. They must be executed as root. This might require that your javascript be ran as root as well.

Sorry, but the post above mine is incorrect. gksu is used for launching graphic programs as root. Shutdown is not a graphical program.

---

### Post by unutbu on 2008-12-18
Titan8990, put this in a script and run it:
```

#!/bin/bash
gksu "shutdown -h now"

```
Your machine will shutdown.

---

### Post by decoherence on 2008-12-18
How to read a password in to a script:

```
#!/bin/bash

# clear sudo's "free ticket" so you HAVE to enter a password
sudo -k

# store what mode the tty is in ... not necessary but good to do
oldmodes=`stty -g`

# turn off echo so that when you type the password someone looking over your should can't see it
stty -echo

# prompt for the password and store it in a variable called "password"
read -p "password: " password

# restore the old echo state so you can see what you type
stty $oldmodes

# pass the password to sudo and have it run shutdown
echo $password | sudo -S shutdown -h now
```

hope that helps

ADD: I re-read your post... you want the password supplied as an argument? That can be done as well with some minor modifications. I'm heading home now so it'll have to be later.

here's a hint: arguments take the form $1, $2, $3, etc in scripts. Hence if I ran the script "mytest.sh" like so

mytest.sh mypassword

then I'd be able to access "mypassword" in the script by referring to variable $1 (for the first argument)

good luck

---

### Post by MrStill on 2008-12-18
Much thanks for the example decoherence. I was able to mod the code to do exactly what I need:

```

#!/bin/bash

sudo -k
oldmodes=`stty -g`
stty -echo
password=$1
stty $oldmodes
echo $password | sudo -S shutdown -h now

```

It cooperates well with my Java application. I owe you a debt of gratitude!

---

### Post by jamesstansell on 2008-12-18
It's great that you got a working answer so quickly!

I just wanted to add that since you are reading the password as a command-line argument, you can remove the 3 stty commands.  They don't particularly hurt but they're sitting there like having sand in your shoe.

You should be aware that putting a password on the command-line is usually frowned on.  Consider these scenarios:

* someone watches you start the program - they see your password
* someone gets a chance to see your command history - they see your password
* someone runs the ps command - they see your password

I'm sure there are other scenarios as well, but my point is that it's usually a good thing to be extra-sure that it's something you really want to do.

---

### Post by decoherence on 2008-12-19
> **MrStill said:**
> Much thanks for the example decoherence. I was able to mod the code to do exactly what I need:

```

#!/bin/bash

sudo -k
oldmodes=`stty -g`
stty -echo
password=$1
stty $oldmodes
echo $password | sudo -S shutdown -h now

```

It cooperates well with my Java application. I owe you a debt of gratitude!

Nice job! Since you're inputting the password from the command line, you can shorten it to just two lines

```

#!/bin/bash

sudo -k
echo $1 | sudo -S shutdown -h now

```

that oughta be enough to do it...

what jamesstansell said is a good thing to consider. if you're concerned about that, consider making a user account specific to the task and edit /etc/sudoers (generally use the command visudo ... hope you like vi!) so the account can only run the shutdown command as root. that way if somebody does see the password for that account, they won't be able to use it to hose the rest of your system -- just shut it down...

we can avoid shutdown asking for a password at all by configuring /etc/sudoers to not ask for a password when running "sudo shutdown -h now"

adding a line like this would probably do it (replace 'username' and 'hostname' with appropriate values, or use 'ALL' for hostname)
```

username    hostname = NOPASSWD: /sbin/shutdown
```

I'm on a suse system right now... i don't recall if ubuntu puts shutdown under /sbin... you can find out easily enough by typing
```

which shutdown

```

anyway, all of this stuff really just moves the security issue around rather than solving it. best thing to do, i think, is type the password at a prompt with echo turned off. of course, only you know how secure the setup needs to be!

cheers

---

### Post by MrStill on 2008-12-19
I understand why sending a password as a command line argument is a bad idea. The password is entered into a Java JPasswordField which replaces the text with dots. The Java application is GUI based and does not utilize the terminal window;so, as far as I know, the password is not immediately visible. Once again, I am still pretty new to Linux , so feel free to correct me if I am wrong. When the Java app calls for shutdown, it closes it self and the terminal window if opened. 

I run this application on my laptop at home; so, I wanted get a working solution to test the app. Should I start making it more secure, I will send the password through the standard input stream...

Thank you for pointing out my security flaws (not being sarcastic). My goal is to include as much functionality as possible.

---

### Post by Titan8990 on 2008-12-19
> Titan8990, put this in a script and run it:
Code:

#!/bin/bash
gksu "shutdown -h now"

Your machine will shutdown.


Didn't say that it wouldn't work, I said it was incorrect.


See:

man gksu

---

### Post by unutbu on 2008-12-19
I'm not sure what you are getting at here.
How should we judge if a solution is correct? Here are the criteria that come to my mind:
[list]
[*]Does it work
[*]Is it a security risk?
[*]Does it break other parts of the system?
[/list]

I read the man page for gksu, and found nothing which suggests its use in this case is incorrect. It also seems to pass all of my criteria for correctness mentioned above. 

Insisting that gksu must not be used because "shutdown" is not graphical seems like a silly artificial restriction to me. If it works and doesn't break anything, why not use it?

---

### Post by walkerk on 2008-12-19
You could edit sudoers to allow /usr/sbin/shutdown to run without the sudo password. You would still need to run it w/ sudo
```
sudo shutdown -h now
```

---

### Post by decoherence on 2008-12-19
it's wrong simply because gksu is not designed to run command line programs. using programs inappropriately can lead to trouble. for instance, 

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

the whole point is that sudo is written to do one thing and gksu is written to do another. sure they can do each other's job a lot of the time but using them in such a way might not be as well tested. thus it's not the best practice which, in some people's view, makes it 'wrong.'

---

### Post by unutbu on 2008-12-19
I think a sort of irrational mysticism has developed out of the heuristic mantra "use sudo for CLI apps and gksu for graphical apps".

The problem referenced on this page
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
has to do with using sudo when gksu is needed. It says nothing about there ever being a problem with using gksu when sudo is needed. In fact, the reason why gksu is needed for graphical apps is because it correctly runs commands with roots environment variables, while sudo runs commands with root privileges, but the normal user's environment variables. In this sense, gksu is more correct than sudo.

In short, I know of no cases of gksu breaking something when sudo would not.

---

### Post by decoherence on 2008-12-19
"heuristic mantra" -- I love that!!

However, with regard to what we are talking about (which is a little off topic now,) I don't think it's irrational or a heuristic. I hope you don't mind if I use your checklist as an example

    * Does it work

in this particular case, it would seem to. that does not mean it will in every case.

    * Is it a security risk?

i don't know, but gksu was written to run graphical programs. that's what the developers test for. why would I use it to run a command line program?

    * Does it break other parts of the system?

i don't know. i have not gone over the source code and even if I did, I bet there could be problems that I don't even see -- it's not my code, it might not even be written in a language I know.

my point here is that with unix systems you don't mess around with alternative commands that generally seem to get the job done when there is a command that you know will get the job done because it was designed to do exactly what you want. I'm not even saying "don't use gksu because it will mess up your system." It *probably won't* mess up your system. But can you say, with complete and absolute certainty, that it won't? I can't -- I haven't 'grokked' the source code behind these tools.

That is why I would suggest that using sudo to run a command line program is a safer bet than gksu. No hard facts to back it up, but years of experience with the UNIX ideology and this is how I interpret it. You could be absolutely right -- it might make no difference at all -- but I'm not interested in testing the theory when there is already something in place that we know does exactly what we want.

---

