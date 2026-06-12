---
title: "Cliche Mouse &amp; Keyboard Problem (Please HELP)"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by 2soos2 on 2011-06-23
(I'm a complete newbie here.) When I installed Ubuntu 11.04  I noticed that there were problems with the mouse and keyboard. After some time or maybe after triggering something, the right click stops working and you can't type with the keyboard. You can however press "CTRL + ALT + DELETE" to launch the shutdown screen. This was happening very frequently so I wasn't impressed with Linux, but then I installed the updates and I noticed that it stopped, or at least I thought it did, but yesterday it happened again! :(:(
I think I did my fair share of searching on the Internet for the solution to this problem. Lots of people claim that turning off key repetitions solves it, but I tried that and the problem pursued. Some people suggested typing something in the terminal. I didn't try it, but the posts that I read said that it didn't work.

Is there an OFFICIAL solution to this problem? Or some update or patch or something to download that can PERMANENTLY fix this?

Thank you. ;)

---

### Post by Beacon11 on 2011-06-23
Okay, I have a couple questions. Most importantly, have you tried different mice and keyboards? If so, have you tried switching the mouse from right-handed to left-handed (thus swapping left and right click) to see if it's actually the software-defined "right click" or the mouse button most to the right?

---

### Post by 2soos2 on 2011-06-23
You could say I've tried different keyboards, as I'm using a laptop (with its built-in keyboard) and a USB keyboard attached. As for the mouse, you could say I've used different mice because there's the built-in touch pad and I have a USB mouse plugged in. The problem is consistent with both. I doubt it's a matter of left-right configuration because I'd doubt that the layout spontaneously changes. I think it's a problem with Ubuntu. I'm not the first to have this problem.

---

### Post by Beacon11 on 2011-06-23
> **2soos2 said:**
> I doubt it's a matter of left-right configuration because I'd doubt that the layout spontaneously changes. I think it's a problem with Ubuntu. I'm not the first to have this problem.

Relax man, I wasn't questioning your sanity. That was a troubleshooting step. I want to know if the problem is the actual hardware right-click (could be a pretty low-level issue) or if the issue is the software handling of the right-click. So, what I want is this: If you change the mouse from right- to left-handed, which mouse click has an issue? Right or left?

---

### Post by 2soos2 on 2011-06-23
> **Beacon11 said:**
> Relax man, I wasn't questioning your sanity. That was a troubleshooting step. I want to know if the problem is the actual hardware right-click (could be a pretty low-level issue) or if the issue is the software handling of the right-click. So, what I want is this: If you change the mouse from right- to left-handed, which mouse click has an issue? Right or left?

Ah, sorry. I get what you're saying. You're trying to pinpoint the  problem by having me change the layout. The only problem is that I can't  change the mouse layout because when I encounter this problem because  although the left click works, it doesn't work properly. I can't click  on anything on the top tab in GNOME, so I can't access the system  settings, which means I can't change the mouse layout. To test this, I'd  have to change my mouse layout, and wait until this error happens.

---

### Post by Beacon11 on 2011-06-23
> **2soos2 said:**
> ... although the left click works, it doesn't work properly. I can't click  on anything on the top tab in GNOME, so I can't access the system  settings...

Ah, interesting, you didn't mention that; so it works other than the panel not responding? Can you move windows around etc.? If not, it makes it sound more like X is locking up. After it happens, try looking for issues in /var/log/xorg.0.log. You might also check out /var/log/messages.

---

### Post by amjjawad on 2011-06-23
Hello and Welcome :)

When you start up your machine and get the login screen, try to choose **GNOME Classic Session** or **No Effect Session**. Check whether you still get the same issue or not?!

I'm suspecting it's a Unity Issue more than an Ubuntu Issue.

---

### Post by 2soos2 on 2011-06-27
Thank you for your help,but...
In response to your post amjjawad:  
I'm using GNOME classic session. I don't like unity nor do I use it. So it's not a Unity issue, but rather a Ubuntu one. See the links below.

Thanks everyone for the suggestions, but I'm guessing you guys don't know the solution to this problem.
Here are some links to show that this is a common problem amongst users switching from Windows. I'm thinking of switching back if I don't get this problem along with others solved soon.

[http://www.linuxquestions.org/questions/ubuntu-63/keyboard-and-mouse-freeze-in-ubuntu-10-04-a-811030/](http://www.linuxquestions.org/questions/ubuntu-63/keyboard-and-mouse-freeze-in-ubuntu-10-04-a-811030/)
[http://www.linuxquestions.org/questions/linux-hardware-18/keyboard-and-mouse-and-ubuntu-freeze-481105/](http://www.linuxquestions.org/questions/linux-hardware-18/keyboard-and-mouse-and-ubuntu-freeze-481105/)

---

### Post by amjjawad on 2011-06-27
> **2soos2 said:**
> Thank you for your help,but...
In response to your post amjjawad:  
I'm using GNOME classic session. I don't like unity nor do I use it. So it's not a Unity issue, but rather a Ubuntu one. See the links below.

Thanks everyone for the suggestions, but I'm guessing you guys don't know the solution to this problem.
Here are some links to show that **this is a common problem amongst users switching from Windows.** I'm thinking of switching back if I don't get this problem along with others solved soon.

[http://www.linuxquestions.org/questions/ubuntu-63/keyboard-and-mouse-freeze-in-ubuntu-10-04-a-811030/](http://www.linuxquestions.org/questions/ubuntu-63/keyboard-and-mouse-freeze-in-ubuntu-10-04-a-811030/)
[http://www.linuxquestions.org/questions/linux-hardware-18/keyboard-and-mouse-and-ubuntu-freeze-481105/](http://www.linuxquestions.org/questions/linux-hardware-18/keyboard-and-mouse-and-ubuntu-freeze-481105/)

I do respect your opinion and I would expect you do the same ;)

You're judging in advance and assume something that may not be correct at all.
I have been installing Linux (Ubuntu or any other distributions) on many machines ... from Pentium II (366MHz and 64MB RAM) on a broken 12 years old laptop to an HP Pavilion Core i5 Laptop. I have never faced any issue and I've using Windows all my life so "switching" has NOTHING TO DO with that :)

Also, don't assume that some solutions/steps won't work JUST because someone else tried it and failed.

Above all, don't assume you have searched for a solution. People sometimes spend their entire life to find something.

And in case you did not find anything, this is not a failure, you just found 10,000 ways that did not work for you :)

Don't blame Linux/Ubuntu. 

NOTHING called impossible in this world.

I'd rather spend my life finding a solution for Linux's problems than using Windows for few mins. I just can't.

ALL THE BEST and please don't be offended, you'll find the help you need but try to be patient ;)

Edit:
And if Ubuntu did not work well with you, there are tons of other alternatives: [http://distrowatch.com/](http://distrowatch.com/)

Remember, you can always TRY without installation. You don't have to "Install" Linux, you can try it on your machine and see whether your hardware will work or not.

---

### Post by Beacon11 on 2011-06-27
> **2soos2 said:**
> [http://www.linuxquestions.org/questions/ubuntu-63/keyboard-and-mouse-freeze-in-ubuntu-10-04-a-811030/](http://www.linuxquestions.org/questions/ubuntu-63/keyboard-and-mouse-freeze-in-ubuntu-10-04-a-811030/)
[http://www.linuxquestions.org/questions/linux-hardware-18/keyboard-and-mouse-and-ubuntu-freeze-481105/](http://www.linuxquestions.org/questions/linux-hardware-18/keyboard-and-mouse-and-ubuntu-freeze-481105/)

Huh. Those links don't really look anything like your problem. They both describe what sound like hard freezes, you don't. You can move your mouse, and you can type ctrl+alt+del. I have yet to find any problems similar to yours. You have also not responded to my troubleshooting suggestions. How do you expect people to help you? Best of luck with Windows.

---

### Post by 2soos2 on 2011-06-27
EDIT:  I can NOT move windows when this problem happens.

I'm sorry Beacon. I haven't checked to see whether I can move windows or not when it happens. But here's the log file attached.
Thanks again.

EDIT:  I just noticed that I wasn't allowed to post the log files, so I zipped them, and here they are.

---

