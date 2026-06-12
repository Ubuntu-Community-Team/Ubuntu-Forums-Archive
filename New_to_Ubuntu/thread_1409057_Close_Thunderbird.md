---
title: "Close Thunderbird"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by boxcorner on 2010-02-17
Hello
I am an M$ Win XP user who is new to Ubuntu 9.10 Karmic Koala.
I have read Keir Thomas' excellent *Ubuntu Pocket Guide and Reference*.
I have also browsed numerous Web page providing advice on installing Thunderbird and found the different instructions for the various versions of Ubuntu somewhat confusing and consequently I may have got muddled.
I am trying to get Thunderbird installed, so I can import my profiles from XP.
I downloaded and double-clicked on thunderbird-3.0.1.tar.bz2
At the command-line I typed: sudo apt-get install thunderbird
Then Applications > Internet > Mozilla Thunderbird Mail/News
whenever I click on the link the following message is displayed:
[I]Close Thunderbird
Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart you computer.[/I]
Restarting the computer does not help.
I have looked in: System > Administration > System Monitor > Processes
but there does not seem to be any process to end, other than the one that produces the message!
Could someone please tell me what I am doing wrong?
Any tips on how to get Thunderbird installed and migrating my profiles from XP would be much appreciated.
Thank you in advance.

---

### Post by capybara! on 2010-02-17
Try to kill thunderbird first. You can use the 'top' command to display running processes, maybe you find the pid of the running thunderbird there, then you can kill it with the 'kill' command. 'killall thunderbird' might help as well. If that does not work, try 'ps aux | grep thunderbird'. What is the output when runn ing this command?

---

### Post by boxcorner on 2010-02-17
> **capybara! said:**
> Try to kill thunderbird first. You can use the 'top' command to display running processes, maybe you find the pid of the running thunderbird there, then you can kill it with the 'kill' command. 'killall thunderbird' might help as well. If that does not work, try 'ps aux | grep thunderbird'. What is the output when runn ing this command?
Many thanks for your reply.
Am using Ctrl+Alt F1 to access the shell and then Ctrl+Alt F7 to revert back to the gui.  Presume that is what I am supposed to do.
Tried *top* but could not see anything saying thunderbird.  Maybe I missed it.
Had already tried *killall thunderbird* (sorry I forget to mention it) result *no process found*
*ps aux | grep thunderbird* produced result *ubuntu 2388 0.0 0.0 3036 796 tty1 S+ 13:23 0.00 grep --color=auto thunderbir*d (thunderbird is red)
Is that what you would expect?

---

### Post by philinux on 2010-02-17
@boxcorner

Have you by chance change the settings in System>prefs>startup application.

Options Tab. Make sure there is no tick in Automatically remember running apps.

You can access the command line by Apps>Access>Terminal.

---

### Post by boxcorner on 2010-02-17
> **philinux said:**
> @boxcorner

Have you by chance change the settings in System>prefs>startup application.

Options Tab. Make sure there is no tick in Automatically remember running apps.

You can access the command line by Apps>Access>Terminal.

No,* automatically remember running apps* in the Options tab was/is not ticked.
Many thanks for pointing out *Apps>Access>Terminal*; seems I need a white stick.
Phew! Now I can use Copy & Paste.

---

### Post by audiomick on 2010-02-17
For cut and paste in the terminal you need ctrl + shift + c and ctrl + shift + v. Took me ages to figure that out...
What is also useful is that the up / down cursor arrows scroll through the last commands given in the terminal.

---

### Post by boxcorner on 2010-02-17
> **audiomick said:**
> For cut and paste in the terminal you need ctrl + shift + c and ctrl + shift + v. Took me ages to figure that out...
What is also useful is that the up / down cursor arrows scroll through the last commands given in the terminal.
Great tip, thanks.  I tried ctrl + c & ctrl + v, but didn´t think of adding shift!

---

### Post by tom.swartz07 on 2010-02-17
> **audiomick said:**
> For cut and paste in the terminal you need ctrl + shift + c and ctrl + shift + v. Took me ages to figure that out...
What is also useful is that the up / down cursor arrows scroll through the last commands given in the terminal.

...and <TAB> will auto-complete whatever youre typing

---

### Post by philinux on 2010-02-17
Getting a bit OT here. ;)

I would do this.

```
sudo apt-get purge thunderbird
```

Delete its .thunderbird config folder, or whatever it's called, in your home. And then reinstall TB from synaptic or terminal.

---

### Post by boxcorner on 2010-02-17
@ tom.swartz07
thanks
@ philinux
I purged TB
Cannot see a config folder in home
In synaptic can only see TB2 not TB3 listed
Reinstalled TB via terminal using sudo apt-get install thunderbird result original problem
Purged TB again
Tried sudo apt-get install thunderbird-3.0.1
Result: Couldn't find package thunderbird-3.0.1
thunderbird-3.0.1.tar.bz2 is in Downloads
When I double-click on it I see a folder called thunderbird in a window showing location root /
Should I be trying to browse to it from synaptics in order to get the package listed?

---

### Post by audiomick on 2010-02-17
It is highly possible that the newest version of TB in the repositories is not the most recent version. Things only get into the repos after they have been checked by the Ubuntu people, and the versions are often a bit older. I don't tend to worry about that mostly. I would rather just accept a slightly older version with a high chance of it working than install a newer version "by hand'" that may give me grief.

As far as I know, apt-get and the synaptic package manager are the same mechanism. Having said that, it can't hurt to purge it again and try installing it from the package manager.

To find the config folder for Thunderbird, you will have to select "view hidden folders" in the "View" menu in the file manager. The hidden folders all have a dot at the start of the name .likethis . The config files for Firefox are in .mozilla, and it wouldn't surprise me if the Thunderbird ones land in there as well.

---

### Post by WildeBeest on 2010-02-17
I have TB3 installed on 9.04 and 9.10. I don't have the link I used bookmarked at home.
I'll post it when I get home. In about 5 hours.

---

### Post by boxcorner on 2010-02-17
@ philinux

Okay, I found and deleted the config folder.  That did the trick, thanks. Took me a while to remember that the dot meant the folder would be hidden.  Hence, (for the benefit of other newbies like me) I needed to ticked the Show Hidden Files box in View.  I installed TB2 via System > Admin > Synaptic.

However, Check for Updates in TB2 is greyed out.  When I downloaded lightning-10b1-tb_sm-linux.xpi I discovered that it would only work with TB3, which is why I tried to install TB3.  So, now I am back to square one in this game. I use the calendar in XP, so imagine I would have a problem importing my profiles without it.

@ audiomick
Thanks.  The dot fooled me for a while.  

I am still using TB2 in XP andI use the Lightning calendar add-on.  When I tried to upgrade to TB3, I discovered that the Lightning add-on had not been updated, so I had to roll back to TB2. 

Now I have TB2 installed in Ubuntu, when tried to install Lightning the message was ¨Lightning 1.0b1 could not be installed because it is not compatible with Thunderbird 2.0.0.23. (Lightning 1.01b will only work with Thunderbird versions from 3.0b4 to 3.0*.)

Hence I am trying to get TB3 installed.

@ WildeBeest
Thanks.

---

### Post by philinux on 2010-02-17
> **boxcorner said:**
> @ audiomick
Thanks.  The dot fooled me for a while.  

I am still using TB2 in XP andI use the Lightning calendar add-on.  When I tried to upgrade to TB3, I discovered that the Lightning add-on had not been updated, so I had to roll back to TB2. 

Now I have TB2 installed in Ubuntu, when tried to install Lightning the message was ¨Lightning 1.0b1 could not be installed because it is not compatible with Thunderbird 2.0.0.23. (Lightning 1.01b will only work with Thunderbird versions from 3.0b4 to 3.0*.)

Hence I am trying to get TB3 installed.

@ WildeBeest
Thanks.

Righto thought as much. Now you got TB2 working as it should be simple to get TB3.
One of the easiest and painless ways is this.
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by WildeBeest on 2010-02-17
I downloaded TB3 from [http://www.mozillamessaging.com/thunderbird/download/?product=thunderbird-3.0.1&os=linux&#9001;=en-US]("http://www.mozillamessaging.com/thunderbird/download/?product=thunderbird-3.0.1&os=linux&lang=en-US")

Un-package the tar to a folder of choice. Most people use the Desktop.

Using nautilus, navigate to the folder. Find "run-mozilla.sh", right click, select properties then select the permissions tab.
Check the "Allow _e_xecuting file as program".

From the terminal CD Desktop
then run sudo sh ./run-mozilla.sh

Viola, TB3 install.

---

### Post by boxcorner on 2010-02-19
@ WildeBeest

Many thanks for the link and helpful instructions. 
I now have run-mozilla.sh in a folder called thunderbird on the Desktop
"Allow _e_xecuting file as program" is checked.
When I run 
sudo sh ./run-mozilla.sh
I get
sh: Can't open ./run-mozilla.sh

Have not succeeded in getting TB3 installed with Lightning 1.0 but have learned a lot about Ubuntu!  Am still using TB2 with Lighting under XP and want to import my e-mails and settings, so am now trying to get TB2 installed with Lightning 0.9 under Ubuntu, instead.  While looking for Lightning 0.9 to download, I discovered this helpful information [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

---

### Post by _khAttAm_ on 2010-02-20
I will guide you via terminal since you are comfortable with it:
Add Development (Mozilla Daily) repo:
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```
Update list
```
sudo apt-get update
```
Install thunderbird:
```
sudo apt-get install thunderbird-3.0
```
Now, you can launch it from: Internet>Shredder 3 Mail/News.

If you do this, you will have development version of Thunderbird (codename shredder) installed and you will get updates almost daily. If that bothers you, you can test it (to make sure it does not crash) and then disable the repository (from System>Administration>Synaptic>Settings>Repos and uncheck the one that says ubuntu-mozilla-daily) and continue using it. 

If it works OK, you can remove the v2.

Hope this helps.

---

### Post by boxcorner on 2010-02-20
Thanks [_khAttAm_]("http://ubuntuforums.org/member.php?u=510062") I appreciate your offer of help.  Using Terminal is not a problem, also I've been experimenting with Software Sources trying different repositories and been using Synaptic Package Manager.  So, Ubuntu feels a lot less strange now!  In fact, I got Shredder 3 installed ok but was unable to get Lightning 1.0 to work, hence I reverted back to TB2.  Currently have got TB2 plus Lightning 0,9 installed and now have my e-mails from XP, having transferred my profiles and altered the profiles.ini however Lightning itself not working properly and the calendar data is missing.  So, I was about to have another go at getting TB3 with Lightning 1.0 installed when I discovered your message.  Will gladly try what you suggested, but need to get Lighting working with it.  Will post an update later.

[COLOR=black]ADDENDUM[/COLOR] - Sunday, 21 February 2010 10:57 AM
Shredder installed ok. Slight glitch whereby e-mails in TB2 Inbox were missing in Shredder's Inbox.  Workaround: moved e-mails from TB2's Inbox into new folder created in Categories and then copied the updated TB2 Profiles folder to Shredder.  Installed Lightning 1.0b1 now working fine, recognises my calendar data.  Sent/received test e-mails and all seems ok.  Great!  Now I've got e-mail working, I can begin to work productively using Ubuntu as my first OS of choice. So, onwards forwards with the rest of the migration. Many thanks for your help.

---

