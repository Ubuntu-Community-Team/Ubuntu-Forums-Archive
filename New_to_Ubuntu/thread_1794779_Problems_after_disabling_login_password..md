---
title: "Problems after disabling login password."
date: 2011-07-01
forum: New to Ubuntu
---

### Post by broc5k on 2011-07-01
Hello everyone, yay first post! Anyways, I disabled the ask for password at login feature because my friend can't seem to remember my password and she needs to use my laptop. After I restarted to make sure it worked, I get this pop-up saying: 
 
"Could not update ICEauthority file /home/broc/.ICEauthority". 
 
I press close, and I get another pop-up saying: 
 
"There is a problem with the configuration server. (/us/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)" 
 
Press close again and a final pop-up saying:
 
"**Nautilus could not create the following required folders: /home/broc/Desktop, /home/broc/.nautilus.** Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."
 
After closing that last pop-up, I get nothing, it just hangs at the default background. I'm a complete noob to Ubuntu so bear with me, however I'm happy to say this is the first problem I've had with it so far :). 
 
Oh and I'm running 10.4
 
Any ideas?

---

### Post by collisionystm on 2011-07-01
My first question would be, what exactly did you do to disable the login password

---

### Post by broc5k on 2011-07-01
I went to Users and Groups then un-checked ask for password at login.

---

### Post by broc5k on 2011-07-01
Seems like someone had a similar issue here:
[http://ubuntuforums.org/showthread.php?t=1753771](http://ubuntuforums.org/showthread.php?t=1753771)
 
I'm going to try logging in as Guest and see how it goes.

---

### Post by broc5k on 2011-07-01
Ok, noob question #2, does Ubuntu not have a guest account by default?

---

### Post by ahears on 2011-07-01
> **broc5k said:**
> Hello everyone, yay first post! Anyways, I disabled the ask for password at login feature because my friend can't seem to remember my password and she needs to use my laptop. After I restarted to make sure it worked, I get this pop-up saying: 
 
"Could not update ICEauthority file /home/broc/.ICEauthority". 
 
I press close, and I get another pop-up saying: 
 
"There is a problem with the configuration server. (/us/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)" 
 
Press close again and a final pop-up saying:
 
"**Nautilus could not create the following required folders: /home/broc/Desktop, /home/broc/.nautilus.** Before running Nautilus, please create these folders, [COLOR=Red][B]or set permissions such that Nautilus can create them."
[/B]  [/COLOR]
After closing that last pop-up, I get nothing, it just hangs at the default background. I'm a complete noob to Ubuntu so bear with me, however I'm happy to say this is the first problem I've had with it so far :). 
 
Oh and I'm running 10.4
 
Any ideas?


Sounds like you logged in as root and started the XServer.... Right? Big mistake. As a result; you have changed the file permissions in the home directory causing root to own your files. You need to change the ownership of your file using the 'chown' command. 

Code:

> 

chown [COLOR=Red]user[/COLOR]:[COLOR=Red]user[/COLOR] /home/[COLOR=Red]user[/COLOR]/.ICEauthority
chmod 644 /home/[COLOR=Red]user[/COLOR]/.ICEauthority

This will change ownership of the file .ICEauthority to the user named 'user' ([COLOR=Red]replace 'user' with_* your *_User name[/COLOR]), and change file permissions to 'read/write' for the owner, and 'read' for anyone else. You can modify this if there are more files to be included.

---

### Post by broc5k on 2011-07-02
> **ahears said:**
> Sounds like you logged in as root and started the XServer.... Right? 

If I did, I have no idea how lol. I ended up formatting and doing a dual-boot install because I need a copy of Windows installed as well. Thank you everybody for all of your help though, I appreciate it.

---

### Post by eveg on 2011-07-25
for goodness sake if you're going online with an unsecured laptop, i hope it doesn't have any personal, much less financial, information on it. if you're only using it for entertainment surfing, all you'll do is pick up malicious programs and, blithely unaware, redistribute them.

---

