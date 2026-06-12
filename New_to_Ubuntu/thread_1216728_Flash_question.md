---
title: "Flash question"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by GodlySoup on 2009-07-18
I don't think I have the right flash installed. Some videos get distorted and some don't even show up at all. This video in particular gives me an error message. [http://www.warcraftmovies.com/movieview.php?id=115589](http://www.warcraftmovies.com/movieview.php?id=115589)

It says Error Line 1 and a scrolling video bar appears with flashing boxes. I keep trying to install Adobe 10 for 64 bit, but I don't think it's working. I go into Preferences for Firefox and try to set up the Applications tab for what I want it to play it with and it doesn't give me much of an option: just VLC media plug-in. 

I've also tried going to add/remove and clicking the Adobe 10 check box but I am unable to because it says underneath: Adobe Flash Plugin 10 cannot be installed on your computer type (amd64). I've downloaded packages onto my desktop for the 64 bit but can't find them in the add/remove. Is there another way to install them? 

Cheers,
GS

---

### Post by drs305 on 2009-07-18
I just installed a fresh copy of Karmic this morning on an AMD64 and this script installed Alpha 10 Flash flawlessly. It should work on your release as well:
[http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

Run the "64bitFlashAlpha" script.

---

### Post by GodlySoup on 2009-07-18
I tried this. Just having trouble with the last part. I can't copy it into the folder because it says permission denied. I am the only user on this computer. How do I copy it over?

---

### Post by rednano12 on 2009-07-18
```
sudo mv /path/of/original/file /path/where/you/want/it
```

---

### Post by GodlySoup on 2009-07-18
Well, I did this... I followed the instructions... uninstalled all Adobe and extracted and moved this file to the ~/.mozilla/plugins folder. But nothing seems to have changed. Did I do something wrong?

---

### Post by jerome1232 on 2009-07-18
restarted firefox?

edit: I kinda hate running random scripts that people link, then  you don't know exactly what was done, it's fairly straight forward to download the .tar.gz from their website, extract the .so file and move it to ~/.mozilla/plugins directory.

---

### Post by drs305 on 2009-07-19
GodlySoup,

If you downloaded the install script, normally it would end up on your Desktop. Doubleclick the Get64bitFlash.tar.gz file and it should offer to extract the files. Select 'Extract', 'all files' and it should leave a file on your Desktop called Get64bitFlash.

Double click the file and select 'Run'  or in a terminal execute these commands:
```

cd $HOME/Desktop  # Changes to the Desktop directory
./Get64bitFlash   # Initiates the script

```
You will be asked for your password, asked if you accept the conditions, and everything else should be done automatically.

---

### Post by GodlySoup on 2009-07-19
Oh snap! It works. Thanks so much. Sorry it took a little explaining for me to get it, but I got it. Hazzah!

---

