---
title: "Where is &quot;Remember Last Session&quot; enable?"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by held7over on 2011-09-03
In Ubuntu 10.10 Gnome I could leave apps, like Terminal open and full sized in Work Space #8 and perhaps do the same with Empathy in Workspace #1 and Thunderbird in Workspace #2, do a shut down, and have them automatically be put back into place at my next boot.

However, in Ubuntu 11.04 Classic Gnome this isn't happening. Is there something I need to enable somewhere? --Like "Remember Last Session" maybe? I have been looking around the menus, but haven't found anything yet...

I guess I forgot where it is at...

Thanks! :)

---

### Post by LowSky on 2011-09-03
The name of the application is gnome-session-properties.

Try opening it from terminal.

But I do think Ubuntu edits the file to hide this option. hmmm.

---

### Post by held7over on 2011-09-03
Hmmmm.  

Running gnome-session-properties from the commandline gives me "Startup Applications Preferences", where I have these things switched off:

Bluetooth
Check for new hardware drivers
Evolution Alarm (I no longer use Evolution)
Gnome Login Sound
HP System Tray Services
Personal File Sharing
Power Manager  (This computer is a desktop)
Ubuntu One
User Folders Update
Visual Assistance
zeitGeist Datahub

Running gnome-session on the command line appears to have drove my computer a bit crazy. I had to control-C out of it....

---

### Post by damnitdan on 2011-09-03
Do you try (in 10.04 at least):

Preferences -> Startup Applications -> Options Tab Settings ?

---

### Post by held7over on 2011-09-03
damnitdan  --  I am running 11.04 on two desktops right night now, but I went and checked on a third desktop I have yet running 10.10 and you are right, the Startup Applications Preferences app has a tab for OPTIONS, which is where I need to go to enable gnome to remember my last configurations. That tab is OPTION missing on 11.04. 

LowSky said that he thinks Ubuntu has edited the file to cause it to hide this Option Tab...

Maybe there is a way to edit the file, whatever it's name is, to have the session memory enabled again...?

---

### Post by LowSky on 2011-09-03
Found it!!!
open gconf-editor then navigate to /apps/gnome-session/options. check auto save session

---

### Post by held7over on 2011-09-04
Thanks LowSky!  

The good news is, this is obviously the right file. The bad news is, auto_save_session was already enabled. Just in case, I unenabled it and then re-enabled it and then rebooted, and my apps weren't restored and put in their workspaces. Weird. Well, it isn't a life and death situation.

And the up side, I have never used gconf-editor before, as I have always had to manually go through a file and edit it, and it looks to be quite handy! Thanks for me on to it.

---

### Post by held7over on 2011-09-09
I want to thank everyone for their thoughtful help, although we ran into a brick wall on fixing this. But as it turns out, I have ran into a lot of other little problems, nothing significant by themselves, like not being able to display a wifi reception percentage on mouse hover which I use a lot, with the exception of late yesterday I loaded an archive DVD and the OS failed to mount it, and no matter what I did, it wouldn't mount. I then rebooted back up into 10.10 and it immediately mounted and read the DVD. I then rebooted back up into 11.04 and it still wouldn't mount the DVD. So, I installed a new install of 10.10 over the 11.04. Problems solved. 

I have heard Ubuntu is going to totally drop Gnome as an alternative in 11.10 and were only marginally supporting it in 11.04. Does anyone know if that is still their plan and if they will support any other alternatives, perhaps lighter weight desktops?

---

### Post by lils001 on 2011-10-25
I just wanted to add that for anyone using 11.10 you can enable "save session" by:
Settings > Settings Manager > Session and Startup
then, at tab 'General', under 'Logout Settings' select "Automatically save session on logout"

---

