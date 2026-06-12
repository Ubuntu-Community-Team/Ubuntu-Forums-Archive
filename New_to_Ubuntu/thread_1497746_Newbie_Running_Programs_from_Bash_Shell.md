---
title: "Newbie Running Programs from Bash Shell"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by jrab227 on 2010-05-31
I actually have a few questions.

First, how would I start a program in a shell? How is this handled? I'm assuming its something like the Path in Windows.

Second, how would I set up a program to run in the Bash with a user defined (me) command?

Next, how would I see what user defined commands are set, like a list, for running programs?

Last, how can I start a GUI on my system from a shell? For instance, if my computer crashed and all I can access is a shell from Ctrl-Alt-F1

---

### Post by sdennie on 2010-05-31
> **jrab227 said:**
> I actually have a few questions.

First, how would I start a program in a shell? How is this handled? I'm assuming its something like the Path in Windows.


Correct.  You can see what the path is with:

```

echo $PATH

```

If a program is not in your path but you'd like to run it, you can also give an explicit path.  A common example of an explicit path would be something like:

```

./a.out

```

That runs the binary named a.out in the current directory.

> 
Second, how would I set up a program to run in the Bash with a user defined (me) command?


Either use an explicit path (described above) or add the location to your path.  A common thing to do is to edit ~/.bashrc and add ~/bin to your path.  Something like this would do the trick:

```

mkdir -p ~/bin
echo 'export PATH=${HOME}/bin:${PATH}' >> ~/.bashrc

```

Now, any programs/scripts you put in ~/bin are in your path.  Though, you may want to either "source ~/.bashrc", restart your terminal or logout/login to make that change work properly.  In the end, you will have to completely logout/login to propagate the changes up to the level of the GUI.

> 
Next, how would I see what user defined commands are set, like a list, for running programs?


If you decided to add ~/bin to your path, this is sufficient:

```

ls ~/bin

```

Though, you can also have shell aliases.  In which case, you may want to also do a:

```

alias

```

That will show you what aliases you've set.

> 
Last, how can I start a GUI on my system from a shell? For instance, if my computer crashed and all I can access is a shell from Ctrl-Alt-F1

If you've gotten to this unfortunate point and Ctrl-Alt-F7 doesn't get you back to the GUI, you could try:

```

sudo service gdm restart

```

---

### Post by Paddy Landau on 2010-05-31
> **sdennie said:**
> A common thing to do is to edit ~/.bashrc and add ~/bin to your path.
Actually, if you have a [FONT=Courier New]~/bin[/FONT] directory, then it's automatically added to your path (see [FONT=Courier New].profile[/FONT]). So, simply create the directory and reboot.

---

### Post by jrab227 on 2010-06-01
Now all that works on Ubuntu,but can anyone decipher this when I try it on Jolicloud? 

jalil@Jolicloud:~/Documents$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I don't exactly understand what that means. Also I'm getting the idea that when you call on a program to start, it only checks one folder (the PATH) if those commands aren't already set. So should just install all programs (or scripts that open programs in different locations) in the PATH? Or add a folder containing these programs into the PATH? Also, where in the file system is the PATH located?

---

### Post by jrab227 on 2010-06-01
I got it now. The PATH is a setting that tells the computer where to look for commands. Those folders are where programs go and editing the path and adding/deleting folders tells linux to change where its looking for commands.

---

### Post by Paddy Landau on 2010-06-01
That's correct.

You can also run a program without the terminal by pressing Ctrl-F2 and typing it there. Beware: if it's not a GUI, you won't see any output!

You asked, "... how would I see what user defined commands are set ...?"

I'm not quite sure what you meant, but you can get help on commands with the built-in manual. From terminal, type *man* followed by the command that you want, e.g. *man ps*. Note that these are all either *programs* or *scripts* rather than built-in commands.

You can get help on built-in commands by finding out about bash, using *man bash* to see the manual.

If you have newbie questions about any command, you can bet that there are tutorials and examples already on the 'net; just Google them. If you get really stuck, come back to the forum.

If these posts have answered all your questions, please mark this thread as solved (go to the top of the page, click "Thread Tools" and "mark this thread as solved").

---

