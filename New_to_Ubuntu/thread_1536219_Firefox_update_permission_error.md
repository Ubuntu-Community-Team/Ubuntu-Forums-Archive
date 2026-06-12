---
title: "Firefox update permission error"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by blues2use on 2010-07-21
Running 10.4, Linux ubuntu 2.6.32-23-generic...

I received an update notification on the desktop about the update to 3.6.7.

I clicked on Help/Check for Updates in Firefox and received this error msg:

[IMG]http://i767.photobucket.com/albums/xx315/blues2use/Misc/Screenshot-SoftwareUpdate.jpg[/IMG]

I'm not sure what step(s) I will need to take to get the update installed.

Any/all suggestions would be most appreciated.

Thanks

---

### Post by lovinglinux on 2010-07-22
Are you using an account with administrative privileges?

---

### Post by blues2use on 2010-07-22
> **lovinglinux said:**
> Are you using an account with administrative privileges?

I'd never had this error before so I ran "**sudo firefox**" from a terminal and performed the update and it worked as expected. 

Still wondering why I had to do it like this...

Thanks for the help

---

### Post by lovinglinux on 2010-07-22
> **blues2use said:**
> I'd never had this error before so I ran "**sudo firefox**" from a terminal and performed the update and it worked as expected. 

Still wondering why I had to do it like this...

Thanks for the help

You should NEVER run Firefox with sudo. Now your profile folder ownership has changed to root and you will have all sorts of troubles. To fix that, see the first item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

If you ever need to run Firefox with administrative rights, which I don't see a good reason to, then you should use gksudo instead, which is the correct method for running graphical interfaces as root.

Now I realized the update warning you received was from Firefox, not the package manager.  I guess I was sleepy when I read your post. The correct way of updating Firefox is using the package manager, not the built-in updater feature of Firefox, which is disabled by default.

So, I recommend that you re-install firefox. First make sure you have the latest software sources. To do that run the following commands:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```

---

### Post by snowpine on 2010-07-22
You should use the Ubuntu Update Manager to upgrade all applications on your system (including Firefox). Updating each application individually is the "Windows Way" and is not necessary on a properly-configured Linux system.

---

### Post by oldsoundguy on 2010-07-22
Currently, I just close that update window and go to the help and select check for updates .. and update in that manner.

When 4.0 comes out, it will NOT allow that as things will change (at least, if past builds reflect same) and you will have to use something like the Ubuntuzilla script .. and then run "gksudo firefox &" in terminal to get a version of firefox that will have the update option available.

---

### Post by mcduck on 2010-07-22
> **blues2use said:**
> I'd never had this error before so I ran "**sudo firefox**" from a terminal and performed the update and it worked as expected. 

Still wondering why I had to do it like this...

Thanks for the help

That's because Firefox is installed system-wide, through Ubuntu's own package management, so the default way of updating is is the same as for every other program in Ubuntu, through the Update Manager. (and since it's installed system-wide, any single user shouldn't be able to update it. That's an admin task since it affcts all users of the system)

Had you just waited a day or two for the update to find it's way into Ubuntu's repositories you would have received the new Firefox version as a normal update.

---

### Post by blues2use on 2010-07-22
> **mcduck said:**
> That's because Firefox is installed system-wide, through Ubuntu's own package management, so the default way of updating is is the same as for every other program in Ubuntu, through the Update Manager. (and since it's installed system-wide, any single user shouldn't be able to update it. That's an admin task since it affcts all users of the system)

Had you just waited a day or two for the update to find it's way into Ubuntu's repositories you would have received the new Firefox version as a normal update.

It did, indeed, just show up as I was posting this reply. My other laptop and desktop both updated last night...guess I was just too antsy!

Thanks for the reply

---

