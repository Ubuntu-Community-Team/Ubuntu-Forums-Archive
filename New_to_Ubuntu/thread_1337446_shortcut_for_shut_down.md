---
title: "shortcut for shut down"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-25
I would like to create a keyboard shortcut for shutting down the computer. 
If I have to use Preferences>>keyboard shortcut, please tell me the command that i must use.

---

### Post by wojox on 2009-11-25
It should already be set. Ctrl + Alt + Delete

---

### Post by Myglaren on 2009-11-25
Push the power button, the options will come up but it will shut down with no further intervention after sixty seconds.

---

### Post by LowSky on 2009-11-25
> **Myglaren said:**
> Push the power button, the options will come up but it will shut down with no further intervention after sixty seconds.

or got to power options and change it from ask to shutdown, and it will do it automatically

---

### Post by iRounak on 2009-11-25
Thanks for the replies.

---

### Post by iRounak on 2009-11-25
But none of this helps. I want to use Ctrl+Alt+Super+S to shut down. No dialog boxes, no waiting etc This is what i do in mac and windows.

---

### Post by Kareeser on 2009-11-26
I honestly don't think it's possible...

The shutdown command is protected, meaning you have to be root (or using sudo) to use it.

The only reason why the user-switcher applet can do it is due to some convoluted reasoning which I didn't bother understanding.

I think it would be beyond the capabilities of a simple script/command...

---

### Post by iRounak on 2009-11-26
> **Kareeser said:**
> I honestly don't think it's possible...



Thanks, I don't know why people avoid saying this. No one expects everything to work everywhere. Its helps to  know that something does not work instead of trying vague alternatives.

---

### Post by jrrader on 2009-11-26
write a script for shutting down using "shutdown -h now". add it to ~/bin/ then create a shortcut to the script

[http://www.ubuntugeek.com/how-to-create-a-custom-keyboard-shortcut-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-custom-keyboard-shortcut-in-ubuntu.html)

---

### Post by iRounak on 2009-11-26
I am afraid I know very little about shell scripting. I tried to create the file using gedit and I got permission error. So I tried Terminal. I dont exactly know what is meant by "~/bin/" because there are more than one bin folders and in Mac OS "~" meant users folder. When I tried to do that in the bin folder located in my users folder, I got this:

sudo echo "shutdown -h now" >  shutfile.sh
bash: shutfile.sh: Permission denied

---

### Post by jrrader on 2009-11-26
I was pretty brief before because I was in a hurry.  Here is the long version:

**EDIT: I thought of an easier way.  See post 13.**

---

### Post by Rubicon_82 on 2009-11-26
Defining a shortcut for 'Halt Without Confirmation' can be done easily in KDE.  I'd be surprised if it couldn't also be done in Gnome.

Procedure for KDE, if it helps:

**1)**  Confirm that non-root users are permitted to shut down KDM (the "AllowShutdown" line in the [X-:*-Core] /etc/kde4/kdm/kdmrc).

**2)**  Define, and assign a keyboard shortcut for the "Halt Without Confirmation" line in the [krunner] section of ~/.kde/share/config/kglobalshortcutsrc.

These settings can also be edited through the "Login Manager" and "Keyboard & Mouse" GUIs in System Settings if you prefer.

---

### Post by jrrader on 2009-11-26
I think I made that more complicated than it needs to be. You probably don't need to make the file shutd or create ~/bin

Instead, you could just do this:

In terminal
```
sudo visudo
```
add this line to the bottom (change username to your username, it's actually the group name):
```
%username ALL = NOPASSWD: /sbin/shutdown

```
Press ctrl+k and then x to save and exit

Set SUID on shutdown
```
sudo chmod u+s /sbin/shutdown
```
Now you'll be able to run shutdown without a password

Then just bind "sudo shutdown -h now" to the keys you want with Keyboard Shortcut or install the stuff from that first link I posted.

---

### Post by iRounak on 2009-11-26
sorry!! I screwed up inspite of your detailed instructions. I did not type my username in place of usergroup. I only typed it in place of username. 

Whenever, I try to use "sudo", I get this error:
>>> /etc/sudoers: syntax error near line 26 <<<
sudo: parse error in /etc/sudoers near line 26
sudo: no valid sudoers sources found, quitting
What do i do now?

---

### Post by anaconda on 2009-11-26
Ok, so your sudo wont work any longer.. bad

YOu can correct the problem by booting to recovery mode, and in there type 
```
visudo
```
and you will be able to edit the sudoers file to correct your problem..

Oh. and if you cant use the "vi" editor, here is a few tips:
vi starts in "command mode" 
i =gets you to insert/edit mode
esc = gets you out of insert mode
:wq = quits and saves the file

---

### Post by iRounak on 2009-11-26
Thanks anaconda for the prompt help. I fixed the sudo problem. However, my shut down problem is still not fixed. I still have to be root to shut down.
Here is my sudoers file:

> # See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

username username=NOPASSWD: /sbin/shutdown

where username is my username

---

### Post by jrrader on 2009-11-26
Sorry you had problems with the sudoers file.  There is one more step that I left out (I was tired)...  We have to set SUID on shutdown

```
sudo chmod u+s /sbin/shutdown
```

Then it should work.

---

### Post by iRounak on 2009-11-28
Many thanks. It does work now.

---

