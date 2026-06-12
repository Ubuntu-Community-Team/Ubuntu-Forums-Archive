---
title: "power manager config, how to log in plase"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by fatharraxman on 2010-11-23
my computer at boot after choose user is not launching in  but give an error message say power manager configuration is not installed how to fix this please

---

### Post by fatharraxman on 2010-11-23
> The message says the configuration default for GNOME  power manager have not been installed correctly please contact your adminstrator
 and the log in screen stays stick hanged up
so is not loggin in

---

### Post by fatharraxman on 2010-11-23
thank you to xchat this is how I solved the problem with chat there for the benefit of others 
> <fatharrahman> my computer at boot after choose user is not launching in  but give an error message say power manager configuration is not installed how to fix this 
<fatharrahman> any help please?
<bioterror> sudo apt-get install gnome-power-manager
<fatharrahman> where to right it it stick in the user password place
<fatharrahman> no other screen 
<aveilleux> fatharrahman: Uh, what?
<aveilleux> fatharrahman: Can you rephrase that?
<fatharrahman> when  try to log on and choose user the screen  stay at the log on screen no place to wright any command it just give you the message above I can not log in
* ridin (~joshua@cpe-76-168-105-117.socal.res.rr.com) has joined #ubuntu-beginners
<aveilleux> fatharrahman: Then... log in and run the command?
<fatharrahman> The message says the configuration default for GNOME  power manager have not been installed correctly please contact your 
<fatharrahman> and the log in screen stays stick hanged up
<fatharrahman> so is not loggin in
<fatharrahman> what to do please
<yofel> fatharrahman: press ctrl+alt+f2, that should give you a text login prompt, login, get a wired network connection (wireless is a bit tricky but not impossible) and run the command
<fatharrahman> it gave me ubuntu login: | what should I write please
<yofel> your username; press enter; your password; press enter
* st33med has quit (Ping timeout: 245 seconds)
* ThisDB_ (~thisdb@cpe-66-25-94-156.satx.res.rr.com) has left #ubuntu-beginners
<fatharrahman> thank you very much the command appeared  should I write sudo apt-get install gnome-power-manager now ?
<yofel> yes, if that doesn't help, run 'sudo apt-get remove ubuntu-desktop; sudo apt-get install ubuntu-desktop' to make sure all packages that should be there are installed
* karthick87 (karthick87@gateway/shell/shellium.org/x-xglmcmfrtzkvviht) has joined #ubuntu-beginners
<yofel> (if you are using Ubuntu Desktop)
<fatharrahman> yes I use  Ubuntu desktop but the command I wrote brought me the following answer : E: dpkg was interrupted you must manually run sudo dpkg --conconfigure -a to correct the problem, I wrote it and then rewrite the command now I logged in thank you very much Ubuntu scholars 

---

