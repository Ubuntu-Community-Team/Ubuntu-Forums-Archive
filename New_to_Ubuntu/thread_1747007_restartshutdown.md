---
title: "restart/shutdown"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by nooneastern on 2011-05-02
since everyone here was so helpful my first question here i go again ....

i can't seem to shut down or restart Ubuntu
i can click the button and it seems to stop a signal to the monitor and disk activity and fans all stop
but the power doesn't go off and it also doesn't restart
i eventually just have to literally pull the plug and plug it back in to boot back up

any ideas at all about this one ?

---

### Post by adit on 2011-05-02
Which computer model you are using?
What happens when you type into terminal?
```
sudo shutdown -h now
```

---

### Post by nooneastern on 2011-05-02
i am using a Dell

---

### Post by adit on 2011-05-02
> i am using a Dell
Mention the full model name. (and whether it is a laptop or desktop)
What happens when you run the command
```
sudo shutdown -h now
```

---

### Post by CaptainMark on 2011-05-02
have you installed all the latest updates, this was an earlier bug that seems to have been fixed for the most part?

---

### Post by nooneastern on 2011-05-02
sorry guys
here are more details:
first off - i am using 10.04 LTS

EDIT: and i have installed all the updates that have come up so far too

and beyond my computer being a Dell i am not sure

also i have run this for my earlier post:
sudo lshw -html > hardware_info.html
and here are the results: [http://www.sendspace.com/file/04xiaw](http://www.sendspace.com/file/04xiaw)
if that helps

i haven't tried to run that command in terminal yet
will it attempt to shutdown the computer when i run it ?

i appreciate the help
:)

---

### Post by nooneastern on 2011-05-02
also i should mention i am running a dual boot with Windows XP through a WUBI install

and i had to edit my GRUB to include this line "i915.modeset=0" to make it work
i learned that from my first thread i started here

---

### Post by nooneastern on 2011-05-02
@[adit]("http://ubuntuforums.org/member.php?u=744678"):

i ran the code you suggested and that worked fine ...

---

### Post by adit on 2011-05-03
> i ran the code you suggested and that worked fine ... 
Then there is no hardware problems with your computer.  Problems are with your settings.
From your post#1
> i can click the button
Exactly which button you clicked?  Did you click on this window? (See the attached screenshot.)

---

### Post by lisati on 2011-05-03
> **nooneastern said:**
> also i should mention i am running a dual boot with Windows XP through a WUBI install


BTW, "dual boot" is commonly interpreted as something different to a Wubi install. Dual boot has its own partition for each OS, and Wubi puts Ubuntu into a folder in the Windows partition.

---

### Post by nooneastern on 2011-05-03
@adit:

yeah i see that screen when i shut down
i click on System in the menu and choose Shutdown to get to it
i assume i just need some code to change settings somewhere then .....

@lisati:

oops yeah i guess you're right. saying WUBI implies that i still have Windows installed too i guess since it's a Windows program. so i shouldn't have said "dual boot"

can't wait until i get more familiar with everything so i can stop being such a dorky noob!! haha

thanks again everyone ....
:)

---

### Post by adit on 2011-05-03
> stop a signal to the monitor and disk activity and fans all stop but the power doesn't go off
Looks like your computer is going for sleep when you select shutdown.
Press Ctrl+Alt+Del keys.  The shutdown dialog will appear.  Select "Suspend" instead of "Shut Down" and see whether similar things happen.

---

### Post by nooneastern on 2011-05-03
when i clicked suspend it went to suspend mode like it should

i should mention that when i try to shutdown or restart it will not wake back up
i have to unplug the computer ....

---

### Post by nooneastern on 2011-05-05
sorry to bump my thread here .... but are there any other suggestions here ?
i would really love to be able to restart my Ubuntu

the Terminal code is good and works for shutting down, but i want to be able to restart, and/or not have to open the Terminal just to shut the computer down

thanks again in advance everyone ....

---

### Post by dcsoldschool53 on 2011-05-05
[B]> **nooneastern said:**
> sorry to bump my thread here .... but are there any other suggestions here ?
i would really love to be able to restart my Ubuntu

the Terminal code is good and works for shutting down, but i want to be able to restart, and/or not have to open the Terminal just to shut the computer down[/B]> **nooneastern said:**
>  [B]

thanks again in advance everyone ....[/B] [B]


Try, right clicking on gnome panel. Click add to panel. Scroll down for the shutdown computer button.

You can also add command buttons to Applications. Right click Applications > Edit Menus > New item. Add as a button type to open in a terminal```
sudo shutdown -h now
```This will open up a terminal so that you can type your password in, or you can add as a button type to open as an application```
**gnome-session-save --shutdown-dialog**
```Give them all names, icons, and comments.

I hope this will help you):P
[/B]

---

### Post by nooneastern on 2011-05-05
@[dcsoldschool53]("http://ubuntuforums.org/member.php?u=1010604")
thanks
but i don't think this will solve my problem
i have access to the actual buttons for shutting down
but clicking on them doesn't do what it's supposed to do

as i stated in my original post here when i click SHUTDOWN or RESTART it doesn't work
the monitor loses it's signal, and the disks and fans spin down
but the computer power stays on
it won't shutdown or restart

but the Terminal code DOES actually shut it down

i hope this makes sense ...

---

### Post by dcsoldschool53 on 2011-05-05
> **nooneastern said:**
> @[dcsoldschool53]("http://ubuntuforums.org/member.php?u=1010604")
thanks
but i don't think this will solve my problem
i have access to the actual buttons for shutting down
but clicking on them doesn't do what it's supposed to do

as i stated in my original post here when i click SHUTDOWN or RESTART it doesn't work
the monitor loses it's signal, and the disks and fans spin down
but the computer power stays on
it won't shutdown or restart

but the Terminal code DOES actually shut it down

i hope this makes sense ...

You may have to reset your gnome panel back to the default setting, or reinstall your  indicator apple.One of them should do the trick.

---

### Post by nooneastern on 2011-05-06
i think you are misunderstanding ....
my panel is fine ... i have the indicator applet there ... i have the main menu there
i have at least TWO options for how to reach the shutdown options
and i can click the buttons no problem ....

the problem, however, is once i click the buttons
whether i click shutdown or restart it doesn't work

the monitor goes black and all disk activity stops
but the power light on the computer stays on forever
i eventually have to just unplug the whole thing
so i can't restart

for reasons that i don't understand this codeworks**[B]sudo shutdown -h now**[/B]
but the buttons simply make the computer stop working
it doesn't restart or shutdown
and it isn't suspended or hibernating
because it won't wake up either

is there a way to fix this ?
or at least a similar code to restart?

---

### Post by mechanizedmedic on 2011-05-17
> **nooneastern said:**
> i think you are misunderstanding ....
my panel is fine ... i have the indicator applet there ... i have the main menu there
i have at least TWO options for how to reach the shutdown options
and i can click the buttons no problem ....

the problem, however, is once i click the buttons
whether i click shutdown or restart it doesn't work

the monitor goes black and all disk activity stops
but the power light on the computer stays on forever
i eventually have to just unplug the whole thing
so i can't restart

for reasons that i don't understand this codeworks**[B]sudo shutdown -h now**[/B]
but the buttons simply make the computer stop working
it doesn't restart or shutdown
and it isn't suspended or hibernating
because it won't wake up either

is there a way to fix this ?
or at least a similar code to restart?

i had a similar problem related to ACPI. go into your BIOS and make sure ACPI is enabled. being a dell it might be called something like powernow or cpu scaling.

---

### Post by fritz269 on 2011-05-17
I had a simular problem with an old dell. What I did was when the screen when blank, I held the power button for about 5 seconds and it seemed to do the trick.

---

### Post by laidback on 2011-05-17
Do you have the Open Office quickstarter running? (puts an icon on the launch panel at the top of the screen, systray), if so get rid of it. You can do this in any of the OOo apps. Tools>Options>Memory uncheck Enable systray Quickstarter.

---

### Post by nooneastern on 2011-05-20
i don't have the quickstarter running  in fact after your question i made sure to shut down all the stuff i had running before trying to shut down or restart usually i don't bother to close Pidgin or CGmail or Dropbox  but even closing all those didn't help  the only way i can successfully shut down  is by typing "sudo shutdown -h now" into the terminal that way works every time  if i use the shutdown options in the System menu it still does the same thing the signal to the monitor goes away, and the drives stop but the fan is still running and the power light stays on  maybe i should just accept the fact that i have to open the terminal when i want to shut down it's not that huge a deal i just hate it when things aren't perfect (i'm too OCD haha)  still working on it here thanks for the help so far

---

### Post by jramshu on 2011-05-20
How long did you wait after the screen went black?

The reason I ask is I have a Compaq that does something similar. The power light and fan runs, but after a couple of minutes it shuts off.

It seems like it's waiting on something to quit running.

---

### Post by tarps87 on 2011-05-20
This may not work but it is worth a try:

Run the command
```
sudo visudo
```

then add the lines:

Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/halt, /sbin/reboot

and

*<your username>* ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

Replace *<your username>* with your username

This use to be an issue with the less common window managers, for more info on the sudoers file:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by nooneastern on 2011-05-20
> **jramshu said:**
> How long did you wait after the screen went black?

The reason I ask is I have a Compaq that does something similar. The power light and fan runs, but after a couple of minutes it shuts off.

It seems like it's waiting on something to quit running.


i decided to time it this time
i waited a full 10 minutes
just sat there
fans running and light on

i really want to be able to actually restart since i use a dual boot system, i would love to be able to go back and forth without having to shutdown

but again the code
```
sudo shutdown -h now
```always works and shuts it down within seconds

---

### Post by nooneastern on 2011-05-20
> **tarps87 said:**
> This may not work but it is worth a try:

Run the command
```
sudo visudo
```then add the lines:

Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/halt, /sbin/reboot

and

*<your username>* ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

Replace *<your username>* with your username

This use to be an issue with the less common window managers, for more info on the sudoers file:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

i wasn't exactly sure where i was supposed to add those lines
so i tried the very end of the file

i tried to restart afterwards but the computer hung for a full 10 minutes
just fan running and power light on

was putting the lines at the bottom correct ?

---

### Post by dcsoldschool53 on 2011-05-23
Have you tried any of the reboot commands for Ubuntu? The following are some of the command that you can use to reboot Ubuntu:
1.```
sudo reboot
```2. ```
sudo init 6
```3. ```
sudo shutdown now -r
```Any one of these commands will reboot your system. All you need to do is find out when one is right for you.

---

### Post by nooneastern on 2011-05-24
ok cool
sudo reboot works
i just made a button for my panel that performs that command
and now i can restart like a champ
not sure why i can't restart or shutdown using the commands in the main menu
but i guess it doesn't matter as long as i can make it happen

i'll mark this thread solved now
thanks everyone !

---

