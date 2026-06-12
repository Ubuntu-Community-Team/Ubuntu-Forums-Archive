---
title: "Linking Engine to Chess game."
date: 2011-01-14
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-01-14
Hi all,

I have downloaded Dreamchess and Crafty from  the Download centre but I haven't a clue as to how to link the engine to the game. I would very much appreciate some help.

I also downloaded crafty-books-medtosmall

  :)

---

### Post by OldBoy44 on 2011-01-15
Bump

  :)

---

### Post by gmargo on 2011-01-15
To run **dreamchess** for the display and use **crafty** for the engine:

Run **dreamchess** from the menu (Applications -> Games -> BoardGames -> DreamChess?).  You can play straight away since dreamchess includes its own chess engine called **dreamer**.  But if you want to switch the engine to **crafty**, then just click on "Configuration.." on the Dream Chess window.  Then where it says "Engine: dreamer" - you can edit the field and replace **dreamer** with **crafty**.  Then hit OK, and start a new game.

You can use **ps(1)** to see what's running:
```

$ ps -efw|egrep -i "chess|crafty|xboard|fairymax"
gmargo   10043  2369 18 15:34 ?        00:00:01 /usr/games/dreamchess
gmargo   10045 10043  0 15:34 ?        00:00:00 crafty
gmargo   10047  2581  0 15:34 pts/1    00:00:00 egrep --color=auto -i chess|crafty|xboard|fairymax

```

---

### Post by OldBoy44 on 2011-01-15
Thanks for your reply gmargo,

How exactly do I edit? I tried messing around with the configuration but couldn't see how to change it. What of the Crafty-books-medtosmall? Do I need to do anything with that?

I am a complete newbie,

Figured out how to edit!

Cheers,  :)

---

