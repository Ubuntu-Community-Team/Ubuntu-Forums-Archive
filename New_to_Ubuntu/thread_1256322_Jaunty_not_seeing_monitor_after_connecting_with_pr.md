---
title: "Jaunty not seeing monitor after connecting with projector"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by stopping on 2009-09-02
I have no option to change the screen rez to normal 1400x after connecting to a projector. The only way I could get jaunty to use the projector was to mirror screens and go with the 800x. 

When using the projector jaunty decided that the main screen should be the projector so my normal desktop was on the projector.

Main problem in string of display problems is now my only two options for screen rez are 800x and 600x. Jaunty don't see my montior now that it has no projector and it thinks my 1400 monitor is 800. 

Paralysed by blocky vision....
 
Please Help

---

### Post by stopping on 2009-09-02
Wht th @#%@# 

Ubuntu is not ready.

[http://bryanfullerton.com/?p=162](http://bryanfullerton.com/?p=162)

How do I do this in terminal? 

I want to change the virtual resolution setting and don't know the commands.

---

### Post by st33med on 2009-09-02
You do not have to do it in the terminal.
Go to System >> Preferences >> Display.

---

### Post by stopping on 2009-09-02
Thanks for responding 33.

This, I have learned is a bug with ubuntu and gnome's "virtual resolution". 

"For some reason (BUG!) the display properties just limited the maximum resolution on the external screen to the virtual resolution it already had, instead of resetting the virtual resolution to fit the preferred size. I was limited to 1152×864, which fit inside the 900px height limit in the 2720×900 virtual resolution set when using my home external monitor."

As I said in my original post,

"Main problem in string of display problems is now [COLOR="DarkRed"]my only two options for screen rez are 800x and 600x[/COLOR]. Jaunty don't see my montior now that it has no projector and it thinks my 1400 monitor is 800."

I have only two options for resolution and they are both from 1990!

The fix is [[COLOR="Red"]here[/COLOR]]("http://bryanfullerton.com/?p=162") but I don't know how to do it in terminal. He says how to do it but don't give the command line breakdown.

---

### Post by stopping on 2009-09-03
You would think driving monitors of various sizes would be easy for ubuntu.

After editing the /etc/X11/xorg.conf file I have some resolution back but it is not a fix. The next time I use this flailing OS to present work on a projector it will fail again in front of a crowd and ubuntu brand will be there for everyone to see. 

Unless of course I simply use windows.

I want to ubuntu succeed but I am growing bitter.

Please don't bother responding to this as I will not be consulting this unhelpful forum any time soon.

---

