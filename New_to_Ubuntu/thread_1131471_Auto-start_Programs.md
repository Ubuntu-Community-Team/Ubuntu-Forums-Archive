---
title: "Auto-start Programs?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by dmaxel on 2009-04-20
Is it possible to automatically run a script when you start your computer? I have a TeamSpeak server and do not want to manually start it with the startscript every time I start my computer after a restart. I hope it's possible to have that script run at system startup so that it starts on its own.

---

### Post by Bölvaður on 2009-04-20
System &#8594; Preferences &#8594; Session

+Add

place what ever command (name of program or script...) into the Command : section

---

### Post by steve101101 on 2009-04-20
> **Bölvaður said:**
> System &#8594; Preferences &#8594; Session

+Add

place what ever command (name of program or script...) into the Command : section

+1 and make sure the script is executable.

---

### Post by dmaxel on 2009-04-20
Well to start it manually i have to navigate to where it is using terminal and cd...

And then use "./teamspeak2-server_startscript start" (without quotes) to start it. Would it still work?

EDIT: Just realized this won't work, as it needs a shell script to start manually. I use that, but I want to know how to start that script at boot automatically.

---

### Post by dmaxel on 2009-04-27
Can anyone help?

---

### Post by t0p on 2009-04-27
If you put the command in as **/path/to/script** it should work I think.  Like, if the script is in your home directory, in a sub-directory called Scripts, you'd put in the command as

```
~/Scripts/scriptname.sh
```, I think that should work.

---

### Post by llamabr on 2009-04-27
Or, you can add a line to your /etc/inet.d/ folder.

There should be a README in there.

---

### Post by dmaxel on 2009-04-27
> **t0p said:**
> If you put the command in as **/path/to/script** it should work I think. Like, if the script is in your home directory, in a sub-directory called Scripts, you'd put in the command as

```
~/Scripts/scriptname.sh
```, I think that should work.
That didn't work either.

However, although I manually have to start the server with a script, the package goes come with a linux_server executable. I tried setting it so it would try to start with that, and it worked! Thanks for all your help though!

---

