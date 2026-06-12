---
title: "unity launcher does not work"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by beew on 2011-05-17
Installed Miro in Natty and noticed that the Unity bar launcher doesn't work. When clicked it pulses for a while and then just stops. The application however can be launched from the dash.

I remember reading about the same behaviour for other applications as well, though I can't find the threads now,

---

### Post by beew on 2011-05-17
So anyone has similar experience or know a fix?

---

### Post by Gone fishing on 2011-05-17
Is that all applications?

I found that Windows Apps launched with Crossover wouldn't start. 

I booted to the classic desktop dragged the menu short cuts to a directory (these worked). I then restarted the Unity desktop and dragged these short cuts to the Unity bar - problem solved.

---

### Post by beew on 2011-05-17
No, not all applications. 

But there are also other odd behaviours like gnome-mplayer's cannot remaximize after minimizing. Clicking the icon only starts a new instance of gnome-mplayer while the old instance is still running in the background.


> I booted to the classic desktop dragged the menu short cuts to a directory (these worked). I then restarted the Unity desktop and dragged these short cuts to the Unity bar - problem solved.

That is weird. But I will try that and see if it works. Thanks.

---

### Post by beew on 2011-05-17
OK, Gone Fishing's method works! This is really strange that Unity needs the Classic Desktop to function properly. What would happen when it is no longer available? I will mark this thread as "solved" but of course it is not really solved when 1) it doesn't work out of the box even though it should and 2) you need to log into a different desktop to solve a unity problem.

---

### Post by beew on 2011-05-18
OK. This actually doesn't work because the launcher created from the classical desktop has disappeared from the Unity bar on reboot.

Now there is no thread tool to mark a thread as unsolved after it has been mistakingly marked as solved, is there?

---

### Post by Gone fishing on 2011-05-18
You need to create a folder say /home/user/icons then create a link from these onto the launcher (you will need to keep the icons in the icons folder) 

You could make this a hidden folder if you wished

---

### Post by beew on 2011-05-18
> **Gone fishing said:**
> You need to create a folder say /home/user/icons then create a link from these onto the launcher (you will need to keep the icons in the icons folder) 

You could make this a hidden folder if you wished

Yes of course! Stupid me. Thanks!

---

