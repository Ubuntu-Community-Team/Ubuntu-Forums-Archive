---
title: "Just about ready to give up and shoot Ubuntu!!!!"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by kermorvan on 2009-03-31
Hi, EVERY time I try to type anything, either in a text program or in an e-mail, the cursor takes on a life of it's own and decides to move the cursor to the middle of a block of text, usually mid word or in e-mail (evolution) to the previous e-mail underneath. Apart from this I can just "lose" the whole text I am working on. I have just spenbt an hour and a half crafting an important e-mail and not only was it sent halfway through the message, after re-doing the same email all my e-mail folders have disappeared with ALL of my Sent and Kept e-mails.
I am now up the proverbial smelly creek paddling with my hands. How clever was I to swallow the hype and get rid of the hated Windows? What genius!!!

Hopeless Regards

Steve:sad:

---

### Post by CRIMPS on 2009-03-31
Sorry to hear about your issues :(

Can you give us some more information?  Start with your hardware.  Also, what version of Ubuntu are you running.  

Help us help you :)

---

### Post by LowSky on 2009-03-31
If you are using a laptop make sure that number lock is off, as having it on can act like the up, left, right, and down arrow keys.

---

### Post by BDNiner on 2009-03-31
Yes, if you are using a laptop it sound like you Num Lock is on. Turn it off and the keyboard should stop jumping around.

---

### Post by burningapathy on 2009-03-31
If this is a laptop, then you might be having the same problem I had with my fat thumbs constantly hitting the touchpad when typing.  I followed instructions similar to this one:

[http://blog.moybella.net/2007/05/21/disabling-synaptic-touchpad-while-typing-in-linux/](http://blog.moybella.net/2007/05/21/disabling-synaptic-touchpad-while-typing-in-linux/)

to cause the touchpad to be disabled while I was hitting the keys.  It was such an awesome change that I wanted to do it in Windows as well, but couldn't find a way.  Now I prefer typing in Ubuntu because the cursor never accidentally moves.  If you are on a laptop and have a touchpad, you might want to start a new thread asking about how to disable it while typing.  The link above might work for you, but I'm not sure that will work for all laptops.  Best of luck, I know your frustration.

---

### Post by Kareeser on 2009-03-31
Make it a habit to check up periodically to see whether you're typing where you're meaning to be typing. Check after every sentence, for example. This can save many embarrassing hours later on.

Your palm may also be resting on the touchpad. Careful!

---

### Post by kermorvan on 2009-03-31
Well you all seem to be pointing to the touchpad - a considered possibility. It doesn't explain the loss of email files, or the pop-up shortcuts when a particular key is pressed while typing, or the fact this is my second attempt at a reply because it just disappeared after back paging x2.

Thanks for all the input and here are my specs

Ubuntu Release 8.10 (Intrepid)
Kernel Linux 2.6.27-11-generic
GNOME 2.24.3

Memory 1.9 GB Intel Dual Core T5500 @ 1.66GHz 
Samsung R40 Laptop

Regards Steve

---

### Post by anewguy on 2009-03-31
Actually, if your touchpad is acting up and pointer jumps around, you never know where it was when you pressed a key - it may have been over something that deletes your mail folders, it may have been over something the hides your mail folders.  If you are having serious problems, consider turning off the touchpad and using an external mouse.  I know that in the past when I had a couple of different laptops, my fat hands where always touching the dang thing even when I didn't know it;)

Dave:)

---

### Post by sgosnell on 2009-03-31
What can happen is that the cursor moves and text is selected at near the same time, and the next keystroke overwrites the selected text. You have to be careful to keep your thumbs away from the touchpad.  If the numlock is enabled, you'll also get quirky behavior.  It's not Ubuntu, it's the design of the keyboard.

---

### Post by kermorvan on 2009-04-01
It seems that it may be the touchpad, however I used the same touchpad with XP and NEVER had any problem with typing............:(

---

### Post by nothingspecial on 2009-04-01
Try this, in your menu go to system > preferences > sessions.
Click add.
Put whatever you want in the name and comment boxes but in the command box type ```
syndaemon -d -t -i 2
```

This will turn off your touchpad for 2 seconds after you touch a key. So nothing will happen to you cursor as you type. Change the 2 to whatever you want.

You have to log out and back in again for it to take effect.

---

### Post by redbob on 2009-04-01
Guys,
I was accompaining this thread because I've got a very good laptop with a very bad touchpad. It's obvious these peripheral devices were made to be used with (argh)Windows. I use an external mouse because of it. 
Nothingspecial: I'll follow your advice and run this command. I was looking for a tool to kill my touchpad, besides I like to roll up desktop cube with it!!! Eheheh...):P

---

