---
title: "Failed to execute child process."
date: 2009-09-28
forum: New to Ubuntu
---

### Post by pirate paul on 2009-09-28
Hi, When I try to launch Vodafone mobile connect I get>

Details: Failed to launch child process"/home/paul/.update-manager-core/meta-release" (Permission denied)

Does this mean there is some sort of child lock, if so how do I remove it.

Thanx.

---

### Post by jimingkui on 2009-09-28
Sounds like file permission problems

---

### Post by philinux on 2009-09-28
> **pirate paul said:**
> Hi, When I try to launch Vodafone mobile connect I get>

Details: Failed to launch child process"/home/paul/.update-manager-core/meta-release" (Permission denied)

Does this mean there is some sort of child lock, if so how do I remove it.

Thanx.

Did you install something using sudo. Anyway do this and post back.
Open a terminal, Apps>access>terminal
Copy and paste the command in to the terminal.

```
ls -la ~/.update-manager-core/meta-release
```

---

### Post by pirate paul on 2009-09-28
Hi, apps>accessories>terminal            >pasted > command not found.

---

### Post by philinux on 2009-09-28
Works fine here.

```
ls -la ~/.update-manager-core/meta-release
-rw-r--r-- 1 philcb philcb 4447 2009-04-28 11:00 /home/philcb/.update-manager-core/meta-release

```

---

### Post by pirate paul on 2009-09-28
Tried that command not found.

---

### Post by philinux on 2009-09-28
Does

```
ls
``` 

and

```
ls -la
```

work. They are lower case L's by the way.

---

### Post by pirate paul on 2009-09-28
ls comes up with a few things.

ls -la comes up with a long list.

I spose that means yes.

Thanks for your time and skill by the way.

---

### Post by philinux on 2009-09-28
In a terminal.

```
cd /home/paul/.update-manager-core
```

Press enter. You should see you have change directory.

Then

```
ls -la
```

Press Enter.

---

### Post by pirate paul on 2009-09-28
paul@paul-laptop:~$ cd /home/paul/.update-manager-core
[email]paul@paul-laptop:~/.update[/email]-manager-core$ 
[email]paul@paul-laptop:~/.update[/email]-manager-core$ ls -la
total 16
drwxr-xr-x  2 paul paul 4096 2009-09-16 14:08 .
drwxr-xr-x 44 paul paul 4096 2009-09-28 13:19 ..
-rw-r--r--  1 paul paul 4447 2009-09-16 14:08 meta-release
[email]paul@paul-laptop:~/.update[/email]-manager-core$

---

### Post by philinux on 2009-09-28
Ok so the permissions are fine. Nothing wrong there.

When you say launch Vodafone mobile, Is there an icon you are clicking?

---

### Post by alienclone on 2009-09-28
sorry to reply to a thread that i have no help to offer on, but i couldnt resist..

"Failed to execute child"  or so the main page led me to believe. (see attached screenshot)

---

### Post by pirate paul on 2009-09-28
Yeh there is an icon for vodafone, when I click on it the wheely thing goes round for a min then stops. When I right click one of the options is launch.

I have another launch icon, which when I click on it, it gives the same reply.

I am a bit slow with computers, I need to top up my vodafone pay as you go before I run out of cred. To top up using their web site, the send an activation code to my SMS, but I cannot get the SMS box to come up. It seems like some sort of child lock.

---

### Post by philinux on 2009-09-28
Ok right click on this icon and choose properties.
Copy whatever is shown in "command" and paste it into a terminal. Hit the enter key.

Any errors will show up in the terminal when you try to lauch. Copy and paste those back here.

---

### Post by pirate paul on 2009-09-28
vodafone-mobile-connect-card-driver-for-linux

Sorry it took so long, I was reading the other stuff, from Ailenclone, I thought you had gone for a cup of tea achrrrrm 

Thanx.

---

### Post by philinux on 2009-09-28
> **pirate paul said:**
> vodafone-mobile-connect-card-driver-for-linux

Sorry it took so long, I was reading the other stuff, from Ailenclone, I thought you had gone for a cup of tea achrrrrm 

Thanx.

If that is what shows up in the "command" box then paste that into a terminal and hit enter. Post back any errors.

---

### Post by pirate paul on 2009-09-28
_SomeApplicationRunner(config).run()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 411, in run
    self.application = self.createOrGetApplication()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 494, in createOrGetApplication
    application = getApplication(self.config, passphrase)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 505, in getApplication
    application = service.loadApplication(filename, style, passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/application/service.py", line 390, in loadApplication
    application = sob.loadValueFromFile(filename, 'application', passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/persisted/sob.py", line 215, in loadValueFromFile
    exec fileObj in d, d
  File "/usr/share/vodafone-mobile-connect/gtk-tap.py", line 34, in <module>
    from vmc.common.startup import create_skeleton_and_do_initial_setup
exceptions.ImportError: No module named vmc.common.startup

Failed to load application: No module named vmc.common.startup

paul@paul-laptop:~$

---

### Post by philinux on 2009-09-28
> **pirate paul said:**
> _SomeApplicationRunner(config).run()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 411, in run
    self.application = self.createOrGetApplication()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 494, in createOrGetApplication
    application = getApplication(self.config, passphrase)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 505, in getApplication
    application = service.loadApplication(filename, style, passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/application/service.py", line 390, in loadApplication
    application = sob.loadValueFromFile(filename, 'application', passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/persisted/sob.py", line 215, in loadValueFromFile
    exec fileObj in d, d
  File "/usr/share/vodafone-mobile-connect/gtk-tap.py", line 34, in <module>
    from vmc.common.startup import create_skeleton_and_do_initial_setup
exceptions.ImportError: No module named vmc.common.startup

Failed to load application: No module named vmc.common.startup

paul@paul-laptop:~$

No idea what that is. Did you install some software from vodafone, or just plug a mobile dongle in.

---

### Post by pirate paul on 2009-09-28
I plugged in the dongle, no icon but vodafone worked any way. When I ran out of cred I went to vodafone with my laptop to top up, they could not do it because they need an SMS to send the activation code to, so I reinstalled windows toped up, reinstalled linux and spent a couple of weeks getting the icon to come up.
Thats as far as I have got, I know it can be done, I had diferent threads to get that far but they fizzled out when they became confusing.

---

### Post by philinux on 2009-09-28
> **pirate paul said:**
> I plugged in the dongle, no icon but vodafone worked any way. When I ran out of cred I went to vodafone with my laptop to top up, they could not do it because they need an SMS to send the activation code to, so I reinstalled windows toped up, reinstalled linux and spent a couple of weeks getting the icon to come up.
Thats as far as I have got, I know it can be done, I had diferent threads to get that far but they fizzled out when they became confusing.

Ok, well good luck. Sounds like you need to dual boot.

---

### Post by pirate paul on 2009-09-28
Yea err thanks any way.... I am gona mark this as solved , even though its not.... start again when I have got time.

PS. Burscough FC rule the globe.

---

### Post by Staccs8 on 2010-11-29
Sorry it took a year to get to this. I only just registered. The error you are having is caused by a permissions fault. Testing in the terminal will not show a file permissions error as the problem is being localized at the program launch. You need to access the program with root privileges. Once you have access to root privileges, either in the file manager (which is easiest for Noobs) right click the program you are having difficulties with. Access 'properties' and then click the 'permissions' tab. Make sure to check the "Allow Executing file as Program" box. Make sure to hit the 'close' button. And that should be all! And more questions should be scooped up by other more patient Linuxers. Have fun!

---

