---
title: "Not letting me enter text in the terminal"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by marteney1 on 2009-11-16
First off, I am a super-noob to Linux, and after some light research I decided to try Ubuntu. I love it so far. The problem I am having started when trying to install Flash player (imagine that). 

I found the commands online and the instructions and followed them to the best of my ability, but when I enter a command, is asks for me to enter my password. When I try to type it in, it doesn't do anything. The flashing cursor stops flashing while I am pushing buttons, but no text gets entered. I even tried copying it from a word processor document and pasting it in there. Still no luck. So I hit return, and it just says "sorry, try again."

Am I missing something here (this is probably the case), or is terminal not working correctly?

---

### Post by drs305 on 2009-11-16
It's a security feature. Just type your password when asked. You won't see anything but it is being entered. When you have typed it, press ENTER. 

Welcome to Ubuntu and the Ubuntu forums.

---

### Post by marteney1 on 2009-11-16
Very awesome, thank you very much. I thought I had been trying that, but apparently my fat fingers like to hit the wrong keys :)

---

### Post by tom.swartz07 on 2009-11-16
glad we got everything solved!

dont hesitate to come here for support in the future!

We do ask that you please mark this thread as solved 'thread tools/mark as solved' so that other people could learn from your question!

Thanks and enjoy!

---

### Post by aysiu on 2009-11-16
It's not really a security feature. It's an inconsistency that is too troublesome to fix.

More details here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by drs305 on 2009-11-16
> **aysiu said:**
> It's not really a security feature. It's an inconsistency that is too troublesome to fix.

Well, it is an inconsistency, but according to Colin Watson in the bug report:
> 
I don't particularly want to change this in shadow; I would get complaints citing security (i.e. you can look over somebody's shoulder and see the number of characters in their password).

So why it was created the way it was. or at least why it wasn't fixed, is probably open to debate.  Of note, the bug report also contains some methods to add visual feedback.

The main reason I posted this was to tell our new user that once a problem is solved there is a way to mark so. Go to the "Thread Tools" link near the top right of the first post. You can mark it solved there. "Solved" can also be removed from a thread here.

Marking a post 'SOLVED' allows helpers concentrate on unresolved threads and assists those with similar issues look for threads which contain a solution.

---

