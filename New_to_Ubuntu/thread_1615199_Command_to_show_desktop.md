---
title: "Command to show desktop"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Jeff.Smith on 2010-11-06
So here is the scenario. I am using Compiz Fusion and I want to bind a button on my mouse to make it show the desktop. For some very dumb reason, Compiz does not allow you to do this by default (you can bind a keyboard sequence to do this or an area of the screen, however you can't bind a mouse click). So as a work around I was wondering if there was a command to make ubuntu show me the desktop, this way I can bind that command to the mouse button and solve my problem. 

I was curious to know if this is even possible and if it is, what is the command and will it look simular (graphically) to the way compiz enable me to show the desktop?

---

### Post by Jeff.Smith on 2010-11-07
So I'm having a new problem that I hope someone here can help me with. While searching for a workaround to the problem listed above I came upon a useful package called 'wmctrl'. This package is supposed to allow you to create a script that forces Ubuntu to show the desktop. 

'wmctrl' can be found [HERE]("http://tomas.styblo.name/wmctrl/")

Now, I'm having trouble installing this package so that I can use it in a later script.

```
#!/bin/sh
if wmctrl -m | grep "mode: ON"; then
exec wmctrl -k off
else
exec wmctrl -k on
fi
```

Here is a screenshot of the terminal and the error that I am running into. 
[IMG]http://i1191.photobucket.com/albums/z468/jeffreyasmith5/Screenshot1.png[/IMG]

I'm pretty new to using the terminal so I'm probably just doing something wrong, but if there is someone out there who understands this stuff, please help.

Jeff

---

### Post by Jeff.Smith on 2010-11-07
bump?

---

### Post by Crimbo on 2010-11-07
I would also like help on this.

Not liking the idea of script though. I'm surprised that compiz doesn't have the option for it, seeing the other effects have mouse binds o.O?

---

### Post by AngusH on 2010-11-07
Why are you trying to install from source? wmctrl is in the repos, just search it in synaptic.
Angus

---

### Post by Jeff.Smith on 2010-11-07
Ok, I've got everything working but for others wanting to do the same thing here are instructions from beginning to end. The first thing you will need to do is grab the wmctrl package from the package manager. Just search it in the synaptic package manager in Ubuntu.

Once you have the package installed, right click anywhere on the desktop and create a blank document and paste this script into it. 
```
#!/bin/sh
if wmctrl -m | grep "mode: ON"; then
exec wmctrl -k off
else
exec wmctrl -k on
fi
```

After you have created this script, give it a name. I used 'Show'. Then you will need to right click on the document you just created and give the permission to be executable. (right click document>Properties>Permissions>Allow Executing)
[IMG]http://i1191.photobucket.com/albums/z468/jeffreyasmith5/screenshot1-1.png[/IMG]

After you have done all this put the Script somewhere you don't mind leaving it. I created a folder called 'scripts' in the document folder and put the script in there.

The Script is now ready to use. All you have to do is go to compiz and point the command to this script. So, just open up compiz and go to the command section. Choose which command you want to use (I used command 0) go to your script and right click it and choose copy. Paste into your chosen command, and then you are free to bind this command to whatever button or keyboard sequence you want. 

Hope this helps anyone else having the same problem.

---

### Post by Jeff.Smith on 2010-11-07
> **Crimbo said:**
> I would also like help on this.

Not liking the idea of script though. I'm surprised that compiz doesn't have the option for it, seeing the other effects have mouse binds o.O?

I'm also surprised that this can't be done by default. However the workaround listed above works quite nicely and you can bind it to any key or keyboard sequence so it's pretty useful.

---

### Post by Crimbo on 2010-11-07
Genius! :D Thanks so much!

---

### Post by Jeff.Smith on 2010-11-07
> **Crimbo said:**
> Genius! :D Thanks so much!

No problem, feel free to message me if you run into any troubles.

---

### Post by ark1-87 on 2013-05-06
this didn't work for me. I use a Logitech m705, and the command works from a terminal but not when I assign it to button 10 in compiz.

EDIT:
it worked if I copy the entire script into the command 0 box.

---

### Post by Crimbo on 2013-05-06
> **ark1-87 said:**
> this didn't work for me. I use a Logitech m705, and the command works from a terminal but not when I assign it to button 10 in compiz.

I forgot about this thread, it has been so long.

It could be that compiz doesn't recognise or is not able to communicate with the Logitech m705... which leads me to ask, is the Logitech m705 work fully elsewhere on the system?

> **ark1-87 said:**
> EDIT:
it worked if I copy the entire script into the command 0 box.

If it works that way, I would stick to that way. It's better than linking to a file, which may unlink when accidentally deleted or moved.

---

### Post by oldos2er on 2013-05-06
If anyone has further questions please start a new thread, this one's quite old.

---

