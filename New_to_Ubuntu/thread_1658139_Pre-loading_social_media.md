---
title: "Pre-loading social media"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by jermza on 2011-01-02
When Ubuntu loads, it doesn't start up Empathy or Gwibber or Evolution.  I added Evolution to the Startup Applications, which is fine because I check mail when I start my PC, so I don't mind the window popping up onto the screen in front of me.

However, if I add Empathy and Gwibber to the Startup Applications, then they also pop up in front of me, which is annoying since I'm not wanting to chat to anyone or check Twitter just yet.

But if don't add them to the Startup Applications, then I have to manually start them up.

Isn't there a way to have them automatically start up in the background?  (The relevant options within their settings are checked, but don't seem to do anything.)

---

### Post by ajgreeny on 2011-01-02
I don't use either of them so am not sure about this, but perhaps they start too soon if you are using the normal command in the startup applications list to start them.

It may be worth trying the "sleep" option within the command, simply to delay the startup by a few seconds.  This was needed in the past for Pidgin or it also started up in the foreground.  It can be done with a shell script, or simply by using a more complex command in the startup applications, and telling it to use bash.

Try ```
bash -c "sleep 10; empathy"
```as the startup command instead of just empathy and it may work for you.

---

