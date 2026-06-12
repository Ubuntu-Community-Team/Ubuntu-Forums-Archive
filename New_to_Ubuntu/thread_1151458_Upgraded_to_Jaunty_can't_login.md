---
title: "Upgraded to Jaunty can't login"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by SisterNotes on 2009-05-06
[SOLVED] Recently I installed Intrepid on an old laptop (compaq Evo N610c). All was well until I accidentally pulled the power cord out. With no battery juice, the computer cut off. That was the beginning of my troubles. When I restarted I got an error that nautilus wouldn't load. After MUCH searching, I found a way to stop getting that error. But, the desktop was still not the same - no icons in the upper right corner.

So, I thought I needed to start fresh, why not go ahead and upgrade to Jaunty (maybe it would solve the problem). I launched the upgrade inside ubuntu desktop and all seemed to work out just fine.

I get all the way through the prompts, restart and get a beautiful new login screen...nevermind that before upgrading I had set up for auto login so I wouldn't have to enter a password. That's OK, I know the username and password. Or so I thought.

I get the message "Incorrect username or password. Letters must be typed in the correct case."

I managed to get to a root terminal prompt after following advice on another thread (typed "e" at the boot selection screen). From there I typed "passwd [username]"
When asked to enter a new password, I can only type one character before I'm asked to retype the password. So I retype the same one character. Then I get the message, "authentication token manipulation error".

I tried addusr and had the same single character password problem.

I'm completely in over my head! I was really looking forward to abandoning windows. But I can't get past the login screen. And if loosing power is going to cause this much trouble I'm really stuck!

Is there a do-over option? I'm glad I didn't try upgrading the desktop computer, then we'd all be stuck.

---

### Post by Didius Falco on 2009-05-07
> **SisterNotes said:**
> Recently I installed Intrepid on an old laptop (compaq Evo N610c). All was well until I accidentally pulled the power cord out. With no battery juice, the computer cut off. That was the beginning of my troubles. When I restarted I got an error that nautilus wouldn't load. After MUCH searching, I found a way to stop getting that error. But, the desktop was still not the same - no icons in the upper right corner.

So, I thought I needed to start fresh, why not go ahead and upgrade to Jaunty (maybe it would solve the problem). I launched the upgrade inside ubuntu desktop and all seemed to work out just fine.

I get all the way through the prompts, restart and get a beautiful new login screen...nevermind that before upgrading I had set up for auto login so I wouldn't have to enter a password. That's OK, I know the username and password. Or so I thought.

I get the message "Incorrect username or password. Letters must be typed in the correct case."

I managed to get to a root terminal prompt after following advice on another thread (typed "e" at the boot selection screen). From there I typed "passwd [username]"
When asked to enter a new password, I can only type one character before I'm asked to retype the password. So I retype the same one character. Then I get the message, "authentication token manipulation error".

I tried addusr and had the same single character password problem.

I'm completely in over my head! I was really looking forward to abandoning windows. But I can't get past the login screen. And if loosing power is going to cause this much trouble I'm really stuck!

Is there a do-over option? I'm glad I didn't try upgrading the desktop computer, then we'd all be stuck.

Boot into **Recovery mode**, and choose the **Command Line with Networking** option when the choices menu comes up. The networking part isn't absolutely necessary, but it won't hurt anything.

When you get the command line type  ```
sudo passwd [username]
``` and see if it will let you change the password with root privileges.

If that's a no-go, try adding a new user with ```
sudo addusr
```.

Come back and post the results - I'm still researching that error, and I'm a concerned about you upgrading before you fixed the problem you had. I've got my fingers crossed (trust me - it can't hurt my typing, might even help it) for you.

I hope this helps...

Regards,

Didius

---

### Post by SisterNotes on 2009-05-07
Didius, thank you.

I tried booting into recovery mode and selecting the comand line with networking option. After it loads, the first prompt is:
"give root password for maintenance (or type Control-D to continue):"

As you may guess, entering a password doesn't get me anywhere. entering a blank password doesn't help either. "Control-D" just brings me back to the option menu.

I didn't set a password for the root directory so I don't know how I'll get around this. I'm open to more suggestions though.

---

### Post by jacksinn on 2009-05-07
Have you tried this thread?
[http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)

Basically you boot to command line like you did but with a couple steps that you didn't' mention in your initial post. I've had to recover my password on other systems before and this worked for me.

---

### Post by SisterNotes on 2009-05-07
Jacksinn, I tried the suggested thread (and a similar thread). I get to a prompt that looks like:
root@(none):/#
I type "passwd username" (using my username of course) and get:
Enter new UNIX password: (I'm getting happy)
I type a single character, just one keyboard tap and end up with the next prompt...
Retype new UNIX password: (argh! So, I retyped my new single character password and end up with...)
passwd: Authentication token manipulation error
passwd: unchanged

hmm, I'm feeling less happy :(

why do I feel "special"...

---

### Post by SisterNotes on 2009-05-07
p.s. how do I get out of the root prompt? I typed "reboot" and get
"shutdown: unable to send message: connection refused"
I tried "shutdown -r now" and get the same message.

last time I was hear I gave up and hit the kill switch...knowing that this causes major problems (like the one I'm in). I'd rather learn how to do it right.

Thanks, I'll stand by for more ideas.

---

### Post by chellrose on 2009-05-07
> **SisterNotes said:**
> p.s. how do I get out of the root prompt? I typed "reboot" and get
"shutdown: unable to send message: connection refused"
I tried "shutdown -r now" and get the same message.

last time I was hear I gave up and hit the kill switch...knowing that this causes major problems (like the one I'm in). I'd rather learn how to do it right.

Thanks, I'll stand by for more ideas.

Try "shutdown -h now".

---

### Post by SisterNotes on 2009-05-08
Sorry, "shutdown -h now" didn't work either so I tried "Exit". Then everything froze and I had to use the kill switch.

I'm back up and running though! I like the look and feel of Jaunty.

I ended up creating a new liveCD and reinstalling as advised by Jared Jared on this post:

[http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-ibex-to-ubuntu-904-jaunty-jackalope-beta.html/comment-page-2#comment-8699]("http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-ibex-to-ubuntu-904-jaunty-jackalope-beta.html/comment-page-2#comment-8699")

Now I will get a battery and hopefully avoid future power outages.

Thank you everyone for your feedback. I'm looking forward to more time on Ubuntu...there seems to be a lot to learn - good exercise for the brain!

---

### Post by SisterNotes on 2009-05-08
I remember reading that I should close the thread once resolved, but I can't remember where I read it. Can anyone give me a hint? I think I can put this one to sleep now.

---

### Post by chellrose on 2009-05-09
> **SisterNotes said:**
> I remember reading that I should close the thread once resolved, but I can't remember where I read it. Can anyone give me a hint? I think I can put this one to sleep now.

Sure, just go to your first post, click edit, and add [solved] to the beginning of the thread title.  (At least, I think that's the official preferred syntax. :KS)

Glad you got it working!

---

### Post by Didius Falco on 2009-05-09
Glad to hear you got it working!

Sometimes, especially when you don't have a lot of data at stake, a reinstall is the easiest fix.

You can see how to mark it solved in my signature.

Regards,

Didius

---

