---
title: "Join to domain, folder redirection and mount home drives"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by declan.marks on 2014-04-20
I want to join Ubuntu or any other Linux OS such as Zorin OS. I found a program called LikewiseOpen but I looked on the Ubuntu Community Wiki which says it it unavailable. Is this true or is it still available.

Once I get the machine connected how would I redirect the folders, such as Documents, Music, Pictures, Video, Desktop and Download to the folders in the user profile located on the windows file server. I want them to be redirected to the same folders that would be used on a Windows profile. Will the folder redirection in Group Policy on windows work or do I have to do something on the local computer.

I would also like to get the user profile home folder mounted like drive mapping in Windows and automatically create a shortcut on the desktop. In Windows you can use the %username% variable to detect the user currently logged on and mount there home folder. How would this be done in linux.


[IMG]http://it.clas.ufl.edu/files/home.png[/IMG]
The example image uses the H: drive as the home drive. This is the drive that I want to mount and shortcut it on the desktop. 

Another thing is I don't want the OS to do is create a local home folder when the user logs on for the first time on the machine. I just want it all to come from the central Windows server. How can I stop local home folder creation?

---

### Post by declan.marks on 2014-05-04
I want to add some Ubuntu machines to my Windows network at my school. Mainly on low end laptops. I want to automatically mount the users active directory home folder on logon. How can I get it to mound the windows share specific to the user logged on. So for example if daniel.smith was logged on it would mount the folder daniel.smith in the network share. I have done some googling and cannot find anything on how to do this. Another thing when the folder is mounted, how can I get it when the user clicks on places/home they will be taken to their active directory network home folder share instead.

Sorry, but I am new to linux, so I don't know very much.

I would be grateful if someone could help me with this problem.

---

### Post by QIII on 2014-05-04
Is this the same question you asked [here]("http://ubuntuforums.org/showthread.php?t=2218421")?

---

### Post by declan.marks on 2014-05-04
Yes it is, but I didn't get any reply. I've decided to split it up into separate threads. I really need help with this.

---

### Post by QIII on 2014-05-04
*Threads **Merged***.

Please do not start duplicate threads.  It actually makes it *harder* for you to get good help.  If one person is helping you in one thread and another person in another, then they are duplicating effort without coordination - and might even provide confusing or contradictory advice.

If you are not getting responses, please simply add another post with the word "bump" to raise it to the top again -- but no more often than once every 24 hours.

Best wishes.

---

