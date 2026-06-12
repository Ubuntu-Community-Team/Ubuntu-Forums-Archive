---
title: "sudoku stopped working"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by blank25 on 2009-03-17
I'm a beginner using xubuntu. I was using the sudoku game. I quit the program and now it won't restart. Can someone explain in simple terms on how to get it to work again? I will greatly thank that person.

---

### Post by Crystek on 2009-03-17
So you go to click on it from the menu but it just doesn't open? 
Did you quit normally or did it crash?
Did you try logging out or rebooting?

---

### Post by Lunx on 2009-03-17
Perhaps try uninstalling and reinstalling?

---

### Post by Volt9000 on 2009-03-17
Try...

ps x | grep sudoku

If you see it listed, take note of the number in the first column. Then try:

kill number

Then run the program again.

If not listed, I have no idea.
Sorry if this doesn't work, I'm just a helpful noob. ;)

---

### Post by rafac24 on 2009-03-17
Unless you have High Scores or something that you desperately must keep....Uninstall and Reinstall lol.

Applications -> Add/Remove..

Type 'sudoku' in the box and uncheck the box. Apply Changes
Then check the box again and Install.

---

### Post by blank25 on 2009-03-25
> **Volt9000 said:**
> Try...

ps x | grep sudoku

If you see it listed, take note of the number in the first column. Then try:

kill number

Then run the program again.

If not listed, I have no idea.
Sorry if this doesn't work, I'm just a helpful noob. ;)

[email]dad@jeremy-old-desktop:~/.adobe[/email]$ ps x | grep sudoku
 6506 pts/0    R+     0:00 grep sudoku
[email]dad@jeremy-old-desktop:~/.adobe[/email]$ kill 6506
bash: kill: (6506) - No such process
[email]dad@jeremy-old-desktop:~/.adobe[/email]$ 

Didn't work?

Already tried to uninstall and reinstall before..
Can I add/remove without being logged in as administrator?

---

### Post by Iowan on 2009-03-25
> **blank25 said:**
> Can I add/remove without being logged in as administrator?
[**sudo?**]("https://help.ubuntu.com/community/RootSudo")

---

### Post by snova on 2009-03-25
What happens if you run Sudoku from a terminal?

Applications -> Accessories -> Terminal

```
gnome-sudoku
```

---

### Post by kevmitch on 2009-03-25
There might be something messed up in your user configuration that reinstalling the game might not fix. 

You can try instead removing your gnome-sudoku data directory:

```
rm -r ~/.gnome2/gnome-sudoku
```

---

### Post by blank25 on 2009-04-06
> **snova said:**
> What happens if you run Sudoku from a terminal?

Applications -> Accessories -> Terminal

```
gnome-sudoku
```
It does the following -

```

dad@jeremy-old-desktop:/home$ gnome-sudoku
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 55, in <module>
    start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/gnome_sudoku.py", line 21, in start_game
    main.start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 1039, in start_game
    u = UI()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 200, in __init__
    if self.select_game():
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 64, in _
    ret = fun(ui,*args,**kwargs)
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 214, in select_game
    choice = game_selector.NewOrSavedGameSelector().run_swallowed_dialog(self.swallower)
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 191, in run_swallowed_dialog
    self.setup_dialog()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 76, in setup_dialog
    self.make_saved_game_model()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 151, in make_saved_game_model
    sudoku.sudoku_grid_from_string(g['game'].split('\n')[1].replace(' ','')).grid,
  File "/var/lib/python-support/python2.5/gnome_sudoku/sudoku.py", line 232, in sudoku_grid_from_string
    assert(len(s)<=GROUP_SIZE**2)
AssertionError

```

I don't know what that means.

Doing "rm -r ~/.gnome2/gnome-sudoku" said 
```
dad@jeremy-old-desktop:~/.cache$ rm -rv ~/.gnome2/gnome-sudoku
rm: cannot remove `/home/dad/.gnome2/gnome-sudoku': No such file or directory
```


Can I do sudo if this account isn't set up with admin rights?

---

### Post by rbkhanna on 2009-04-07
I am using Kubuntu and facing the same problem. Help

Ravi

---

### Post by kevmitch on 2009-04-07
Intrepid?

---

### Post by kevmitch on 2009-04-08
Try completely removing and then reinstalling "gnome-games" in synaptic package mahager.

---

### Post by rbkhanna on 2009-04-08
Already tried. Did not work. On starting a blackbox appears on the desktop for a fleeting second and then disappears. Iam using Kubuntu.
Ravi

---

### Post by theozzlives on 2009-04-08
From what I read, the process is still running. Try turning off your computer and pull the cord for 15 seconds and see what that does.

---

### Post by rbkhanna on 2009-04-09
Switched off system. Removed batteries from my laptop for a minute. Problem still persists. Some other suggestions please.

Ravi

---

### Post by anewguy on 2009-04-09
find the process id as per an early post (the one with the grep on sudoku).  then do this is a terminal:

sudo kill -kill process-id



Dave :)

---

### Post by kevmitch on 2009-04-09
If you've turned off the computer there is **NO** way that sudoku is still running. It doesn't appear that that is the problem so much as the symptom. 

I find it kind of strange you have no files for the program in your home directory. Did you have it running before?

In any case, my best guess is that your version of the package is somehow corrupted. Did you try uninstalling  and reinstalling the "gnome-games" package? 

If that doesn't work, it looks like it's a python program. (Python is a widely used interpreted language). You might also try reinstalling things like "python-gtk2", "python-glade2", "python-gnome2".

---

### Post by rbkhanna on 2009-04-09
I have tried uninstalling and reinstalling the package. I have the python programmes already on my computer. I tried the 'kill' routine as suggested by 'anewguy,' but nothing has worked. I have the games files in my home directory under \usr\bin\games. The programme was running fine. I was in the middle of a game when I closed the programme and then shut down my computer. The game stopped working after that. All other games in the gnome games package are working fine. 

Ravi

---

### Post by retiefdv on 2009-05-08
I am using Sudoku on Ubuntu Hardy. Now, a "Bug Buddy" window pops up every time and I cannot get it working again. The error seems to be similar to others reported on this post. I have tried all the solutions proposed here, namely, remove the app, using the "Add/Remove" utility and reinstalling the same way, deleting the gnome-sudoku folder under ~/.gnome2, etc. The problem just stays here with no solution forthcoming. Could this perhaps be as a result of some update gone wrong?

---

### Post by Erewhonman on 2009-07-15
I too have Bug Buddy problems and tried all of the proposed solutions and none have had any effect.  Might have to buy a newspaper to get my sudoku fix!

---

### Post by lavinog on 2009-07-15
have you tried:
```

rm -rv ~/.sudoku

```

since you uninstalled and reinstalled, the problem is either config entries in the home folder, or the version you are using has a bug.
Actually it is a bug either way because it should handle config issues in a better way than crashing.

---

