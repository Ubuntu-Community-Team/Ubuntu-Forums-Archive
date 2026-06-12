---
title: "Using a wine program as the default"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by ubername on 2008-12-26
Hi

My realplayer install seems to have gone west, and I can't' find how to fix it.  However .rm files seem to play really well using a media player classic via wine. Can anyone help me with how I make it so that double clicking on a file with a .rm extension opens with Media Player Classic?

TIA

---

### Post by mc4man on 2008-12-26
How it opens or works you won't know till you try but...
right click on any .rm file -> properties -> open with -> add -> use a custom command -> browse. 
Then click your home folder and browse to your .wine  and find the mpc .exe or whatever it's called,  click 'open' and 'add'.

---

### Post by ubername on 2008-12-26
> **mc4man said:**
> How it opens or works you won't know till you try but...
right click on any .rm file -> properties -> open with -> add -> use a custom command -> browse. 
Then click your home folder and browse to your .wine  and find the mpc .exe or whatever it's called,  click 'open' and 'add'.


Thanks. How do I get my hidden folders (i.e. those starting with .) to show up in the 'Custom command' list?

---

### Post by mc4man on 2008-12-26
Mine always do but try this

Home folder (nautilus) edit -> preferences -> views and click 'show hidden and back up files'.

Then maybe restart (ctrl+backspace and ck. again

---

### Post by ubername on 2008-12-26
> **mc4man said:**
> Mine always do but try this

Home folder (nautilus) edit -> preferences -> views and click 'show hidden and back up files'.

Then maybe restart (ctrl+backspace and ck. again

Thanks. My 'hidden' folders show in Nautilus but not in the 'Custom Command' Dialogue.

---

### Post by mc4man on 2008-12-26
When you go browse to home folder (where your not seeing the hidden folders, files) right click on the listing screen and you'll get option to show hidden files

Side note: 
Home folder (nautilus) edit -> preferences is also known as 'file management'
You can add it to your System -> prefrences menu

Right click on Applications -> edit menus and scroll down to preferences. You can enable file management in right side column.

---

### Post by ajcham on 2008-12-26
> **ubername said:**
> Thanks. My 'hidden' folders show in Nautilus but not in the 'Custom Command' Dialogue.

In the Custom Command dialog, right-click on the file listing and select "Show _H_idden Files".

Once you've selected the program, you will need to edit the custom command further, by putting the wine command in front of the path to the Windows executable, so it will look something like:
```
wine '/home/username/.wine/drive_C/programdir/program.exe'
```

I'll be interested to know whether or not this works - I've never had any need of it before, but there's always a first time.

---

### Post by ubername on 2008-12-27
> **ajcham said:**
> In the Custom Command dialog, right-click on the file listing and select "Show _H_idden Files".

Once you've selected the program, you will need to edit the custom command further, by putting the wine command in front of the path to the Windows executable, so it will look something like:
```
wine '/home/username/.wine/drive_C/programdir/program.exe'
```

I'll be interested to know whether or not this works - I've never had any need of it before, but there's always a first time.

Thanks for this. I think I am not going to get this working because although I can get MPC to run when double clicking the file, it recognizes the '/' in the linux path to the file as indicating a switch (command line parameter?) and then doesn't know the switch.

---

### Post by mc4man on 2008-12-27
I fooled around with that last night and there would only be 2 possible ways.

If mplayerc.exe could be entered directly in the command then a switch could be added to the command. You'd need to create a wrapper script and probably a .so similar to what notepad has.

Otherwise if a script could be created that opened mpc, gave it a path to the file clicked on and a proper switch than the command (file association) would be the script location.

More than likely better to do as your doing now or try to fix realplayer

---

