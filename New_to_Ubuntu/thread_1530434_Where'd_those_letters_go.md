---
title: "Where'd those letters go?"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by DoghouseRiley on 2010-07-13
I installed Ubuntu using wubi on my Windows XP system, and everything went smoothly. However, once I had it installed and went into Ubuntu, I find that the letters 'v' and 'q' don't show up on the screen when I type them. Everything else is working wonderfully, but those two missing letters are making it difficult for me to do things. 
 
Has anyone ever seen this issue?

---

### Post by mikewhatever on 2010-07-13
What keyboard layout do you use? Check it under System->Preferences->Keyboard.

---

### Post by DoghouseRiley on 2010-07-14
I have tried all the generic keyboards, and all the Microsoft keyboards, and the letters 'q' and 'v' are missing in action. It is a Microsoft Natural Ergonomic Keyboard v.4000. It is plugged into one of the USB ports on the computer. 

Still mystified.

---

### Post by da burger on 2010-07-14
Open a terminal and run "xev"(without the quotes).

Put your mouse over the window and make sure you aren't moving it. Then press the buttons q and v and see if it generates any output. If it doesn't then those key presses are never getting to ubuntu.

---

### Post by DoghouseRiley on 2010-07-14
Okay, it was tricky to type 'xev' without the letter v working, but I figured it out with the keyboard map and clicking on the letters.

I ran xev and indeed, the letters q and v are not getting from the keyboard to the computer. I am at a loss to explain why though.

---

### Post by da burger on 2010-07-14
> **DoghouseRiley said:**
> Okay, it was tricky to type 'xev' without the letter v working, but I figured it out with the keyboard map and clicking on the letters.

I ran xev and indeed, the letters q and v are not getting from the keyboard to the computer. I am at a loss to explain why though.

I should have thought of that...

I'm afraid I can't really help you with that. Just to check, I assume that the keys still work in windows?

---

