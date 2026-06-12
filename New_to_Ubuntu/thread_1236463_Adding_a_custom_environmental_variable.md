---
title: "Adding a custom environmental variable"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by binaryburnout on 2009-08-10
I am trying to add a custom environmental variable inside my ~/.bashrc file but it doesn't seem to like a space within one of my folder names. I have installed WINE and used that to run STEAM. Naturally Steam installed to ~/.wine/drive_c/Program Files/Steam, so I wanted to make a variable to would allow me to navigate to that folder without typing it out every time. But the "Program Files" directory is giving me problems. I have added the following to my ~/.bashrc file in hopes that it would work...
[LIST]
[*]export STEAM=$HOME/.wine/drive_c/Program\ Files/Steam:
[*]export STEAM=$HOME/.wine/drive_c/"Program Files"/Steam:
[*]export STEAM="$HOME/.wine/drive_c/Program Files/Steam":
[/LIST]
*No I am not adding all three entries to the ~/.bashrc file at once. I am trying each attempt one at a time.* All of the above always come out with the same error...
```
bash: cd: /home/binaryburnout/.wine/drive_c/Program: No such file or directory
```
It doesn't seem to like the space within the Program Files directory no matter how I wrap it. What am I missing?

---

### Post by asmoore82 on 2009-08-10
The example with quotes around everything is the most proper and correct.
```
export STEAM=" ... "
```
The problem is you have to remember to quote the environment variable when you reference it:
```
echo "$STEAM"
```

---

### Post by Paddy Landau on 2009-08-10
To clarify what asmoore82 said, your command should look like this:
```
export STEAM="$HOME/.wine/drive_c/Program Files/Steam:"
```Ideally, you should use curly brackets around the variable names, thus:
```
export STEAM="${HOME}/.wine/drive_c/Program Files/Steam:"
```In this case, the curly brackets won't make a difference, but it's something to bear in mind.

If you're using Wine, you may find it a lot easier to install [PlayOnLinux]("http://www.playonlinux.com/"). It's a kind of Wine manager that makes it much easier to install, run and uninstall programs in Wine. That way you never have to deal with Wine directly.

---

### Post by credobyte on 2009-08-10
> **asmoore82 said:**
> The example with quotes around everything is the most proper and correct.
```
export STEAM=" ... "
```The problem is you have to remember to quote the environment variable when you reference it:
```
echo "$STEAM"
```

Correct me if I'm wrong but .. 
```
echo "$STEAM" > $STEAM
```

The same as for [COLOR=RoyalBlue]$HOME[/COLOR] .. why would you type it in quotation marks ?

---

### Post by Paddy Landau on 2009-08-10
> **credobyte said:**
> The same as for [COLOR=RoyalBlue]$HOME[/COLOR] .. why would you type it in quotation marks ?
When there are spaces or special characters in the string, there will be a big difference.

For these purposes, $HOME and "$HOME" are effectively the same, as $HOME contains only simple printable characters without whitespace.

But, say:
```
export STEAM='/home/binaryburnout/.wine/drive_c/Program Files/Steam:'
cd $STEAM
```is equivalent to
```
cd /home/binaryburnout/.wine/drive_c/Program Files/Steam:
```So cd will try to change directory to _/home/binaryburnout/.wine/drive_c/Program_, and wonder what you meant by _Files/Steam:_.
Instead do
```
cd "$STEAM"
```which is the equivalent of
```
cd "/home/binaryburnout/.wine/drive_c/Program Files/Steam:"
```Are you sure that need that trailing colon?

---

### Post by binaryburnout on 2009-08-11
I must say I am quite amazed at the quality of input and conversation taking place in this thread. I am used to pages of flames and put downs about being a "nub" and how I should be more "1337" before getting my question answered.

That aside you all indeed solved my problem. Simply putting the *export variable* declaration inside quotes as well as calling the variable within quotes works.

Thanks much.

---

### Post by Paddy Landau on 2009-08-11
> **binaryburnout said:**
> I must say I am quite amazed at the quality of input and conversation taking place in this thread. I am used to pages of flames and put downs about being a "nub" and how I should be more "1337" before getting my question answered.
Yes, this forum has a large number of friendly and generous people with quality advice. I love it.

And today, I've learned a new word: [1337]("http://en.wikipedia.org/wiki/Leet")! :D

---

