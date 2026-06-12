---
title: "Failed Rt2x00 Git installation - what's the best course of action?"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by tjsilver on 2011-03-18
Hello,

I was in the process of trying to get a USB WAP working on a very ancient Acer laptop in Maverick and one post I read suggested installing RT2x00 - so that was what I was doing when I realised the time!

So I left work with a view to continuing this morning. However, what I didn't appreciate was that I'd plugged the laptop into a socket that the office cleaners use.

Obviously, on returning to the office, I found the laptop was off.

The machine was set to hibernate on low battery power so on turning on all looked fine but it's not!

The last three lines of the Terminal read -

Initialized empty Git repository in /home/tim/rt2x00/.git/
remote: Counting objects: 2089639, done.
remote: Compressing objects:  12% (49696/386135)

but there's no further progress and the cursor is blinking away in bottom left corner.

What's my best course of action? Do I just close the Terminal and start again? Is there any 'house-keeping' I should do before starting again? 

Tim

---

### Post by andrewthomas on 2011-03-18
> **tjsilver said:**
> Hello,

I was in the process of trying to get a USB WAP working on a very ancient Acer laptop in Maverick and one post I read suggested installing RT2x00 - so that was what I was doing when I realised the time!

So I left work with a view to continuing this morning. However, what I didn't appreciate was that I'd plugged the laptop into a socket that the office cleaners use.

Obviously, on returning to the office, I found the laptop was off.

The machine was set to hibernate on low battery power so on turning on all looked fine but it's not!

The last three lines of the Terminal read -

Initialized empty Git repository in /home/tim/rt2x00/.git/
remote: Counting objects: 2089639, done.
remote: Compressing objects:  12% (49696/386135)

but there's no further progress and the cursor is blinking away in bottom left corner.

What's my best course of action? Do I just close the Terminal and start again? Is there any 'house-keeping' I should do before starting again? 

Tim Since it is only 12% done compressing the files, let alone downloading them, you could just delete the folder it was cloning into and start again from the git clone git command that you last did.

---

