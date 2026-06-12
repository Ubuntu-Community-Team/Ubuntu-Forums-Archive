---
title: "File Permissions and Types"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by ftabor on 2009-04-04
I have created a file, using Gedit, and it's a shell script.  

```
#!/bin/bash
sudo apt-get update

```

The script works, that's not the problem.  Now, I've named the file update-shell.sh and saved it.  It has a shell script icon.  Clicking on the file before changing the permissions opens the file in Gedit.  That's good, it's still a text file, at this point.

After changing the permissions to execute, (I've used sudo chmod +x in the terminal as well as right click>properties>permissions allow file to execute) I'm unable to get the file to either run in terminal, or ask what to do with the file.

Is there something I'm missing, or is this the proper behavior?

---

### Post by mbzn on 2009-04-04
Try "chmod 'filename' 550" that should work fine...

---

### Post by cosine352 on 2009-04-04
> **ftabor said:**
> I have created a file, using Gedit, and it's a shell script.  

```
#!/bin/bash
sudo apt-get update

```

The script works, that's not the problem.  Now, I've named the file update-shell.sh and saved it.  It has a shell script icon.  Clicking on the file before changing the permissions opens the file in Gedit.  That's good, it's still a text file, at this point.

After changing the permissions to execute, (I've used sudo chmod +x in the terminal as well as right click>properties>permissions allow file to execute) I'm unable to get the file to either run in terminal, or ask what to do with the file.

Is there something I'm missing, or is this the proper behavior?

try this

> gedit update.sh
> #!/bin/bash
gksu apt-get update

then 
> chmod +x update.sh

in the terminal 
> ./update.sh

I do not know why are you trying to do this. as > sudo apt-get update is simple enough

---

### Post by ftabor on 2009-04-04
> **cosine352 said:**
> try this




then 


in the terminal 


I do not know why are you trying to do this. as  is simple enough

Because I'm writing the script for cron, there will be no one around to enter a password when it runs, so sudo won't work.

---

### Post by cosine352 on 2009-04-04
then do the cron job for root

---

### Post by ftabor on 2009-04-04
> **mbzn said:**
> Try "chmod 'filename' 550" that should work fine...

All that does make the file "read only" to me, and locked to all others.  

I'm trying to get it to display the dialog that asks to Run in Terminal or Display.  All I get when I click it is it opens in Gedit.

---

### Post by ftabor on 2009-04-04
> **cosine352 said:**
> then do the cron job for root

My problem is not with my script, and this has nothing to do with cron.  this has to do with what action I get when I open a file with a .sh extension from my own home directory.

I should get a dialog box with a choice to Run in Terminal or Display.  I do not.  It opens in Gedit without asking.

Forget about what the script does, and where, it's irrelevant.  All Im' concerned with is the file action when it's clicked on.

---

