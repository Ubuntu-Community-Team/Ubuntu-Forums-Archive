---
title: "Mouse pointer and citrix"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by towe0609 on 2010-03-05
Dear all

I use Lotus Notes for email etc through Citrix. I've managed to install Citrix OK but have 2 issues with the mouse.

1. The mouse pointer is misaligned (it is actually above where you see it on the screen - so to click something, you hold the pointer a few mm below it). I have worked out that if the window is not 'maximised', this alignment is fixed. So while this would be nice to fix, not essential.

2. In the left hand pane, where the folder navigation is, the mouse completely dissappears, and using the 'twisties' to open subfolders etc is really hit and miss. Is there some way I can get my mouse back?

I've had Ubuntu for a matter of days only - so please keep it simple! I'd really appreciate some help!

Tim

---

### Post by Kulgan on 2010-03-05
Do you have desktop effects enabled? This sometimes causes odd rendering errors like this.

(System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects)

---

### Post by towe0609 on 2010-03-06
Thanks Kulgan - I have already tried changing this setting, and unfortunately it makes no difference to this problem.

Any other suggestions?

---

### Post by towe0609 on 2010-03-08
I used Applications > Accessories > Take Screenshot to try to take some pictured to post here to show my problem - and what do you know - the mouse pointer is shown in the screenshot, even though it cannot actually be viewed on the screen.

Does that give anyone a hint as to the solution to this?

---

### Post by Kulgan on 2010-03-08
Sorry for delay.

1. I suspect that this has to do with a misunderstanding between the two systems. Many apps, such as tightvncviewer, don't expect you to have a cursor when viewing remotely, instead giving you a square point which does the same thing without lagging. It could be that the pointer is being rendered directly on top of this instead of offset to the "pointer" part because one side does not expect there to be a cursor in the first place. I think you'll just have to live with that... 

As for 2. 
What client version do you use? 

The following post suggests mouse problems at least up to 11.100, 
[http://forums.citrix.com/thread.jspa?messageID=1440191](http://forums.citrix.com/thread.jspa?messageID=1440191), and "some of the pointers appear to have pixels lost while others are presented as fully see-through" seems to match your problem.

---

### Post by towe0609 on 2010-03-09
> **Kulgan said:**
> 
As for 2. 
What client version do you use? 


11.100 from [http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755)

Thanks for the link. I've tried to register for that Citrix forum to post there. Seems registration is not instant, and I'll have to wait.

---

### Post by Kulgan on 2010-03-09
Great, I hope that you find a solution. 
Please post back for the record if you do so.

-K

---

