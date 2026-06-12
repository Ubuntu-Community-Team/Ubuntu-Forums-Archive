---
title: "failure to suspend?"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Stord on 2010-07-26
On my laptop, i like to put my computer into hibernate and immediately shut the lid. However, each time i do this i get an error message when i go back to my computer:

'Failed to suspend
Your computer failed to suspend.
The failure was reported as: Sleep has already been requested and is pending'

Any way to get around this? It happens every time.

---

### Post by Jazzy_Jeff on 2010-07-26
Sounds like a hardware issue. How about telling us what computer you have.

---

### Post by Zeike on 2010-07-26
Are you waiting until your laptop is hibernating before shutting the lid?

The only way I can think to not have to do that is to just set your computer to do nothing when the lid is closed.  Or you should set it to hibernate when the lid is closed, and just close the lid when you want it to hibernate.

---

### Post by CLCressman on 2010-07-26
> **Stord said:**
> On my laptop, i like to put my computer into hibernate and immediately shut the lid. However, each time i do this i get an error message when i go back to my computer:

'Failed to suspend
Your computer failed to suspend.
The failure was reported as: Sleep has already been requested and is pending'

Any way to get around this? It happens every time.

If you are not waiting for the computer to shut down before you close the lid and you have your computer set to suspend when you close the lid, then you are asking it to do two things at once. I would suggest you set it to hibernate when you close the lid, then just close the lid when you are ready to hibernate.

---

### Post by egalvan on 2010-07-26
> **Jazzy_Jeff said:**
> Sounds like a hardware issue. How about telling us what computer you have.

Further to Jazzy_Jeff;

How much RAM does it have?

What size swap?

To HIBERNATE you **must** have swap equal or larger than RAM.
Verify it.

---

### Post by Stord on 2010-07-27
Well, setting it to hibernate on lid close worked fine! So i guess ubuntu cant handle me telling it to hibernate and then immediately closing the lid. I have a compaq presario laptop, 7.9 gb swap,  and
2.7 gb memory.

---

