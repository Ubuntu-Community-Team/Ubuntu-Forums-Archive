---
title: "[SOLVED] My Firefox got invaded"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by zaivala on 2008-12-15
Apparently some popup got into my Firefox (3.0.x), although I approved no such.  On every screen, either I have some little box floating across the screen asking me to click on it, or I get slow page loads with lots of black flashes.  

Being a newbie, I tried to uninstall and reinstall... but Add/Remove Programs won't let me uninstall.

I also tried using Seamonkey, but that won't let me install my plugins without being Root.  So for now I'm back in Windoze until someone can help.

Any ideas?

---

### Post by Keen101 on 2008-12-15
You could try reinstalling using synaptic package manager.

>System >Administration >Synaptic

If that doesn't help try to do a "complete removal" from synaptic since that will remove configuration files. (It should only remove firefox, and maybe java, but if it say's it's also going to remove ubuntu-desktop then don't do it.)

That is a really weird issue. I've never heard of that before, not even on windows.

---

### Post by maddog46113 on 2008-12-15
Try this, note you will lose all data in firefox and have to reinstall flash and all the addons but its worth it to get firefox back to normal.

Open Terminal
```

sudo apt-get remove firefox --purge

```

Then type the following:
```
 sudo apt-get install firefox
```
Then to reinstall flash:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Toshibawarrior on 2008-12-15
Depends on which webpages you visit...Somehow some pages (most likely promotional, pornographic and torrent sites) have a way to infiltrate some pop-ups into Firefox independently of which add-ons you use. You can try what Keen101 suggested, but if you keep visiting those kinds of sites expect some pop-ups to come along.

I've got these pop-ups from guitar tabs sites and vacation booking sites with stupid promotional banners and pop-ups that say "Click Here You WoN!" and stuff like that. It happened to me in XP, on Vista and here on Ubuntu too...:(

Hope this helps!

---

### Post by zaivala on 2008-12-16
Truth be told, I visited a porn site a friend mentioned over the weekend, and that's when the trouble started.  I don't do that hardly at all, and had never been to this site before (word of warning: it was redtube.com).  If there is an easier way to purge the demon, please let me know.

---

### Post by zaivala on 2008-12-16
> **maddog46113 said:**
> Try this, note you will lose all data in firefox and have to reinstall flash and all the addons but its worth it to get firefox back to normal.

Open Terminal
```

sudo apt-get remove firefox --purge

```

Then type the following:
```
 sudo apt-get install firefox
```
Then to reinstall flash:
```
sudo apt-get install flashplugin-nonfree
```

Thank you for this.  I will do that if, after hearing back from toshibawarrier, it is my last resort, which I fear it may be.

Moss

---

### Post by adobrakic on 2008-12-16
try installing adblock plus!

---

### Post by zaivala on 2008-12-16
> **adobrakic said:**
> try installing adblock plus!

Already did, it didn't stop this one.

---

### Post by scorp123 on 2008-12-16
Guys,

Removing and installing a program again in order to "fix" it is Windows-thinking and is not likely to help here. So you guys better drop your old habits.

Fact is that the program is doing fine, it functions as intended. So why do you want to remove it??? The fact that it shows a stupid pop-up has nothing to do with the program itself but rather with the user's settings.

So in order to reset the program it should be enough to simply erase the user's Firefox settings and then start it again ... that would give this user a clean new profile: 

**[COLOR="Red"]Warning: This command will completely wipe your Firefox settings![/COLOR]** ```
rm -rf ~/.mozilla
```

Installing and reinstalling is overkill ... and it's not likely going to help anyway if you're not taking care of the user settings in **~/.mozilla** ... And no: a "apt-get --purge remove" only removes system-wide settings, user settings are not taken care of. ;)

---

### Post by zaivala on 2008-12-16
> **scorp123 said:**
> Guys,

Removing and installing a program again in order to "fix" it is Windows-thinking and is not likely to help here. So you guys better drop your old habits.

Fact is that the program is doing fine, it functions as intended. So why do you want to remove it??? The fact that it shows a stupid pop-up has nothing to do with the program itself but rather with the user's settings.

So in order to reset the program it should be enough to simply erase the user's Firefox settings and then start it again ... that would give this user a clean new profile: 

**[COLOR="Red"]Warning: This command will completely wipe your Firefox settings![/COLOR]** ```
rm -rf ~/.mozilla
```

Installing and reinstalling is overkill ... and it's not likely going to help anyway if you're not taking care of the user settings in **~/.mozilla** ... And no: a "apt-get --purge remove" only removes system-wide settings, user settings are not taken care of. ;)

Sorry for the Windows thinking -- but if you'll note, I DID ask how to fix it WITHOUT reinstalling it.  I have been all through the Preferences panel, and there's nothing to clear popups which have loaded -- that I can see.  And help is appreciated.

---

### Post by azebuski on 2008-12-16
I couldn't resist visiting redtube.com just to see and I found no adverse affects.  Each link I clicked on resized my Firefox window and moved it slightly off screen but I maximized each time and all was fine.  I have experienced no pop ups or anything else.

---

### Post by zaivala on 2008-12-16
I did the 

rm -rf ~/.mozilla

It didn't even ask for my password, just did it and gave me a command line... no "Done." or anything...

And yeah, it worked.  Thanks loads.  I only have to restore every bloody thing I ever did, but it's worth it.  Good thing I had FoxMarks.

Hugs,
Moss

---

### Post by scorp123 on 2008-12-16
> **zaivala said:**
> I did the 

rm -rf ~/.mozilla

It didn't even ask for my password You're deleting your own settings in your own home directory ... and you're obviously already logged in otherwise you wouldn't be able to copy & paste that command into the shell .... So why should it ask you for your password again? :D

> **zaivala said:**
>  just did it and gave me a command line... no "Done." or anything...  Different than Microsoft programs where you have to thank the Gods if a program does what it was supposed to do Unix programs will simply assume that whatever you typed there is exactly what you wanted. So why should it tell you anything when it does precisely as you told it? It is **_YOU_** who is telling the program what to do here... not the other way round.

So unless there was something to complain about (e.g. "Access denied" or "No such file or directory", or something along those lines) the program will do what it is told to do and keep its mouth shut. 

So if a program ends without complaining and without giving any errors ... then it means it worked. ;)

> **zaivala said:**
>  I only have to restore every bloody thing I ever did Learn how to make backups! ;)

[http://ubuntuforums.org/showthread.php?t=616707](http://ubuntuforums.org/showthread.php?t=616707)
[http://ubuntuforums.org/showpost.php?p=6281196&postcount=761](http://ubuntuforums.org/showpost.php?p=6281196&postcount=761)

---

### Post by scorp123 on 2008-12-16
> **zaivala said:**
> Sorry for the Windows thinking -- but if you'll note, I DID ask how to fix it WITHOUT reinstalling it.  BTW, most programs will keep their settings in a "hidden" folder inside your own home directory.

The folders are "hidden" because they have a dot "." at the beginning of their names. And I write "hidden" because it's only pseudo-hidden. It's easy to unhide and see the files if you want.

In "Nautilus" (that's your File Manager in Gnome ... usually accessible via **Places > Home Folder** ...) you simply press Ctrl+H and you will see those "dot-files".

In a shell the files can easily be seen with commands such as e.g. ```
ls -al
```

You access those directories then with their names, e.g. ```
cd ~/.mozilla
```

When you look you will easily recognize the pattern here. Most programs keep their settings in one of those "dot-folders" which is usually named after the program which keeps its settings there. So Mozilla Firefox will keep its settings in a folder called ".mozilla", Mozilla Thunderbird will default to ".mozilla-thunderbird", Evolution defaults to ".evolution", and so on.

There are a few illogic ones, e.g. Pidgin seems to use ".purple". I don't get the logic behind that but this is how it is. Other programs seem more consistent.

Why I am telling you this ... If ever again a program does weird things, you can check if moving or renaming that relevant "dot-folder" can fix the problem (if it did: you could still wipe it ... if it didn't you can still rename it back).

---

### Post by philinux on 2008-12-16
Before doing any of this someone should have advised the OP to backup his bookmarks.

Bookmarks>Organise Bookmarks>Import and Backup>Export HTML.

---

### Post by Toshibawarrior on 2008-12-16
> **zaivala said:**
> Thank you for this.  I will do that if, after hearing back from toshibawarrier, it is my last resort, which I fear it may be.

Moss

I'm so sorry! It was nighttime here and I went to sleep. I just saw your posts. :( Deeply sorry...

But as an advice you might want to check and install these add-ons from the Mozilla site:

**Flashblock**-------->Blocks Flash media unless you click on it.
**Adblock Plus**------>Blocks most pop-ups.
**ProCon Latte**------>This is like a Parental Control that blocks sites by rating, keywords or descriptions, I use it as a guardian against unwanted sites. Best of all is that it is very easy to configure and it's not TOO invasive like other parental control add-ons. As I said I use it to know which sites are "bad" and it blocks the site and gives you a message when that happens.

And yes, porn sites are bad in any OS. They contain tons of malware and unwanted stuff, so if I were you I'd steer away from all that. Truth is that I'm disgusted by those sites. Sure they might be fun for some people, but I have deep respect for women, and those sites promote the exact opposite. This is just my personal 2 cents on the topic though.

Anyways, everyone here got to help before I did. Remember that to delete most program's user setting you have to go to your /home folder and delete the corresponding ".<program's name>" folder just like you did in command line. But if you navigate to the /home folder in Nautilus it'll a lot easier and you can actually see what you did, command line might be tricky and not always self-explanatory.

Well, I'm off, ring the bell if you need something else ;):)!

---

### Post by Keen101 on 2008-12-16
i recommend this. It helps me avoid sites that might be suspicious or dangerous. [http://www.mywot.com/en/download/ff](http://www.mywot.com/en/download/ff)

---

### Post by jolly_grunt on 2008-12-16
NoScript and AdBlock Plus have been a good combo for my Firefox install. I have yet to have any sort of infiltrations, and I visit questionable sites on a daily basis.

[http://noscript.net/]("http://noscript.net/")

[http://adblockplus.org/en/]("http://adblockplus.org/en/")

---

### Post by caravel on 2008-12-16
> **jolly_grunt said:**
> NoScript and AdBlock Plus have been a good combo for my Firefox install. I have yet to have any sort of infiltrations, and I visit questionable sites on a daily basis.

[http://noscript.net/]("http://noscript.net/")

[http://adblockplus.org/en/]("http://adblockplus.org/en/")

I'm glad someone mentioned noscript at last.  It is this add on that you need to install above all else.  When you visit such dodgy sites do not allow any scripts whatsoever.  For all other sites you can enable scripts from the originating site and then block those from the ad trackers.  I've used this add on with firefox for a few years and it is IMHO the best add on available for firefox.  Adblock, though it is useful for getting rid of annoying banners as required, won't give you any protection from such malicious scripts.

---

### Post by scorp123 on 2008-12-16
Another thing you can do and it's very easy:

you can put unwanted web-sites into your **/etc/hosts** file and give them an impossible IP address, therefore making them unreachable for you (which can be a good thing).

Let's suppose for a second that I am deeply offended by this web-site and I do not want it to be reachable any longer from my PC:
[http://www.vatican.va](http://www.vatican.va)

All I have to do is to add it to my /etc/hosts file and give it an IP address that is impossible (and yet technically still valid):
```
Terminal, using nano:
sudo nano /etc/hosts

Terminal, using vim:
sudo vim /etc/hosts

GNOME Desktop (as in Ubuntu):
gksudo gedit /etc/hosts

KDE Desktop (as in Kubuntu):
kdesu kate /etc/hosts
```

Once the file is open add this line on the bottom:
```
0.0.0.0   www.vatican.va
```

Tadaaaa ... the web site is no longer reachable (/etc/hosts usually overrides DNS resolution!). The IP address "0.0.0.0" usually means your default route, but other than that it points to Nirvana. So the IP address is valid and yet you won't reach anything meaningful by sending packets there. 

Of course, depending on your needs and tastes it may be advisable to change the above address to something more disturbing than the Vatican's web site ;)

**_And for the lazy amongst us:_**

You can download pre-assembled huge lists of known ad servers and otherwise problematic hosts here:

[http://pgl.yoyo.org/adservers/](http://pgl.yoyo.org/adservers/)
[http://hostsfile.mine.nu/](http://hostsfile.mine.nu/)
[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)
[http://someonewhocares.org/hosts/zero/](http://someonewhocares.org/hosts/zero/)

Those files are really huge .... so it usually should be enough if you just use one of them at a time.

Download your hosts file of choice, copy & paste it, attach it to the end of your own hosts file ... and voila! You will likely never ever see an ad again :)

Together with NoScript, AdBlock Plus, GreaseMonkey and other such tools you should be pretty safe now against web-based malware.

---

### Post by Golem XIV on 2008-12-16
> **philinux said:**
> Before doing any of this someone should have advised the OP to backup his bookmarks.

Bookmarks>Organise Bookmarks>Import and Backup>Export HTML.

+1

I personally use Foxmarks, both because I have 3 separate systems that I want to share the bookmarks and because it is a convenient way to keep them backed up.

---

