---
title: "starting firefox from tty2"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by audit on 2010-07-14
Would someone be willing to list the commands I need to enter to open firefox from tty2. I believe that if I have the list of commands I can figure out what I don't understand.

thanks.

---

### Post by Zeike on 2010-07-14
I don't know that this is possible.

You might be able to achieve it with the "--display" command line argument, but I don't know that this will do what you want it to.

Firefox is a graphical application only, and as such it will only display in an X session, not on a virtual terminal.

If you need a webbrowser for use on a virtual terminal try links or lynx.

---

### Post by audit on 2010-07-14
can I start an X session from tty2? I guess what I am really asking is can I run a bash script from tty2 that would open firefox and switch me to the display where firefox is running?

---

### Post by Zeike on 2010-07-14
You could do this, but the question is why not just start firefox from within an already running X session?  If you'd like firefox to run at startup you can just add it to your "startup applications"

---

### Post by audit on 2010-07-14
I don't know how to do this; what I want is an example. The reason is I want to understand a process. I am tired of being at the mercy of some programmer who tells me how to use my computer (I actually thought this was one of the driving reasons for linux).

---

### Post by Zeike on 2010-07-14
Again, I don't think this is possible.  If it is, I don't know how to accomplish it.  And it certainly wouldn't the easiest way to launch firefox.

The reason I asked why you wanted to do this is not because I'm a programmer dictating to you how to use your computer; I was going to try to come up with an alternative solution to your problem.

You could launch firefox from a tty with something like "firefox --display=:0", but it will display on the currently running X display :0.  I'm not sure how'd you go about switching to that display from a script.  I only know of the usual ctrl-atl-F# key commands.

---

### Post by audit on 2010-07-14
I appreciate your response--I did not think ill of you. Thanks

---

### Post by Zeike on 2010-07-14
> **audit said:**
> I appreciate your response--I did not think ill of you. Thanks

No worries :)

For the record I'm not a programmer, I'm a biologist.

---

### Post by 8Kuula on 2010-07-14
Hmm. you can start another xserver to from tty2 with *startx :1* command.
Thou that requires manualy to switch tty2 (ctrl+alt+f2), loging in and giving command.

But that is just in theory, for my part.

I do not think there is easy way to make that. But that's just me...

---

### Post by masque7 on 2010-07-14
[QUOTE=audit]The reason is I want to understand a process. I am tired of being at the  mercy of some programmer who tells me how to use my computer (I  actually thought this was one of the driving reasons for linux)..[/QUOTE]
Think of an operating system from a conceptual perspective. It has many different layers that have certain functions and capabilities. 

At the very bottom we have the hardware: the CPU, the RAM, your monitor, your keyboard and mouse, bluetooth and wifi on the motherboard, etc.

We then have another layer on this. Power management, memory management, graphics drivers, input drivers for mice and keyboards, the hard disk file system, network drivers, etc. This is the kernel, which is Linux. (that's all Linux is. It's not an operating system unto itself)

We then have another layer containing libraries for programming languages like Perl, Python, and Ruby. We have widgets and APIs for graphicsl applications like Firefox and Pidgin. That's QT, that's GTK+, it's gstreamer sound, it's the connection manager, and application servers. This is called userspace. This is GNU. (That's why GNU is the operating system and all the applications that comprise it)

On the very top we have the applications themselves. This is also GNU and GPL stuff. So we have Firefox here, we have Skype, we have Thunderbird, we have VLC, etc. Firefox uses widgets. Some browsers use the Webkit API. Google Chrome does. It would go back to the last layer and use that engine. Of course, it travels back even further to do the job.

You're trying to run Firefox without giving it what it needs to run. It's like trying to get in a car and drive it without any wheels.

A tty isn't using any of the graphical components. To write a bash script to load Firefox from a tty wouldn't be possible without starting x first. X is the program that provides you with an interactive graphical interface, of which GNOME and XFCE utilise. 

Another example is, how would you log in to your GNOME desktop from a tty? Well firstly you would have to start gdm (the gnome login manager)/start x.

---

### Post by audit on 2010-07-14
tried ```
startx :1
```
and this is what I saw:
> 
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log



---

### Post by Zeike on 2010-07-14
> **audit said:**
> tried ```
startx :1
```
and this is what I saw:

You're only going to be able to run one X server at a time unless you do some serious hacking.  You already have one running on :0, no need to start another on :1.  Just run "firefox --display=:0", and that should launch firefox on the X display on :0

[COLOR="MediumTurquoise"]EDIT: scratch that, you can start an additional x server by running "startx -- :1", and presumably yet another with "startx -- :2"... you get the idea.[/COLOR]

---

### Post by audit on 2010-07-14
if i run this script:
```

#! /bin/bash
firefox --display=:0
exit

```

from tty2 if opens firefox, but I have to manually press [alt]+F7 to see it.

---

### Post by Zeike on 2010-07-14
> **audit said:**
> from tty2 if opens firefox, but I have to manually press [alt]+F7 to see it.

I'm done some searching and found out about chvt.

from the manpage:
```
CHVT(1)                                                                CHVT(1)



NAME
       chvt - change foreground virtual terminal

SYNOPSIS
       chvt N

DESCRIPTION
       The  command chvt N makes /dev/ttyN the foreground terminal.  (The cor&#8208;
       responding screen is created if it did not exist yet.  To  get  rid  of
       unused  VTs,  use deallocvt(1).)  The key combination (Ctrl-)LeftAlt-FN
       (with N in the range 1-12) usually has a similar effect.



                                26 January 1997                        CHVT(1)
 Manual page chvt(1) line 1/19 (END)

```

so if your X server is running on tty7, you can do "chvt 7".

If you start up another additional xserver with "startx -- :1", it will probably get put onto tty8, in which case you can use "chvt 8"


EDIT:
here is a little script that should switch you over to tty7, run firefox on that display, then once you quit firefox, it should switch back to whatever tty you were using previously.  I haven't really tested it though.
```

#!/bin/bash
temp=$(tty)
chvt 7
firefox --display=:0
chvt ${temp:8}

```

---

### Post by audit on 2010-07-14
if i run this:

```

#! /bin/bash
startx --:1
firefox --display=:1
exit

```

I get this
```
xauth:  error in locking authority file /var/run/gdm/auth-for-gms-XLt1aL/database
xauth:  error in locking authority file /var/run/gdm/auth-for-gms-XLt1aL/database
xauth:  error in locking authority file /var/run/gdm/auth-for-gms-XLt1aL/database
xauth:  error in locking authority file /var/run/gdm/auth-for-gms-XLt1aL/database

X: user not authorized to run the X server, aborting.
xauth:  error in locking authority file /var/run/gdm/auth-for-gms-XLt1aL/database
Error: cannot open display: :1

```

---

### Post by Zeike on 2010-07-14
I think it has to be:
```
startx -- :1
```
with a space between "--" and ":1" to work.  Not sure though.

Also, see the short script I edited into my previous post.

I'm sure you could make some improvements on it by determining which tty the X server is running on and switching to that initially, rather than just using tty7 blindly.

EDIT:
I should add that there is another problem with this:
> **audit said:**
> if i run this:
```

#! /bin/bash
startx --:1
firefox --display=:1
exit

```
That is, the startx script doesn't exit until you end the X session.  So in order to do this correctly I think you'd need to change it to something like:
```

#!/bin/bash
temp=$(tty)
startx -- :1 &
sleep 5
# next you could find out what tty the X display :1 is running on.  I'm not quite sure how to do this yet.
# then just do chvt N, with whatever ttyN the display is running on.
firefox --display=:1
#when firefox closes, switch back to original tty
chvt ${temp:8}

```

---

### Post by audit on 2010-07-14
saw it and it worked! when I commented out the last line. Thanks, that gives me enough to start with.

Not sure why it did not work the way you designed it, but I'll figure that out later.

---

### Post by audit on 2010-07-15
this almost works but...
```
#!/bin/bash
keep=1
chvt 7
while [ ${keep} != 0 ]
do
keep=$(firefox --display=:0)
done
#when firefox closes, switch back to original tty
chvt 2
```

---

### Post by bodhi.zazen on 2010-07-15
All I did was

Ctrl-alt-F2 -> login

export DISLPAY=:0

firefox

Ctrl-alt-F8

Firefox is running as expected.

You might wish to take a look at a few things.

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

Also take a look (for science) at man xhost and X security.

Note: After you edit /etc/X11/Xwrapper.config , you will need to start a window manager ...

```
/usr/bin/startx /usr/bin/fluxbox -- :1
```This will start a new X session .

Now

export DISPLAY=:1
firefox

And firefox will start in the second X session (Ctrl-Alt-F9)

Well, that should get you started, enjoy !!

---

