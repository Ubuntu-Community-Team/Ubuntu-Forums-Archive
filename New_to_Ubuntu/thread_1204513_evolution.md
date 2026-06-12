---
title: "evolution"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by misswham on 2009-07-04
When I double click on the evolution icon the ball turns like it is getting ready to open and i see it in the toolbar at the bottom but then the ball disappears and it also disappears from the toolbar.

Why can't I open it?

---

### Post by wojox on 2009-07-04
What happens when you open it from

Applications > Internet > Evolution ?

---

### Post by niteshifter on 2009-07-04
Hi,

Let's get some more info on this. Open Terminal and start Evolution "manually":
```
foo@bar:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...

```
That second line is what I get starting Evolution, yours (I'm betting) will be different. Copy and paste what you get here, please.

---

### Post by misswham on 2009-07-04
the same thing happens when i open it from applications and internet

---

### Post by misswham on 2009-07-04
aretha@aretha-desktop:~$ foo@bar:~$ evolution
bash: foo@bar:~$: command not found
aretha@aretha-desktop:~$ evolution-shell-Message: Killing old version of evolution-data-server...
bash: evolution-shell-Message:: command not found
aretha@aretha-desktop:~$ foo@bar:~$ evolution
bash: foo@bar:~$: command not found
aretha@aretha-desktop:~$ evolution-shell-Message: Killing old version of evolution-data-server...
bash: evolution-shell-Message:: command not found
aretha@aretha-desktop:~$ 


tried it twice and the same thing.  it just started today.

---

### Post by SunnyRabbiera on 2009-07-04
hmm, you didnt remove it by mistake?

---

### Post by misswham on 2009-07-04
No, it is still in applications internet and then evolution mail.  it was still on my toolbar at the top.

---

### Post by SunnyRabbiera on 2009-07-04
> **misswham said:**
> No, it is still in applications internet and then evolution mail.  it was still on my toolbar at the top.

Just because it has a menu entry doesnt mean its installed though.
You didnt upgrade or anything correct?

---

### Post by misswham on 2009-07-04
I did the upgrades that come automatically and I didnt recall seeing an evolution upgrade.

---

### Post by misswham on 2009-07-04
and in add/remove it is still checked.

---

### Post by Faceless79 on 2009-07-04
> **misswham said:**
> aretha@aretha-desktop:~$ foo@bar:~$ evolution
bash: foo@bar:~$: command not found
aretha@aretha-desktop:~$ evolution-shell-Message: Killing old version of evolution-data-server...
bash: evolution-shell-Message:: command not found
aretha@aretha-desktop:~$ foo@bar:~$ evolution
bash: foo@bar:~$: command not found
aretha@aretha-desktop:~$ evolution-shell-Message: Killing old version of evolution-data-server...
bash: evolution-shell-Message:: command not found
aretha@aretha-desktop:~$ 


tried it twice and the same thing.  it just started today.

 Ok did you include Foo@Bar in the code? Dont. JUST type in evolution at a command prompt

---

### Post by misswham on 2009-07-04
yes i think so.  i copied and pasted everything.  i posted what came up above this post and i see foo bar there.

---

### Post by QIII on 2009-07-04
Just for future reference, "foo" and "bar" are just generic shorthand for "somthing" and "something else".  Like variables.

foo@bar is a non-machine-specific shorthand.

I know.  That my seem FUBAR...

---

### Post by wojox on 2009-07-04
Ok

```
sudo killall -r evolution*
```

Then

```
sudo killall -r gnome-keyring*
```

Reboot

---

### Post by misswham on 2009-07-05
Thank you that worked?  Now how do I mark a thread solved?  I used to could find it but now i cant.

---

### Post by stinger30au on 2009-07-05
the solved button has been removed

at the end of the thread click the edit tags

and put in there

evolution, solved, wont start

done!

---

### Post by LewRockwell on 2009-07-05
> **misswham said:**
> Thank you that worked?  Now how do I mark a thread solved?  I used to could find it but now i cant.

Re: Marking A Thread As SOLVED

The BEST solution/action, once a thread becomes "solved" is for the ORIGINAL thread CREATOR to edit their first post title to include "[SOLVED]"

To wit:

original title might be "why are some CD brands better than others?"

adjusted title would then be "[SOLVED] - why are some CD brands better than others?"

***This action, CONSISTENTLY applied, will make you a forum STAR PLAYER!***

.

---

