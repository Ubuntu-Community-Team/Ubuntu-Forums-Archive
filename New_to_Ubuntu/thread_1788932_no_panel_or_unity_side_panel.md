---
title: "no panel or unity side panel"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by bob brazie on 2011-06-23
This morning I started my machine and there is no panel or unity side bar. Needless to say the system is pretty useless. <g>

Any ideas?

---

### Post by verymadpip on 2011-06-23
Hi Bob.

Try ctrl + alt + f1 to bring up a terminal.  You'll have to log in with username & password (I think).  Don't worry if you can't see anything when you type your password, that's normal.

Then try this command:

```
sudo service gdm restart

```That worked for me.  If it doesn't you could try the full tutorial at:

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

As I say, the restart gdm worked for me, but you may need the additional steps.

Good luck.

---

### Post by bob brazie on 2011-06-23
Thanks but that did not do the trick for me. It restarted and the same thing happened.How would I start the login screen? or Evolution for that matter?

I will read the information later today when time permits.

Thanks, Bob.

---

### Post by akand074 on 2011-06-23
You should be able to press Ctrl + Alt + T and it will open up a terminal. You can run anything from the terminal. Just run "evolution" to start evolution. Though I believe you can type 'unity --replace' in the terminal and that should work.

---

### Post by verymadpip on 2011-06-23
Sorry it didn't work.  That's a drag.  Unity's not been too problematic for me.  I had the same issue a couple of times.  I think it got fixed with an update.
I've probably jinxed myself *again* by writing that.  :rolleyes:

Keep us posted on how it goes.

---

### Post by bob brazie on 2011-06-23
Any idea why that happened so suddenly?

---

### Post by rvchari on 2011-06-23
> **akand074 said:**
> You should be able to press Ctrl + Alt + T and it will open up a terminal. You can run anything from the terminal. Just run "evolution" to start evolution. Though I believe you can type 'unity --replace' in the terminal and that should work.

sorry to jump into this thread..
i had faced similar problem earlier in the day. nothing worked but just a blank screen. i simply shut down and rebooted... i needed 2 such cold shut down and reboots before i got the unity desktop back.
earlier unity had the global menu bar displayed and window buttons were also displayed. but now neither the global meny bar nor the window buttons on the unmaximised window appears.

will the unity --replace option work for me ?

---

### Post by bob brazie on 2011-06-23
Ctrl + Alt + T does nothing at this point....

Bob

---

### Post by bob brazie on 2011-06-23
I have re-booted several times to no avail.

Bob

---

### Post by verymadpip on 2011-06-23
In all honesty I've no clue as to the "why" of this.  I just don't have enough knowledge of the workings of Ubuntu.

The first time it happened I rebooted & logged into the classic desktop which seemed to work okay.
I quite like Unity even though it has it niggles for me.  I'm getting used to it & beginning to be a little more productive with it so I wanted to persevere.
The next time it happened I jumped onto the web (on an old box I have lying around) & looked for a solution, as you know.

Since a GDM update, probably a couple of weeks ago now, things have been okay.

I think a lot of people have noticed bugs in Natty & I was seriously considering going back to 10.10 until maybe 12.04 LTS.  I bet by then Unity will fly.  10.10 runs faster on my parents PC than 11.04 does on mine. Their box has 1/4 the RAM  & 2/3 CPU speed of my box.

Wow, off topic ramble, sorry.

Can you get into a terminal with ctrl + alt +f1? (f1 - f7 will bring up a terminal I think).
You could try the **unity --replace** command there if ctrl + alt + t won't do it.

TBH we need someone who knows more than me mate.

PS try **unity --reset** in a terminal as per:
[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by bob brazie on 2011-06-23
unity --replace did the trick for some reason ?????????

Thanks for the help!

---

### Post by verymadpip on 2011-06-23
Great.
Could you mark the thread as solved using the thread tools near the top of the page (on the right in red) please mate?

---

### Post by John_Anon on 2011-06-23
Once again, ctrl-alt-t

unity --reset

and then wait a few seconds.

---

### Post by bob brazie on 2011-06-23
Not a problem, sorry I forgot to do that. <g> 

And again, thank you! Bob.

---

