---
title: "What I 've done now ?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Hellinas on 2010-10-24
Hello to everybody !!! I would like from someone to tell me if there is something I should worry about with my actions on trying to do something ...
   I wanted to copy all the settings (desktop, apps, appearance ...) from root user to a new one. Here are my steps

1. created the new user
2. From konqueror show the hidden files and copied all the hidden files from "root" folder to home/user folder
(I took some copy errors from files dir's I do not remember which ones ... I remember "dev" folder was one of them now but I ignored all of them and finished copying)
3. Went to home/user folder, opened a terminal and run the command 
chown -R user:group .*
4. I rebooted my system and logged in as my new user
  
  Everything so far looks working as I wanted but I 'd like to know if there is something to worry about for the future. Thanks in advance !!!

---

### Post by ArgusVision on 2010-10-24
Seems an odd way to do it, but it shouldn't cause any immediate issues.
I t will use alot of unneeded space. (ie. /etc, /dev, /usr ) There are quite a few directories of considerable size.
I would also be slightly concerned about having some of the more sensitive files like /etc/passwd and /etc/shadow in a standard user's home directory.

---

### Post by wojox on 2010-10-24
Why was your thought process behind doing this?

---

### Post by Hellinas on 2010-10-24
Well about space root folder size is 312mb and for a new user 119mb ... I did it trying to copy one profile to another ...  Am I going to have any security issues or unstable system working with the new user ? Your opinion ?  Thank you again for bothering.

---

### Post by SuaSwe on 2010-10-24
I don't think it'd cause any issues either but I too am curious what the reason was for this move. :D Generally you'd have a root account (inaccessible without sudo) from which backend info for all users is shared by all user accounts on the machine. How come you copied all the root stuff over to a regular user acocunt?

---

### Post by Hellinas on 2010-10-24
I just wanted to to have the same settings for the new user but as I understand from your sayings I have a new user with root capabilities ? Ok I've done nothing then :(  Could someone tell me how to copy prorams, desktop, fonts, appearance... sets to a new account from root account ? (pls...)

---

### Post by SuaSwe on 2010-10-24
Well, all those settings (or a lot of them, anyway) will be in the /home directory of the previous user, so you could try copying the relevant files from that user's directory into the new one. The / (root) directory, which doesn't contain "settings" files so much as "application" and "run" files, is shared between users anyway without you having to copy it over. :)

Do you literally want both user accounts to be identical, then?

---

### Post by SuaSwe on 2010-10-24
If you want them both to be identical, have a look at this (old but still relevant) post:

[http://ubuntuforums.org/showthread.php?t=365440](http://ubuntuforums.org/showthread.php?t=365440)

Edit: If you're not completely comfortable with the procedures involved, feel free to post here for advice first before doing anything. :)
2nd edit, just to clarify: The new user you've created doesn't have any elevated permissions - only "root" (not an actual user account as such) has them. What you have now is essentially a backup folder of the system files in the form of a user's home directory.

---

### Post by Hellinas on 2010-10-24
"IIf you want them both to be identical, have a look at this (old but still relevant) post:

[http://ubuntuforums.org/showthread.php?t=365440](http://ubuntuforums.org/showthread.php?t=365440)

IIf you're not completely comfortable with the procedures involved, feel free to post here for advice first before doing anything. :)
2nd edit, just to clarify: The new user you've created doesn't have any elevated permissions - only &quot;root&quot; (not an actual user account as such) has them. What you have now is essentially a backup folder of the system files in the form of a user's home directory."

Thank you very much [SuaSwe]("http://ubuntuforums.org/member.php?u=789466") you are very helpfull !!! Unfortunately I am gonna try it tomorrow cause is time for sleep ...

---

### Post by Hellinas on 2010-10-25
Well I thing that answer is exactly what i did with the difference that I wanted the settings from the root user. So with this way you can copy one user to another :). I am happy I found it myself but is there a way to do what I want or I just should have done a normal user, set the thinks I want and then starting the replicas ?

---

### Post by Hellinas on 2010-10-28
How can I mark it as SOLVED ? :P

---

### Post by Rasa1111 on 2010-10-28
see "Thread Tools", right above your post, in red? 

 click that and "mark as solved". :)

---

