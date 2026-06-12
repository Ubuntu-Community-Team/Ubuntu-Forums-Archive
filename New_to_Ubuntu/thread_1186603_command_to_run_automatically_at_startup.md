---
title: "command to run automatically at startup"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-13
Just installed jaunty (32 bit).  Nautilus doesn't work UNLESS I open a terminal and type

sudo chmod a-r /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so

and this is unpleasant to have to do every time I boot.

Is there a way (that beginners like me can understand) I can put that command in a file and have it executed automatically at startup?

---

### Post by Celauran on 2009-06-13
You could alias it temporarily just to save you some typing until you're able to find and address the cause of the problem.

---

### Post by Crunchy the Headcrab on 2009-06-13
I have a similar problem on Jaunty 64.  I have to run

> sudo sh -c "echo 0 > /sys/class/leds/asus\:\:touchpad/brightness" to turn off the lights on my Asus touchpad.  However this is a pain to run every time my computer is turned on.  Plus I have users without administrator access so they can't use the sudo command.  This touchpad is very bright and annoying, it also heats up the wristpad unnecessarilly.

I've made a shell script so that I can just click it, insert my password and turn off the pad.  Now I need to know how to make it run at startup without requiring a password.  Editing sudoers?  Is that safe?

---

### Post by raymondvillain on 2009-06-13
> **Celauran said:**
> You could alias it temporarily just to save you some typing until you're able to find and address the cause of the problem.

This sounds like something wonderful.  Where does one learn to alias?

Thanks for your suggestion.

---

### Post by ENigma885 on 2009-06-13
Y don't u use (System>>Preferences>>Sessions)?
Yet, I'm not sure of wat u have to do to execute a command with root privileges with this.

---

### Post by synapsys on 2009-06-13
System >> Preferences >> Startup Applications >> Add

Enter command just as you would in terminal. 
Add '&& exit' to the end of command to close terminal or '&' to leave it open
Give it a name.
Check the box next to it.

That should slap a nice big bandaid on there.

Alias howto:
[http://www.linfo.org/alias.html](http://www.linfo.org/alias.html)

---

### Post by Crunchy the Headcrab on 2009-06-13
@ synapsys that doesn't work for commands that require root access does it?

---

### Post by shifty_powers on 2009-06-13
it should do,it will just ask for your password...

---

### Post by synapsys on 2009-06-13
[http://ubuntuforums.org/showthread.php?t=889113](http://ubuntuforums.org/showthread.php?t=889113)

---

### Post by jakupl on 2009-06-13
This is probably easier [http://ubuntuforums.org/showthread.php?t=172173](http://ubuntuforums.org/showthread.php?t=172173)

---

### Post by raymondvillain on 2009-06-13
Thank you synapsys!

I followed your advice and it works fine.

Now I have nautilus back.  Hope that the underlying bug is fixed before the next release.

---

### Post by Crunchy the Headcrab on 2009-06-14
I just added the command to /etc/rc.local.  It doesn't require a password and loads before login.  Thanks Jakupl!

---

