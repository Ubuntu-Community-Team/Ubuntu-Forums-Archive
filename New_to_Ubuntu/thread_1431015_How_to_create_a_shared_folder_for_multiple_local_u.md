---
title: "How to create a shared folder for multiple local users"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by kichigai_dave on 2010-03-16
I've tried searching through past posts and other sites as well as the beginners PDF, but to no avail. I've came across a lot of people asking this question, but never saw a good answer yet.
 There has to be a simple way to create a shared folder that multiple local users can access. I would like a folder (containing sub-folders for organization) to store music, pictures, videos, etc... that any local user can access, add, delete, modify. I've attempted using permissions, shared, put them in the "Public" folder, etc...  But when I log in as a different user, it's not there. Well, at least not easily accessible. 
This seems like it would such a common thing, and for people wanting to dump windows, a very necessary thing. I've got tons of Music, pictures, videos, etc... that I would like to be shared easily. My wife is not real computer literate and it needs to be as simple as possible.

---

### Post by sikander3786 on 2010-03-16
The easiest way to share folders locally is by placing them in a separate FAT or NTFS partition preferably NTFS.

It doesn't sound good for Ubuntu to use Microsoft Technologies to share data across users but....

Might be some good new features are introduced in Lucid Lynx.

[http://brainstorm.ubuntu.com/idea/3916/](http://brainstorm.ubuntu.com/idea/3916/)

Regards.

Sikander.

---

### Post by egalvan on 2010-03-16
> **sikander3786 said:**
> The easiest way to share folders locally is by placing them in a separate FAT or NTFS partition preferably NTFS.

It doesn't sound good for Ubuntu to use Microsoft Technologies to share data across users but....

Sikander.

But what?

FAT has **zero** permissions options...
NTFS uses a totally different system from Linux and is limited.

This is something that is done every day, in thousands of Linux installations... using native Linux file systems.

But I agree, the methods and tools to achieve this could be easier...

There are several methods to achieve this, if all users are Linux.

One...
set up a dedicated folder, make sure that permissions allow ALL USERS to READ/WRITE/EXECUTE files.

Two, set up a dedicated folder (or partition, or drive), and use symlinks to allow users to access the data (this is the method I use, a little more difficult to set up, but much more *user*)-friendly. Each user has a "local copy" of the data...
no need to navigate directories to find it.

---

### Post by kichigai_dave on 2010-03-16
thanks for the reply,

That's what I was thinking of doing when I was dual booting. I eventually took the plunge tonight and just wiped windows completely off my laptop and re-installed Ubuntu 9.10. I could probably take a chunk of free space and do that. I was just hoping that there was an easy solution I was overlooking that I could do in Ubuntu. Right now, I've got everything stored on a removable HDD. 
I was thinking of creating another folder, not sure where exactly I should put it though. I'm pretty sure it shouldn't be in the "home" folder, because that would probably cause more permission issues. I created a group called "mediashare" and added all the users to that group. Now, I figured I could create the folder and set the permissions for that group to access & modify, etc... But where should the folder be located, and would that work? I'll play a little more tomorrow.

---

### Post by inobe on 2010-03-16
> **kichigai_dave said:**
>  I would like a folder (containing sub-folders for organization) to store music, pictures, videos, etc... that any local user can access, add, delete, modify. I've attempted using permissions, shared, put them in the "Public" folder, etc...  But when I log in as a different user, it's not there. Well, at least not easily accessible. 
This seems like it would such a common thing, and for people wanting to dump windows, a very necessary thing. I've got tons of Music, pictures, videos, etc... that I would like to be shared easily. My wife is not real computer literate and it needs to be as simple as possible.

this is very simple and can be done in ten minutes.

here's a post i made a week ago

[http://ubuntuforums.org/showpost.php?p=8953525&postcount=2](http://ubuntuforums.org/showpost.php?p=8953525&postcount=2)

a little terminal action is required but much quicker.

---

### Post by HermanAB on 2010-03-16
The folder can be wherever you want, but /home is the only directory I ever back up, so I would put shared schtuff in /home/public or some such, and make it 'sticky' and group 'user'.

---

### Post by inobe on 2010-03-16
herman is correct, you can do mkdir where ever

---

### Post by kichigai_dave on 2010-03-16
Not really what I was looking for, but I guess there's more than one way to skin a cat. I was just hoping to simply have a shared local folder between users to share music, movies, etc... all in one location. Not over the network to other computers and hopefully not using a program to access, such as samba or nautilus, etc... I am not dual booting on this laptop, I have completely removed windows and only have Ubuntu now.

What if I make a separate partition for this and set up folders for the applicable media. Since it's not part of the file system, would everyone have access and permissions to add and modify? Should I make it a certain type of file system? 

What is the purpose of having a "Public" folder in your home directory, if the "Public" (other local users of this laptop) can't see what you put there?

I'll play around a little more, and try a few things out. If that doesn't work, I'll try the Samba idea. I just can't believe it's this difficult to do something this simple. Should be a common and easily achieved task, I hope newer versions address this as more people are fed up with Windows.

---

### Post by kichigai_dave on 2010-03-16
Any ideas? Suggestions? 
Has anyone ran into this before and found an easy way to accomplish this?

---

### Post by sandyd on 2010-03-16
```

sudo mkdir /opt/shared
sudo chmod 777 /opt/shared

```

---

### Post by Miljet on 2010-03-16
> What is the purpose of having a "Public" folder in your home directory, if the "Public" (other local users of this laptop) can't see what you put there?
I think that you are confusing /home with /home/(your_name). In other words, you would have a /home/jack/ and a /home/jill/ and a /home/both/. Then make sure that both Jack and Jill are members of the group both.

If you want to make it even more seamless, make a symlink from /home/jack/Pictures to /home/both/Pictures and another symlink from /home/jill/Pictures to /home/both/Pictures. And do the same for Documents, Music, Videos, etc.

---

### Post by kichigai_dave on 2010-03-16
When I try that, I get a message that says:  cannot create directory `/opt/shared': Permission denied

---

### Post by kichigai_dave on 2010-03-16
I just don't understand why there is a folder under /home/username/ called public if it cannot be seen by my other local users. Which is what I would think of as public, not over a network, etc... Must be for something else, not what I thought the name "public" implied.

---

### Post by inobe on 2010-03-17
> **kichigai_dave said:**
> 

I'll play around a little more, and try a few things out. If that doesn't work, I'll try the Samba idea. I just can't believe it's this difficult to do something this simple. Should be a common and easily achieved task, I hope newer versions address this as more people are fed up with Windows.

i truly assumed you wanted to share files with other computers ?

my directions were specific to that, turn that box into a file server/ usable desktop.

i'm really having trouble understanding, how will you share anything if it isn't over a network ?

---

### Post by inobe on 2010-03-17
ahh your talking about multiple accounts.

carlee pointed that out [http://ubuntuforums.org/showpost.php?p=8979207&postcount=10](http://ubuntuforums.org/showpost.php?p=8979207&postcount=10)

---

### Post by Miljet on 2010-03-17
> I just don't understand why there is a folder under /home/username/ called public if it cannot be seen by my other local users.

It seems that you are still missing the point. You do NOT create a public folder under /home/username. Instead you create it under /home. It will be on the same level as /home/username, not subordinate to it.

---

### Post by sandyd on 2010-03-17
> **kichigai_dave said:**
> When I try that, I get a message that says:  cannot create directory `/opt/shared': Permission denied

fixed.

---

### Post by kichigai_dave on 2010-03-17
Carlee, 
            Thanks, I ended up looking into it and figured out that I needed to either be logged in as root or use the super user. It worked, I dropped in a few test files and was able to access them from different users. Thank you, that was what I was looking for.
 Now I'm just looking to make a link to the desktop or menu bar for the shared folder. It would make things a lot easier for my wife who has only used windows and is slightly computer challenged. (I'm working on that). Would you suggest a hard link or sym link, or something altogether different. I know it's not windows, but is there something similar to a shortcut? I tried right clicking on the file to try the "Link" option, but it wasn't highlighted as an available option. Probably need to be root again?
Thanks,

---

### Post by kichigai_dave on 2010-03-17
> **Miljet said:**
> It seems that you are still missing the point. You do NOT create a public folder under /home/username. Instead you create it under /home. It will be on the same level as /home/username, not subordinate to it.
No, I'm not talking about a folder I created. There is already a folder there named "Public". I just don't understand why.... if it doesn't work as a public folder. Seems quite ironic that a folder named "Public" can't be seen by the "Public" (as in local and/or network users).

I was able to create a shared folder under the "opt" folder using Carlee's suggestion, and it seem to work fine. I was just commenting on the fact that there's already a folder under each user name's home, called "Public". What is the purpose of this folder if no other users (the Public) can access it? /home/username/public. Just curious.

---

### Post by lateralus-paradox on 2010-03-17
> **kichigai_dave said:**
> Now I'm just looking to make a link to the desktop or menu bar for the shared folder. It would make things a lot easier for my wife who has only used windows and is slightly computer challenged. (I'm working on that). Would you suggest a hard link or sym link, or something altogether different.

 
I'm pretty new to ubuntu, but I noticed that if you right click the desktop there is a funtion to create a link/shortcut to a specified destination. I'm assuming that you can enter in a location in the file system for which that shortcut will open, giving you a quick link to the folder. (again I'm quite new to ubuntu, I am using ubuntu 9.10 as well, you may not be, and this is just something that came to mind when I read through your question)
 
lateralus-paradox

---

### Post by blur xc on 2010-03-17
> **Miljet said:**
> I think that you are confusing /home with /home/(your_name). In other words, you would have a /home/jack/ and a /home/jill/ and a /home/both/. Then make sure that both Jack and Jill are members of the group both.

If you want to make it even more seamless, make a symlink from /home/jack/Pictures to /home/both/Pictures and another symlink from /home/jill/Pictures to /home/both/Pictures. And do the same for Documents, Music, Videos, etc.

BAM!  That's what I've done on my system...  My umask values aren't right though so every once in a while I have to do a chown -R .shared /home/shared (I think that's right, it's been a while since I've done it) to fix the group ownership of all the files...  Takes a couple of seconds...  I should write a script though.

My music folder points directly to the /home/shared/Music directory.  Very snazzy...

BM

---

### Post by kichigai_dave on 2010-03-17
> **lateralus-paradox said:**
> I'm pretty new to ubuntu, but I noticed that if you right click the desktop there is a funtion to create a link/shortcut to a specified destination. I'm assuming that you can enter in a location in the file system for which that shortcut will open, giving you a quick link to the folder. (again I'm quite new to ubuntu, I am using ubuntu 9.10 as well, you may not be, and this is just something that came to mind when I read through your question)
 
lateralus-paradox

(I'm using 9.10) When you right click on the desktop it give you the option to:

[LIST=1]
[*]Create folder
[*]Create launcher
[*]Create document
[/LIST]
I haven't seen a way create a link from the destination. Usually I think you have to right click on the source and create a link. However, that option is not highlighted as an available task when I right click on my shared folder. I probably have to be signed in as root or open the terminal, then use super user and manually do it. Looking through the Linux-faq.pdf right now for the right commands on how to do that. Thanks.

---

### Post by sisco311 on 2010-03-17
@OP

Use ACLs or bindfs.

[uhelp]/community/UbuntuLTSP/ACLSupport[/uhelp]

[http://code.google.com/p/bindfs/](http://code.google.com/p/bindfs/)

---

### Post by Morbius1 on 2010-03-17
sisco311's recommendation is probably the only way you're going to get 100% or your original requirement:
> I would like a folder (containing sub-folders for organization) to store music, pictures, videos, etc... that any local user can access, add, delete, modify.The chmod 777 method will get you to 75%

USER1 AND USER2 will be able to access and add files
USER1 will be able to delete USER2's files
USER1 will not be able to read, modify, and save USER2's files to the same file name
USER1 will be able to read, modify, and save USER2's file to another file name.

I guess it depends on how literal your requirement is for "modify".

[COLOR=Blue]EDIT[/COLOR]: I think that was sikander3786's logic in recommending a FAT32 or NTFS partition as a common repository. Unlike linux, you set permissions of a windows partition ( and anything subsequently added to it ) at time of mount. Add a umask=000 to the fstab line for an ntfs partition and everyone will have read / write access to the partition and everything in it.

---

### Post by sisco311 on 2010-03-17
OKAY, here is a *mini* HOWTO:
[list=i]
[*] install bindfs:
```
sudo apt-get install bindfs
```


[*] create a hidden & a visible directory for the files:
```
sudo mkdir /home/.media
sudo mkdir /home/media
```


[*] create a new group:
```
sudo groupadd media
```


[*] add the user(s) to the group:
```
sudo gpasswd -a **usrname** media
```
repeat this for all users. Log out and log back in your current user.


[*] edit the fstab file:
```
gksu gedit /etc/fstab
```


[*] add a new entry at the end of the file:

```
bindfs#/home/.media    /home/media    fuse    group=media,perms=g=rwx
```


[*] mount the filesystems menitioned in fstab:
```
sudo mount -a
```


[*] move the files you want to share in the /home/media directory
 
[/list]

---

### Post by blur xc on 2010-03-17
> **sisco311 said:**
> OKAY, here is a *mini* HOWTO:
[LIST=i]
[*] install bindfs:
```
sudo apt-get install bindfs
```
[*] create a hidden & a visible directory for the files:
```
sudo mkdir /home/.media
sudo mkdir /home/media
```
[*] create a new group:
```
sudo groupadd media
```
[*] add the user(s) to the group:
```
sudo gpasswd -a **usrname** media
```repeat this for all users. Log out and log back in your current user.
[*] edit the fstab file:
```
gksu gedit /etc/fstab
```
[*] add a new entry at the end of the file:

```
/home/.media    /home/media    bindfs    group=media,perms=g=rwx
```
[*] mount the filesystems menitioned in fstab:
```
sudo mount -a
```
[*] move the files you want to share in the /home/media directory
[/LIST]


Do you not need to do a chmod g+s to the /home/media directory with this method?

BM

---

### Post by sisco311 on 2010-03-17
> **blur xc said:**
> Do you not need to do a chomod g+s to the /home/media directory with this method?

BM

No, bindfs allows you to mount part of the file hierarchy somewhere else (just like mount --bind), but it also allows you to change the permissions off the mirrored directory (just like you can set permissions at mount time for NTFS & FAT partitions for all the files and folders).

---

### Post by Morbius1 on 2010-03-17
Followed your HowTo - verbatim 

sudo mount -a

Results in 
> mount: unknown filesystem type 'bindfs'
Is there a step missing or is this a user error on my part.

---

### Post by sisco311 on 2010-03-17
> **Morbius1 said:**
> Followed your HowTo - verbatim 

sudo mount -a

Results in 
Is there a step missing or is this a user error on my part.

Sorry, I didn't read the man page carefully...

It should be:
```
bindfs#/home/.media    /home/media    fuse    group=media,perms=g=rwx
```

---

### Post by Morbius1 on 2010-03-17
There you go. I'll have to admit though your original way makes more sense as it had a consistant syntax with other fstab entries ;)

I just started exploring ACL's because of your posts and now I have this.

Thank you very much.

---

### Post by kichigai_dave on 2010-03-17
Hmmm... Very interested in this latest method. I'll try it out tonight when I get home.

I really appreciate everyone's input!

---

### Post by lateralus-paradox on 2010-03-17
> **kichigai_dave said:**
> (I'm using 9.10) When you right click on the desktop it give you the option to:

[LIST=1]
[*]Create folder
[*]Create launcher
[*]Create document
[/LIST]
I haven't seen a way create a link from the destination. Usually I think you have to right click on the source and create a link. However, that option is not highlighted as an available task when I right click on my shared folder. I probably have to be signed in as root or open the terminal, then use super user and manually do it. Looking through the Linux-faq.pdf right now for the right commands on how to do that. Thanks.

I looked a little closer at it when I got home today, and if you right click on the desktop, and click on New Launcher it will open a small window. From that window select Location from the drop down menu, then you can add a name to it, then browse for the location that you want it to go to. Add a comment if you wish and I think that should do it. Maybe you'd have to add some ownerships for that particular folder, but from what I've been reading over the last 12 hours it doesn't seem too hard. Hope this is somewhat informative.

---

### Post by kichigai_dave on 2010-03-18
> **lateralus-paradox said:**
> I looked a little closer at it when I got home today, and if you right click on the desktop, and click on New Launcher it will open a small window. From that window select Location from the drop down menu, then you can add a name to it, then browse for the location that you want it to go to. Add a comment if you wish and I think that should do it. Maybe you'd have to add some ownerships for that particular folder, but from what I've been reading over the last 12 hours it doesn't seem too hard. Hope this is somewhat informative.

I figured out how to get it to work. I couldn't browse to add it because it wanted a file, not a folder. So I selected location, added a name, manually typed in the path, added comments, and then clicked OK. This put a launcher on the desk top to the locaton I specified.

(to clarify, I used Carlee's suggestion on the shared folder in the /opt directory)

I was still experiencing permission issues, between the users however. So I signed in as root, and changed the permissions for the group to have the correct rights. So far, so good. Well, see if it stays that way as I add, delete, re-organize, etc...

---

### Post by kichigai_dave on 2010-03-18
> **sisco311 said:**
> Sorry, I didn't read the man page carefully...

It should be:
```
bindfs#/home/.media    /home/media    fuse    group=media,perms=g=rwx
```


So that replaces step 6 in your code?

---

### Post by lateralus-paradox on 2010-03-18
> **kichigai_dave said:**
> I figured out how to get it to work. I couldn't browse to add it because it wanted a file, not a folder. So I selected location, added a name, manually typed in the path, added comments, and then clicked OK. This put a launcher on the desk top to the locaton I specified.
 
(to clarify, I used Carlee's suggestion on the shared folder in the /opt directory)
 
I was still experiencing permission issues, between the users however. So I signed in as root, and changed the permissions for the group to have the correct rights. So far, so good. Well, see if it stays that way as I add, delete, re-organize, etc...
 
I was messing around last night as well, trying to install my copy of Doom3 to my machine, but I have a cracked copy so it didn't work. I was looking for a way to delete it and the way that I finally managed to delete it was with a gksudo command.
 
What I did was create a copy of the file location i needed and changed the command line to gksudo nautilus /path/to/file. ( i can't remember for sure if i typed in the location or not, because i used it on the "Computer shortcut from the Places menu)
 
But in your case I'm assuming if you change the command line of your launcher to ```
gksudo nautilus /your/file/location/
```it should open the folder/file as root with all permissions on it. Only be extra careful using this since you will have all root permissions for any location you visit while using it.
 
Hope this helps some.

---

### Post by kichigai_dave on 2010-03-18
Well, I tried Carlee's suggestion and everything seemed to go ok, until I tried to simply take a picture and resize it. It wouldn't let me save the new file due to permissions. Even though I've repeatedly set the permissions for me to add, delete, read, write, etc... 

This is crazy that something soooo simple should be this difficult. I'm going to try the other method suggest by sisco311. This should be something that can be accomplished in just a few clicks and verification of administrative rights. I can see why a Windows user with little computer skills would feel daunted by trying to move to this OS. I've spent the last week trying to simply make a shared folder that a couple local users can share their music and other common stuff. 

I hope this next method works. If not, I'm sick of dealing with all the permission issues that never seem to stay put or work right. I'll just make a partition and put everything there! Any suggestions on a partition tool to accomplish this?

---

### Post by Morbius1 on 2010-03-18
> Well, I tried Carlee's suggestion and everything seemed to go ok, until I tried to simply take a picture and resize it. It wouldn't let me save the new file due to permissions. Even though I've repeatedly set the permissions for me to add, delete, read, write, etc...I think you're confusing directory permissions with file permissions. The chmod thing at a directory level will allow anyone to add or delete any file that's in there. But if Bob add's a file to that directory it will will save as bob:bob with a mode of 755 by default. bob is the owner and bob is the group. bob can write to the file but everyone else can only read.

dave can not open bob.jpeg , edit it , and save it as bob.jpeg
dave can open bob.jpeg , edit it, and save it as dave.jpeg.

What you are looking for is called "inheritance".  ACL's and bindfs can do that. Samba in the networking world can do that. There's a way to set the default permissions on all newly created files in linux by  setting a profile. But then everyone would have access to everyone else's files not just the shared directory.

---

### Post by sisco311 on 2010-03-18
> **kichigai_dave said:**
> 

This is crazy that something soooo simple should be this difficult. 


Well, while I agree that it should be easier, but you have to understand that this is a security v.s. usability question.

In Windows, by default, you are logged in as an Administrator (almost root) which by the way is a huge security risk. That's why you don't have to bother yourself with file permissions, but if you create a non-privileged account you will have to use ACLs in Windows NTFS partisions too if you want to create a shared folder (folder is the Windows equivalent of a directory :evil: :)).

---

### Post by blur xc on 2010-03-18
> **sisco311 said:**
> (folder is the Windows equivalent of a directory :evil: :)).

I prefer to think of it as a Folder being a GUI version of a directory, regardless of os...

BM

---

### Post by lateralus-paradox on 2010-03-18
Well... I did a little messing around again, and came up with this.

If you go to the Public folder that you were talking about, right click it, and select Make Link, then move the "Link to Public" to where you need it (I'm going to assume the desktop). From there right click it and select Properties. Choose the Permissions tab and set them up similar to this for what you need. (I changed mine so that everyone should have the ability to create, read, write, and delete any file within the folder Public) 

Don't forget to click on apply the permissions to enclosed files. Then it should let you do whatever you want. I don't have multiple accounts so I can't test it but I was just hoping to give you another way to do it before you take time to make a new partition.
[IMG]http://i39.tinypic.com/vou6tf.jpg[/IMG]
(sorry for the big image size but I don't know how to make it smaller and keep it readable)

Let me know if this works or if I'm just reposting something that you have already tried.
Hope it helps and saves you the trouble of making a new partition.

---

### Post by kichigai_dave on 2010-03-20
Been gone for a couple days. Yeah, that's what I tried, but the same issue persists when a certain user adds/makes a file. Then other users can access it, but can't modify it in any way. Even though you would think by setting it for the group and others to read/write/modify, etc... it would let you.??

 I understand the need for security, but the whole point of a local shared folder/directory, is that there's nothing there that's needs to be secure. It's a "SHARED" directory for the specific purpose of "SHARING" data that need not be restricted between local users in any way. Absolute overkill in the security standpoint and shows inability to be flexible and inability for users to tailor the configuration to fit their specific wants/needs. Very disappointing for someone wanting to drop Windows for an OS that is supposed to be specifically designed as an "Open source alternative to Windows and Office". This should really be addressed in future revisions, possibly a set up to compete with Windows Media Center as this is a very common want/need for home use.

I'll still keep at it, but I just can't recommend it right now to my friends and family who I've been trying to talk them into getting rid of Windows. They would end up being in the same situation as I am right now. I'll try the bindfs and ACL method, or move to a separate partition just for sharing media. I just can't imagine an average home user to be willing to put this much time and effort into something that should already have been addressed in an OS as an alternative to Windows.

---

### Post by kichigai_dave on 2010-03-20
> **sisco311 said:**
> Well, while I agree that it should be easier, but you have to understand that this is a security v.s. usability question.

In Windows, by default, you are logged in as an Administrator (almost root) which by the way is a huge security risk. That's why you don't have to bother yourself with file permissions, but if you create a non-privileged account you will have to use ACLs in Windows NTFS partisions too if you want to create a shared folder (folder is the Windows equivalent of a directory :evil: :)).

I agree with the diminished security of Windows. However, we are talking about a Local Shared folder between local users of the same pc. No network sharing whatsoever. I don't see a need for this much security when the goal is to share the folder. Obviously if it is a Shared folder, don't keep anything in it that you don't want shared/unsecure.

---

### Post by Morbius1 on 2010-03-20
> an OS that is supposed to be specifically designed as an "Open source alternative to Windows and Office".I was not aware that was the goal of linux. I always thought that the main goal of linux was world domination of the Server market :P

---

### Post by kichigai_dave on 2010-03-20
> **Morbius1 said:**
> I was not aware that was the goal of linux. I always thought that the main goal of linux was world domination of the Server market :P

I'm talking about Ubuntu specifically. On the main page it states exactly that, right under "What is Ubuntu". 

I've delved into several Linux OS's in the past and have personally used some at home. This latest adventure was due to many of my friends and family constantly dealing with virus and spyware issues. Actually was kind of selfish on my part, as I was always the one they called to fix their pc's. I swear I need one of those T-shirs: "No, I will not fix your computer!". 

I was doing some research on what are the best Linux OS's that are designed for people wanting to migrate from Windows and that are the easiest to do so. Almost all recommendations I received were for either Fedora or Ubuntu, most saying that these two were pretty much set up for that. I decided on Ubuntu as it seemed to be the more finished OS's and not as many bugs in the non-beta releases. All my friends and family do is surf the internet, play some games (mostly flash based), email, and store/share thier media. 

So far, the only issue I've run into is the sharing of the media between local users on the same pc. That is what this whole thread has been trying to figure out. All I want is a reliable, easy to set up method to share media (music, videos, pics, etc...) between local users. That way I don't have to physically support my friends and family as I've been doing so with Windows.  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

