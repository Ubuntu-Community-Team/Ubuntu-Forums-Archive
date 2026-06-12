---
title: "How to get my toolbar back?"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by paparoo on 2010-12-31
Me again, with a similar problem as last time.

I was playing Jumbo, a solitaire game in /usr/games/sol. I messed around with the View and managed to lose my entire toolbar, both top and bottom. Now I can find no way to go back and undo my choice. And I cannot start a new game, undo moves, see the score, etc.

Whatever I did affects all the games in the sol directory, it seems. Same problem, whether run in gui or terminal.

How do I restore that area of the game to default?

Thanks
paparoo

---

### Post by howefield on 2010-12-31
Try pressing Alt + F2 keys to bring up the Run dialogue window. Type gconf-editor and press enter.

Navigate to apps > aisleriot and place a check against show_statusbar and show_toolbar.

Restart the game, did that fix it ?

---

### Post by paparoo on 2010-12-31
I have a new hero! Thanks a million! Back to 'normal', whatever that is for me.

Howie is 2 for 2, folks.

paparoo

---

### Post by howefield on 2010-12-31
Any time, just keep 'em easy ;-)

Messing around a little further, I don't think you need to invoke gconf-editor, simply placing a check against the relevant items in the game menu, then restarting the game should work.

---

### Post by paparoo on 2010-12-31
News to me. How would I access the game menu?

---

### Post by howefield on 2010-12-31
The menu as in the attached picture ?

Game, View, Control, and Help.

The controls for status bar and tool bar are under the View menu.

---

### Post by paparoo on 2010-12-31
That was my problem - they were not visible after I had cleared their selection.

---

