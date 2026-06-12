---
title: "Connect to RDesktop on Boot"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by RobinsonGrimes on 2008-09-26
First Off: This may be the wrong place for this topic, if so, can someone please point me in the right direction.

Now that that's done, onto this :arrow: RDesktop!

Does anyone know how, if possible to connect directly to another computer using RDesktop, on boot. I currently have Ubuntu HH log on to my admin account automatically, and under sessions I have disable all startup programs. I then added a startup command named auto-login with the code:
```
rdesktop -u myUser -d myDomain -f -n myName server
```

This code works when put into the terminal standalone, however on boot, it beings the connection, i.e. I actually see windows loading, then it stops and goes back to Ubuntu.

Has anyone else had this problem, or better yet, does anyone know the solution?
Thanks in advanced,
RGC

---

### Post by RobinsonGrimes on 2008-09-29
bump!

---

### Post by jonobr on 2008-09-29
Did you say, when you execute the script in a terminal it works ok?
i.e. ./rdesktop_start_script   ??

---

### Post by RobinsonGrimes on 2008-09-29
Yes, when the aforementioned code is copied and pasted into the terminal, it works exactly as planned. As for /rdesktop_start_script, I have no idea what your talking about. I am still a beginner when it comes to Ubuntu, but I understand some basic concepts. I just don't understand why Windows begins to load, and then stops if I use a startup session command.

---

### Post by jonobr on 2008-09-29
the ./<filename> means create something like a text file which can be automatically executed on boot up.
So If I create a test file named test in my home directory , I put the line you mentioned 
and then to execute it I do a ./testfile
That can be automatically started on boot up.


Im trying to execute that on my own local machine here but am getting an error,
Im going to try it some more and see whats going on.
I would like to get this working as well, as Im constantly RDPing into machines and having it done of startup would be useful

---

### Post by RobinsonGrimes on 2008-09-29
OK, well...I am not running a specific script file on boot, when I go to System->Preferences->Sessions and add a new Startup Program, I do not browse for a file, instead I just insert the command into the text box. Is that my problem, or is this considered correct aswell?

---

### Post by jonobr on 2008-09-29
Interesting, Im having a hard time starting this, I dont know why.....

Heres what I would try if I was doing this.

Go to applications-> text editor (lets avoid vi unless you know it.)

paste your script, save it as something.
This will probably save in your home dir.
Then go the sessions, add the file at your startup.
save and try it.

There may be some permissions problems , you might need to allow it to be executed, but give that a try see how it works

---

### Post by RobinsonGrimes on 2008-09-29
Trying now!

---

### Post by jonobr on 2008-09-29
BTW, when you save it, you can try executing it on the command line.
SO if you create a text file called rdestop_start and its in you home dir,
go to your home directory and try ./rdestop_start that will exectue and will show you whats its doing on startup

---

### Post by RobinsonGrimes on 2008-09-29
Permission Denied? Do you know the work around this?

---

### Post by jonobr on 2008-09-29
In your home dir where your file is now or wherever its located, try chmod 755 <filename>

chmod 755 rdestop_start

---

### Post by jonobr on 2008-09-29
I should also mention, I recommend understanding file permissions before you take my advice on setting them.

I could be any kind of a nasty person :D

(Im not though)

---

### Post by RobinsonGrimes on 2008-09-29
Ok, well I changed it and nothing bad happened :D so I guess your not a bad person, or at least nothing has gone wrong yet...
But, on the positive side, RDesktop got the farthest it ever got on boot, it continued to the login screen, and then BOOM back to ubuntu!

---

### Post by jonobr on 2008-09-29
can you do a ls -l on the file in a terminal window
again is the name of the file is rd_start
type ls -l rdstart

then type whoami

post both on this,

---

### Post by jonobr on 2008-09-29
I think I missed your intervening post.
Sounds like the script executes now, except its that Rdesktop craps out?
IS that right?

---

### Post by jonobr on 2008-09-29
Im guessing you dont have permissions to execute rdesktop either from the permissions  you set the owner of the files and/or the user you are..

---

### Post by RobinsonGrimes on 2008-10-01
Ok well... sorry about my sudden dissapearance. I was called into a meeting, and since I only work on M/W/F I didn't post yesterday. About file permissions. I believe I do have the correct permission to run the script because on boot it initializes the script, the windows login screen appears, and then rdesktop ends. Also, if I run the script after full boot, it runs fine. I think theres some process that Ubuntu runs, or upon initialization, that kicks me out of Rdesktop. It may kick you out of any program, I just happen to only be trying to run RDesktop.

---

### Post by jonobr on 2008-10-01
Darn.... I thought from the silence that meant you were rocking...

Also M/W and F? Can I get a job there :D

I got my script to work.
I setup a simple file which  just had
rdesktop -u <myusername> <target_machine>
where target machine was name or IP address.

I put it in sessions, rebooted and it opened the session to the other machine,
I am currently doing this also for my calendering client.
There doesnt seem to be a problem.

I am guessing when you run the script, in the terminal its opening the session fine and there are no firewall restriction and RDP is enabled on the remote machine.
Also, that you are trying the script with the same target machine as the offline testing without automatically starting.

I suppose Im saying, Im not sure I can figure out where your issue is :(

There may be some conflict on startup, but I cant figure that from here :(:(

---

### Post by RobinsonGrimes on 2008-10-01
OK...So I guess I'll try a more basic version of the script, similar to what you are using with only 2 parameters...But the entire purpose of this script was to use an OLD, VERY OLD, computer that can run Ubuntu then connect to a very new, powerful server, in hopes of "bypassing" the hardware limitation of the computer, since the dud computer would never technically do anything(after startup that is). I guess I'll try it and be back in a sec. If it works, it must be some problem with the -f functionality on boot, otherwise idk what the problem is...
It's only an internship XD not technically a job...

EDIT: NO Avail!

---

### Post by jonobr on 2008-10-01
The -f switch shouldnt make a difference

Not second guessing you,
but just checking , you can run from command line to this machine, correct?
On a terminal you can do you rdesktop command,
You can also run the ./script and it works also,

You can do it via the gui
Apps->internet->term services clent.

If all that works and  you can log in ok, Im lost:confused:

---

### Post by RobinsonGrimes on 2008-10-01
> **jonobr said:**
> On a terminal you can do you rdesktop command,
You can also run the ./script and it works also,

You can do it via the gui
Apps->internet->term services clent.


That makes two of us, because yes it works in all of those instances...I just shut down the main server for today, so I can no longer test any ideas.  Hopefully I'll talk to you, or someone who can help me :), Friday, and get this sorted out.

---

### Post by RobinsonGrimes on 2008-10-03
Bump!

---

### Post by RobinsonGrimes on 2008-10-06
Bump

---

