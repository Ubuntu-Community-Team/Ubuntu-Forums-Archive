---
title: "How can I get all the output that have passed in terminal during installation"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by xptional on 2011-03-18
How can I get all the output that have passed in terminal during installation ?
Thanks for your help :)

---

### Post by The_Eggert on 2011-03-18
> **xptional said:**
> How can I get all the output that have passed in terminal during installation ?
Thanks for your help :)

Not sure what you mean..
Du you want the output written to a file or what?

In that case it would be:
```

command > file | cat file

```

---

### Post by runeh76 on 2011-03-18
Click ur terminal profile, and set "rolling" unlimited.

---

### Post by nothingspecial on 2011-03-18
If you mean the terminal output when installing something with apt ---

```
sudo less /var/log/apt/term.log
```

---

### Post by xptional on 2011-03-18
I have installed the program, network simulator, 

I need all the things that have been passed on terminal, when i do scrolling up, it limits to scroll to go to the begining, where i type my command, but i need to go untill there to copy all the output. 

I did unlimited scolling in terminal profile, but it did not help me, 

I dont need logfile, i need the text that has passed very quickly during installation. 

hope you got my request.

---

### Post by seawolf167 on 2011-03-18
Setting rolling to unlimited would only affect commands after the setting change. Unless you look at the log files, I don't know of any place the terminal output would be stored pre-settings change.

You can see your input with 

```
history
```

and for future reference, if you need to store your terminal output/input, but don't want it in a text file, i.e.

```
command > some_file
```

the easiest & best way (IMO) to do that is to use

```
script
```

to store all the messages. Then you can review everything that happened with proper formatting in a terminal.

---

### Post by xptional on 2011-03-18
i am new to Ubuntu and don't know much about how commands are utilised. 

Anyhow, I came able to do by unlimited scrolling; then copy and paste .., Its an idiot work not efficient but i did in this way, 

i will prefer, if i will get command line solution to save the display on the terminal while installation. in my case, for NS2 installation. 
the command that i utilised is ```
./install
``` and then display text come but dont know how to save it in a file.?:(

---

### Post by kansasnoob on 2011-03-18
You can always poke about (carefully) in /var/log. I'm often unsure just what I'm looking for, and some files are "root privilege" only so I usually install the package "nautilus-gksu" so I can right-click on anything with a "lock" and select "open as administrator". **Just be careful using root privileges in Nautilus!**

Then you could go to Places > Computer > File System > var > log ............... then if you're looking for info regarding the installation of a package probably look in "apt". Just an example of the various files in "apt":

```
lance@lance-desktop:~$ ls /var/log/apt
history.log        history.log.5.gz  term.log.10.gz  term.log.6.gz
history.log.10.gz  history.log.6.gz  term.log.1.gz   term.log.7.gz
history.log.1.gz   history.log.7.gz  term.log.2.gz   term.log.8.gz
history.log.2.gz   history.log.8.gz  term.log.3.gz   term.log.9.gz
history.log.3.gz   history.log.9.gz  term.log.4.gz
history.log.4.gz   term.log          term.log.5.gz

```

If the installation was recent you'll likely see the info you're looking for in either "history.log" or "term.log". 

Now, I know I'm repeating myself, but **[COLOR="Red"]always be careful using root privileges in Nautilus![/COLOR]**

If you break it, you own it!

But AFAIK there is a history of almost everything in /var/log:

```
lance@lance-desktop:~$ ls /var/log
alternatives.log       dpkg.log               popularity-contest
alternatives.log.1     dpkg.log.1             popularity-contest.0
alternatives.log.2.gz  dpkg.log.10.gz         popularity-contest.1.gz
alternatives.log.3.gz  dpkg.log.2.gz          popularity-contest.2.gz
alternatives.log.4.gz  dpkg.log.3.gz          popularity-contest.3.gz
alternatives.log.5.gz  dpkg.log.4.gz          popularity-contest.4.gz
alternatives.log.6.gz  dpkg.log.5.gz          popularity-contest.5.gz
alternatives.log.7.gz  dpkg.log.6.gz          popularity-contest.6.gz
apparmor               dpkg.log.7.gz          pycentral.log
apport.log             dpkg.log.8.gz          samba
apport.log.1           dpkg.log.9.gz          speech-dispatcher
apport.log.2.gz        faillog                syslog
apport.log.3.gz        fontconfig.log         syslog.1
apport.log.4.gz        fsck                   syslog.2.gz
apport.log.5.gz        gdm                    syslog.3.gz
apport.log.6.gz        gufw_log_server.txt    syslog.4.gz
apport.log.7.gz        gufw_log.txt           syslog.5.gz
apt                    installer              syslog.6.gz
aptitude               jockey.log             syslog.7.gz
aptitude.1.gz          jockey.log.1           udev
auth.log               jockey.log.2.gz        ufw.log
auth.log.1             jockey.log.3.gz        ufw.log.1
auth.log.2.gz          jockey.log.4.gz        ufw.log.2.gz
auth.log.3.gz          kern.log               ufw.log.3.gz
auth.log.4.gz          kern.log.1             ufw.log.4.gz
boot                   kern.log.2.gz          unattended-upgrades
boot.log               kern.log.3.gz          user.log
bootstrap.log          kern.log.4.gz          user.log.1
btmp                   lastlog                user.log.2.gz
btmp.1.gz              lpr.log                user.log.3.gz
ConsoleKit             lpr.log.1              user.log.4.gz
cups                   lpr.log.2.gz           vbox-install.log
daemon.log             lpr.log.3.gz           wtmp
daemon.log.1           lpr.log.4.gz           wtmp.1.gz
daemon.log.2.gz        mail.err               Xorg.0.log
daemon.log.3.gz        mail.info              Xorg.0.log.old
daemon.log.4.gz        mail.log               Xorg.1.log
debug                  mail.warn              Xorg.1.log.old
debug.1                messages               Xorg.2.log
debug.2.gz             messages.1             Xorg.2.log.old
debug.3.gz             messages.2.gz          Xorg.3.log
debug.4.gz             messages.3.gz          Xorg.3.log.old
dist-upgrade           messages.4.gz          Xorg.4.log
dmesg                  news                   Xorg.4.log.old
dmesg.0                pm-powersave.log       Xorg.5.log
dmesg.1.gz             pm-powersave.log.1     Xorg.5.log.old
dmesg.2.gz             pm-powersave.log.2.gz  Xorg.failsafe.log
dmesg.3.gz             pm-powersave.log.3.gz  Xorg.failsafe.log.old
dmesg.4.gz             pm-powersave.log.4.gz

```

---

