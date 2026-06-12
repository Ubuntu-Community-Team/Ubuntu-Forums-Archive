---
title: "[SOLVED] Planet Penguin Racer won't save games."
date: 2008-12-09
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-09
I turned all the max settings on Planet Penguin Racer on my Dell mini 9. and now it wont open anymore.

I even used the Add/Remove app. removed it and reinstalled it, restarted, it didn't work.

Ben told me this:

I am not sure on where it stores its settings. You might try firing up a terminal and running a

Code:

> ls -lha

look and see if there are any directories resembling something to do with the game, such as .ppracer or something (no idea what it might be called). mv that to something else and try running the game.

Code:

> mv nameofdirectory nameofdirectory_backup

_____________________

which I did. the game runs now and it works great.

but the problem is that I start on level 3 (which is the level I was on before I did all the commands above.) , I cant access level 1 and 2. When I beat level 3, it doesn't save the levels that previously have beated. So, I have to endurer starting at level 3 each time when i start the game.

is there a solution to fix this?

---

### Post by shiningkenmonster on 2008-12-09
i just removed the game and reinstalled it. It still has the same problem. It doesn't save previously game that i've beated. 

the only way i think to fix this is to do a whole system restore to fix this game. egh, that would be a burn.

---

### Post by shiningkenmonster on 2008-12-13
i did a system restore to solve this myself

---

