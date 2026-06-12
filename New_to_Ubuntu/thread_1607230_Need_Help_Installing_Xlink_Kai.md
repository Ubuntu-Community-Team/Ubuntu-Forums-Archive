---
title: "Need Help Installing Xlink Kai"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by ShadowVegan on 2010-10-27
I'm new to Ubuntu (just started using yesterday) and am trying to figure out how to install Xlink Kai. I did a search on the Ubuntu forums and someone suggested [this]("http://www.teamxlink.co.uk/forum/viewtopic.php?t=23134&sid=740d2bf29b817aae11a8e9c712a48896") topic at the Xlink Kai forums. I tried following the instructions. I downloaded the x86 version of Kai to my home directory. Then I opened the terminal and entered the first command that the topic suggested ('sudo mv kaid ../../bin'). I entered my password. Then the terminal says 'mv: cannot stat 'kaid': No such file or directory'
How do I get past this? Is there a tutorial better than the one in that topic? Thanks.

---

### Post by Terl on 2010-10-27
The commands work fine but some questions.  Did you type the quotes when you entered them?  If so, don't.  The next is, run it from your home.  Not your download folder or wherever you have the kaid file.  The commands work perfectly from your home folder.

To be sure you have everything in the right place, type ls in your home directory, the prompt will show user@host:~>  When you type ls you should see kaid file listed.  If not there move it to there, then the commands will work as they gave it to you...

---

### Post by ShadowVegan on 2010-10-27
No, I did not include the quotes. Just included here for clarity. I saved kaid to my home folder because that's what the other topic said to do. Where exactly do I type Is? In terminal? How to I get to home directory in terminal? Thanks.

---

### Post by Terl on 2010-10-27
Yes, type everything in a terminal.

Wherever you are in the terminal, if you type cd ~ you will go instantly to your home folder.  When you first open terminal you will be in your home folder (unless you changed something).  Type ls at the prompt and then enter.  You should see kaid file listed.  If not you need to move it to that location.  A lot of times downloads go to /downloads in your home folder.  If it is there you can easily move it with nautilus.  If you'd rather, you can do all this graphically by typing in a terminal gksu nautilus It will ask for a password, enter it, and then the file manager opens in root mode so you can move files to where they go.

---

### Post by ShadowVegan on 2010-11-03
Sorry for the late response. I typed ls and Kaid does show up. I also went to my home folder to confirm that it's there. However I still get the same error 'mv: cannot stat 'kaid': No such file or directory'

I think I know the problem now. The folder is not called 'kaid', it is called 'kaid-7.0.0.7-linux-x86'
The command seems to be working but the xlink kai site is down so I can't see the rest of the walkthrough right now.

I will post here if it doesn't work.
Thanks for the help.

---

