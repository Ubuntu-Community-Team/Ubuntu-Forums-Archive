---
title: "Help with a terminal problem"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by chris.willis on 2010-03-11
Hi there,

I recently switched from Ubuntu which I've been using for a few years, to Kubuntu 9.10. I have 2-3 issues I can't seem to resolve, and will make separate posts for them.

I'm wondering if you can have a look at this post: [http://ubuntuforums.org/showthread.php?t=1193010](http://ubuntuforums.org/showthread.php?t=1193010)

The issue is that I want to set up an executable terminal file on my desktop to make a backup of my files. I'm struggling trying to do it. If you read the link it'll make more sense.

Can someone please advise how in Kubuntu, I can have a desktop icon which backs up my files by copy only? My Windows machine used to have a batch file with the Dos command: "copy /y j:\Personal\*.* C:\Personal" on the desktop. I'd like to know the Kubuntu equivalent.

Hope I've explained it thoroughly. The old post didn't contain the full solution because I got there by fluke. If someone has a step by step process, that will be great.

---

### Post by patchwork on 2010-03-11
You have the script and just need to make the launcher, right?

why not just make a link?

```
ln -s /locationofscript/scriptname ~/Desktop/Back-up.ln
```

---

### Post by chris.willis on 2010-03-11
I'll need help right from the start. It confused me last time and that was a while ago! Hope you don't mind. I really should know more about this stuff. I've been using it for a while.

---

### Post by patchwork on 2010-03-11
From your old thread:

```
#!/bin/bash
cp -uvr /source/dir/* /destination/dir/
```

Enter this in your text editor (KATE I think, in kde?), change the directory locations, and save it in what ever location you want ( /home/<username> is probably good.)  

For simplicity, let's call the file backup.sh

Now, make it executable:
```
sudo chmod +x ~/backup.sh
```

Test it, make sure it works for you:
```
 ./backup.sh
```

Now create the link

```
ln -s ~/backup.sh ~/Desktop/Backup
```

Now you should have a link on your desktop to the script in your user's home folder...

---

### Post by wannabegeek on 2010-03-12
Hi,

I've just begun to learn to how to back up more carefully...I use rsync, which I'm told  should be run from a script, since you can erase everything you are trying to back up with a simple inversion of the destination/source aruguments...


wbg

---

### Post by chris.willis on 2010-03-12
OK, I'm getting there: I've double checked everything and I'm up to the last line of code to create the link. I've checked by Backup.sh link works and it does.

When I double click the link I created on the desktop, it comes up with a dialog screen asking "Open with", and it lists the categories in my Kickoff applications directory, so it won't run. It appears to be prompting with what program I want to run the script with, rather than just running it. Everything up to using the link works. Any ideas? I repeated the above process three times to make sure I wasn't missing a step.

---

### Post by patchwork on 2010-03-12
You'll probably have to select Konsole, but I think it will only need to be done the first time you run it (Once you associate .sh with Konsole).

---

### Post by chris.willis on 2010-03-20
I'm completely confused. Maybe I'll just do it manually.

---

### Post by hictio on 2010-03-20
> **wannabegeek said:**
> Hi,

I've just begun to learn to how to back up more carefully...I use rsync, which I'm told  should be run from a script, since you can erase everything you are trying to back up with a simple inversion of the destination/source aruguments...


wbg

You can simply add the option '-n' to your rsync execution, that way it will do a dry run, a test, without modifying or erasing anything on the destination.
You should really use it like that the first time, or while testing something, more useful if you add a verbose option, you can really prevent a mistake.
Something like this:

```

rsync -e ssh -navzr --delete /path/origin/ server:/path/destination/

```

---

### Post by chris.willis on 2010-03-22
I found a GUI for rsync which is much easier for people like me. It's really easy to use. Simply look for grsync in the repository and install it. There's an icon under 'System'. Run it, select the options - brilliant piece of work! I'm really getting to grips with some Kubuntu teething issues. Excellent OS.

---

