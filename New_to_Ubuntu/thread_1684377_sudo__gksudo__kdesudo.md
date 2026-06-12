---
title: "sudo / gksudo / kdesudo"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-02-09
Hello!

The [wiki]("https://help.ubuntu.com/community/RootSudo") states

> 
You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo  sets HOME=~root, and copies .Xauthority to a tmp directory.  This  prevents files in your home directory becoming owned by Root.  (AFAICT,  this is all that's special about the environment of the started process  with gksudo vs. sudo).


I experienced the files-becoming-owned-by-root behaviour only once with a third-party program and was wondering whether there are "normal" (meaning programs in the repositorys or frequently used pre-installed programs/commands) that would produce that problem when used with *sudo*.

The background of this question is that after I encountered the problem with the third-party program I proposed an idea at [Ubuntu brainstorm]("http://brainstorm.ubuntu.com/idea/27102/") but people there ask whether that problem really occurs as noone else seems to ever have had that problem.

Does anybody know more about this? The warning is quite explicit, but noone seems to ever have experienced it.

Thank you,

Blutkoete

---

### Post by kellemes on 2011-02-09
Never experienced it myself..
Can you remember the 3rd party app that showed this behavior?
Anyway, if this behavior is practically non-existent it seems to be a good idea.

---

### Post by Primefalcon on 2011-02-09
I have, and I had to use a lived disk to fix permissions

---

### Post by Blutkoete on 2011-02-09
The third-party app was MATLAB. I sudoed the install script (.sh) which itself invoked a graphical installer and in the end the .matlab folder in my home folder was owned by root which I had to change in order for MATLAB to be able to save the configuration.

Primefalcon, do you remember which command caused your problem?

My idea would only be a mere inconvenience to many people if the problem itself is almost non-existent but might save people from having to repair their system if the problem happens with "normal" commands as well.

---

### Post by mikewhatever on 2011-02-09
> **Blutkoete said:**
> 

The warning is quite explicit, but noone seems to ever have experienced it.



Says who?
It happens rarely because most gui programs are never run with sudo or gksudo, which makes what you propose an overkill. Regardless, the problem is easily reproducible, just try it yourself, in fact, you should have done it before brainstorming, just to have some first hand experience.

---

### Post by migs73 on 2011-02-09
have a look at this;

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

there is a link near the top to discussions about what sudo can do to GUI's.

---

### Post by Blutkoete on 2011-02-09
> **mikewhatever said:**
> Regardless, the problem is easily reproducible, just try it yourself, in fact, you should have done it before brainstorming, just to have some first hand experience.

I did the brainstorming after I had first hand experience with the problem. I was just looking for other examples because running MATLAB isn't exactly something many people do.

I'll add migs73's link to the brainstorm idea.

Thank you all!

---

### Post by Rebelli0us on 2011-02-27
I was saving/copying existing text files to my Desktop and they never showed up, they just disappeared. Finally I had to copy/paste the content to a new file to work around this bug. Then a few days later a logged in as root and all the files were in root's desktop! Is this the same problem?

---

