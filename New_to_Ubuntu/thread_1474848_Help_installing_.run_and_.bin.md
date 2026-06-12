---
title: "Help installing .run and .bin"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Axilus on 2010-05-06
Hello,

I just purchased some games to play on ubuntu (world of goo, penumbra, gish, aquaria, and lugaru) and I'm am having a bit of trouble with installing them.

I managed to get both penumbra, gish, and world of goo installed perfectly using the command:
```
sudo sh /home/emmanuel/penumbra_overture_1.1.sh
``` 

However, both aquaria and lugaru are different kinds of installer files (one is a .bin and the other is .run). No matter which one I try to do they both give me this error message in the terminal:
```
/home/emmanuel/Archive/Games/aquaria-lnx-humble-bundle.mojo.run: 1: Syntax error: "(" unexpected

```


Also I have another question to do with Gish. I have put the folder in /usr/games however when I make a shortcut in the menu to run the executable it doesn't run properly (which is kind of strange being that it runs perfectly fine otherwise).

Help me out.
Thanks

---

### Post by Sealbhach on 2010-05-06
Oh you bought the [Indie Bundle]([http://www.wolfire.com/humble)?](http://www.wolfire.com/humble)?)

With these sort of files I just right-click on them, select properties and allow executing them as a program. Then I double-click on it and select "run in terminal". You don't need to faff about with the command line unless you really want to.

You'll need to give us the full error message for Aquaria, there's a bit more there.

.

---

### Post by Axilus on 2010-05-06
Unfortunately there isn't any more to the error message, but don't worry about it; your other suggestion worked like a char :D

---

### Post by Axilus on 2010-05-06
> **Axilus said:**
> 
Also I have another question to do with Gish. I have put the folder in /usr/games however when I make a shortcut in the menu to run the executable it doesn't run properly (which is kind of strange being that it runs perfectly fine otherwise).


Any suggestions for my other problem?

---

### Post by Sealbhach on 2010-05-06
Test the shortcut command in the terminal, you might get some feedback on why it won't start.

.

---

### Post by Axilus on 2010-05-06
It still runs with no errors. Here is the difference (the window that looks fine is run from the actual file itself, the white window is run from terminal/shortcut):

---

### Post by _0R10N on 2010-05-06
When I was a kid, I used to spend hours playing the Wolfenstein game. Is it possible to get the new game for Linux?

---

### Post by Sealbhach on 2010-05-06
> **Axilus said:**
> It still runs with no errors. Here is the difference (the window that looks fine is run from the actual file itself, the white window is run from terminal/shortcut):


Right, here is the command you need for your shortcut:

 **sh -c "cd /usr/games/gish153 && ./gish"**

This moves you to the directory where the gish binary is and then executes it from within that directory.

Let me know if it works.
.

---

### Post by madjr on 2010-05-06
> **_0R10N said:**
> When I was a kid, I used to spend hours playing the Wolfenstein game. Is it possible to get the new game for Linux?

there's one wolfenstein with mods in here i believe

[http://www.playdeb.net/](http://www.playdeb.net/)

as for the latest probably could get it to work with wine, but am not sure.

as for the games mentioned on the thread, i love them

i learned from it here first
[http://www.omgubuntu.co.uk/2010/05/how-much-would-you-pay-for-five-great.html](http://www.omgubuntu.co.uk/2010/05/how-much-would-you-pay-for-five-great.html)

thanks for the instructions

as for the installers, would be a good idea to go to their forums and suggest them .debs

---

### Post by Axilus on 2010-05-06
> **Sealbhach said:**
> Right, here is the command you need for your shortcut:

 **sh -c "cd /usr/games/gish153 && ./gish"**

This moves you to the directory where the gish binary is and then executes it from within that directory.

Let me know if it works.
.
Yes, thank you very much. May you please explain why that code works? I'm trying to get used to the terminal.

---

### Post by Sealbhach on 2010-05-06
> **Axilus said:**
> Yes, thank you very much. May you please explain why that code works? I'm trying to get used to the terminal.

sh starts up the shell

-c indicates that what is coming next is a command

the command is

cd 

change directory

to

/usr/games/gish153

&& means "once you've finished that, do the following"

./gish 

means execute this file from within this directory.  If you didn't add the "./" it would probably complain that gish is not in the path or environment or something.

.

---

### Post by madjr on 2010-05-08
hopefully with the funds they've raised, they could have some better installers in the future like WOG :D

---

### Post by Axilus on 2010-05-09
> **Sealbhach said:**
> sh starts up the shell

-c indicates that what is coming next is a command

the command is

cd 

change directory

to

/usr/games/gish153

&& means "once you've finished that, do the following"

./gish 

means execute this file from within this directory.  If you didn't add the "./" it would probably complain that gish is not in the path or environment or something.

.

Thanks, that was very helpful; I'm starting to get use to this command line interface. :D

---

### Post by haydoni on 2010-05-09
The (bizarre?) error which I get:

The file aquaria-lnx-humble-bundle.mojo.run executable, however when I double click, my computer thinks... then does nothing.
Is there a "fail-safe" terminal command which I'm missing?

Also, I installed penumbra but am unable to execute its file either.. it quotes, a no such file or directory error (though these files are there!!)... any ideas?

---

### Post by Axilus on 2010-05-09
> **haydoni said:**
> The (bizarre?) error which I get:

The file aquaria-lnx-humble-bundle.mojo.run executable, however when I double click, my computer thinks... then does nothing.
Is there a "fail-safe" terminal command which I'm missing?

Also, I installed penumbra but am unable to execute its file either.. it quotes, a no such file or directory error (though these files are there!!)... any ideas?

For aquaria, right click; go to permissions; then make sure it's marked as allow executing file as program.

When you try to execute penumbra, do you run it from the terminal or double click it?

---

### Post by haydoni on 2010-05-09
Previously I'd tried both and neither had worked. Then (with no other changes) it worked upon a double click...

Just the .bin to go... (it says it can't find the file - I have put the name in correctly (I dragged and dropped!), upon ls the filename is white (others red and green) and I can't tab to it even though it is the only file beginning with l... very odd).

---

### Post by Axilus on 2010-05-09
> **Sealbhach said:**
> Oh you bought the [Indie Bundle]([http://www.wolfire.com/humble)?](http://www.wolfire.com/humble)?)

With these sort of files I just right-click on them, select properties and allow executing them as a program. Then I double-click on it and select "run in terminal". You don't need to faff about with the command line unless you really want to.

You'll need to give us the full error message for Aquaria, there's a bit more there.

.

Try whats above for Lugaru, it worked for me but for the shortcut I originally put this:
```
"/usr/games/lugaru/lugaru"
```
And it worked.

---

### Post by bruno9779 on 2010-05-09
> **haydoni said:**
> Previously I'd tried both and neither had worked. Then (with no other changes) it worked upon a double click...

Just the .bin to go... (it says it can't find the file - I have put the name in correctly (I dragged and dropped!), upon ls the filename is white (others red and green) and I can't tab to it even though it is the only file beginning with l... very odd).

If the .bin does not autofill with tab, it is probably because the file is not set as executable. This is confirmed from the white color uou get when doing ls (it should be green)

do:

```
sudo chmod +x *filename.bin*
```

and then try again.

Now it should autofill and run.

---

### Post by haydoni on 2010-05-10
I'd already chmod -x ... no luck/change.

Perhaps the .bin file is corrupted, I'll try and download it again...

---

### Post by haydoni on 2010-05-10
For convenience I'll link this [other ubuntu-forums page]("http://ubuntuforums.org/showthread.php?t=1473008&highlight=aquaria") which explains how to install the games from the [humble bundle]("http://www.wolfire.com/humble").

---

### Post by jtarin on 2010-12-13
> **madjr said:**
> there's one wolfenstein with mods in here i believe

[http://www.playdeb.net/](http://www.playdeb.net/)

as for the latest probably could get it to work with wine, but am not sure.

as for the games mentioned on the thread, i love them

i learned from it here first
[http://www.omgubuntu.co.uk/2010/05/how-much-would-you-pay-for-five-great.html](http://www.omgubuntu.co.uk/2010/05/how-much-would-you-pay-for-five-great.html)

thanks for the instructions

as for the installers, would be a good idea to go to their forums and suggest them .debs
[Here is a link]("http://www.wolfenstein3d.co.uk/") to many mods of Wolfenstein which will run in DOSBOX and newer versions of Win. DOSBOX is available through the repositories......Install DOSBOX. The mods need no installation just unzip and right-click the executable to run in DOSBOX. Some I run in VirtualBox that only have a Win executable.

---

