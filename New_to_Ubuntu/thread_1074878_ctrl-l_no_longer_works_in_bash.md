---
title: "ctrl-l no longer works in bash"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by uberg on 2009-02-19
I did not realise how much I used this until it disappeared.  i can no longer use ctrl-l (lowercase L) to clear the screen in bash.  The only thing that i can think of is i have started experiment with the program "screen".  By experiement i mean i have just started to use it.  Right as i was doing this i noticed that ctrl-l no longer works.  Even when i am not using screen.  
Thanks in advance for your words of wisdom.
Joe

---

### Post by scorchgeek on 2009-02-19
Until the problem gets resolved, you can use the following command to clear the screen instead:
```
clear
```

---

### Post by taurus on 2009-02-19
Or you can edit ~/.bashrc[/code] and include an alias for it.

```
alias ^L=clear
```
The ^L means hold down the <Ctrl> while pressing the letter l case.

---

### Post by uberg on 2009-02-19
Thank you for the 'clear' suggestion.  I am a shortcut junkie though.  That's why i use vim and have ```
set -o vi
``` in my .bashrc file.   I just found out how to do that bit recently and i am still tickled. :D 

i tried putting ```
 'alias ^L=clear
``` in my .bash_alias file; in my .bashrc file; with uppercase L; with lower case L; with single quotes around 'clear'; without single quotes around clear; all to no avail.

What happens when i press ctrl+L is```
joe@eliza:~$ ^L
```.  Always hoping for beautiful suprises as so often happens while using this thing i hit enter:```
bash: 
      : command not found

```  i wasn't really expecting anything to happen but there it is.

Thank you for your time.  If you think of anything else it would be much appreciated.  
Joe

---

### Post by taurus on 2009-02-19
Just so we are clear here.  You are not supposed to type in the ^ and then letter L after that.  Instead, you're supposed to type in alias <white_space> hold down the <Ctrl> key while hitting the letter L--^L.  Then, add =clean right after that.

Save it.  Now, you need to source your ~/.bashrc so the new alias will be available.

```
source ~/.bashrc
```

---

### Post by uberg on 2009-02-19
[SMACK-on-the-forehead] i did not know that.  And now it works.  Sort of.  ^L still appears on the screen when i press cntl+l; however, when i hit enter it does clear the screen.  So it's half-way there and something to keep my fingers happy until i can figure out went wrong.  i've done a little searching on Google but the results usually have to do with other problems with control sequences and most of them having to with windows. ;-)  My search continues though.

[SMACK-on-the-forehead-again]  i also did not know about 'source'.  Whenever i make a change in my .bashrc or .bash_alias files i thought i had to exit the terminal and start another.  Yea!  That is much faster and much much more convenient.  Both 'man' and 'info' do not show an entry though.  'which' reveals nothing.  So what is this construct?

Still haven't found out what went wrong but already i have learned a lot.  Thanks taurus.

Joe

---

### Post by ericomattos on 2009-04-12
I had the same problem and have found a better solution.

I put in "/etc/inputrc" file the following lines:

```

# for Ctrl+l clear screen
"\C-l":'clear\n'

```


Now, when I press Ctrl+l, the screen is cleaned without need to press ENTER.

Source: 
[http://www.linuxquestions.org/questions/linux-general-1/any-way-to-create-bash-short-cuts-like-ctrll-for-clear-and-ctrld-for-exit-554420/](http://www.linuxquestions.org/questions/linux-general-1/any-way-to-create-bash-short-cuts-like-ctrll-for-clear-and-ctrld-for-exit-554420/)
[http://www.linuxquestions.org/questions/linux-general-1/any-way-to-create-bash-short-cuts-like-ctrll-for-clear-and-ctrld-for-exit-554420/]("http://www.linuxquestions.org/questions/linux-general-1/any-way-to-create-bash-short-cuts-like-ctrll-for-clear-and-ctrld-for-exit-554420/")

---

### Post by llamabr on 2009-04-12
Good.  Now to the solution.  You broke bash when you started messing with screen?  Maybe we should see what's in your .screenrc

---

### Post by uberg on 2009-05-01
Dear ericomattos and llamabr,

    First, let me apologize for not getting back to your posts in a more timely manner.  I was amazingly distracted for a couple of weeks and am only now able to catch up on my communications.

    Second, THANK YOU for your time and your advice.  Although I eventually figured out how things got broke I am still stumped as to a solution.  Again I should apologize because I did not post a follow-up when I figured the "how's" correctly but at that point it was some time after the original post. 

    Llamabr, I was wrong about Screen being the culprit.  It was suspect but the evidence could never really prove it.  This bothered me to no end until I eventually figured out that Screen was not the villian.  Eventually.  =)  Around the same time that I was experimenting with Screen I had also found this clever new trick.  The trick is to put ```
 set -o vi 
``` into my .bashrc file.  This is so I can use Vi key-bindings on the command line.  Cool!  When I comment this out from the .bashrc file  works fine again.  Now that I know that it is there, however, having Vi key-bindings on the command line is something that I just can't live without.  So  remains broken.  :(

    Ericomattos, your solution does provide a better solution than the previous suggestion.  Unfortunately, for me, the difference is only marginally better.  When I place your suggested addition to my /etc/inputrc file it does allow me to quickly clear the terminal.  But only from an empty "line".  Your solution inserts "clear" followed by "new-line" which works fine as long there isn't anything else typed on the line.  This doesn't work well when done with any other characters on the line.  Just an error.  I miss  the most about half way through a long command string and I think to myself, "This output would be a lot easier on my eyes if I could clear the terminal - RIGHT NOW."   before ```
set -o vi
``` would let me clear the terminal but keep intact the command I was in the middle of typing.  Now I could just put ```
clear;
``` in front of whatever I am working on but who thinks of that before your half way through?  LOL

    So I found out how I broke it but the cure (losing my Vi key-bindings) is not worth the pain.  

    Is there another solution?  Any thoughts?  Or reading material?  Maybe I should have posted in another spot but even though I have some Linux skills I feel perpetually like a newbie.  LOL.  Maybe someday I won't feel so clueless. 

    Gentlepersons, thank you for you time and kindly advice,
    bigjoe

---

### Post by abhi2706 on 2010-01-04
I also faced the same problem. One solution, I found on following location also:
[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)


Ctrl-l/Ctrl-W and other key-bindings are EMACS key-binding. So just set following command in your ".inputrc" (I prefer this) and check whether it works or not

set -o emacs


For me it worked.

In case, your problem is solved and you have some other solution, then let the ppl know.

---

### Post by Hubi17 on 2010-05-26
I don't know if it's the solution to your problem, but to clear the screen when using vi keybindings you have to exit input mode then press Ctrl+L.
So the key combination would be:

Esc
then
Ctrl+L

Edit: This also works when there is some text already on the command line.

---

### Post by uberg on 2010-05-26
Dear Hubbi,
       That's it!  That's it!  That's it!

       That is exactly what I was looking for.  Although I would much rather not go into "normal" mode that's a small price to pay.  Thank you so much.  Most of the time when I am looking to use ctrl+l I am in the middle of a long piece of code and realize it would be better on my eyes to view the output on a clear screen and that's what I was missing.  Thank you so much.  I will now mark this as solved.  

Joe

---

### Post by estragib on 2012-01-13
Put this in your ~/.inputrc to get roughly the same behavior in insert mode.

```
set keymap vi-insert

$if Bash
    "\C-l": "\e\C-la"
$endif
```

It maps ^L in insert mode to ESC (exit insert mode), ^L (clear screen) and a (append). If you're used to vi, you'll know that exiting insert mode moves the cursor one character left, which is why I'm using "a" instead of "i". This will, of course, misplace your cursor by one if you press ^L at the beginning of the line.

---

