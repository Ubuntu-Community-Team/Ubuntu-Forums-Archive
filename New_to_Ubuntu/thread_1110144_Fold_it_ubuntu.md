---
title: "Fold it ubuntu"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-03-29
I would like to install fold it on my machine- is there a repository?  I tried off the Fold it site ([http://fold.it/portal/](http://fold.it/portal/)) but I have no idea how to intall .tar.bz files.  I suppose help would be appreciated on that front too!

---

### Post by leonardo_neo on 2009-03-29
> **qwertyuiop96 said:**
> I would like to install fold it on my machine- is there a repository?  I tried off the Fold it site ([http://fold.it/portal/](http://fold.it/portal/)) but I have no idea how to intall .tar.bz files.  I suppose help would be appreciated on that front too!

Well, after reading your question, I downloaded the foldit package to check how to install that.

It is a tar.gz file. There are certain ways to install tar.gz files, but it is always recommended to read the 'Readme' file first.

When I read the read me file, it says "To start the game, run Foldit from this directory."

I tried to run the game by click the 'Foldit' file from the directory, and it works.

So here is what I recommend. First download the Linux tar.gz file from the website. Then extract the file by right clicking on it and selecting "Extract Here". Once extracted, then open the folder and simply click the 'foldit' file. It will run! :)

---

### Post by qwertyuiop96 on 2009-03-29
Well, Fold it now works, but when I go to Preferences > Main Menu and make an app launcher, when I click on the launcher nothing happenes. This is annoying, sice it is apain to get to where the file actually is...

---

### Post by t0p on 2009-03-29
[www.getdeb.net]("http://www.getdeb.net") is a good place to look for .debs.  But if the developer hasn't got it on his site, I wonder if *anyone* has got it.  Bite the bullet and compile.

For instructions on how to deal with .tar.gz look [here]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by qwertyuiop96 on 2009-03-29
I didn't really have to compile, the program was just in the archive.  However, as I think I said before I can't link to it in pref > main menu.  Nothing happenes.  Minor, but still,...  Any ideas?

---

### Post by InfectedWithDrew on 2009-03-29
You won't be able to make a launcher unless you do something like this for the code in the launcher:

```
cd /home/user/Desktop/name-of-the-folder-you-extracted-to/ && whatever-the-command-to-run-fold-it-is
```

Sorry I can't be more explicit but this is how you'd do it (pretty sure).  This assumes you extracted to your desktop.

----------------
Now playing: [Cobra Starship - It's Warmer in the Basement](http://www.foxytunes.com/artist/cobra+starship/track/its+warmer+in+the+basement)

---

### Post by qwertyuiop96 on 2009-03-30
Still doesn't work- though now it tells me "Permission denied" and I extracted it to /usr/local/src/Foldit which I have read/write permissions for.

---

### Post by qwertyuiop96 on 2009-04-05
The all-Powerful bump!

---

### Post by spiderbatdad on 2009-04-05
run fold it from the command line...thats all. move it to your home directory.```
cd Foldit
./Foldit
```thats how you run it. The instructions are included in the archive.

---

### Post by llamabr on 2009-04-05
> **qwertyuiop96 said:**
> Still doesn't work- though now it tells me "Permission denied" and I extracted it to /usr/local/src/Foldit which I have read/write permissions for.

You shouldn't have write permission to that dir.  Though you can add that path to your $PATH so that you don't have to cd to it every time.

Your question seems to have changed, since the beginning of the post.  Now that the software is working, you want a launcher rather than having to run it from cli?

What have you tried, and what error do you get?

---

### Post by qwertyuiop96 on 2009-04-06
Yes, to all.  The question has changed.  The launcher doesn't seen to be working- if I make one in pref>main menu the launcher doesn't do a thing when I click on it.  BTW, it is in my /home directory.

---

### Post by qwertyuiop96 on 2009-04-15
Bump

---

### Post by llamabr on 2009-04-15
I can't seem to remember what the question is now.

Are you able to run it from cli?

Now you're just trying to make it launch from, where?  The panel?  Or the desktop?  From the panel, you just right click, choose add to panel, then custom application launcher.

Likewise with desktop.  Right click, create launcher.

What error are you getting?

---

### Post by llamabr on 2009-04-15
Oh, I see, you want it to be in the drop down menu under applications, somewhere?  You need to know where it actually is, then.  Do a:

```
which foldit
```

---

### Post by qwertyuiop96 on 2009-05-03
Ah well.  I installed it with Wine, and for some reason it works better through Wine. ?!?!?!  Don't ask me!  Anyway, now everything works.  Thanks everyone for your help!

---

### Post by bradyo on 2009-11-15
Foldit seems to run without error only when the current working directory is set to the folder containing the Foldit executable. And ubuntu launcher doesn't let you set command as "cd /home/username/Foldit/ && Foldit" (not sure why). So as a solution, just create a shell script to cd to the correct directory and run the executable, then you can run this script in your launcher

cd into your Foldit directory and create a file "run.sh" with the following contents:

#!/bin/sh
cd /home/username/Foldit/
./Foldit


Now you can add launcher command:

sh /home/username/Foldit/run.sh


works for me at least! enjoy :D

---

### Post by _Narcisse_ on 2009-11-15
Hello,

I just downloaded it, installed freeglut3, and it starts but with no sound.

Any idea anyone ?

Thanks

---

### Post by WarriorIng64 on 2010-03-10
Yeah, when I installed Fold It on my Windows/Ubuntu dual-boot laptop a few months ago, I was able to get it to run, but also with no sound. I posted this as a bug report on Fold It's forums a couple months ago ("No sound in Linux version" or something like that), though I doubt it'll ever get attention. So many bugs reported there for various things, and also take into account that most Fold It players except me seem to prefer the game being totally silent for some reason.

Now I want to run it on my new Ubuntu desktop (more power), but after downloading and extracting, I double-click on the application in the extracted folder and absolutely nothing happens. I tried downloading it again, but same result. Even in the terminal, I am able to see the application, but when I run this in the game's directory to try to start it:

```
./Foldit
```...the terminal tells me it's not a directory or something like that, even though *it's sitting right there and I can see it with the ls command*! I don't remember having to go through this on my laptop...I dunno.

Fold It for Linux is really goofy. I wish the Fold It team would give it a bit more attention to match with the Windows version.

---

### Post by perlon on 2011-09-23
> **WarriorIng64 said:**
> Yeah, when I installed Fold It on my Windows/Ubuntu dual-boot laptop a few months ago, I was able to get it to run, but also with no sound. I posted this as a bug report on Fold It's forums a couple months ago ("No sound in Linux version" or something like that), though I doubt it'll ever get attention. So many bugs reported there for various things, and also take into account that most Fold It players except me seem to prefer the game being totally silent for some reason.

Now I want to run it on my new Ubuntu desktop (more power), but after downloading and extracting, I double-click on the application in the extracted folder and absolutely nothing happens. I tried downloading it again, but same result. Even in the terminal, I am able to see the application, but when I run this in the game's directory to try to start it:

```
./Foldit
```...the terminal tells me it's not a directory or something like that, even though *it's sitting right there and I can see it with the ls command*! I don't remember having to go through this on my laptop...I dunno.

Fold It for Linux is really goofy. I wish the Fold It team would give it a bit more attention to match with the Windows version.

Exactly the same thing happens to me. I experienced this strange behaviour only one time other than this, with the program "Tux NDS Trimmer". Dunno how to solve...

---

### Post by sffvba[e0rt on 2011-09-23
Back to sleep thread...


404

---

