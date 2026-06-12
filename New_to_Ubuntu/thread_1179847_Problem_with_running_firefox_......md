---
title: "Problem with running firefox ....."
date: 2009-06-06
forum: New to Ubuntu
---

### Post by karan_sharma01 on 2009-06-06
I am using ubuntu 8.04 

Initially the problem with firefox was that with flash player.Web sites like youtube,com always ask to get latest flash player even though i had installed firefox many times with command "apt-get install flashplugin nonfree" .

Then i upgraded firefox with command " wget -P ~ [ftp://ftp.mozilla.org/pub/firefox/releases/3.0b3/linux-i686/en-US/firefox-3.0b3.tar.bz2](ftp://ftp.mozilla.org/pub/firefox/releases/3.0b3/linux-i686/en-US/firefox-3.0b3.tar.bz2) && tar xjf ~/firefox-3.0b3.tar.bz2 -C ~"

now the problem is when ever i click firefox icon it shows 
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

if i start firefox from terminal as super user its running all right ....
but with any other user its showing the same message .
And also the problem of flash player is still not solved ..its again showing the same message "get latest flash plugin""....


please help..

---

### Post by kalesh7 on 2009-06-06
Remove all flash plugins, remove firefox then install firefox from the package manager, then run firefox and get to a flash enabled site, firefox should show a bar near the top that says something like "plugins are needed to display all the media on this page" (I forget the exact wording" hit install or whatever button it is. it will search and give you a list of options, install one from it preferably the one that appears to be the latest one from abode.

---

### Post by karan_sharma01 on 2009-06-06
still the same problem 
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."
running from terminal .....with super user only

---

### Post by ddrichardson on 2009-06-06
run firefox from the command line (as normal user) using:```
firefox -p
```This will identify if you have a profile issue.

---

### Post by Knacker_Ned on 2009-06-06
I often have the "Firefox is already running" problem - despite reinstalling Firefox (3.0.10). There's no consistency, either. About half the time Firefox loads fine, but on other occasions I have to use the killall command to get it to load.

---

### Post by Knacker_Ned on 2009-06-06
Apologies to karan_sharma01 for butting in here, but this is what I get when typing firefox -p at the terminal: 

the choose user profile window pops up with only the default option showing. I click on Start Firefox and Firefox runs okay. But when I close Firefox, the terminal window now says "firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server &#65533;&#65533;re/locale/en/LC_MESSAGES/libc.mo0."

I then started Firefox again (by clicking on the icon) and it starts okay (on this occasion, anyway).

---

### Post by Knacker_Ned on 2009-06-06
Ahah! Tried the same process again and this time Firefox wouldn't load, coming up with the message:

"[COLOR=#000000][FONT=DejaVu Sans]Firefox cannot use the profile "default" because it is in use. To continue, close the running instance of Firefox or choose a different profile."[/FONT][/COLOR]

---

### Post by karan_sharma01 on 2009-06-06
with firefox -p .. iam getting 3 option for profile(default,default user,default_user)....and running with all 3......
please help 


:-(

---

### Post by derekeverett on 2009-06-06
Hi there...

I would try running ps -e in the terminal and get the process numbers for each instance of firefox.

Then maybe try kill -p processnumber for each instance. That should get rid of them all.

As far as getting flash to work sudo apt-get install ubuntu-restricted-extras should take care of most of your woes.

I'm no expert here but I think that should work...

---

### Post by Curvature_Tensor on 2009-06-06
Two options:

1. delete the .lock file created on your computer to launch a new firefox.  
2. always start firefox from terminal, when done, close the terminal after closing the browser screen.

---

### Post by ddrichardson on 2009-06-06
Can you post the output of:```
wheris firefox
```

---

### Post by Knacker_Ned on 2009-06-07
Thank you everyone for helping us both with our problems. I'll begin with ddrichardson's request as it's the simplest for a newbie to understand. ;) 

I typed in wheris firefox at the terminal and received this:

/usr/bin/firefox /usr/lib/firefox /usr/share/firefox

---

### Post by 3rdalbum on 2009-06-07
Your other problem (Flash doesn't work):

The Flash Player package does not contain Flash Player, it actually contains a script that downloads Flash Player from the Adobe website. When Hardy was released, the Flash package worked. However, a year has passed and now the file is no longer on Adobe's server in that location.

You need to manually install Flash Player from the Adobe website, or update to the latest Ubuntu (9.04).

---

### Post by MadnessRed on 2009-06-07
> **Knacker_Ned said:**
> I often have the "Firefox is already running" problem - despite reinstalling Firefox (3.0.10). There's no consistency, either. About half the time Firefox loads fine, but on other occasions I have to use the killall command to get it to load.

bit drastic, whenever I have that problem I just open the system processes and kill the firefox process.

---

### Post by ddrichardson on 2009-06-07
Part of the problem is the way you have installed Firefox. Uncompressing a non-debian specific tarball means there are likely to be issues and one that springs to mind is the different locations for plugins (/usr/share and /usr/local/share).

I'd stronly advise you to remove the current copy and install an aptitude controlled copy unless there is a specific reason not to be using one in the repository.

---

### Post by Knacker_Ned on 2009-06-07
MadnessRed: I'll remember that. Thanks for the tip.

ddrichardson: I don't recall uncompressing a non-debian specific tarball, though it could quite easily have happened when using the Hardy Heron version of Kubuntu. Since then I've upgraded to Jaunty Jalope. Anyway, I'm going to give your suggestion a go and will report back here - hopefully - later today. Thanks again for your help.

---

### Post by ddrichardson on 2009-06-07
> **Knacker_Ned said:**
> MadnessRed: I'll remember that. Thanks for the tip.

ddrichardson: I don't recall uncompressing a non-debian specific tarball, though it could quite easily have happened when using the Hardy Heron version of Kubuntu. Since then I've upgraded to Jaunty Jalope. Anyway, I'm going to give your suggestion a go and will report back here - hopefully - later today. Thanks again for your help.
You said in your first post:> Then i upgraded firefox with command " wget -P ~ [ftp://ftp.mozilla.org/pub/firefox/re...-3.0b3.tar.bz2]("ftp://ftp.mozilla.org/pub/firefox/releases/3.0b3/linux-i686/en-US/firefox-3.0b3.tar.bz2") && tar xjf ~/firefox-3.0b3.tar.bz2 -C ~"
That's a generic Linux build.

---

### Post by Knacker_Ned on 2009-06-07
> **ddrichardson said:**
> You said in your first post:
That's a generic Linux build.

No, you're confusing me with the original poster. Sorry.

Anyway, I've used Synaptic to remove all trace of Firefox. I also deleted  /usr/bin/firefox /usr/lib/firefox /usr/share/firefox and then reinstalled Firefox from Synaptic but to no avail as the original problem has returned, that is, I sometimes can't reload Firefox because it says Firefox is already in use. 

Don't know if it helps any, but when this occurs and I check Show System Activity, the running application is usr/lib/firefox and the Parent is Ksystraycmd.

---

### Post by ddrichardson on 2009-06-07
Oh OK I'm with you now sorry - is it related to this:
[https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/306056](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/306056)

Really, raising a bug report with Mozilla is likely to yield the best results.

---

### Post by Knacker_Ned on 2009-06-07
> **ddrichardson said:**
> Oh OK I'm with you now sorry - is it related to this:
[https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/306056](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/306056)

Really, raising a bug report with Mozilla is likely to yield the best results.

Will do. Thanks again for your help. :)

---

### Post by karan_sharma01 on 2009-06-09
output of "whereis firefox "


root@Rocky:/home/karan# whereis firefox
firefox: /usr/bin/firefox /usr/share/firefox


i've reinstalled firefox from synaptic package manager and still suffring from those problems .....:(:(:(:(:(

please help ...thanx

---

### Post by karan_sharma01 on 2009-06-09
please help sumbody

---

### Post by ddrichardson on 2009-06-09
You're missing some of the symlinks.

I'd advise you to ask Mozilla, [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs) is a good place to start filing bugs as Mozilla is upstream.

---

### Post by karan_sharma01 on 2009-06-10
some how i've managed to solve one problem .....now my firefox is running from the icon ......

well i am no expert in Ubuntu but i think the problem was that only root user has the permissions to access profile.ini and cl67a3c0.default folder  in home/.mozilla ......so i replaced the whole firefox folder in .mozilla folder with the firefox folder from firefox-3.0b3.tar.bz2 package having the appropriate privileges for all users that i've downloaded from the internet ..............
now its running fine 

thanx all for the help!!!!!!


:D:D:D:D:D:D:D:D:

---

### Post by Lykopis on 2009-06-30
I had this problem with Firefox as well. So here's what I did maybe this will help someone out there, but this is for the KDE (Kubuntu) users.
Open "System Settings" and on the  "advanced" tab click "Session Manager" Change the setting from "Restore previous session" to "Start with an empty session"  Click the apply button and exit.

Ok what this does is to make sure all processes are killed at log- off Firefox included.

Next I went to my home folder under view I clicked  "show hidden files" .
Find the .mozilla folder  and right click on it then go to the "Permissions" tab.
Change the Permissions for all fields to "Can View & Modify Content"  
Click the "Apply changes to all subfolders and their contents" box.
Click the OK button and exit all windows then log off and back on.
You should be able to start Firefox now and if Firefox crashes a log-off will kill it's process.
Also you might wish to try the Opera Browser it doesn't suffer from this bug. but you have to get it from the Opera site.
I don't think it's in the Ubuntu repositories but it does work. 

You can get Opera here
[http://www.opera.com/](http://www.opera.com/)

---

