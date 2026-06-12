---
title: "Sharing and partition issues"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by nVee on 2009-11-25
O boy ... have I been struggling with the simplest of things today! It has now gotten to such an extent where I dont feel in a mood to struggle anymore, and fear that my windows CD may just get to run one more time ...

I have Ubuntu 9.10 installed

1) On installation of 9.4, apache worked like a charm, after i upgraded to 9.10, now it does not work. It says it is installed, along with PHP, mysql and phpmyadmin, but when I do [http://localhost](http://localhost) or [http://192.168.0.1](http://192.168.0.1) it says page cannot be displayed. I have uninstalled everything and re-installed it, same story.

2) The hard drive I installed ubuntu on appears to be a NTFS partition (was a windows drive and did not re-partittion it) now it appears that I cannot share any folders on it. When I right click > sharing options > share this folder > apply > click okay to set additional permissions I am faced with a "could not change the permissions of folder "www".

3) I have 2 additional hard drives which i re-partitioned and formatted using Gparted. I then went to places > mount the drive. Now it created a shortcut on my desktop called 500 GB filesystem and 400GB filesystem, but i cannot do anything in it. I cannot create files or folders in it. How do I get this to work? I want to use it to save my work on it.

4) Lastly I am planning to share printers, but i figured I would do that when 1 - 3 has been sorted out :( 

Please, I am a absolute beginner, and rely totally on forums and feedback from users, so if anyone could help (and be patient with the explanation) i would really appreciate it!

---

### Post by cariboo on 2009-11-25
> 1) On installation of 9.4, apache worked like a charm, after i upgraded to 9.10, now it does not work. It says it is installed, along with PHP, mysql and phpmyadmin, but when I do [http://localhost](http://localhost) or [http://192.168.0.1](http://192.168.0.1) it says page cannot be displayed. I have uninstalled everything and re-installed it, same story.

Is apache running? Check in System-->Administration-->System Monitor-->Processes

> 2) The hard drive I installed ubuntu on appears to be a NTFS partition (was a windows drive and did not re-partittion it) now it appears that I cannot share any folders on it. When I right click > sharing options > share this folder > apply > click okay to set additional permissions I am faced with a "could not change the permissions of folder "www".

I would suggest you check again, because Ubuntu won't run on an ntfs formatted partition. Are you asked for authentication when trying to change permissions, as you must be root to change permissions on any directory outside your home directory.

> 3) I have 2 additional hard drives which i re-partitioned and formatted using Gparted. I then went to places > mount the drive. Now it created a shortcut on my desktop called 500 GB filesystem and 400GB filesystem, but i cannot do anything in it. I cannot create files or folders in it. How do I get this to work? I want to use it to save my work on it.


How are the partitions mounted and what permissions do they have?

> 4) Lastly I am planning to share printers, but i figured I would do that when 1 - 3 has been sorted out 

I would suggest using the cups interface to share your printer. Access it at [http://localhost:631](http://localhost:631)

I looks like all of your problems are permissions related. You can change permission by running nautilus as root. Press Alt-F2 and type:

```
gksudo nautilus
```

---

### Post by nVee on 2009-11-25
Thank you for your reply.

1) You we're right, it was apache which was not started. I read in a earlier tutorial I had to add a line of code to a file (something about ServerName = localhost) and that appeared to stop apache from running. When I removed the line, apache runs and I can access it on the network. Now the problem is phpmyadmin. When I type in [http://192.168.0.1/phpmyadmin](http://192.168.0.1/phpmyadmin) I get a "permission denied, i dont have the correct permissions to access phpmyadmin" It would appear that php is working as well, its now just phpmyadmin ...


2) No i am not asked to root. Well, i was with a previous application, but not when I try to share. What is funny I got this to work so simple on my laptop ... how do I get root?

3) partitions is ext3 on both of them (i read that that is the correct partitions to use) and I went to PLACES > clicked on the hard drive which said Mount 500GB Filesystem - What is weird is that the labels I gave them is not the same labels. Dont know if this makes sense?

4) Ill look into the printers shortly ... :)

5) i tried gksudo nautilus which allowed me to share the folder, thank you! However, I have created a new "administrator" at user settings, but when I go from e.g. my windows machine and type in \\192.168.0.1\www (the directory shared) it asks me for my username and password, but it does not accept it. infact, it would appear that it does not even accept my root username and password, so again, back to square one :) I think what makes ubuntu cool is that you feel chuffed if you actually get something right :)

---

### Post by nVee on 2009-11-25
for what its worth, when I right click on any of the new hard drives, and go to permissions, it says I am not the owner of the hard drive, so again, I guess it boils down to some previlledge thing, but is there a way I can permanently set it that I dont have to change permissions or do something when I want to alter the hard drive?

---

### Post by nVee on 2009-11-25
I have already done "sudo chown -R server /media/work" which does not return anything when I type it in, so I am not sure if it works or not, but I do know that I still am unable of doing anything on the hard drive.

---

### Post by nVee on 2009-11-25
no answers ... i think its time to call it a day. Ubuntu may be free, but it makes the simplest of tasks a mountain to get over. I just dont see why we have to struggle to get the simple things to work. I mean getting a hard drive to actual do its purpose, i cannot share because I first need to log a program in as root to change previlledges...

Just too much man :) good luck to you guys!

---

