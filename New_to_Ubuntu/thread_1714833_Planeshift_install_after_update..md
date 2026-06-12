---
title: "Planeshift install after update."
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Newuser901 on 2011-03-25
I install the game. get into it from the applications/game window(before hitting play) where it lets me change setting wants me to update(yes/no) and repair etc. Did a repair and or let it update(I can repair till I'm blue in the face no problem). Same result either way. after the update though It shuts down and whenever I try to restart the app from applications games on the gui I always get this error:

Could not launch 'PlaneShift'

Failed to execute child process "/opt/PlaneShift/pslaunch" (Permission denied)

I have seen the thing and tried it but can't get it to work where you do this.

One thing said use chmod -R user:group /filepath/folder(or whatever they said) I got it to enter without errors, unless I still did it wrong, but nothing happened. what should I do. How do you do that correctly. Or is that the wrong thing to do?

How do I get the gui starting method working?

I also can't get the confirmation email for the game from registering but that is another issue.(told it to send again.) don't know if this is an issue or not. 8) have to look up on their forums.


sudo chown -R your_username_here:users /opt/PlaneShift/ <--- the command they say to use. got it to enter and go to an empty command line with no errors but doesn't affect it. Do I have to enter it from a certain location from that path? I'm not sure about the username:users part either. I just put in my user name and it worked. I also put in combinations of user  user:user :user user:, since i don't know my group and I think they are the same, and they all do the same thing once I realized I put PlanetShift in the folder name at the end instead of PlaneShift.

I am using ubuntu 10.10 btw. Unless that changes when you have to pick out an option on startup where you can do memtest or do recovery modes. I always pick the newest version and no recovery if it pops up.

---

### Post by Newuser901 on 2011-03-25
Ok. I found the way to do it form a post in search. could't find it at first. or looked up the wrong things. Now I hit play and it flickers back to the game. I'll have to play with the settings etc.

Used:

sudo chmod -R a+rx(or a+rwx) /opt/PlaneShift/ seems to have solved the first problem. Betting the next might be the screen resolution. Or I have to start hunting again.

And I did a repair and then found it would go to the login screen when I turned the resolution to something less than my screen. Not equal... Is that always an issue? curious before I mark this as solved. Unless someone can offhand answer about the email not sending my thing to activate. I haven't looked it up yet but... hey why not. 8)

Fixed the email thing too. Forums said something about some emails or isps blocking the verification email. Not to say too much but I have at&t/yahoo the main account won't take it but the junk filter/side ones work. So if you have it you can use your alt @yahoo.com junk filters to get it. 8p

YAY game!! time to try it finally. It's been two days. lol No thanks to any of you 8p hehe

---

