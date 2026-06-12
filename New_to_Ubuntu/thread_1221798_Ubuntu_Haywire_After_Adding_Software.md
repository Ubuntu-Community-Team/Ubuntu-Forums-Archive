---
title: "Ubuntu Haywire After Adding Software"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by lorenbr on 2009-07-24
I recently added a couple of pieces of software to my computer, running Hardy Heron, and after restarting the computer, there were some remarkable changes to my system.

The software I added was Apache, PHP5, MySQL, Kannel ([www.kannel.org](www.kannel.org), a program for "for serving... short messages [SMS] and pushing WAP service indications"), and PlaySMS ([http://code.google.com/p/ya-playsms/](http://code.google.com/p/ya-playsms/), a program for "various services such as an SMS gateway, personal messaging systems").  I also ran the standard software updates.

When I restarted my computer, some very strange things changed:

All my available hard disk space had disappeared.  My computer now thinks it has 0 bytes available, even after I created about 700 megabytes of new space.  Before the install I had over 4 gigabytes of available disk space.

All the program folders (e.g. Games, Office, Audio and Video, etc.) had disappeared from my drop down menu.  Now I only have "Places," "System," and "Quit" on my drop down menu.  This means I can't run any programs that weren't already added to my quick launcher.

The bookmarks bar has disappeared from my Firefox.  In fact all the bookmarks have disappeared.  My bookmark folder has just become empty.  And my firefox is behaving strangely in other ways.  I couldn't log onto this forum because it wouldn't register my click on the "login" button.

I am sure there are more strange symptoms that I haven't found yet.

I am sure this is a result of my novice messing around with database and web server applications.  I tried to fix it by removing the things I had installed, but I wasn't able to uninstall playsms.  I kept getting error messages from MySQL.

I would really appreciate some guidance here.

---

### Post by jrothwell97 on 2009-07-24
My first suggestion would be to start by opening up a terminal and running

```
sudo apt-get clean
```

It sounds like package files may be eating all of your disk space, and this command clears all the redundant package files from the system (e.g. packages that have already been installed). I may be entirely wrong, but it's worth a shot.

---

### Post by lorenbr on 2009-07-24
Thanks jrothwell97,

I've done everything I can think of with apt-get.  I ran apt-get clean and apt-get autoclean, to no avail.  Since the first post, I've succeeded in removing Kannel (I think - I got another error message that I ignored) and PlaySMS, but it hasn't really helped.  I now have 18.7 megabytes of harddrive space, but my main menu still lacks applications.  And I cannot open Preference > Main Menu to fix that either.

Any other ideas?

---

### Post by lorenbr on 2009-07-24
Since my last post, most of the problems have cleared up.  I honestly cannot say why, but I'm now able to recover some of my hard drive space by deleting extra files, and my Firefox bookmarks have returned.  However, I am still not able to get to any Applications.  Either from the "Main Menu" or the "Menu Bar."  And I am still not able to open Preferences > Main Menu to add Applications to the Menu Bar manually.  I am attempting to upgrade to Intrepid in hopes that this will solve my problem, but if anyone can tell me an easier way to do return my menu bar to normal, it would be much appreciated.

Thanks

---

