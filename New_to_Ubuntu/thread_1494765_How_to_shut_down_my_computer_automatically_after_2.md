---
title: "How to shut down my computer automatically after 2 hours?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by adit on 2010-05-27
I am using ubuntu 9.10.  I want to shut down my computer after 2 hours (from now) automatically.  How to do that?

---

### Post by Ozymandias_117 on 2010-05-27
```
sudo shutdown -h 120
```

---

### Post by 1991sudarshan on 2010-05-27
if you put -r instead of -h the system will restart!!

---

### Post by jerrrys on 2010-05-27
and for the got to have a GUI person (me); there is **kshutdown** in synaptic

---

### Post by nhasian on 2010-05-27
you could also use the *at* command

> **Ubuntu Unleashed]
If there is a time-intensive task you want to run, but you do not want to do it while you are still logged in, you can tell Ubuntu to run it later with the at command. To use at, you need to tell it the time at which you want to run and then press Enter. You will then see a new prompt that starts with at>, and everything you type there until you press Ctrl+D will be the commands you want at to run.[/QUOTE]

for more info see

```
man at
```

I wouldn't use kshutdown unless you want it to install all the KDE libraries!

[QUOTE=jerrrys said:**
> and for the got to have a GUI person (me); there is **kshutdown** in synaptic

---

### Post by adit on 2010-05-27
```
sudo shutdown -h 120
```
Will this code shut down the computer without any user intervention?  Will it shut down even if some programs are running?
For example I am editing some file in open office writer.  The changes are not saved and I keep the open office program window open.  I type the above code into terminal and go away from the computer.  I am afraid that after 2 hours the computer will display the dialog box  "Save changes to document before closing?" and waiting for my input.
I want to the computer to shut down forcibly even if programs with unsaved changes are running.  Will the above code do that?

---

### Post by jerrrys on 2010-05-27
> **nhasian said:**
> you could also use the *at* command



for more info see

```
man at
```I wouldn't use kshutdown unless you want it to install all the KDE libraries!

it didn't get too carried away...

[ATTACH]158430[/ATTACH]

---

### Post by Ozymandias_117 on 2010-05-27
> **adit said:**
> ```
sudo shutdown -h 120
```
Will this code shut down the computer without any user intervention?  Will it shut down even if some programs are running?
For example I am editing some file in open office writer.  The changes are not saved and I keep the open office program window open.  I type the above code into terminal and go away from the computer.  I am afraid that after 2 hours the computer will display the dialog box  "Save changes to document before closing?" and waiting for my input.
I want to the computer to shut down forcibly even if programs with unsaved changes are running.  Will the above code do that?

It will shut down no matter what's going on.

---

### Post by varunendra on 2010-05-27
Is there a way to do it through power management such that computer shuts down whenever it is left idle for 2 hrs.?

---

### Post by Ozymandias_117 on 2010-05-27
If there is, I'm unaware of it, sorry. :(

Note: Just a quick look at it's man page says > It  supports features such as suspending, hibernating, screen blanking, cpu frequency switching...

---

### Post by sdennie on 2010-05-27
I haven't tested this but, I'm reasonably confident it will work.  First, go to System->Preferences->Power Management.  In as many tabs as you can find the option, change "Put system to sleep when inactive for" to 2 hours.  Then, hit Alt-F2 and start gconf-editor.  Navigate to /apps/gnome-power-manager/actions.  Change sleep_type_ac and sleep_type_battery to both be "shutdown" like some of the other options are likely set to.

Again, I didn't test that but, I'm reasonably certain it will work.

---

### Post by Dayofswords on 2010-05-27
i can't script or anything but if you make a script to run at startup, you could probably make it do this kind of thing:

if mouse and keyboard arent moved or touches, start counting to 2 hours, when two hours hit, do command "sudo shutdown -h now"

but you'd need to type your pass... so it needs to be sudo'd and at login you'd need to type your pass... or something

i have no idea if this is possible if things work this way, but sounds like a concept that could work...just throwing out ideas

EDIT: meant **can't** script!

---

### Post by Ozymandias_117 on 2010-05-27
> **sdennie said:**
> I haven't tested this but, I'm reasonably confident it will work.  First, go to System->Preferences->Power Management.  In as many tabs as you can find the option, change "Put system to sleep when inactive for" to 2 hours.  Then, hit Alt-F2 and start gconf-editor.  Navigate to /apps/gnome-power-manager/actions.  Change sleep_type_ac and sleep_type_battery to both be "shutdown" like some of the other options are likely set to.

Again, I didn't test that but, I'm reasonably certain it will work.

I had found that, but on the bottom it says > Possible values are "hibernate", "suspend" and "nothing".

---

### Post by Ozymandias_117 on 2010-05-27
> **Dayofswords said:**
> i can script or anything but if you make a script to run at startup, you could probably make it do this kind of thing:

if mouse and keyboard arent moved or touches, start counting to 2 hours, when two hours hit, do command "sudo shutdown -h now"

but you'd need to type your pass... so it needs to be sudo'd and at login you'd need to type your pass... or something

i have no idea if this is possible if things work this way, but sounds like a concept that could work...just throwing out ideas

You could modify your sudoers file so it doesn't ask for a password for sudo shutdown

---

### Post by varunendra on 2010-06-03
Hey people!
It's a good question here. Anybody any solutions?

---

