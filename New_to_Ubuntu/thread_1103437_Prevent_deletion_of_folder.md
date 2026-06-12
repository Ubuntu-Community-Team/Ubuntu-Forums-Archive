---
title: "Prevent deletion of folder"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by niko123 on 2009-03-22
Hello everyone,

I have created an image that i will be placing "out there" for the students at my University to use. BUT because these will be our first linux machines...i want to make sure everything is perfect...


Anyways i was told that i was not able to hide the file system completely from the limited users... But can i make it "hidden"?  

If not my other question would be if there would be a way that i can prevent those very, very, very limited user from deleting ANYTHING from the "filesystem".

Although these user dont have access to the terminal or the root password. If someone wanted to destroy/abuse a computer they would....sad. But true.  

Please do provide me with ANYTHING!!

I dont want my first 50 Linux machines to be put out there...and destroyed because "someone" decided to abuse it!

---

### Post by jimv on 2009-03-22
As far as I know, unless they have sudo, regular users can't delete anything except what's in their home folder.

---

### Post by llamabr on 2009-03-22
What exactly do you want to hide?  And why?

Most system files come world readable, but only user writable.  And those that should be protected (logs, passwords) come world unreadable.

The linux file structure and permissions structure already satisfy this concern.  Unless I misunderstand what you want to hide.

---

### Post by Shazaam on 2009-03-22
Also understand that any knowledgeable user with a linux livecd can wreak havok on an operating system.

---

### Post by niko123 on 2009-03-22
Thanks for all the input so far everyone, my goal here is when these machines are placed out in the public for public use, i want to make sure, that "if" someone were to attempt/try...(whatever the case may be) that they will not be able to touch/delete any folder inside the file system.

I know this is going to be a bit sad...but i know that in the windows machine i would be able to put a policy..on that user. So that if they were to attempt to delete anything inside the C: they wouldn't be able to...because with the policy they are "hidden" and the only folder they would be able to see is there "Documents folder" So i wanted to do the same thing...but this ISNT windows :)

Thanks

---

### Post by sleepyjon on 2009-03-22
> **Shazaam said:**
> Also understand that any knowledgeable user with a linux livecd can wreak havok on an operating system.

All you have to do there is disable booting from anything but the HD, and password protect the bios.

---

### Post by apmcd47 on 2009-03-22
> **niko123 said:**
> Thanks for all the input so far everyone, my goal here is when these machines are placed out in the public for public use, i want to make sure, that "if" someone were to attempt/try...(whatever the case may be) that they will not be able to touch/delete any folder inside the file system.

I know this is going to be a bit sad...but i know that in the windows machine i would be able to put a policy..on that user. So that if they were to attempt to delete anything inside the C: they wouldn't be able to...because with the policy they are "hidden" and the only folder they would be able to see is there "Documents folder" So i wanted to do the same thing...but this ISNT windows :)

Thanks

Linux doesn't need such a policy because system folders are by default secure from abuse by normal users. This policy had to be added to Windows because of the history of Windows - a file system with no user access control; programs which would open .dll files read-write!

Given Shazaam's comment, you might want to consider looking at the BIOS to see what you can do to prevent users from rebooting them into a live CD or a live USB! But otherwise, they are safe. Just make sure the superuser password is disabled (with Ubuntu this is default); your password is unguessable, and none of the students are in any sudo groups.

Andrew

---

### Post by niko123 on 2009-03-22
Everyone,

Thanks for all all the comments, i feel much more confident now!!! Thanks for all the comments...

My last question is the comment made by apmcd47 "and none of the students are in any sudo groups."

Just to make sure i am on the right page you are talking about the
```
 sudo gedit /etc/sudoers 
``` 
correct?

Please let me know..thank you everyone

---

