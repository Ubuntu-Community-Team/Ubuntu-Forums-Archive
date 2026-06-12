---
title: "make files accessible (should be same in ubuntu)"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by libihero on 2011-04-26
im a noob when it comes to these things. so i tried fedora 15 with gnome 3, and i have to partitions, one is a home partition and the other is for the os. well i scrapped fedora and now i wanted to try the kubuntu 11.04 with kde 4.6. the problem is that now when i erased the fedora and put kubuntu in its place, running kubuntu doesnt allow me to access or edit a lot of the files in my home partition. also, when i try to put some in the trash, it says "name trash already exsits, do you want to give it another name" but it wont even let me give it another name. is there something quick i can run that can give me access to editing all of those files again?

---

### Post by snowpine on 2011-04-26
The files are owned by your Fedora user. You can use "chown" (type "man chown" for more details) but be very careful! File permissions are very important to a Linux system.

In the future you can use a different username when installing a new distro, then copy any necessary files over from the old user's folder.

---

### Post by libihero on 2011-04-26
gahh fedora! wat command can i do to give permission to all files in my home folder, and then i'll just copy the documents out in a reinstall

---

### Post by snowpine on 2011-04-26
Like I said, use 'chown' to CHange OWNership of a file or files.

---

### Post by hodge3153 on 2011-04-26
> **libihero said:**
> gahh fedora! wat command can i do to give permission to all files in my home folder, and then i'll just copy the documents out in a reinstall

Fedora, by default starts user id's at 1000 while Ubuntu starts user id's at 500.  The files are stored with the user id not the actual user name.  Because of this, Ubuntu does not recognise the files as being owned by you.  Now assume you user-name is matt ( please substitute your real user-name here), use the following command: 
sudo chown -R matt:matt  /home/matt/

Now as snowpine suggested, man chown is really the best place to start.  Before you perform the above command type man chown and convince yourself I know what I am saying.  You know Turst but verify ;-)

---

### Post by coffeecat on 2011-04-26
> **hodge3153 said:**
> Fedora, by default starts user id's at 1000 while Ubuntu starts user id's at 500.

Actually, it's the other way round but, yes, this is the basis of the OP's problem. :)

---

### Post by libihero on 2011-04-27
thanks!

---

### Post by gregorthebigmac on 2011-05-05
I know the issue has been resolved, but I think some further clarification would help anyone else having similar issues, as I was one of them until an hour ago. I didn't realize you had to run chmod from a parent directory that you actually have read/write access to, so I was trying to run chmod on the actual folder in question, which wasn't working.

But after running this in the terminal from the parent directory, it worked fine:

```
sudo chmod 777 -R <directory>
```

**Edit: Be wary of using this, though, as I have just been informed this will actually give read/write access to all of the files to everyone, so unless you're using this as a quick backup and wipe of your system, I wouldn't recommend it! :)

---

