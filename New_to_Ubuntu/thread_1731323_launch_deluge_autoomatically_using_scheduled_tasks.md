---
title: "launch deluge autoomatically using scheduled tasks"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by steninj on 2011-04-17
hey i'v got a situation..

i want to launch deluge using scheduled tasks..,,
everyday at 02:10am...(i don't want to use deluge scheduler)

i want to know  command and default behaviour.

&if posible..give me a command so that my system automatically shuts down at 7am...

please help..i need a solution..

i am using ubuntu 10.10

thank you :)

---

### Post by Paddy Landau on 2011-04-17
To schedule tasks, you need *cron*. Google *cron* (or type [FONT=Courier New]man 5 crontab[/FONT] in a terminal) to find out how it works.

Type the following command from the terminal or from Alt-F2:
```
VISUAL='gedit' crontab -e
```This will bring up your cron table, which is probably empty.

Enter the following lines (blank lines and lines starting with # are comments and are ignored).
```
# Prevent filling up your mailbox.
MAILTO=''

# Start Deluge every day at 2:10 a.m.
10 2 * * * deluge
```Save the file and close gedit.

To shut down, enter the *shutdown* command into Alt-F2 (type [FONT=Courier New]man shutdown[/FONT] into a terminal to find how it works).
```
sudo shutdown -P 7:00
```Note: If you use a terminal, you will have to modify the command so that you can close the terminal:
```
sudo nohup shutdown -P 7:00 &>/dev/null &
```

---

### Post by steninj on 2011-04-17
thnx for ur interest Paddy Landau,,
but its not working :(

---

### Post by Paddy Landau on 2011-04-18
> **steninj said:**
> thnx for ur interest Paddy Landau,,
but its not working :(
You need to be much more specific than that. Remember that I can't see your computer.

What's not working -- Deluge or shutdown or amending your crontab?

How do you know it's not working -- does it give an error? Does Deluge simply not start? What exactly is (or is not) going on?

---

### Post by steninj on 2011-04-19
am really sorry for that,,now i will explain...

"VISUAL='gedit' crontab -e" i tried this command in alt+F2..
then i get this error..
"Could not open location 'file:///home/stenin/VISUAL=&apos;gedit&apos;%20crontab%20-e'"

Error stating file '/home/stenin/VISUAL='gedit' crontab -e': No such file or directory...

then i tried it in terminal...
i saved it and closed gedit..
but i get this message in terminal..



stenin@DreamER:~$ VISUAL='gedit' crontab -e

(gedit:3605): Gtk-WARNING **: Attempting to store changes into `/home/stenin/.recently-used.xbel', but failed: Failed to rename file '/home/stenin/.recently-used.xbel.JJX6TV' to '/home/stenin/.recently-used.xbel': g_rename() failed: Operation not permitted

(gedit:3605): Gtk-WARNING **: Attempting to set the permissions of `/home/stenin/.recently-used.xbel', but failed: Operation not permitted

(gedit:3605): Gtk-WARNING **: Attempting to store changes into `/home/stenin/.recently-used.xbel', but failed: Failed to rename file '/home/stenin/.recently-used.xbel.D3O5TV' to '/home/stenin/.recently-used.xbel': g_rename() failed: Operation not permitted

(gedit:3605): Gtk-WARNING **: Attempting to set the permissions of `/home/stenin/.recently-used.xbel', but failed: Operation not permitted

(gedit:3605): Gtk-WARNING **: Attempting to store changes into `/home/stenin/.recently-used.xbel', but failed: Failed to rename file '/home/stenin/.recently-used.xbel.DODOTV' to '/home/stenin/.recently-used.xbel': g_rename() failed: Operation not permitted

(gedit:3605): Gtk-WARNING **: Attempting to set the permissions of `/home/stenin/.recently-used.xbel', but failed: Operation not permitted

(gedit:3605): Gtk-WARNING **: Attempting to store changes into `/home/stenin/.recently-used.xbel', but failed: Failed to rename file '/home/stenin/.recently-used.xbel.R4C9TV' to '/home/stenin/.recently-used.xbel': g_rename() failed: Operation not permitted

(gedit:3605): Gtk-WARNING **: Attempting to set the permissions of `/home/stenin/.recently-used.xbel', but failed: Operation not permitted
crontab: installing new crontab
stenin@DreamER:~$ 



i will try shutdown commmand later and tell you..

now,,

YOU PLEASE CONSIDER THIS TOO

i'v launched deluge&shutdown command osuccessfully in one of the previous version of ubuntu..


i opened "scheduled tasks" using some command...
then  i add a recurrent task,one for deluge& one for shutdown..

i used this command i think.. "deluge --ui=gtk"

i don't have the shutdown command with me now

now i forgot even its "default behaviour" which i used then..
i'v no idea about programng and all,i got this commands from some sites..

thank u Paddy Landau...

---

### Post by BugBuster on 2011-04-19
Since deluge is a gui application you need to specify the display environment variable in the crontab.. like
> 
10 2 * * * export DISPLAY=:0.0 && /usr/bin/deluge



Also to shutdown...you have to add the following to the root's crontab
> 
00 07 * * *   halt


adding sudo shutdown to your crontab will not work...as you won't be able to enter the sudo password.

---

### Post by Paddy Landau on 2011-04-19
> **steninj said:**
> "VISUAL='gedit' crontab -e" i tried this command in alt+F2..
then i get this error..
"Could not open location 'file:///home/stenin/VISUAL=&apos;gedit&apos;%20crontab%20-e'"
Sorry, that was my mistake. You were right to try it from the terminal.

> **steninj said:**
> i saved it and closed gedit..
but i get this message in terminal..
That is a bit strange. Please try this (in a terminal):
```
cd ~
sudo chown stenin:stenin .recently*
```Then try again to edit your crontab.

BugBuster is right about putting *halt* into your root's crontab if you want to execute it every day.
```
sudo VISUAL='gedit' crontab -e
```I had understood it was a one-off request, in which case entering it into the terminal as I showed you would do fine.

---

### Post by steninj on 2011-04-21
thank u guys,
but

it shows this error..

chown: changing ownership of `.recently-used.xbel': Operation not permitted


but now am able to shut down automatically...
i used this command in scheduled tasks.. "/sbin/shutdown -h now"

&i used this command to get sch.tasks.. "sudo gnome-schedule"


i want deluge to be launched everyday,at a specific time..

---

### Post by Paddy Landau on 2011-04-21
> **steninj said:**
> chown: changing ownership of `.recently-used.xbel': Operation not permitted
Did you remember to put 'sudo' in front of the chown command?

---

### Post by steninj on 2011-04-22
yes... ofcourse i did...
but still it shows the same messege

---

### Post by Paddy Landau on 2011-04-22
I guess we have to get back to basics.

First, let's have a look at what you already have in your crontab. In your terminal, enter the following command to see what you already have.
```
crontab -l
```If you have a crontab and want to remove it entirely, enter the command:
```
crontab -r
```To be thorough, let's repeat that for root:
```
sudo crontab -l
```Let us know what your results.

---

### Post by steninj on 2011-04-25
thank everyone...

i got a solution...
regarding [SIZE=2]auto launch deluge[/SIZE]

access scheduled tasks from your applications menu..(because u don't need to run it as root)

add a recurrent task...

use the command "deluge-gtk"

set behaviour as "X application"

set time&date in advanced options...
so u can launch deluge everyday at a specific time..

now,regarding [SIZE=2]autoshutdown[/SIZE],,,,

use the command "sudo gnome-schedule",,,, u can access sched.tasks as root by this command..

then add a recurrent task with command "/sbin/shutdown -h now"

specify time&date etc..

your system will shutdown automatically....

thank u guys,, evryone's opinion helped me alot..

thank u so much :)

---

### Post by Paddy Landau on 2011-04-25
I'm glad you have solved it. I don't have gnome-schedule installed, but I see it's a GUI front-end for cron. So, you are changing cron but doing it the easy way. If you enter the following two commands, you can see what changes were made to yours and root's respectively.
```
crontab -l
sudo crontab -l
```BTW, when you use a GUI, do not use sudo. Use gksu instead. So, this is wrong:
```
sudo gnome-schedule
```This is right:
```
gksu gnome-schedule
```I don't remember the technical reasons (actually, I didn't fully understand them), but there are times when using sudo with a GUI can land you in some difficulty. For example, I've read that [FONT=Courier New]sudo firefox[/FONT] can leave your Firefox inoperable, whereas [FONT=Courier New]gksu firefox[/FONT] is safe.

---

### Post by steninj on 2011-04-26
i really apreciate [Paddy Landau]("http://ubuntuforums.org/member.php?u=572807") for all ur help...

i worked with "sudo" and everything was just fine..

so i cnt agree that,its completely wrong..

actually am new to ubuntu and my kwoledge is very little regarding it :D

but i like ubuntu very much :*

thnk u all....

---

