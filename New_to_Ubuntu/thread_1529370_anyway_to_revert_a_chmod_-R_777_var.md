---
title: "anyway to revert a chmod -R 777 /var"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by InfernalAngel on 2010-07-12
Hi there I did this command by a mistake 
sudo -R 777 /var

now all the permission of my /var folder was set to 777 ... :(. Anyway to revert that folder to previous state ?

---

### Post by nothingspecial on 2010-07-12
:shock: You didn`t want to do that

It depends what is in it. Some software will put some of it`s stuff in there, so it depends what you have installed.

There can be thousands of different files in /var

---

### Post by Mariane on 2010-07-12
Do you remember what the previous permissions were? 
I sympathise, I also do chmod 777 when I get fed up with the restrictions getting in the way of legitimate uses. 

To revert I type 
sudo chmod 710 stuff (or whatever seems nearest to the original)
Then
ls -lh to look at the permissions
Then
sudo chmod u-x stuff 
or whatever is needed to fine tune the permissions back to what they were. I seldom hit it spot on with the 3 digits but it is faster than doing every single option via the u/g/a method. 

Hint for next time if you have forgotten:
Before changing the permissions, open a terminal window and type
cd /var
sudo ls -lhR > permissions.txt

Then all the permissions file by file and directory by directory are written in the file permissions.txt and you can look at it to see what needs to be reverted. 

For now, if you don't remember the original setting, the 755 setting seems to me to be a safe bet. If some programs don't work anymore with this at least you will have some clue as to why and you will be able to modify some particular permission accordingly (you might get error messages such as "can't open schmilblick.glob"). 

If some programs just fail to launch when you click on their icon, you can try to launch them by typing their name in the terminal. They still won't launch but at least you will be able to read the error message saying why it does not launch. 

Mariane

---

