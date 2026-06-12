---
title: "How to Automate a Terminal Command?"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by Habeouscorpus on 2010-12-23
I.E by shortening a long command to a one word command.

Such as: "sudo mount /dev/fd0 /media/floppy" to "floppy mount"

After doing a quick search online, I found infomation about something called an "alias." I thought it was what I was looking for, but the information pages for it confused me. Are there any easy explanations out there?

---

### Post by Jose Catre-Vandis on 2010-12-23
You need to put alias' in your ~/.bashrc file.

For your example:

```
sudo nano ~/.bashrc
```
scroll down to just above the #Alias definitions section (you will see a few alias' there already. Type this in on a blank line:
```
alias floppymount='sudo mount /dev/fd0 /media/floppy'
```
Should now look like this:
```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

alias floppymount='sudo mount /dev/fd0 /media/floppy'

# Alias definitions.
# You may want to put all your additions into a separate file like
```

If I remember correctly the effect is immediate so your alias should work, if not logout and log back in again, or reboot. You will still have to enter your password, unless you put mount in your sudoers, but a) that's not a great idea, and b) that's another thread entirely!

---

### Post by lijcam on 2010-12-23
One quick and dirty way I do it at home is just put your command in a blank file in your home directory.

```
~$ touch myscript.sh 
~$ echo "the commands you want to execute" > myscript.sh
~$ chmod +x myscript.sh
```

Then you can run it from your home with ```
~$ sh myscript.sh
```
If it needs root privileges just put sudo in front.

---

### Post by Habeouscorpus on 2010-12-23
Okay, thank you! I'll try it and see it anything blows up. :)

---

### Post by AlphaLexman on 2010-12-23
You can also:
```
source ~/.bashrc
```
after any changes to ~/.bashrc without having to logout, login or reboot!

---

### Post by brishu on 2010-12-23
you can't do it as two words, it needs to be one word like floppyMount, and as Jose said, you need to put it into your .bashrc file

you don't need to do 'sudo nano ~/.bashrc'

just nano ~/.bashrc (~ = /home/yourName)

if you prefer a more GUI based approach open up gEdit (or another text editor) and open the file at /home/yourName/.bashrc

and add your alias in anywhere (I would recommend you do it at the very end, simply because you don't have go looking for it if you want to change it or remove that alias)

also, the effect is NOT immediate, the way we normally think of immediate. It will only work on terminals created AFTER the edit was made. So, just open up a new terminal, if you did it via terminal, and it should work.

Also: this is more a one step process:
echo "alias floppyMount='sudo mount /dev/fd0 /media/floppy'" | tee -a .bashrc
or 
echo "alias floppyMount='sudo mount /dev/fd0 /media/floppy'" >> .bashrc

---

