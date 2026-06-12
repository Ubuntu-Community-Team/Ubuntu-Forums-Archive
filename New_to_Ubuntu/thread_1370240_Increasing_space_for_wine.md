---
title: "Increasing space for wine"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by anand_30 on 2010-01-02
I use wine 1.1.31 in ubuntu 9.10(dual boot with xp).I have installed ubuntu 9.10 giving it only 10 Gb space.so i am now feeling shortage of space to install windows softwares and games using wine.Is it possible for wine to use space of D drive(file system FAT) which belong to windows?

---

### Post by Methuselah on 2010-01-02
It may be possible to mount the drive and create a WINEPREFIX on it.
[http://wiki.jswindle.com/index.php/Advanced_Wine_User_Installation#Changing_the_location_of_Wine.27s_fake_windows](http://wiki.jswindle.com/index.php/Advanced_Wine_User_Installation#Changing_the_location_of_Wine.27s_fake_windows)

---

### Post by anand_30 on 2010-01-02
Thank you for your help.Now trying to understand the part if I will not get that I will ask you.:P

---

### Post by anand_30 on 2010-01-02
I tried the commands
export WINEPREFIX=/media/A44D-12A7/wine
According to post it should move wine to my D drive but then i tried to install fifa 07 and it gave me error that 'insufficient space' even though i have lot of space in D drive.So that command is not working for me,I am a newbie so please can you help me giving detailed commands?

---

### Post by Methuselah on 2010-01-02
I explained what the link said after the line but I have also provided a new option that might be easier and more convenient for you.

1. Choose configure wine from the wine menu or enter **winecfg** in a terminal
2. On **drives** tab choose **Add**
3. Select a drive letter (example E) and hit OK
4. Select drive E in the list and edit the path to **/media/A44D-12A7/wine** [make sure this path and the 'wine' directory exists]
5. Select OK to save everything
This is equivalent to adding a new drive to the wine fake windows.

Now when you are running the Fifa installer, choose to install FIFA in drive E rather than C.
Most installers give an option for where to install the program.


_________________________________OR_______________________________________

This is the follow up on the original suggestion in the link for your information.
If the suggestion above works you do not have to do this.

In a terminal, enter

```

export WINEPREFIX=/media/A44D-12A7/wine
cd **/directory-fifa-setup-is-located**
wine **fifa07setup.exe**

```

Of course you'll have to supply the correct name for the bolded things.
When installation is complete you'll have to launch the fifa executable in wine.
It will be somewhere under /media/A44D-12A7/wine/drive_c/Progam\ Files

eg.

```

cd /media/A44D-12A7/wine/drive_c/Progam\ Files/**Fifa07**
wine **fifa07.exe**

```

Once again, I don't know the correct names of the fifa stuff.

You'll essentially have two different fake windows, the original one under /home/you/.wine and the one at /media/A44D-12A7/wine .
You'll have to export the WINEPREFIX first when you want to install/run stuff in the one on the /media drive.

---

### Post by thatguruguy on 2010-01-02
Why go through this trouble at all if you already have windows installed?  Why even run Wine if you're still running windows?

---

### Post by Methuselah on 2010-01-02
You must be pretty low on space though.
It might come back to haunt you with other things!

---

### Post by Methuselah on 2010-01-02
> **thatguruguy said:**
> Why go through this trouble at all if you already have windows installed?  Why even run Wine if you're still running windows?

I was wondering that too...but maybe he wants to see if they work in wine.

---

### Post by thatguruguy on 2010-01-02
> **Methuselah said:**
> You must be pretty low on space though.
It might come back to haunt you with other things!

Actually, the problem is he only allocated 10 G to his ubuntu partition, and now he's trying to cram a bunch of bloated Windows-based programs in there.  It makes absolutely zero sense.  He needs to either get rid of Windows altogether and just use Wine to run the Windows programs he wants, or install his Windows programs within Windows.  What he's trying to do now is just kinda dumb.

---

### Post by anand_30 on 2010-01-03
> **thatguruguy said:**
> Actually, the problem is he only allocated 10 G to his ubuntu partition, and now he's trying to cram a bunch of bloated Windows-based programs in there.  It makes absolutely zero sense.  He needs to either get rid of Windows altogether and just use Wine to run the Windows programs he wants, or install his Windows programs within Windows.  What he's trying to do now is just kinda dumb.

Ya its kinda dumb but there no alternative to me.My windows is crap it hangs while playing games also it has some virus problems but I can not completely remove it due to the fact that I share the pc with my sister she uses some testing programs which may not work in wine and its a bad thing to force her to use ubuntu with which she is not familiar.When I get my own laptop there is no doubt I am gonna use whole space for ubuntu.:P

---

### Post by anand_30 on 2010-01-03
Thank you very much Methuselah,your first option worked.I installed fifa 07(only sound working with blank screen),autocad 2004(worked),autocad 2006(doesnt work).\\:D/

---

### Post by Methuselah on 2010-01-03
Hopefully you have 3D working correctly or else games will be rather slow.
Also if you do have 3D working and are running desktop effects, it might be a good idea to disable them when trying wine games.

Some programs might also work when run in a virtual desktop, you can try that if you like.
Under wine configuration/graphics choose 'emulate a virtual desktop' and select a size.

Finally, playonlinux is an effort to configure wine to run some common games properly.
You can learn more about it here:
[http://www.playonlinux.com/en](http://www.playonlinux.com/en)

I have heard it spoken of though I have never used it myself.

All the best!

---

### Post by anand_30 on 2010-01-03
> **Methuselah said:**
> Hopefully you have 3D working correctly or else games will be rather slow.
Also if you do have 3D working and are running desktop effects, it might be a good idea to disable them when trying wine games.

Some programs might also work when run in a virtual desktop, you can try that if you like.
Under wine configuration/graphics choose 'emulate a virtual desktop' and select a size.

Finally, playonlinux is an effort to configure wine to run some common games properly.
You can learn more about it here:
[http://www.playonlinux.com/en](http://www.playonlinux.com/en)

I have heard it spoken of though I have never used it myself.

All the best!
thank you sooooooo much for your help.I now have downloaded PlayOnLinux it shows lot of applications and games which can be run on wine with proper configuration.
I tried fifa in virtual desktop but same result but I am happy to get information about it.
Its a very good effort of wine to introduce such a software which some day will make windows shut down.:)

---

