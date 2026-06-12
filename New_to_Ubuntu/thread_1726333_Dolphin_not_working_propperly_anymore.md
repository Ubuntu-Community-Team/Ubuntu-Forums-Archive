---
title: "Dolphin not working propperly anymore"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by mastablasta on 2011-04-11
I upgraded the KDE to 4.6.2 Now all effects work as they should. And even the AudioCD is recognised (though still not playing in GUI).
 
However now Dolphin doesn't work anymore as it did before. When i open it it takes a long time to load. And keeps doing something on the disk. Everything is very slow compared to how it was before. When i click on folder it take a while to open it and in the mean time there is no indication that i clicked on something.
 
Is there an issue with it? should i wait for it to go through disk and read all the files first or what?
 
I don't understand why the slowness. I tried Krusader and it was as fast as before, but Dolphin.... Terrible.
 
It all started when my wife decided to mount the camera (honestly i didn't open dolhpin before) and it didn't want to mount it. Or rather it was taking very long time to open and then it just dissapeared, reappeared but only the window nothing inside. so i tried to close it. And then a message came up saying that dolphin is not responding.
 
Then the computer didn't want to shut down propperly. it was going through splash screen, spewing out some messages and then it all stopped and i was at cursor in TTY1 (or it was the same as if i used Alt+Ctrl+F1). I logged in and tried with shutwodn command but it didnt' shut down. screen just went black and that was it.
 
I tried uninstalling the dolphin and reinstalling. This seems to have slved the shutdown issue as i was able to shut it down propperly, but the camera files still can't be opened with it (it can be opened with another programme for watching pictures, my guess is Krusader might also be able to access it).
 
What could be wrong?

---

### Post by rosencrantz on 2011-04-11
What size and which card type does the camera load? Some (especially Compact Flash) are particularly slow to the point of Dolphin/Konquerors interface not being able to properly load cards with a lot of images before the camera shuts off... Did you ever try digikam? Somehow that works better for me.

I have also noticed some weird shutdown failures lately.
The command that always works for me is
sudo shutdown -h now
Cheers, rosencrantz

---

### Post by mastablasta on 2011-04-11
> **rosencrantz said:**
> What size and which card type does the camera load? 
Sony memory stick pro i think it's 2GB in size. 
 
> 
 Did you ever try digikam? Somehow that works better for me.
 
Ok i will give it a try. 
 
But the problem is that slowdown is also there for normal file browsing which is actually impossible. And the disk light is keep on and on and from time to time it is off then i click and then it's reading and reading... I would say somehting is wrong with disk if other file manager weren't having a nromal performance.
 
> 
I have also noticed some weird shutdown failures lately.
The command that always works for me is
sudo shutdown -h now
Cheers, rosencrantz
 
Perhaps some search feature got enabled that requires it to gather all data first to be able to browse later on. 
 
I will try it with -h parameter next time if it gets stuck again.
 
I just hope these issues will be solved by 11.04.

---

### Post by SeijiSensei on 2011-04-11
+1 for digiKam

Do you experience this slowness in all directories or just some?  If the latter, try deleting the .directory file at the top of that directory, and see if that helps. This fixed the performance problem for me in early 4.x versions, though I haven't had any such problems in more recent KDE releases, certainly not in 4.6.x.

If you have external devices attached, I'd try disconnecting them and see how dolphin performs.  Then reconnect them one by one and see if it changes things.

---

### Post by mastablasta on 2011-04-11
slowdown i sin home and all subdirectories. i haven't explored much arround since it's so slow. perhaps .directory file might solve it. I will try. I didnt' have porblem with original Kubuntu KDE. And like i said i don't have problem in Krusader (but my wife doesn't really like it-she uses Windows explorer on the XP maschine we have. OMG!)


EDIT: I just FIGURE OUT why it's running so slow. It is connected with this issue i posted - *buntu not playing AudioCD:  [http://ubuntuforums.org/showthread.php?t=1705396](http://ubuntuforums.org/showthread.php?t=1705396)

I just heard it going click, click , click trying to read the CD. I ejected the CD and suddenly it runs as fast as before. It could be cause i said automount all devices in the system settings!? OK now i know i need to solve this. Or take out the Audio CD :-)

---

### Post by rosencrantz on 2011-04-11
edit: depending on your PATH, you might not find shutdown with non-root login. So, correcting my previous post,
sudo /sbin/shutdown -h now
is better.
(shutdown options: -h for halt, -r for restart)

---

