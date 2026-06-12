---
title: "Samba Permissions"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by danimal87 on 2007-03-02
Hi, I've just got samba running for the first time and I can connect to the server and everyone can put files in or get files out or create files, but heres the problem say I want to put a paper I'm writing on one computer into the shared folder I can't than open that file back up and edit. Is there a way to make it sol that and file placed into or created in the shared folder can be edited by anyone?

---

### Post by LotsOfPhil on 2007-03-02
When you put the file in your shared folder you can make it read/write-able by anyone. Just type:

chmod 666 file

I don't think samba is messing with anything. It is just preserving the permissions that are on the file to start with.

---

### Post by dannyboy79 on 2007-03-02
yeah, if you can put a file in a folder (which basically means writing that file to that location), than that means that that folder is already writable so most likely it's the file's permissions. 666 will make the file readable and writable for the owner, the group, and everyone else. If you did 777, than that would make it executable for all the above people as well but if it's not an executable file than no need for that. Another way to do it would be sudo chmod uga+rw file. I believe this is the same thing, since I am saying that u=user, g=group, a=everyone else should have r=read and w=write added, +, to the file.

---

### Post by LotsOfPhil on 2007-03-02
He shouldn't need to use sudo (since it's his file to start with). And chmod uga+rw is the same as chmod 666.

---

### Post by dannyboy79 on 2007-03-02
> **LotsOfPhil said:**
>  He shouldn't need to use sudo (since it's his file to start with). And chmod uga+rw is the same as chmod 666. 
I always just suggest people use sudo since half the time people come back and say, "gedit /etc/fstab didn't work", or they say "I do the changes but they don't stick" or "it won't let me save the file". Then I think to myself, don't they know about sudo. That's the reason I just put it in there always when helping people.

> **LotsOfPhil said:**
>  And chmod uga+rw is the same as chmod 666. Yeah, thanks for telling me that. You must not have read that part where I specifically said, "Another way to do it would be sudo chmod uga+rw file. I believe this is the same thing," I inform people of this so they can learn, telling people how to change permissions using the octal digits doesn't teach them anything nor is it easy to remember or understand how it works since it's derived by adding up the bits with values 4, 2, and 1.

---

### Post by LotsOfPhil on 2007-03-02
This seems like a good opportunity to post this:

[http://xkcd.com/c149.html](http://xkcd.com/c149.html)

---

### Post by dannyboy79 on 2007-03-02
indeed, I like that!!!!!!!

---

### Post by dannyboy79 on 2007-03-02
hey there, check this out if you think it's silly of me to suggest sudo all the time.

[http://www.ubuntuforums.org/showthread.php?t=374437](http://www.ubuntuforums.org/showthread.php?t=374437)

you'll get a kick out of it!

---

### Post by LotsOfPhil on 2007-03-02
Sometimes it is good that you have to click reply, type it in and then click post reply. Lots of time to erase "unhelpful" words :)

---

### Post by danimal87 on 2007-03-02
So, is there a way to make it so everything put into the folder has those permissions by default?

---

### Post by dannyboy79 on 2007-03-02
> **danimal87 said:**
> So, is there a way to make it so everything put into the folder has those permissions by default?

if it's over samba, you want to add the create mask option and or the directory mask.

create mask = 0644
directory mask = 0755

this would make all files owned by that user who put it there and readable by everyone. the directory makes all directories writable by everyone and readable and executable for everyone. just change it to 0666 if you want it readable and writable for everyone.

---

### Post by dannyboy79 on 2007-03-02
> **LotsOfPhil said:**
> Sometimes it is good that you have to click reply, type it in and then click post reply. Lots of time to erase "unhelpful" words :)

not sure what you mean here?

---

