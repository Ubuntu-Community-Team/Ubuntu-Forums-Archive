---
title: "Firefox 3.5/3.0 confusions"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by torfosnaes on 2009-10-31
Upgraded ubuntu 9.04 to 9.10; it seems to be installed, although screen fonts and application displays are defaulted from  9.04 customizations, but the problem with Firefox seems insurmountable.

Firefox won't run.

Tried the chown command but that didn't work.
Can run sudo firefox-3.5 in trerminal but hat doesn't allow click from document or e-mail.
Bookmarks in place.
Looking through file system shows both 3.0 and 3.5 still all over the place so I am uncertain which to modify or delete.

The problem seems top be with ubuntu insistence on making Firefox a buil-in app (like Windows Internet Excplorer); hey guys, it doesn't work. IN 9.04 upgrading Firefox 3.0 to 3.5 nearl;y broke my system and now the upgrade is treathening to do the same.
Forum and help screens don't seem towork and I am getting panicy at the thought of rebuilding everything.

I am running i386 ubuntu 9.10 server on a eeepc; everyhting works but FIrefox.

Thanks for any help received; by the way epiphany works good when defaulted, however, epiphany isn't accepted by secureity conscious sites like on-line banks.

---

### Post by HiImTye on 2009-10-31
try

[LIST=1]
[*]preferences>preferred applications
[*]on the very first page at the top choose 'custom' (from the drag down) then in the text box put
[*]```
firefox-3.5 -new-tab "%s"
```
[/LIST]
hope that helps

---

### Post by torfosnaes on 2009-10-31
Nope; still reluctant to start; Applications - Internet - Firefox and the little wheelie runs around but eventually fails. Did reboot after changing preferences still nothing.

There was a fix in 9.04 about chown the firefox but that doesn't work either.

It is baffling and frustrating.

---

### Post by torfosnaes on 2009-10-31
Nope; still reluctant to start; Applications - Internet - Firefox and the little wheelie runs around but eventually fails. Did reboot after changing preferences still nothing.

There was a fix in 9.04 about chown the firefox but that doesn't work either.

It is baffling and frustrating.

---

### Post by phillw on 2009-10-31
> **torfosnaes said:**
> Nope; still reluctant to start; Applications - Internet - Firefox and the little wheelie runs around but eventually fails. Did reboot after changing preferences still nothing.

There was a fix in 9.04 about chown the firefox but that doesn't work either.

It is baffling and frustrating.


try ...

```
gksudo firefox 
```

does it launch ? - please don't go surfing in this mode !!!!

Phill.

---

### Post by torfosnaes on 2009-10-31
Yes.
It opens after asking for root password.
It did so from terminal with sudo firefox.
Opened to a ubuntu page with a google window.
Help About shows 3.5.4 but no addons or bookmarks as when it runs from terminal.
Thre is some misplacement of profiles is my guess.
Firefox 3.5 folder off home is marked as abandoned.

Thanks for the interest and help.

---

### Post by bandgeek on 2009-10-31
I had the same problem that you have. Read the chown help file and it all makes sense. You don't actually type the dollar signs in the original chown script. Give this a try.

```
sudo chown -R **[COLOR="Red"]username[/COLOR]**:**[COLOR="red"]username[/COLOR]** ~/.mozilla
```

---

### Post by torfosnaes on 2009-11-01
Still not working with bandgeek;s suggested chown script.
Will read chown file carefully again.
Any further suggestions appreciated, I miss my firefox.

---

### Post by torfosnaes on 2009-11-01
Uninstalled all firefox 4.5 using synaptic manager.
Then reinstalled firefox 3.5 only along with several items that go with it automatically.

When screen came back icons were in the application dropdown (not working) and on toolbar (not working).
I changed the properties of the toolbar ir icon to sudo firefox and lo and behold, it runs with all my addons and bookmarks.
It didn't ask for password so I am still in root, I guess,; will reboot and see what happens next.

Surely it has to be easier than this!

---

### Post by torfosnaes on 2009-11-01
Rebooted server and same old problem, firefox won't run.
Did chown command, nothing.
It will run using terminal and sudo firefox as before, but automatic links from e-mails or documents fail as well.
Where do I look next for switch to get it out of root mode.
Does anyone have any experience where it just works after an upgrade?
WHy does my firefox-3.5 folder off root have.abandoned after it?
I copied the profile from firefox-3.0 and still nothing.

---

### Post by Pelsia on 2009-11-01
I had the same problems with Firefox too when it upgraded to 3.5; though after hearing about problems with certain device drivers with 9.10 that I know I would run into I'm waiting on upgrading Ubuntu itself till it gets more stable.  Anyways though, after 3.5 was 'upgraded' it wrought havoc and finally only recourse was to remove both 3.5 and 3.0 completely with synaptic, then do just the 3.0 install.  

Firefox is a great browser and would assumably like to have the latest (and generally faster) version; though between 3.0 and 3.5 (on other machines) didn't really notice a big difference, and haven't run into something that *requires* 3.5 yet.  To get a functional version of 3.5 in our situation I think the best bet is to compile it manually from source.  If or when it start spitting out errors during the make or install process it'll be clear what needs to be done to fix this odd problem.

P.S.  Though its kind of frowned upon here, I prefer compiling/install stuff like this as the real root# user and not doing sudo for each command.  Coming from a FreeBSD background when something needs to be done as root I find its better to just su and do it as root, fixing permissions after the fact (if necessary) is the easy part.

---

### Post by peakshysteria on 2009-11-01
> **torfosnaes said:**
> Yes.
It opens after asking for root password.
It did so from terminal with sudo firefox.
Opened to a ubuntu page with a google window.
Help About shows 3.5.4 but no addons or bookmarks as when it runs from terminal.
Thre is some misplacement of profiles is my guess.
Firefox 3.5 folder off home is marked as abandoned.

Thanks for the interest and help.

Never use plain sudo!! That will mess up permissions in your profile.

Check out **[[COLOR="Red"]Ubuntuzilla[/COLOR]]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#tochome10")**!! It might help you set things straight.

---

### Post by bandgeek on 2009-11-01
**[COLOR="red"]Read all the way through the instructions and print this since you won't have an internet browser.[/COLOR]**

If your have Thunderbird installed backup your emails and settings.

Backup your bookmarks and passwords. Go to your home directory and hit Ctrl+H*(Ctrl+H shows hidden files)*. Find the file .mozilla file.Open it and copy the file labeled firefox to a location of your choice.

Open synaptic now completely remove any package that has to do with Firefox. *You don't need to remove flash if it's installed.*

Now were going to remove the Firefox configuration file in your home directory. Open nautilus as root.```
gksudo nautilus
```
Go to your home directory and hit Ctrl+H. Find the file .mozilla file. Click on it and Shift+Delete.*(Shift+Delete permanently deletes a file)*.

Now reinstall Firefox```
sudo aptitude install firefox
```

Take the firefox file you copied earlier and put it where it belongs.

Run the chown script that I posted earlier```
sudo chown -R [COLOR="red"]username:username[/COLOR] ~/.mozilla
```

Install your favorite add-ons and there you go. I suggest Xmarks since it automatically backs up your bookmarks and passwords.

---

### Post by mgmiller on 2009-11-01
> Never use plain sudo!! That will mess up permissions in your profile.

+1

This is very important!!! never run a graphical application with sudo.  Only use gksudo or gksu to to run graphical apps.

sudo is only used for non-graphical terminal commands and such.

---

### Post by torfosnaes on 2009-11-03
From bad to worse!
chown command apparently with the -R changed more than just the firefox folders.
now server will not boot to normal login - gives a .ICEauthority error which is presumably fixed by yet another round of chown commands - although not in my case; and a server configuration error in /usr/lib/libconf2-4/gconf-sanity-check-2 and exited with status 256.

---

### Post by bandgeek on 2009-11-04
Boot into recovery mode and choose to drop to a root shell.
```
sudo chown **[COLOR="Red"]username:username[/COLOR]** ~/.ICEauthority
chmod 644 ~/.ICEauthority
chown -R root:root /usr/lib/libconf2-4
exit
```

---

