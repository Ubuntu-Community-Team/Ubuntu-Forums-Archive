---
title: "error using multiple commands in terminal"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by silverdragon27 on 2010-09-11
Hello all, 
I am fairly new to linux and have been adapting well from my former windows environment; however I have come across a small problem when trying to make certain tasks easier. I am attempting to create a custom application launcher (within terminal) that will run the following commands
```
sudo iptables -t nat -A OUTPUT -d xxx.xxx.xxx.xxx -j DNAT --to xxx.xxx.xxx.xxx
cd .wine/dosdevices/c:/users/USER/Local\ Settings/Application\ Data/Ragray
wine heRO.exe -1rag1
```
I have tried using " ; "  as well as the " && " to run them together but terminal seems to always close without completing the commands. They seem to run fine as long as I do them one line at a time. 
When I try to run the wine app with the full directory name it returns an error that "There was an error creating the child process for this terminal" (not sure if this helps)
I have searched through the forums and tried to generate an apport for this but as it doesn't seem to be a crash I am at a loss as to how else I can find out what I'm doing wrong. Any help would be appreciated. Thank you.

---

### Post by MichealH on 2010-09-11
To run two, or however many commands as you want, you can use && but make sure they have a space between them. For example:

```
sudo apt-get update && sudo apt-get install package
```

---

### Post by gzarkadas on 2010-09-11
Specify the full path to the folder (the cd command). Note everything that is in bold below (with blue what you need to change, with red problems-see below). Put the ; between each commands and make it all one single line.
[INDENT]sudo iptables -t nat -A OUTPUT -d xxx.xxx.xxx.xxx -j DNAT --to xxx.xxx.xxx.xxx **;** cd **/home/[COLOR=Blue]<my-account>[/COLOR]/**.wine/dosdevices/c[COLOR=Red]**:**[/COLOR]/users/USER/Local\ Settings/Application\ Data/Ragray **;** wine heRO.exe -1rag1
[/INDENT]Note that the : character is the path separator in all unix-like systems. So the : in the directory must change to the really used character(s). Navigate with Nautilus inside the .wine folder to see what the real path is. Select 'View|Show Hidden Files' to be able to see .wine.

If after all this the command does not execute, put it in a text file, add `#!/bin/bash' as the first line and make it executable: From Nautilus select the file, right-click and select 'Properties' from the menu that appears. Go to (User) `Rights' tab and check the 'Execute' box. Then use the path to this file as the command. 

A nice place to put this file is ~/bin. You can then put this folder in your path (edit your ~/.bashrc to make it permanent) and all scripts inside will be accessible in your terminal without specifying the full path.

---

### Post by silverdragon27 on 2010-09-11
Thanks for your help guys, putting it in a text file and running with the bash tag worked wonderfully. It's amazing how many people are afraid of linux when all it has done for me is make my tasks more simple =P

---

