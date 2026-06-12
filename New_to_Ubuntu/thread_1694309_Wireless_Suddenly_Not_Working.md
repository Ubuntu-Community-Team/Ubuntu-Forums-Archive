---
title: "Wireless Suddenly Not Working"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2011-02-24
In the morning, my wireless was working. I came home in the afternoon, and no wireless. I have to authorize any updates, so that didn't happen while I as gone. 

I restarted the router. Nothing

I restarted the computer. Nada.

I thought maybe I inadvertently picked up a stray virus. Not likely, but possible, to a point (hey, I'm grasping at straws here). I had been meaning to roll back from 10.10 to 10.04 for a few months now anyway, so I spent last night backing up my stuff and installing Lucid. 

I made sure updates were installed, wireless drivers installed (first option-Broadcom B43 wireless driver, second option Broadcom STA wireless driver).

I'm stumped.

What factors affect a previously-working wireless system that can cause it to go kerflooey like this? Auto eth0 works fine, it's how I'm able to post this message. Logic says to me that it's gotta be something within the router/modem. I checked the threads in Absolute Beginner and didn't see anyone with a similar problem (working wireless-->non-working wireless).

I'm fairly comfortable running things from the command line, although I'm still at a 
1. Follow
2. Basic
3. Steps
4. Exactly As Written
level-- trained primate, unable to extrapolate, intuit, or diagnose. A big advantage is that this system is not completely set up, so I can reinstall anything and start over.

---

### Post by yeats on 2011-02-24
This was happening on my wife's Toshiba laptop for a while, and it turns out that the graphics card was getting really hot, which made the wireless card automatically switch off and it could not be fixed until I removed all power sources (including the battery) for a minute or so, then turned everything back on.  Can you try that, just in case it's that easy to fix?

Otherwise you'll need to provide some more information, including the full hardware specs (wireless card model especially) and eventually some system logs.

> I thought maybe I inadvertently picked up a stray virus. Not likely, but possible, to a point (hey, I'm grasping at straws here).

Nope.  The fact that it also doesn't work on a fresh install points to a hardware issue.

---

### Post by grahammechanical on 2011-02-24
Here is a link to the trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by Amanda HazLaPaz on 2011-02-24
I'm marking this thread [SOLVED], but only because sheer stupidity trumped dumb luck.


I was so fixated on the dialog coming up and then typing in the keychain password that I wasn't actually READING what the dialog said. Inputting the password FOR THE ROUTER was what just got me back on the wireless. Argghh

I'm so sorry to have bothered everyone, but maybe you at least got a smile out of it and said 

1- "Yep, I've done something equally dumb, but I was never so foolish as to write the details in a thread" 
OR
2- "Crazy lady, RTFM!"

So, yes, the moral of the story is always read the instructions, and make sure you READ the instructions, don't just assume it looks like those seven other similar dialogs you often see while continuing the same fruitless action.

Thank you, yeats for reading and responding (glad you got your wife's laptop fixed), and grahammechanical for pointing me to the troubleshooting guide (invaluable!)

---

### Post by grahammechanical on 2011-02-24
You never actually said that you were being asked to authenticate the connection, which then tried but failed to connect.

I have made the same mistake of putting in the wrong password myself. So, I know the error and the fix. Some who have this problem insist that they are putting in the correct password. For anyone who is reading this thread, I think that it is best to double check the silly, stupid things before doing the more drastic things, like using a hammer to fix it.

Regards.

---

### Post by Amanda HazLaPaz on 2011-02-24
> **grahammechanical said:**
> You never actually said that you were being asked to authenticate the connection, which then tried but failed to connect.

What I thought I saw in the small dialog that popped up was a keychain (keyring?) confirmation. The shape and size of the dialog looked just like the process I needed to go through for starting my wireless each time I restarted the computer.

What actually was popping up was a "please validate your login to the router" dialog. When I finally *paid attention*, I got much better results (i.e., the correct information was input and I got the result I desired).



> **grahammechanical said:**
> For anyone who is reading this thread, I think that it is best to double check the silly, stupid things before doing the more drastic things, like using a hammer to fix it.


Well said! Even when you're **sure** everything is correct, it's worth it to take a careful look and doublecheck all settings and dialogs.

---

