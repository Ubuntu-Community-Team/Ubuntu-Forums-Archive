---
title: "[SOLVED] Ubuntu goes BLACK with Compiz"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by babloo75 on 2008-12-20
I did a blunder with my ubuntu.. don't know how to bring it to the same state as was before.
I have activated magic lamp and fade effects with compiz advanced effects, and now when ever i click (both right and left) the screen goes black. is there any way to bring it to the same state as before.
right now i am typing this help from windows as the above stated problem is preventing me from working on ubuntu..
PLEASE HELP URGENTLY..
do i need to format my ubuntu partition and reinstall it as what ever you suggest me, i don't think i will be able to do as even a single click makes the screen go BLACK..
or can i access my data on ubuntu from windows(so that i can save it b4 formatting the ubuntu partition)
please help

---

### Post by overdrank on 2008-12-20
Hi and see if you can reach the command line with the keys ctrl, alt, F1 and enter the command ```
metacity --replace
``` then try the keys ctrl, alt, F7 returns you to the desktop.

---

### Post by babloo75 on 2008-12-20
No it didn't solve the problem. The same thing persists. whenever i click, the screen goes black.

---

### Post by overdrank on 2008-12-20
> **babloo75 said:**
> No it didn't solve the problem. The same thing persists. whenever i click, the screen goes black.

Have you tried booting into recovery mode and use the xfix option,

---

### Post by prshah on 2008-12-20
> **babloo75 said:**
> I did a blunder with my ubuntu.. don't know how to bring it to the same state as was before.

Press Alt+F1 to bring up the top menu; Then navigate to System-Preferences-Appearance-Visual Effects-None (Press Alt+N)-Close (Alt+C).

Now visual effects will be disabled.

Try your clicking now. It should work as before. 

If you still get the same BLACK screen error, then it is related to some other problem and not compiz; can you post a screenshot of the BLACK screen? Is it a text mode screen?

---

### Post by babloo75 on 2008-12-20
I tried xfix option... it failed.
Then tried Alt+F1... the same black colored command appeared. and then- over that black colored window nothing could be read.
but i remember the area covered by that black window was under main menu command..
as i wrote nothing could be read so unable to post the screen shot.

But i have been able to partially save my data by running the live cd and then accessing ubuntu partition thru that and copying few files from there to the windows partition. but a majority of files are still not copied (as it said access denied)
i don't know why is it behaving like this.. is it a kind of virus or so..

---

### Post by babloo75 on 2008-12-20
> **prshah said:**
> Press Alt+F1 to bring up the top menu; Then navigate to System-Preferences-Appearance-Visual Effects-None (Press Alt+N)-Close (Alt+C).

Now visual effects will be disabled.

Try your clicking now. It should work as before. 

If you still get the same BLACK screen error, then it is related to some other problem and not compiz; can you post a screenshot of the BLACK screen? Is it a text mode screen?

No it is not a text mode screen.. all is fine till i click. i can see both upper panel and the lower one along with icons on desktop. the moment i click to open a command e.g "Places" it opens a window below it, but its of black color and not readable. till this time the background of desktop wallpaper can be seen clearely. and now,if i click the portion of desktop not covered by black window, the whole desktop goes black.
this happened only after i modified compiz configuration, b4 that it was just running fine...

is it possible for me to remove compiz thru live cd or by any other means? i think that will solve the problem

---

### Post by prshah on 2008-12-20
> **babloo75 said:**
> 
is it possible for me to remove compiz thru live cd or by any other means? 

Looks to me like a compositing problem. The metacity suggestion earlier on should work. Try it from a virtual terminal (Applications-Accessories-Terminal) or press Alt+F2 and give the command```
metacity --replace
```

Or you can "blindly" disable visual effects; by guessing the menu option placements.

Or, if you insist on blocking compiz; boot off the live CD (or go to recovery mode); mount your "/" partition to /mnt (no need in recovery mode); navigate to /mnt/usr/bin (/usr/bin in recovery mode); either remove exec permissions or move the compiz.real file.```
sudo mount /dev/sda1 /mnt -o rw
cd /mnt/usr/bin
#either
sudo chmod a-x compiz.real
#or
sudo mv compiz.real compizreal

```

Replace /dev/sda1 with the actual partition id of your "/" (root) partition.

This will totally prevent compiz from launching. If the Xserver (GUI) fails to load properly (missing titlebars, etc) use the metacity command as outlined previously in a terminal (Applications-Accessories-Terminal)

If you run into trouble, post back.

---

### Post by babloo75 on 2008-12-20
> **prshah said:**
> Looks to me like a compositing problem. The metacity suggestion earlier on should work. Try it from a virtual terminal (Applications-Accessories-Terminal) or press Alt+F2 and give the command```
metacity --replace
```

Or you can "blindly" disable visual effects; by guessing the menu option placements.

Or, if you insist on blocking compiz; boot off the live CD (or go to recovery mode); mount your "/" partition to /mnt (no need in recovery mode); navigate to /mnt/usr/bin (/usr/bin in recovery mode); either remove exec permissions or move the compiz.real file.```
sudo mount /dev/sda1 /mnt -o rw
cd /mnt/usr/bin
#either
sudo chmod a-x compiz.real
#or
sudo mv compiz.real compizreal

```

Replace /dev/sda1 with the actual partition id of your "/" (root) partition.

This will totally prevent compiz from launching. If the Xserver (GUI) fails to load properly (missing titlebars, etc) use the metacity command as outlined previously in a terminal (Applications-Accessories-Terminal)

If you run into trouble, post back.

Yes, it seems to work partially. I opened Alt+F2. It opened a small black window. I typed "metacity --replace" blindly and then pressed enter.
Atleast I m able to see my ubuntu now.
What should I do now?
Once I reboot, the same problem arises again.
and following the same Alt+F2 then metacity --replace------- it disappears till the next reboot.
Thanks a ton. atleast I am using internet from ubuntu now.
Can U please suggest a permanent remedy to this or i will have to remove compiz and re install it again.
Thanks Thanks......
Thanks a ton...

---

### Post by babloo75 on 2008-12-20
Yes now I have removed compiz from my system. the problem is solved now.
Thanks to all of You for your help.

One last help now
Should I reinstall Compiz on my system. Will it create the same problem for me now, please guide me for any special precaution. Please reply so that I can mark this thread as solved.
Bye bye to all of you.

---

