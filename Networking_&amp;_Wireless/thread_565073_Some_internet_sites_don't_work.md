---
title: "Some internet sites don't work"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by JFonner on 2007-10-01
I have read other threads like this and still can't figure out my problem.

Here is a summary:

I recently moved and since the move, my duel booting Windows/Ubuntu (Feisty 
Fawn) computer will only access all internet sites from the Windows side.

On the Ubuntu side, only a few internet sites work.  Google and Gmail both work.  Even Ubuntu.com won't work.

My labtop is running off the same router and it's only operating system is Ubuntu, thus I know it's possible, plus before the move I did not experience any problems.  I even tried a Fedora live cd and the same problems it's the exact same problem.  

I have read about MTU's and don't really understand

---

### Post by gautada on 2007-10-01
I have posted a similar problem on this [thread]("http://ubuntuforums.org/showthread.php?t=541299").  Maybe a firefox issue.  But yours sounds different.

---

### Post by JFonner on 2007-10-02
I can't try another web browser because I cannot connect to the software sites.  

This is really frustrating, anyone else have any ideas???

---

### Post by Lambert on 2007-10-02
> **JFonner said:**
> I can't try another web browser because I cannot connect to the software sites.  

This is really frustrating, anyone else have any ideas???


Open up network tools (system->administration->network tools) click on the tab ping. Enter this in the box [COLOR=SeaGreen]**91.189.94.199**[/COLOR] and see what your results are.

If you get succesful packets 100% then the problem is in the dns server settings. If it doesn't work, then we'll have to dig a little deeper.

---

### Post by JFonner on 2007-10-02
Ok, when I did the ping, I recieved 100% on the packets?

How do I fix the DNS settings?

Thanks,

---

### Post by noob12 on 2007-10-02
Try this thread:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by kevdog on 2007-10-02
Your hosts file arent blocking these sites are they??

---

### Post by JFonner on 2007-10-03
no, it is a home network, so I should have access to everything.  I have access on the windows side of the machine.

It's weird because I tried a Fedora Live CD and had the exact same problem, it's selective sites.  I can get to Google, my work email, and certain others, then other sites like CNN.com or ubuntu.com just never load.

I'm gonna try the commands from the last post

---

### Post by JFonner on 2007-10-20
Well 2 weeks of non-stop fiddling, tweeking, cursing and almost giving up, I decided to try one more approach. 

I grabbed a brand new network card (D-Link) from a friends house and put it into my computer, and wahoo!!, no more problems.   The actual problem must be somewhere with on the onboard ethernet card.  At this point, I don't really feel like investing any more energy into the issue, it now works.

I feel a bit guilty about not trying to work through the problem and understand it completely, yet I have other things in my life that are a bit more important.

---

