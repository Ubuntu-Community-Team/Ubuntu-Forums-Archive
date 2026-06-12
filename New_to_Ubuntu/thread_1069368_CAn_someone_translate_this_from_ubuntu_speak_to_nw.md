---
title: "CAn someone translate this from ubuntu speak to nweb speak?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by shateredsoul on 2009-02-13
Hi Everyone,

So I installed a program called spss on ubuntu (it's for statistical analysis).  It doesn't play well with compiz so I had to turn off my affects when I want to use it.  I'm trying to figure out how to make it work and work without turning it off... and I did find a thread (so I did do my research) but I'm having a hard time understanding what the person's descriptions mean.  There's two lines of code he refers to.  But i'm not sure if I have to enter this in the terminal or actually go in and edit the spss code.  Does anyone know what this means?

Also, how do you edit the code for a program (incase I have to do that)? (I can't find a thread on this =().  

> 


I just wanted to let anyone interested know that SPSS 16 for linux does work. At first impression everything works fine though the processing of analyses seems somewhat slower than on windows (same machine).

There were a few quirks I had to deal with to get it all going.

The installer is Java based and there currently is a bug that appears to cause a lot of Java based stuff to fail on Hardy. To be able to run the Java based installer run the following command:

Code:

export LIBXCB_ALLOW_SLOPPY_LOCK=true

As far as I can see this only needs to be done once before running the installer and not thereafter to run the program.

Apparently SPSS also doesn't like compiz. It will run fine if you turn off compiz but with compiz on it doesn't display properly. There is a workaround for this... you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:

Code:

export AWT_TOOLKIT="MToolkit"

Don't ask me what that does I didn't come up with it myself.

You can then create a launcher that will launch SPSS by using the command to \SPSS16\bin\spss rather than "SPSS" (in caps which is the regular launcher).

There you have it. I didnt come up with any of this myself but I pieced it together from random searches. (i.e. this french ubuntu forum [http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272](http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272))

To: Mods... is this the right forum section for this?

Hope this helps a few of you.

As far as I know there are no Java based problems in 7.10.

---

### Post by mrbiggbrain on 2009-02-13
> **shateredsoul said:**
> Hi Everyone,
I just wanted to let anyone interested know that SPSS 16 for linux does work. At first impression everything works fine though the processing of analyses seems somewhat slower than on windows (same machine).

There were a few quirks I had to deal with to get it all going.

The installer is Java based and there currently is a bug that appears to cause a lot of Java based stuff to fail on Hardy. To be able to run the Java based installer run the following command:

Code:

[COLOR="Red"]export LIBXCB_ALLOW_SLOPPY_LOCK=true[/COLOR]

As far as I can see this only needs to be done once before running the installer and not thereafter to run the program.

Apparently SPSS also doesn't like compiz. It will run fine if you turn off compiz but with compiz on it doesn't display properly. There is a workaround for this... you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:

Code:
[COLOR="Blue"]
export AWT_TOOLKIT="MToolkit"[/COLOR]

Don't ask me what that does I didn't come up with it myself.

You can then create a launcher that will launch SPSS by using the command to \SPSS16\bin\spss rather than "SPSS" (in caps which is the regular launcher).

There you have it. I didnt come up with any of this myself but I pieced it together from random searches. (i.e. this french ubuntu forum [http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272](http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272))

To: Mods... is this the right forum section for this?

Hope this helps a few of you.

As far as I know there are no Java based problems in 7.10. 

ok, from what i understand the red is just creating a variable for the shell so the program can do something wierd (built into the installer)

the blue, needs to be added to the fie listed, its just a shell scripts, just open it in a text editor (like kate, or vim) and add the lines under #!/bin/sh part of the code (next line)

---

### Post by llamabr on 2009-02-13
Code:

export LIBXCB_ALLOW_SLOPPY_LOCK=true

As far as I can see this only needs to be done once before running the installer and not thereafter to run the program.

Apparently SPSS also doesn't like compiz. It will run fine if you turn off compiz but with compiz on it doesn't display properly. There is a workaround for this... you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:

Code:

export AWT_TOOLKIT="MToolkit"

It looks like the first one you type right into a terminal, on the command line.

The second one you want to put in the file /SPSS16/bin/spss

so on the command line:

cd SPSS16/bin/
nano spss

and then put the code after the #!/bin/sh

Note that he's got the slashes backward, and note that I'm not encouraging you to do any of this, as I have never installed SPSS (because I use R).

Good luck.

---

### Post by shateredsoul on 2009-02-13
Ok it's making more sense now

I did the first one. So, for the second one can I just open that file with a text editor? or is there a special program for that?

also what do you mean by command line?

thanks!

---

### Post by shateredsoul on 2009-02-13
so i changed the shell to

#!/bin/sh 
export AWT_TOOLKIT="MToolkit"
cd "/home/omar/Desktop/SPSS16"
#"/home/omar/Desktop/SPSS16/bin/spss"
exec "/home/omar/Desktop/SPSS16/bin/SPSS" $@

and I ran the first one in the terminal..
It's still not working unless I turn off compiz.I's running, i just can't see the cells or images.

---

### Post by shateredsoul on 2009-02-13
When I enter the first code into the terminal.. i don't get a response from the terminal.  It just goes on to the next line.  NO error, no "OK", or install... so I'm not sure if it worked

---

