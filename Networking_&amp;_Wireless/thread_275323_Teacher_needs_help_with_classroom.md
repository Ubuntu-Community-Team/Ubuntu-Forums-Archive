---
title: "Teacher needs help with classroom"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by knichel on 2006-10-11
Greetings,
I am teaching in a high school.  I have a group of students for 1/2 day and another group for the second 1/2 day.  I have 10 computers that they use.  I installed 6.0.6 on them and installed all the software I want them to have access to.  I wish to have roaming login available as well as server stored documents.

Currently, I have another server in the room (not set up by me) running Gentoo.  The documents are served from that server as nfs share.  The remote login is handled via NIS from same server.

I have been trying to create a drop box (students can write to, but no browse or delete from).  I need to be able to mount this folder and have rwx privs for myself.  I do not login against the server like the kids.  I have my own laptop that I use.  I have an account on the server which has same username as my account on my laptop, however, UID's are different.  The purpose of the drop box is for handing in asignments for me to grade and display on projector to the class.

I have tried to get assistance in #ubuntu and #linuxhelp along with reading wikis and forums.  In the IRC channels, 5 people respond with 5 different ideas.  Each trying to convince me that their idea is more sound than the others.  I have been told to use samba to share the documents as it has better control of permissions.

Can someone tell me...  
Should I be using a server running UBUNTU or is  it OK that it is GENTOO?  

Should I share via nfs or samba?

Should I try to match my UID on both server and laptop? or is groups the way to go?

When I mount a volume using nfs, is there a way to specify to use permissions based on an account on the server so I can get rwx since I am the owner (my account on server) of the drop box?

I would appreciate the assistance as I am somewhat of a linux newbie.  


Mike

---

### Post by wieman01 on 2006-10-11
Ok, I am not an expert in this field, either, but I think this can be the starting point of a good (and hopefully beneficial) discussion. I'll try my luck. :-)

1. It's OK if the server is running Gentoo. Linux is Linux & it won't matter much.
2. Sharing via NFS as it usually has a much better performance. I understand there are no Windows machines in your classroom that need to access the file server. Therefore, SAMBA is pointless.
3. Match your UID on both server & laptop. The group is for the kids. This way you will be able to distinguish between your profile & theirs.
4. The permissions on the server work like the ones for the Linux file system that you control through "chown", "chgrp", "chmod". That's why I suggested the groups & UID under point 3.

Does that help? Any others with bright ideas?

---

### Post by wieman01 on 2006-10-11
BTW: I hope you won't find this kind of competitiveness you have mentioned in here. People are pretty relaxed in this forum. :-)

---

### Post by knichel on 2006-10-11
Thanks for the input.  I never find the competitiveness in the forums.  Only IRC.  Sometimes it spins off into off topic discussions.

So, how do I deal with the UID change?  Match the server to my laptop or visa versa?  Then what do I do with the files I own?  Won't I need to chown those files?  As I understand it, even though a username is shown in owner field, it really sets owner by uid.  On the server I have an admin login as well as a standard user login.  I imagine it will be easier to change my uid on the server to match my laptop (I hope the uid is still available on the server).

Thanks again.
Mike

---

### Post by wieman01 on 2006-10-12
Ok, here is my idea. First of all ensure that **_all_** UID's are consistent both on the file server & the network PC's (including your laptop). Up to you which way you do that.

Then create a folder on the file server:
1. Owner = your_user [COLOR="Red"](chown)[/COLOR]
2. Group = students [COLOR="Red"](chgrp)[/COLOR]
3. Rights = +d+r+w+x-d-r+w-x-d-r-w-x [COLOR="Red"](chmod)[/COLOR]

This way your kids could write files to the server, but won't be able to delete, read or execute them. Does that make sense?

According to my understanding nobody will have to "chown" files since the ownership/group is assigned based on the user's profile who write the files to the server.

---

### Post by hsweet on 2007-11-19
What about Edubuntu.?
One server, one hour (if you've done it a half dozen times :) no local hard drives.  
Easy to make a drop box.  
A folder in /home that everybody can write to.
Just one computer to set up and administer.

Linux is good, only one computer is even better.

---

