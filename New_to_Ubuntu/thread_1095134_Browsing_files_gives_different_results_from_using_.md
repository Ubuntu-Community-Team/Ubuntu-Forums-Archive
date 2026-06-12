---
title: "Browsing files gives different results from using the browse button..."
date: 2009-03-13
forum: New to Ubuntu
---

### Post by triplenine on 2009-03-13
...on websites. Weird. So I was getting some pictures off of my camera card to post to a blog. I was changing some names on the card, then dropped them to my "Pictures" folder. When I tried to browse from the website applet to select the pictures for uploading I could not see them in the browser window. I thought it might be the site but the same thing occurred on another as well.

I have noticed similar activities with other newly created files as well. When files are renamed or moved are there permission issues that I should be a ware of that will cause applications not to recognize the file? While I understand that some files are protected more so in *nix than in other OSes, I feel like I do not have full control over my basic media files.

Let me know if you have any ideas or can educate me on how newly named files are handled. This is affecting my work and I can't have that.
Ubuntu 8.04
using integrated card reader on a Dell mini 9
-999

---

### Post by pytheas22 on 2009-03-13
How did you copy the files onto your hard drive originally?  Depending on how you did it, there could be permissions issues, but unless the command-line was involved, that's unlikely.

You can check the permissions of files in Ubuntu by right-clicking on them, selecting 'Properties' and navigating to the "Permissions" tab.  What does it say about the permissions on the files you're trying to copy?

---

### Post by triplenine on 2009-03-13
The moving was done using cut and paste. The permissions were read and write for me and I tried setting them to read and write for root and everyone else and that didn't change anything...

---

### Post by quinnten83 on 2009-03-13
i've noticed this as well, on my Xubuntu machine.
This happens when I move files on my main desktop to a nfs share that is on the Xubuntu machine. i can't see the file on Xubuntu untill I restart.
I don't know what causes it, and quite frankly I thought I was just going insane.

---

### Post by pytheas22 on 2009-03-13
> The moving was done using cut and paste. The permissions were read and write for me and I tried setting them to read and write for root and everyone else and that didn't change anything...

That's strange.  If you have read and write permissions, the files should definitely be visible.  Is the problem resolved after a reboot, as the poster above suggests?  It's also possible that this is due to a weird issue with Firefox; you might have better luck using a different browser, like Konqueror, which you can install by typing:
```

sudo apt-get install konqueror
```

and then launch from the Applications>Internet menu.

Also, which websites in particular are giving you problems?  I'd be interested to see if the problems occur for me as well.

---

### Post by triplenine on 2009-04-02
Sorry about taking so long to get back to this. I had to use my windows machine to get this done...

So it does not help to reboot the machine. I was using shrinkpictures.com and a blog backend that I use to administer my entries. I will be working again tonight so I will be able to get a better specific description.

It seems to happen anytime I browse from an app. I noticed something similar when using VLC. I browsed through the VLC "Open Playlist" command and I cannot see the playlists that I just created, yet I can see them fine using the File Browser.

Confusing. Is there something that needs to be done to give applications permissions to view the file system?

---

### Post by pytheas22 on 2009-04-02
It seems very strange to me that none of your applications can see the files (and it's all files now, not just pictures?  Or only some files?).  Could you post the output of this command so I can exactly see what the permissions look like on your pictures:
```

ls -l ~/Pictures
```

(That command assumes your images are in a folder at /home/username/Pictures; if the path is different, please change the command appropriately.)

---

### Post by triplenine on 2009-04-03
I would agree that it is strange...
Here is the output:
```

-rwx------ 1 chris root 691792 2009-04-02 21:44 SANY0926.JPG
-rwx------ 1 chris root 640068 2009-04-02 21:46 SANY0927.JPG
-rwx------ 1 chris root 683936 2009-04-02 22:02 SANY0928.JPG
-rwx------ 1 chris root 585808 2009-04-02 22:03 SANY0929.JPG
-rwx------ 1 chris root 614172 2009-04-02 22:03 SANY0930.JPG
-rwx------ 1 chris root 957572 2009-04-02 22:03 SANY0931.JPG
-rwx------ 1 chris root 861080 2009-04-02 22:04 SANY0932.JPG
-rwx------ 1 chris root 618220 2009-04-02 22:04 SANY0933.JPG
-rwx------ 1 chris root 970992 2009-04-02 22:05 SANY0934.JPG

```

Let me know what you think. I have tried from the media card and from copies that I placed in the Pictures folder. Does the "Browse" option in an app require different permissions from the standard user permissions?

---

### Post by pytheas22 on 2009-04-03
That output is interesting.  It's weird that the files are owned by you (assuming your account name is 'chris'), but belong to the group 'root'--they should belong to 'chris'.  I don't know how they ended up that way (probably related to the way they were copied off the digital camera), but try running these commands to change them to your group and see if it makes a difference:
```

chown -R chris:chris /home/chris/Pictures
```

---

