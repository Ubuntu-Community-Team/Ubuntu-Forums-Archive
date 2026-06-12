---
title: "[SOLVED] gimp only works in terminal"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by jorge ortega on 2008-12-26
Mi gimp has stopped working other than in the terminal. The icon on desk doesn't open it and neither does the menu command. I can't even open gimp from a picture. All I can do is open gimp from the terminal and use its browser(not very good) to open a picture to work on it. Does anyone has any clue what the problem might be? I would appreciate any help plese, I'm working with the gimp all the time.
Thanks

---

### Post by RomeReactor on 2008-12-26
Hi. Check the properties of an image file to see if Gimp still shows up as an option in the "open with" tab. Also right-click on the menus in the top panel and select "Edit menus"; see if the entry for Gimp reads **gimp-2.6 %U** (assuming you're using the default version of Gimp that ships with Intrepid).

---

### Post by jorge ortega on 2008-12-26
If that is any help I forgot to say that I'm using Ubuntu 8.4 and gimp 2.4.5

---

### Post by jorge ortega on 2008-12-26
Yes, all that is fine, everything shoes where it needs to show. It is just that it doesn't work.

---

### Post by RomeReactor on 2008-12-26
Do you get any error messages when running it from the terminal? Are the other programs opening correctly when launched from the menu?

---

### Post by jorge ortega on 2008-12-26
No, from the terminal it works just fine. I forgot to mention that if I close the terminal Gimp closes too.

---

### Post by RomeReactor on 2008-12-26
When you run a program from the terminal, closing the terminal also terminates the program.

I can only think that if Gimp runs OK from the terminal, then there's a problem with the launcher in the menus; did you have any updates that coincide with this behavior? have you tried to make another entry for Gimp in the menus?

---

### Post by jamesrl on 2008-12-26
Does Alt-F2 gimp work?

---

### Post by jorge ortega on 2008-12-26
I allowed backports updates for a while so I updated to 2.4.5. I think (but i'm not sure) it was with this one that the problem initially happened (but after several days). Then I removed gimp and dependencies, switched off backports updates and reinstalled the whole thing, but the problem stays.

---

### Post by RomeReactor on 2008-12-26
Which version do you have installed now? Does it match the command in the menus?

---

### Post by jorge ortega on 2008-12-26
Does alt F2 work? 
I did't know about that command but I just tried it and it doesn't work
Does the menu item match the version? 
After getting rid of 2.4.5 i delated menu entrances and I reinstalled them after reinstalling gimp with no luck

---

### Post by RomeReactor on 2008-12-26
Please post the output of this:
```
ls /usr/bin | grep gimp
```

Also post the 'Command' entry in the launchers that don't work.

---

### Post by jorge ortega on 2008-12-26
hi Rome Reactor, this is the update:
I tried to type the commmand you game me and i couldn't because one of the symbols i codn't find (USA layout keyboard i discovered). I changed this to UK layout and I restarted the computer. No this the good part: I restarted it from the previous kernel (the one I had before last update of kernel). I did this because the last kernel (or now the first one on the list when booting) is giving me trouble: it doesn't start well and certain things that i keep discovering don't work properly. The matter is, gimp works fine now, when restarted with the previous kernel. Why this is I don't have a clue and is something I will have to chase up. In the meantime i'm just going to stick to the previous kernel. Thanks so much for your atention.

---

### Post by RomeReactor on 2008-12-26
Glad you got it working.

While you stick with the previous kernel, it might be a good idea to reinstall the problematic one.

Good luck.

---

