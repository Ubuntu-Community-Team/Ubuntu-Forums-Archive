---
title: "How to copy/paste output from tty console?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Zeniff on 2010-01-13
Hi~

On all the extra tty consoles shown when pressing CTRL+ALT+F1,F2,etc, how can I copy the output from there?

I'm trying to solve another problem where the tty console is messed up and doing crazy things, but I can't even ask on this forum properly until I can copy and paste what it's showing.

I also don't know where it saves the output, in case I'm supposed to find it somewhere... there are so many "logs" in the log viewer, but no information saying what logs are logging what.

Thanks for any help~~ O_O

---

### Post by mbzn on 2010-01-13
You could try to redirect the output
it will look something like 

(command that does weird things) > cat >> /home/(your username)/Desktop/1.txt 

or something like that
Just tested this and it works but someone with more command line knowledge could maybe give you a better command

---

### Post by Zeniff on 2010-01-13
Thanks! That will be useful for me in the future~

But in the meantime, I'm looking more for something that will let me copy what's already on the screen. This is because what's happening on my tty console seems to be random and crazy, so I was hoping to get the earlier stuff that happened.

I'll definitely try what you said at least from now on to make sure I can at least get that.

---

### Post by prshah on 2010-01-13
> **Zeniff said:**
> 
On all the extra tty consoles shown when pressing CTRL+ALT+F1,F2,etc, how can I copy the output from there?

tty console is messed up and doing crazy things, but I can't even ask on this forum properly until I can copy and paste what it's showing.

You can install "screen" ```
sudo apt-get install screen
``` and then, from your tty console, launch it with the command```
screen -L
``` Everything that occurs in this screen session will be logged into a file "screenlog.n" (n=0,1,2,3...) which will be in the same directory from where the screen command will be executed.

If your console gets weird characters when you type, you can "reset" it with the command ```
reset
``` This will just reset your console to defaults, it will not reboot your computer or so.

---

### Post by mbzn on 2010-01-13
If it is random, I know my laptop does random errors(I think only in tty1) but i believe it's related to my bluetooth device that is not functioning properly. But to solve your problem it might be worth it to type out what you see...

---

### Post by audiomick on 2010-01-13
ctrl+shift+c to copy
ctrl+shift+v to paste

in the terminal

but that's not what you need is it?

does the "print" button on the keyboard do anything useful?

---

### Post by Zeniff on 2010-01-13
Hmmm... well, after my clock reset to UTC suddenly and the admin password stopped working, I decided to reboot. So, unless it logged the output from tty1, I guess it's lost... :(

My reason for this thread was originally so I could provide more info for another problem:
[http://ubuntuforums.org/showthread.php?t=1379862](http://ubuntuforums.org/showthread.php?t=1379862)

Thanks, I'll try the screen program. But, how could I get it started so that it would capture stuff in my case in the other thread?

Thanks about the ctrl+shift+c, but what about for tty consoles, how can I highlight the text if it's not in an X environment?
Nope, sorry. It doesn't seem like "printscreen" button does anything either.

---

### Post by Zeniff on 2010-03-17
I just now found out the (almost) exact thing I had been looking for that would have been perfect for the situation I was in when I started this post.

In a tty console, you can save about one whole screen's worth of previous output from stdout (standard output) which is great because you can save after it's already on the screen:
```

sudo screendump N > screenoutput.txt

```Where N is the number of the tty console you want and screenoutput.txt is the text file to which to create and save.
 Apparently, you need to be root to access the stdout, so that's why sudo is there.
Unfortunately, it only seems to save the last page worth of output. I don't know how to get more, yet.
 
You can also have the error output (debug stuff?) save to a file if you do it ahead of time:
```

nautilus 2> erroroutput.txt

```This will make the errors only go the file, though. I don't know other options, yet.
My nautilus always gives errors if run from the terminal, so I used it to test the command.

However, that seems to only get error messages. Here are two ways that seem to get all the other standard output minus the standard error:
```

pidgin -d | tee -a PidginDebugStuff.txt
pidgin -d >> PidginDebugStuff.txt

```
The tee command will put stdout into the file, and also still show it onscreen, while >> will only send it to the file and it won't appear onscreen.

Cut and Paste:
Ctrl+K to cut everything to the right of cursor.
Ctrl+Y to paste to the right of the cursor.
Only can cut and paste within the same tty, though.

You can scroll up or down after lots of output with Shift+PageUp and Shift+PageDown.

From man pages of screendump and bash ("kill" and "yank" commands) and [www.linux.org's]("http://www.linux.org%27s") free beginner Linux course.

The advice everyone gave was all very useful in many situations. Thank you very much! I've used your advice several times! ^^/

---

