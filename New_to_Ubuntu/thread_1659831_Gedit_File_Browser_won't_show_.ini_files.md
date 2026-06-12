---
title: "Gedit File Browser won't show .ini files"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by metalball on 2011-01-04
Hey all,

i'm trying to figure out howcome i can't see simple text filetype like ini in gedit File Browser ?
it's frustrating to use nautilus every time i need to edit ini file! maybe i'm missing something?:confused:

thanx

---

### Post by khelben1979 on 2011-01-04
What version of [Gedit]("http://projects.gnome.org/gedit/") are you using? 

Also, I'm sure there must be other applications which can do the same as Gedit and if this software does not meet your expectations, maybe it's time to switch to something else? In the meantime, we can focus on Gedit and we'll see how that looks like.

---

### Post by coffeecat on 2011-01-04
I've just grabbed two .ini files from my Windows D:

The first shows text in the Nautilus icon. Running the file command gives me:

```
$ file install.ini 
install.ini: ASCII text, with CRLF line terminators
```If I right-click on it, gedit is already selected as the default app and it opens OK.

The second shows binary in the icon and 'file' gives me:

```
$ file globdata.ini 
globdata.ini: Little-endian UTF-16 Unicode text, with CRLF line terminators
```If I right-click no apps are suggested, but 'open with other application' leads me to 'Text Editor' (which is gedit) and it also opens just fine.

What are you doing to try to open your ini files in gedit?

---

### Post by cgroza on 2011-01-04
> gedit File Browser ?
Gedit is a text editor, same as notepad, only 1000x better.

---

### Post by khelben1979 on 2011-01-04
I think he means that he cannot click on the .ini files in the file browser choosing the open file option, since it's not listed in the file window, but I'll wait to see what metalball responds.

---

### Post by metalball on 2011-01-04
> **khelben1979 said:**
> I think he means that he cannot click on the .ini files in the file browser choosing the open file option, since it's not listed in the file window, but I'll wait to see what metalball responds.
you are right, thats what i've ment. they are not listed in the file browser pane, nore some other plain text extensions.


i'm new to ubuntu, and i'm moving from windows envoirment, and i've been using NPP until now.

i've tried  lots of Linux editors, Kate was the best replacement for NPP, but it had some issues running on Gnome, so between Geany and gedit, i've chose gedit.

i've found alternative file browser plugin "Eddt", but its not as comfortable as the native File Browser,
so is there any way to make the File Browser pane show me other types than .php, .html, .css, .cs, .xml etc ?

---

### Post by metalball on 2011-01-04
> **coffeecat said:**
> 
What are you doing to try to open your ini files in gedit?
i'm trying to edit them ;)

---

### Post by lidex on 2011-01-04
I'm perhaps lost here but I can see file extensions in nautilus and gedit, including the file open window. Have you checked your preferences?

---

### Post by spook1980 on 2011-01-04
right click open with then navigate to gedit

---

### Post by metalball on 2011-01-04
> **lidex said:**
> I'm perhaps lost here but I can see file extensions in nautilus and gedit, including the file open window. Have you checked your preferences?
i can see in nautilus and file open menu. i can't see in the File Browser PANE.

---

### Post by metalball on 2011-01-05
ok, i see that my point is not clear to everyone, so i made a screenshot:
[[IMG]http://img191.imageshack.us/img191/1664/geditfilebrowser.png[/IMG]]("http://img191.imageshack.us/i/geditfilebrowser.png/")


as you can see, there are .ini files in the folder, which gedit File Browser can't see, and i don't understand why.

---

### Post by khelben1979 on 2011-01-05
Once again, what version of Gedit are you using? It might be a bug in that specific version.

---

### Post by metalball on 2011-01-05
gedit 2.30.3

but isn't it the plugin bug?

---

### Post by khelben1979 on 2011-01-05
> **metalball said:**
> gedit 2.30.3

but isn't it the plugin bug?

I don't know. You can e-mail one of the developers and ask them if they know anything about this. You'll find them [here]("http://git.gnome.org/browse/gedit/tree/AUTHORS").

I think they know better than anyone regarding this issue.

---

### Post by coffeecat on 2011-01-05
> **metalball said:**
> i'm trying to edit them ;)

Yes, that's obvious. I meant what are you doing to open .ini files in gedit: double-click,  right-click, open Gedit and File > Open?

> **metalball said:**
> ok, i see that my point is not clear to everyone, so i made a screenshot:

...

as you can see, there are .ini files in the folder, which gedit File Browser can't see, and i don't understand why.

Open Gedit, Then File > Open. In the file browser that opens, navigate to the folder with your .ini files. Now look towards the bootom right of that window. There's a drop down with two choices: 'All Files' and 'All Text Files'. If you have 'All Text Files' selected, select 'All Files' instead and all your .ini files should appear.

---

### Post by metalball on 2011-01-05
> **coffeecat said:**
> Yes, that's obvious. I meant what are you doing to open .ini files in gedit: double-click,  right-click, open Gedit and File > Open?



Open Gedit, Then File > Open. In the file browser that opens, navigate to the folder with your .ini files. Now look towards the bootom right of that window. There's a drop down with two choices: 'All Files' and 'All Text Files'. If you have 'All Text Files' selected, select 'All Files' instead and all your .ini files should appear.

look, i'm not having troubles opening those files in any way except for the one i've described earlier. i know how to open files into gedit, thats not the issue!
the issue is that i can't see some files from the [COLOR=Red]*_**FILE BROWSER PANE**_*[/COLOR], and that's what i'm trying to resolve.

> I don't know. You can e-mail one of the developers and ask them if they know anything about this. You'll find them [here]("http://git.gnome.org/browse/gedit/tree/AUTHORS").

I think they know better than anyone regarding this issue. 	
thanx, i'll try contacting them !! :)

---

### Post by mc4man on 2011-01-05
I would just d. check here and see if under [filefilter] it's set to id=0

gedit ~/.gnome2/gedit/gedit-2
(or browse there if an empty file comes up

Otherwise file a bug, no issue here w/ .ini, in a terminal

ubuntu-bug gedit

you could also enable 'show hidden files' though clearly these are not doesn't hurt to try

---

### Post by metalball on 2011-01-05
> **mc4man said:**
> I would just d. check here and see if under [filefilter] it's set to id=0

gedit ~/.gnome2/gedit/gedit-2
(or browse there if an empty file comes up

Otherwise file a bug, no issue here w/ .ini, in a terminal

ubuntu-bug gedit

you could also enable 'show hidden files' though clearly these are not doesn't hurt to try

no filefilters found.

ofcourse i've tried the "show hidden files"... no luck.

currently left a post for the developer of the plugin, if he won't reply soon, i'll report a bug

---

### Post by mc4man on 2011-01-05
> no filefilters found.
Not to waste your time - somewhat curious
Did you do as was suggested - change the search criteria to "All Files" ? Or try toggling back and forth a few times

If so then you should have something like this in the above mentioned file (id=0 is all files, id=1 is text only
> [window]
width=1584
height=474
state=0
side_panel_active_page=827629879

[filefilter]
id=0

---

### Post by metalball on 2011-01-05
> **mc4man said:**
> Not to waste your time - somewhat curious
Did you do as was suggested - change the search criteria to "All Files" ? Or try toggling back and forth a few times

If so then you should have something like this in the above mentioned file (id=0 is all files, id=1 is text only
yes, added the filter, my gedit-2 looks like this:
```

[window]
width=1280
height=752
state=4
side_panel_active_page=582577284
side_panel_size=211
bottom_panel_active_page=508528508
bottom_panel_size=200

[filefilter]
id=0 
```still can't see files.

btw, i don't think that its gedits issue, but the FileBrowser plugins. so changing gedits conf won't help.
the Eddt browser shows all files.

---

### Post by mc4man on 2011-01-05
Well it would seem you have a bug of sorts.
 if you get it sorted would be interesting to know why.

( if you were to place or create an .ini in your home folder somewhere - does it show?

---

### Post by metalball on 2011-01-05
> **mc4man said:**
> Well it would seem you have a bug of sorts.
 if you get it sorted would be interesting to know why.

( if you were to place or create an .ini in your home folder somewhere - does it show?

nope, tried to create on desktop. can't see. anyway, i'm waiting for the developer to reply,
i'll post it to ubuntu-bug if he won't reply in a few days.

---

### Post by mc4man on 2011-01-05
Well, good luck w/ this, hope it gets resolved.

the only other thing i'd try is to temporarily create a new user, log in to it and see if gedit works there. (likely not, but does eliminate any local cause of this behavior

---

### Post by phishsauce on 2011-02-06
[http://superuser.com/questions/194091/why-wont-gedit-file-browser-plugin-show-files](http://superuser.com/questions/194091/why-wont-gedit-file-browser-plugin-show-files)

---

### Post by apoole7 on 2011-04-08
I have just sort of resolved the same problem trying to show .bat files in the browser pane.
It is not ideal & may effect other default actions but....

gksu gedit /usr/share/mime/packages/freedesktop.org.xml

Search for ".sh"
line 11325 of mine shows <glob pattern="*.sh"/>
copy & paste this on a new line below & change .sh to .ini

close gedit 

sudo update-mime-database /usr/share/mime

Launch gedit again & ini files should show, from not much experience & no testing I am not sure exactly what else that would mean to .bat or .ini files within your environment. So normal caveats apply on trusting strangers!

---

### Post by cyclonesoftware on 2011-07-02
If anyone is still looking for a solution to this,  if you right click and choose "filter -> show binary" and "show hidden" ini, and .htaccess (what is was looking to solve) will appear. 

Why it filters them out in the first place I would assume is a bug as neither ini or htaccess are binary files but...

---

