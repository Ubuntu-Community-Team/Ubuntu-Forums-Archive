---
title: "HELP!!!!! NO DESKTOP after login. Blank screen."
date: 2009-11-10
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-11-10
After logging in my screen is one big orange blank! No Desktop.

I had earlier today went in terminal mode and performed:

mv .evolution .evolution.corrupt

After shutting PC down and rebooting the blank screen problem arose.

What to do? Running Microsoft Windows sucks right now.

HELLLLLLLLP!

Ed

Update: This is affecting both users assigned. No Desktop for me or my wife.

---

### Post by theozzlives on 2009-11-10
> **ozark_hillbilly said:**
> After logging in my screen is one big orange blank! No Desktop.

I had earlier today went in terminal mode and performed:

mv .evolution .evolution.corrupt

After shutting PC down and rebooting the blank screen problem arose.

What to do? Running Microsoft Windows sucks right now.

HELLLLLLLLP!

Ed

login with recovery mode, go to root prompt, go to your home:
```
mv .evolution.corrupt .evolution
reboot
```

---

### Post by unamanic on 2009-11-10
Moving your evolution folder should not have caused this problem.  evolution would have just recreated an empty .evolution folder on its next launch. At the login screen, press [crtl] + [alt] + F1 then login text mode and issue the following commands:
```

mv .gconf bak.gconf
mv .gconfd bak.gconfd
exit

```

Then press [crtl] + [alt] +F7 and login.  All of you gnome settings will have defaulted  back to thier standard configuration.  The .gconf directories hold more than gnome configs though, so if use f-spot you want to manually copy it's relevant directories from you bak.gconf directories to your .gconf directories after logging in again.

---

### Post by ozark_hillbilly on 2009-11-10
> **theozzlives said:**
> login with recovery mode, go to root prompt, go to your home:
```
mv .evolution.corrupt .evolution
reboot
```


Oz,

No workee:

cannot stat   .evolution.corrupt   No such file or directory

????

Ed

---

### Post by ozark_hillbilly on 2009-11-10
Unamanic,

I wish it were so simple. No change in problem after entering your suggested commands.

I'm totally lost on this one,

Ed




> **unamanic said:**
> Moving your evolution folder should not have caused this problem.  evolution would have just recreated an empty .evolution folder on its next launch. At the login screen, press [crtl] + [alt] + F1 then login text mode and issue the following commands:
```

mv .gconf bak.gconf
mv .gconfd bak.gconfd
exit

```

Then press [crtl] + [alt] +F7 and login.  All of you gnome settings will have defaulted  back to thier standard configuration.  The .gconf directories hold more than gnome configs though, so if use f-spot you want to manually copy it's relevant directories from you bak.gconf directories to your .gconf directories after logging in again.

---

### Post by unamanic on 2009-11-10
Ok, next is to try on a new user, may something else in your profile is borked.

Back to the command line
```

sudo useradd testuser
sudo passwd testuser
[give the test user a password]

```
then back to the login screen and try to logon with the testuser account and see if it works.

Forgot to ask earlier, you are are on a standard ubuntu install or are you using kubuntu or xubuntu or some other non standard window manager.

---

### Post by ozark_hillbilly on 2009-11-10
Unamanic,

I appreciate your help as this is a SERIOUS problem if I can't get the desktop back.

I have a standard Ubuntu Intrepid Ibex 8.10 (with online updates) install.

I will go try your 2nd suggestion.

thanks,

Ed



> **unamanic said:**
> Ok, next is to try on a new user, may something else in your profile is borked.

Back to the command line
```

sudo useradd testuser
sudo passwd testuser
[give the test user a password]

```
then back to the login screen and try to logon with the testuser account and see if it works.

Forgot to ask earlier, you are are on a standard ubuntu install or are you using kubuntu or xubuntu or some other non standard window manager.

---

### Post by ozark_hillbilly on 2009-11-10
Ok, I added new testuser and logged on. Same problem: no desktop.
I got this message before log on:
Your home directory is listed as '/home/testuser' but it does not exist. Do you want ot log in with root directory as your home directory?
I said yes.

One thing I did earlier today was to revert back to corrupt Evolution using "restore" tar file as I wanted to regain my mail messages. But SMTP problem came back as well. So I went back to mv .evolution .evolution.corrupt to remove SMTP problem (it was asking for password to a deleted account when invoking Send/Receive). Things looked fine and worked fine with new SMTP account data. 
All was well til I shut PC down and later booted up.

Stumped,

Ed

---

### Post by unamanic on 2009-11-10
I forgot that useradd doesn't add the home directory by default., you can create it by issuing the following commands:
```

sudo mkdir /home/testuser
sudo chown -R testuser:testuser /home/testuser

```

Incedentally, I just tested trying to start a gnome session without having a home directory and got a blank background, without any panels. It got me thinking that you might have a permissions problem in your home directory.  Try issuing a:

```

sudo chmod -R [username]:[username] /home/[username]

```

---

### Post by ozark_hillbilly on 2009-11-10
OK, added /home/testuser directory and chown command.
Logged on as testuser. No Desktop still.

command:    sudo chmod  -R eld:eld /home/eld     generated chmod error:

         chmod: invalid mode eld:eld    (eld is my owner name)

The swampwater is turning to quicksand!  :^ )

Ed

---

### Post by unamanic on 2009-11-10
oops chown, not chmod.

---

### Post by unamanic on 2009-11-10
Ok, I'm stumped without looking at the sytem.  Seems like in gnome is fubar.  If the box is connected to the net, you could do a "sudo aptitude install xubuntu-desktop" or sudo aptitude install kubuntu-desktop" this will give you an XFCE or KDE destop environment to log into.  It should be enough to get your data off, or at least give you a GUI to further troubleshoot.

---

### Post by ozark_hillbilly on 2009-11-10
OK, chown it is. To be clear about things another person sent me a private message suggesting:

mkdir dotbak
mv .gconf* .config dotbak
sudo /etc/init.d/gdm restart ; exit

Not sure about that string of commands but it didn't work either.

Maybe too many cooks spoil the broth.  :^ (

---

### Post by ozark_hillbilly on 2009-11-10
This is getting pretty deep for an ole man like myself. I DO NOT want to lose my Desktop data or Linux partition files.

What is a suggested course of action someone with limited Linux capabilities should attempt?

Ed

P.S. All this GD trouble because Evolution got confused when I deleted an SMTP mail account.
     Sheeeez.

---

### Post by unamanic on 2009-11-10
almost everyone is suggesting the same things, moving your configuration files so that the system can recreate them from the default.  The fact that a new user did not work means that no matter its systemic, not just a single user.

Some more things to check:

1) is your drive full?
```

df -h

```
mine looks like:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G  7.0G   12G  39% /
/dev/sda8             228G  127G   90G  59% /home
/dev/sda1             194M   23M  162M  13% /boot
/dev/sda7             194M  5.6M  179M   4% /arch
/dev/sda3              20G  172M   19G   1% /ubuntu
/dev/sda2              20G  172M   19G   1% /suse
tmpfs                 1.9G  7.8M  1.9G   1% /dev/shm

you should look for 90s and 100 and

2) is /tmp writable
```

ls -al /

```you should see a line that looks like:
drwxrwxrwt.  24 root root  4096 2009-11-10 22:50 tmp

Look at the first bit if you have dashes where I have r, w, or x then we'll need to fix it.


If these two are good, I'd recommend doing a "sudo aptitude install kubuntu-desktop" (if you get an error about aptiude not found use apt-get in its place).  After it's done, you'll have a "kde session" option in your sessions menu at the login screen.

---

### Post by ElSlunko on 2009-11-10
What about trying to reinstall gnome? (I'm a newb so take it with a grain).

---

### Post by ozark_hillbilly on 2009-11-10
Using chown generated changing ownership not permitted error messages. ???

If I go KDE what do i do then to fix Gnome? This is unfamiliar territory for me. 

Unfortunately I don't have hours and hours to trouble shoot my way out of this. Not being versed in the Linux environment and commands makes this almost an effort in futility. I HATE to revert to DOS but may not have a choice.  It seems Linux problems aren't easily fixed for the uninitiated and consequently MANY give up and go back to DOS. That sucks but is reality probably.

Frustrated,

Ed

---

### Post by ozark_hillbilly on 2009-11-10
I'll check these things out as well. May not get back tonite as I have to hit the sack for work tomorrow. Bummer.

Ed

---

### Post by unamanic on 2009-11-10
Did you put sudu on front of the chown command?
```

sudo chown  -R eld:eld /home/eld

```

this tells the system to do it with super user permissions.

Going KDE will give you a way to have a GUI while troubleshooting as well as giveing you a way to use machine until this gets ironed out.

---

### Post by ozark_hillbilly on 2009-11-10
Umanic,


Drive is definitely NOT FULL. Lots of space.
/tmp is writable.....looks like your line of code at beginning.

sudo chown did work this time....i forgot to sudo it. No change though.

May try to install KDE at this point (tomorrow).

Stay tuned as I'll need LOTS more help!  :^ )

Ed

---

### Post by asuastrophysics on 2009-11-11
What exactly did you do on your desktop before you couldn't login? 

was that evolution thing the only thing you changed? 

Did you change anything in /etc/X11/xorg.conf?
 
*****Can anyone remind me where the services.list is for each user?****

if none of the above happened, perhaps your individual user "startup programs" configuration file was tampered with. It could be starting an application that's stopping X.

---

### Post by draxenato on 2009-11-11
Here's something you could try. Get to a command prompt, either CTRL-ALT-F1 or select the xterm option at the login screen if it's available.
Once at the command prompt type;

sudo su - 
{enter your password when prompted}
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
dpkg-reconfigure -phigh xserver.xorg
exit

What we just did was 'su' to the root account so everything we do from now is as the root user, be *very* careful. Then we copied the existing X config file to a backup (the .orig file). The secret sauce is in the dpkg line, that forces the xserver.xorg package to reset itself as if it were freshly installed. The final 'exit' line takes us out of the root shell we spawned with the 'su -' command, you probably don't wanna be running with root privs any longer than you have to be.
After all this I would gracefully reboot the box to make sure the changes stick.

---

### Post by rabbithunter666 on 2009-11-11
Facing same problem. I will try these method tonight.

---

### Post by pb1jb1 on 2009-11-11
Funny enough the same happened to me this morning.

I was having issues with Samba where when I browsed to the network folder and drilled down to my domain it mentioned something like unable to browse network files. I was able to connect to all machines using IP.
So I uninstalled all and anything to do with samba rebooted and bam blank desktop
I was able to brower everything via the command line access the web but no icons.
I was unable to click and open my home folder or other homy/ network icons.

Put me in a bad mood as now im at work with a broken computer that I have turned off in discussed

---

### Post by pb1jb1 on 2009-11-11
Im going to try this tonight

sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity

---

### Post by pb1jb1 on 2009-11-11
Didnt work

logged on as root still no access to any folders.

rebuilt machine

---

### Post by ozark_hillbilly on 2009-11-11
Hello Linux Gurus,

Well I spent a couple hours downloading Kubuntu and it cleanly installed and I am now running on the KDE display manager.

It gives me access to everything it seems but I want to go back to Gnome as soon as possible.

What is recommended troubleshooting to correct corrupt Gnome?
 I don't want to jeopardize any data on my Desktop or user files.

Waiting for advice,

P.S.
All my grief came about after doing a  mv .evolution .evolution.corrupt.
Then restoring my .tar file to regain mail messages. This also restored my corrupt SMTP mail account data so I was forced to do the mv evolution again. All this went without incident until I rebooted the PC.
 My SMTP mail account data had became corrupt after deleting a mail account under Edit Preferences Mail Accounts. Every time I invoked Evolution's Send/Receive function it prompted me for the deleted mail account's password. This also halted any further retrieval/sending of mail.

---

### Post by ozark_hillbilly on 2009-11-11
Astro,

See my latest entry on the thread and it explains what I did before Gnome went tits up on me.
I am using KDE temporarily. Need suggestions on what to look at for fix.

Ed

---

### Post by unamanic on 2009-11-11
First thing you need to do now that you have a working GUI is backup all of your data.  I'm trying to get an 8.10 ISO downloaded to put in a virtual machine so I can have the same set up as you.

---

### Post by ozark_hillbilly on 2009-11-11
Sounds good Will!
I am all ears at this point.

Ed

---

### Post by itsbrad212 on 2009-11-11
just throwing it out there. try this:

```

sudo /etc/init.d/gdm stop
startx 

```

---

