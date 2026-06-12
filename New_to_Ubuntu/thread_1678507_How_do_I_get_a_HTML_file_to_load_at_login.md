---
title: "How do I get a HTML file to load at login?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by In2Blues on 2011-01-30
Since I've finally made the complete break to Linux and am an absolute beginner, I thought this would be the appropriate place to post.

I've searched the forums and Google and found multiple "answers", but nothing seems to work.

I want to automatically load a HTML file (on my hard drive) into Firefox whenever I log into my computer.  I'm running Ubuntu 10.10 and am the only user (for now).

I've read about /etc/rc.local and .profile, tried them both, but can't get the file to load.  I've been reading and trying to understand how to do this for over an hour.  It can't be that hard to get a file to load at login, so I must be missing something.

Any help will be greatly appreciated.

---

### Post by woodcarver on 2011-01-30
I'm not too familiar with Ubuntu either but it seems logical to me that you'd need to load the browser at login and have your HTML file as your homepage. IF it was Windoze, I'd write a batch file and load it on login.

---

### Post by davec64 on 2011-01-30
> **woodcarver said:**
> I'm not too familiar with Ubuntu either but it seems logical to me that you'd need to load the browser at login and have your HTML file as your homepage. IF it was Windoze, I'd write a batch file and load it on login.


What about using **System >> Preferences >> Startup Applications**

Select **Add** and enter **firefox** as the command.

Then if you have the HTML file set as your home page, it should load up.  :)

---

### Post by Joeb454 on 2011-01-30
Add the following to the list in **System > Preferences > Startup Applications**:

*For a local html file*
```
firefox /path/to/file
``` Naturally replacing /path/to/file where appropriate

*For a website*
```
firefox http://ubuntuforums.org
``` Again, replacing as appropriate.

You should be able to use another browser too, by replacing the word firefox for that browser name

---

### Post by In2Blues on 2011-01-31
The batch file would have been my first choice in Windows, too.  I could load Firefox but don't want to change the home page unless I have to.  Thanks for the suggestion.


> **woodcarver said:**
> I'm not too familiar with Ubuntu either but it seems logical to me that you'd need to load the browser at login and have your HTML file as your homepage. IF it was Windoze, I'd write a batch file and load it on login.

---

### Post by In2Blues on 2011-01-31
Like I said above, I don't want to change my homepage unless I have to.  Thanks, though.

> **davec64 said:**
> What about using **System >> Preferences >> Startup Applications**

Select **Add** and enter **firefox** as the command.

Then if you have the HTML file set as your home page, it should load up.  :)

---

### Post by In2Blues on 2011-01-31
Aha!  I knew it was something easy that I was overlooking.  It works perfectly.  Thanks so much.

This forum is fantastic.

I love Linux!!!


> **Joeb454 said:**
> Add the following to the list in **System > Preferences > Startup Applications**:

*For a local html file*
```
firefox /path/to/file
``` Naturally replacing /path/to/file where appropriate

*For a website*
```
firefox http://ubuntuforums.org
``` Again, replacing as appropriate.

You should be able to use another browser too, by replacing the word firefox for that browser name

---

