---
title: "done something a bit silly with firefox"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by leyo on 2009-08-18
Having just installed Ubuntu today I've already managed to screw something up, woops. I wanted to install Firefox 3.5 and tried following some instructions on a webpage that I can't for the life of me find again so I don't know how to undo what I did. 

It went wrong, and now when I try to launch firefox I get an error message -- "could not launch application, failed to execute child process "firefox" (no such file or directory)"

These screenshots might explain something:

[IMG]http://farm4.static.flickr.com/3457/3834070068_69b382ec42.jpg[/IMG]

[IMG]http://farm3.static.flickr.com/2518/3834070078_2ed7fd9edc.jpg[/IMG]

I've clearly done something quite silly (and feel especially stupid for losing the instructions which I was trying to follow.)

Any ideas about how to fix it would be appreciated!

---

### Post by Penguin Guy on 2009-08-18
[COLOR="Red"]Warning: this solution will erase all your bookmarks, history, etc.[/COLOR]

Delete [COLOR="Green"]~/.mozilla[/COLOR]. Open the Synaptic Package Manager, search for Firefox and reinstall ([COLOR="Green"]Right Click -> Mark for Reinstallation[/COLOR]).
**or**
```
mv ~/.mozilla ~/.mozilla~
sudo apt-get install --reinstall firefox
```

---

### Post by leyo on 2009-08-18
> **Penguin Guy said:**
> [COLOR=Red]Warning: this solution will erase all your bookmarks, history, etc.[/COLOR]

Delete [COLOR=Green]~/.mozilla[/COLOR]. Open the Synaptic Package Manager, search for Firefox and reinstall ([COLOR=Green]Right Click -> Mark for Reinstallation[/COLOR]).
**or**
```
rm ~/.mozilla
sudo apt-get install --reinstall firefox
```

I don't know where that directory is, and the command line doesn't seem to work:

```
 rm ~/.mozilla
rm: cannot remove `/home/leonie/.mozilla': Is a directory
```

Sorry, I'm really struggling to understand the file structure and where everything is/how to find it.

---

### Post by themusicalduck on 2009-08-18
Try this

```
rm -r ~/.mozilla
```

---

### Post by Penguin Guy on 2009-08-18
> **leyo said:**
> I don't know where that directory is, and the command line doesn't seem to work:

```
 rm ~/.mozilla
rm: cannot remove `/home/leonie/.mozilla': Is a directory
```

Sorry, I'm really struggling to understand the file structure and where everything is/how to find it.
No, it was my fault. [COLOR="Green"]~/.mozilla[/COLOR] is a directory and therefore you need to add the [COLOR="Green"]-r[/COLOR] parameter (stands for recursive) to delete it. Try this: [COLOR="Green"]mv ~/.mozilla ~/.mozilla~[/COLOR].

_**Short Explanation of Linux File Structure:**_
[SIZE="3"][COLOR="Green"]/[/COLOR][/SIZE] At the start of a path means the root of the filesystem, it is equivelant to [COLOR="Green"]C:\[/COLOR] in Windows.
[SIZE="3"][COLOR="Green"]~[/COLOR][/SIZE] At the start of a path means your home directory; in your case [COLOR="Green"]/home/leonie[/COLOR], therefore [COLOR="Green"]~/.mozilla[/COLOR] = [COLOR="Green"]/home/leonie/.mozilla[/COLOR].
[SIZE="3"][COLOR="Green"]~[/COLOR][/SIZE] At the *end* of an item means backup (e.g. [COLOR="Green"]important-file.txt~[/COLOR]), these files are usually hidden, you can toggle this by pressing [COLOR="Green"]Ctrl + H[/COLOR] in Nautilus.
[SIZE="3"][COLOR="Green"].[/COLOR][/SIZE] At the start of an item means hidden file (e.g. [COLOR="Green"].secret-file.txt[/COLOR]), these files are usually hidden, you can toggle this by pressing [COLOR="Green"]Ctrl + H[/COLOR] in Nautilus.
[SIZE="3"][COLOR="Green"]..[/COLOR][/SIZE] The directory above, for example if you are at [COLOR="Green"]/root/Desktop[/COLOR] and type [COLOR="Green"]cd ..[/COLOR] you will then be at [COLOR="Green"]/root[/COLOR].

---

### Post by philinux on 2009-08-18
How about renaming his firefox folder or backing up his bookmarks first. It looks like he got 3.0 and 3.5 installed.

---

### Post by Penguin Guy on 2009-08-18
> **philinux said:**
> How about renaming his firefox folder or backing up his bookmarks first. It looks like he got 3.0 and 3.5 installed.
Good idea, I have changed my two posts and added this code: [COLOR="Green"]mv ~/.mozilla ~/.mozilla~[/COLOR]. Which should be quite safe.

---

### Post by leyo on 2009-08-18
Thanks very much for your guidance re. the commands! I've been typing things in without knowing what I'm doing (how I got myself into this pickle).

I get the impression maybe what the guide I tried to follow the first time round was doing was making the firefox shortcut at the top of the desktop link to firefox 3.5 instead of 3.0? When all that didn't work I then realised that Shiretoko was available in the add/remove programs thing and installed that, but it's listed as a separate program instead of replacing the old firefox.

Luckily I don't have anything to lose on here as I only installed Ubuntu today and I haven't imported my backed up bookmarks yet. However, following the commands above in this thread cleared the few settings which I'd changed in Shiretoko when using it ... but hasn't fixed the original problem of the error message when trying to use the firefox shortcut.

Very confused. I'm such a n00b.

---

### Post by philinux on 2009-08-18
The shortcut at the top of your desktop. Right click it and choose properties. Tell us what command it's using.

Shiretoko will remain as is until Karmic comes out in Oct. Then it will be the default browser in ubuntu. 

When you install it from add remove it copies your 3.0 profile over to use. The two remain separate. If you add a bookmark in one it will not appear in the other and vice versa.

---

### Post by leyo on 2009-08-18
> **philinux said:**
> The shortcut at the top of your desktop. Right click it and choose properties. Tell us what command it's using.


It's using this command: firefox %u

---

### Post by philinux on 2009-08-18
Ok so I would reinstall firefox 3.0 from add remove then.

---

### Post by leyo on 2009-08-18
> **philinux said:**
> Ok so I would reinstall firefox 3.0 from add remove then.

Appears to have no effect...

---

### Post by philinux on 2009-08-18
Ok, use synaptic package manager. Find firefox 3.0.xx and mark it for complete removal. Then reinstall it.

Another thing to try is open a terminal and type firefox to run it. See what error messages appear.

---

### Post by leyo on 2009-08-18
I found how to fix it! This was the guide I'd been trying to follow:

[http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

Which has instructions for undoing it in case of problems. D'oh.

Thanks for trying to help :) I'm going to proceed a bit more cautiously from now on until I get the hang of what's going on in Ubuntu.

---

