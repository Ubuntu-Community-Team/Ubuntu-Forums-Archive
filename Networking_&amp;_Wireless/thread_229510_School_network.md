---
title: "School network"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by rottdog on 2006-08-04
I recently installed dapper on my cousins desktop, he finally realized windows sucks and wanted to try this , he loves it and is finally getting used to it. However now he is going back to school next month and we have no idea how they are gonna react to him having linux on his pc as they are very anal when it comes to their network , the tech people there didnt even know what linux was when he asked them if he could use it. This is a link to what network settings need to be in windows so i figured i'd ask you guys if by looking at this would he need to make and changes and if so what, It maybe a dumb question but i myself am still new to Ubuntu and linux in general i'm a recently converted windows user 

[http://helpdesk.jwu.edu/stu_resnet_ri.htm](http://helpdesk.jwu.edu/stu_resnet_ri.htm) 

Any help would be greatly appreciated

---

### Post by sethmahoney on 2006-08-04
My main concern would be that "clean access" software, which appears to be Windows-only.  You might try calling them back and asking if it is possible to have internet access with a mac computer - if they say yes, then at least in principle its possible to access their network without Windows.

---

### Post by tkiesel on 2006-08-04
Looks like your cousin should be able to get on his school's network without any problem rottdog.  Standard default Ubuntu networking settings should be fine for the section entitled "windows xp" on the page you linked.  That part is about general networking access, internet access, etc. There are a few things I see that might cause snags, but then they very well might not. I can use an Ubuntu machine without trouble to get access at the school that I work at, and the setup sounds much the same.

Now, the section on that page that begins "identifying your computer" is about getting logged into the campus network. (i.e. sharing files, drives, workgroups, etc on the school network, not just general internet access)  This deals with configuring Samba on his Ubuntu system.

That will likely take a bit more tweaking from him.

Here's a few steps that I think will get him in the ballpark:

To replace steps 1-4 of the "identifying your computer" school directions:

1. Click on System->Administration->Networking

2. Choose the General Tab

3. Change the hostname to your USERNAME as directed by that school setup webpage.

4. Click OK

For steps 5-6 of the 'identifying your computer' directions:

1. Click on System->Administration->Shared Folders
(If you get a message saying this isn't set up yet, choose Samba and agree to install it. Wait for it to install fully, etc.)

2. If there are no folders shared yet, click "Add". (don't worry, we'll get rid of this "dummy" share in Step 6)  If you already have some shares, click on one of them and choose the Properties button.

3. On the window that appears, click the button "General Windows sharing settings".

4. enter STUDENT for the Domain/Workgroup. I don't think it matters if it's in all caps, but make it in all caps just in case. ;)

5. Click OK on that general settings window and OK on the 'Share folder' window.

6. If you had to make a new "dummy" share in Step 1., go ahead and delete it now. It was the general settings we wanted to fix anyway.

7. Hit OK on the 'Shared folders settings' window.

After completing these two sets of steps, go ahead and reboot to let the system recognize its new host name.  

With those steps, I think your cousin's machine should plug itself right into the campus network, rottdog!

RE: the "Clean Access" client (if yoru cousin attends in Providence) If he has trouble logging into the network because he needs validation through the Clean Access client, he'll just need to let the help desk of the campus network know that he's connecting with a non-windows operating system and that automatic updates are on by default on his OS. They should be able to make provision for him to login without requiring the Clean Access client.

take care,
-T

---

### Post by rottdog on 2006-08-05
thanks for all the info , i will  see if this works next month when he gets back to school. hopefully he won't have any problems. thanks again guys i really appreciate it

---

