---
title: "A few Problems"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by phoenix6561 on 2009-11-02
I just did a fresh install of 9.10 and am having a few issues as i am relively new at this they could be simple but i have no clue.
1.when i add programs to system/preferences/startup applications they do not start on boot even if i know they are the right command and can go to terminal and they boot right up 
2. every time i reboot pidgin boots 2 i don't want it to and its not in the start up apps
3. i un-installed pulse audio because it was making my speakers pop even when muted now i have no volume control at all.

any ideas?

---

### Post by gdonwallace on 2009-11-02
Interesting.

1.  I would check the permissions on the programs that you are trying to launch.  Go to the directory and do <b>ls -l | pg</b> and this will give you a long listing of the program names and directories.  The first column is the permissions.  The next 2 columns show who owns the file.  To make a program run there needs to be an 'x' in the permissions.  For normal users to run the program there should be an 'x' at the 6th and 9th position (Not counting the first character)  As to the owner of the file, if it is not you (i.e. your login name) then you may not have permission to run the program from within x-windows.  

2.  Right click on the icon for pidgen and see if it gives you an option for preferences.  If not try a left click.  Either way it should.  Go through the prefs until you find an option to start pidgen on boot up or login, disable that and it won't boot up when you login.

3.  I would re-install pulse-audio.  That way you can get sound.  However; I would go to the sound settings under preferences menu and change the settings from ALSA to OSS, that may fix your problem with the popping noise.

Good luck.

---

### Post by phoenix6561 on 2009-11-02
pulse audio fixed it but still having trouble with the other 2 
pidgin dosn't seem to have a setting like that at least not that i can find
and i have rights to all the files i a trying to auto run

---

### Post by NickJones on 2009-11-03
System, Prefernces, Startup Applications, 
Un-Tick Pidgin.

---

