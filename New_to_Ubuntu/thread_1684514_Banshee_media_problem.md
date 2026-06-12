---
title: "Banshee media problem"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by PhilRogers34 on 2011-02-09
I have just installed ubuntu onto an ext hard drive and it seems to be working as it should, the problem i currently have is my music is being imported into banshee media player but when i select and album or a track it won't play, all i get is a little grey 'x' next to the track that is supposed to be playing. i know the music is fine because it will play on vlc media player along with films and vids.  i tried checking the box in preferences to add menu integration, i have tried uninstalling and re-installing 3 times, through the software centre and once through the synaptic manager.  can anyone tell me where i'm going wrong or how to fix this issue?  also which media player is the best equivalent to windows media player? i want one where my music gets imported once and that it is it, i just load the app, select an album and it plays, i noticed a few ubuntu players need me to import the media everytime i open them, but much for me! lol

---

### Post by Dutch70 on 2011-02-09
Have you tried Rythymbox or Amarok? 

Also if you've moved your songs around since loading them in Banshee that could be the problem.

---

### Post by PhilRogers34 on 2011-02-09
i just had a play about with armorok and rhythmbox,  i didn't like amorok, it doesn't sort the music properly and only saves it all as one big playlist. rhythmbox sorts it better but i have no icon when i close the window so i have to open it up again by going through applications - sound+video then rhythmbox. i was hoping to find a solution for banshee so i could keep using that one. cheers anyway though.

---

### Post by tea for one on 2011-02-09
> **PhilRogers34 said:**
> i just had a play about with armorok and rhythmbox,  i didn't like amorok, it doesn't sort the music properly and only saves it all as one big playlist. rhythmbox sorts it better but i have no icon when i close the window so i have to open it up again by going through applications - sound+video then rhythmbox. i was hoping to find a solution for banshee so i could keep using that one. cheers anyway though.

Good evening

Assuming that you are using Gnome, there is an icon for Rhythmbox in the top panel.

Open Rhythmbox
A little icon should appear in the top panel controlled by the indicator applet 
(Right click top panel > Add to panel > Select indicator applet > Click Add > Close)
Allow the application to bring your music in from the Music folder
Close Rhythmbox with the X and the icon should remain.
Left click the icon > Show Rythmbox or Quit

I hope that this will help you

---

### Post by PhilRogers34 on 2011-02-11
I'm not getting the icon when i open rhythmbox, any icons i add do not have anything to do with ryhthmbox

---

### Post by tea for one on 2011-02-13
I'm pretty sure that the indicator applet is installed as a default so I am a little perplexed that the Rhythmbox icon does not appear in the panel when you open the application.

You could add a dedicated Rhythmbox launcher to the panel.

Select Rhythmbox from the menu.
Right click
Select "Add this launcher to panel"

---

### Post by linuxsyst on 2011-02-13
Try Movie Player

---

### Post by CaptainMark on 2011-02-13
If the OP's asking to keep banshee lets help them with that first, have you tried highlighting all the music in your banshee library and removing it, just ctrl+A and right click and remove from library then try re adding the music, its possible youve added the music intially and banshee has built its database based on those locations and then another music player has rearranged your music folder for you and banshee doesnt know. 

Seen as removing and reinstalling banshee would leave the configuration and database files intact its entirely possible that this is what is causing it.

Or close banshee and run in a terminal 
```
rm ~/.config/banshee-1/banshee.db
```

---

### Post by PhilRogers34 on 2011-02-13
Cheers Mark, i shall have a go at that, i inported all my music into rhythmbox and amorok so that might be the problem. also with rhythmbox i didn't want the launcher icon, i wanted the icon that appears when the programme is active, in the toolbar at the top, the one i right click and select 'quit' from.   but if i get banshee working properly then i won't have to worry. cheers.

---

