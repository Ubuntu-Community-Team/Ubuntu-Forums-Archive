---
title: "Alas, hit and miss with printer after cup updates"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Georgia boy on 2010-06-03
Hi. After all of those updates we got for cups the other day I thought that maybe the disappearing printer would be fixed. Yesteday printer showed when wanting to print. This morning no such luck. Had to do the sudo cups bit again to show printer. Just me or are others still having the printer disappearing still?

Tom

---

### Post by philinux on 2010-06-03
> **Georgia boy said:**
> Hi. After all of those updates we got for cups the other day I thought that maybe the disappearing printer would be fixed. Yesteday printer showed when wanting to print. This morning no such luck. Had to do the sudo cups bit again to show printer. Just me or are others still having the printer disappearing still?

Tom

I would use system>admin>printing. Remove printer and add it back again afresh.

---

### Post by Georgia boy on 2010-06-03
I'll have to make sure that it's showing first before I try that. Because everytime it disappears all the options for that is grayed out on me. Can't do anything in there. Believe me, I tried. So, should I delete it and then let them try to find each other or should I do the printer add?

Thanks

Tom

---

### Post by Morbius1 on 2010-06-03
If you can't resolve this by removing and adding the printer and if the problem is that you have to restart cups at every boot then I would suggest the following:

Create a script:[FONT=sans-serif]
[/FONT]```
gksu gedit /etc/network/if-up.d/cups
```With this content:
```
#!/bin/sh
service  cups restart

```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups
```Reboot

---

### Post by Georgia boy on 2010-06-03
I'll see what happens when I turn system on in the morning. If same thing then first I'll try the remove and reinstall. If that fails then I'll do the codes that you mentioned. 
Just have to keep on plugging don't we?

Thanks all.

Tom

---

### Post by Georgia boy on 2010-06-04
This morning the printer showed, so while it was there I went ahead and did a removal/reinstall. It did a wonderful print test. Liked that. Going to check and see that it maintains showing up every time. If it don't then I'll do the terminal bit on it. 
Thanks for the advice.

Tom

---

### Post by Georgia boy on 2010-06-05
Okay, remove and reinstall of printer only lasted one day. So, I did the first command in terminal and got the window I show in the screen shot. Now, do both of the other codes go into the terminal one at a time or do I put both of them in the terminal at the same time? What happens with the other Window? 
Sorry for stupid question but, don't know which way to go next and don't want to screw something up by accident.

Thanks

Tom

---

### Post by jarmore on 2010-06-05
I have same problem.

Middle code only goes in window ... then File/Save ... to save it ... then close window.

Then last code (3rd) goes in Terminal ... then reboot. Thats what I did ... works for me ... printer is showing.

---

### Post by Georgia boy on 2010-06-05
Thanks for the explanation Jarmore. Mine was showing due to doing another remove and reinstall but I decided to go ahead and do the terminal bit also. Getting tired of the hit and miss with the printer showing or not when wanting to print something.

 I've bookmarked this thread so I can keep going back to it to try things again. I was hopping against hope that all of those cups updates that had come out before would actually had done the fix for the on and off again printer problems that we are having. Guess that wasn't one of the fixes included when those updates came out. But we can say one thing though. We are having a "Learning experience" aren't we? :)

I just got kind of confused with which command went where after I got that other window popping up. 
Well,here's wishing that everyone is having a great weekend. It's kind of a hot one for me but hey, that's what air conditioning is for right? :lolflag:

Tom

---

### Post by jarmore on 2010-06-05
Time will tell if it "sticks" Tom. You can see the file just created in your file manager ... File System/etc/network/if-up.d/cups ... and remove it if desired. If I find the same annoyance again ... I'll post back. Thanks for posting the problem ... helped me ... hopefully :)

---

### Post by Georgia boy on 2010-06-05
Hopefully this will help us out. Otherwise, we'll have to keep punting and see what happens right?:-\"

---

### Post by Morbius1 on 2010-06-06
Georgia boy, sorry for the confusion. It looks like jarmore way able to interpret my gibberish.

Not that I'm smart enough to know the exact reason for this but I don't think the problem is with CUPS. I think the problem is with upstart. In the rush to make Ubuntu boot as fast as possible some services are either not started in the correct sequence or some services are tied to the network being up before they are executed. Execute before the network is up and the service dies. Execute after and the service start successfully.

That was the theory behind placing a script in /etc/network/if-up.d. By design any script placed there will execute only after the network is up.

---

### Post by fro1269 on 2010-06-06
> **Morbius1 said:**
> If you can't resolve this by removing and adding the printer and if the problem is that you have to restart cups at every boot then I would suggest the following:

Create a script:[FONT=sans-serif]
[/FONT]```
gksu gedit /etc/network/if-up.d/cups
```With this content:
```
#!/bin/sh
service  cups restart

```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups
```Reboot

this worked like a charm.

---

### Post by jarmore on 2010-06-06
Yes .. thanks Morbius1 ... usually my printer has disappeared by now ... but still there. And thanks for the explanation of what the script actually does and possibly why its needed ... nice to know.

---

### Post by Georgia boy on 2010-06-07
Thanks for the help Morbius1. So far it's working like a champ!!
I'm going to mark this as solved. Looks like this thread has helped others with the same problems. Really appreciate the information.

Tom

---

### Post by Ithiel on 2010-06-18
This should work:

sudo nano /etc/rc.local

before the word "exit 0", insert the following line:

service cups restart

and save the file by using Ctrl + x.

---

