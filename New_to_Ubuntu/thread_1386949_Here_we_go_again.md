---
title: "Here we go again"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by iggy pop on 2010-01-21
I like using Ubuntu 9.10 but getting really fed up now. Having failed miserably to install the latest version of the Opera browser 10.10 despite all the  help from forum members. I tried this time to install Google's browser "Chrome"  and once again failed miserably.

I downloaded the .deb package, opened a terminal and typed: cd Desktop
I then typed: "ls" to make sure the package was there and finally i typed:

sudo dpkg -i google-chrome-beta_current_i386.deb and failed 

I think it about time i ditched Ubuntu 9.10

---

### Post by lotharmat on 2010-01-21
Why not just double click on the deb?

---

### Post by Sir Jasper on 2010-01-21
Hi,

All my downloads are to my Desktop. After downloading all Debian packages [thus far], I have double left-clicked on the file and installations have been automatic and perfect.

My regards

PS If that fails, post back as it is an almost 100% certainty someone will help you.

---

### Post by snowpine on 2010-01-21
> **iggy pop said:**
> I like using Ubuntu 9.10 but getting really fed up now. Having failed miserably to install the latest version of the Opera browser 10.10 despite all the  help from forum members. I tried this time to install Google's browser "Chrome"  and once again failed miserably.

I downloaded the .deb package, opened a terminal and typed: cd Desktop
I then typed: "ls" to make sure the package was there and finally i typed:

sudo dpkg -i google-chrome-beta_current_i386.deb and failed 

I think it about time i ditched Ubuntu 9.10

How about instead of just saying "it failed" you copy & paste the actual error message so we can help?

---

### Post by elliotn on 2010-01-21
> **iggy pop said:**
> I like using Ubuntu 9.10 but getting really fed up now. Having failed miserably to install the latest version of the Opera browser 10.10 despite all the  help from forum members. I tried this time to install Google's browser "Chrome"  and once again failed miserably.

I downloaded the .deb package, opened a terminal and typed: cd Desktop
I then typed: "ls" to make sure the package was there and finally i typed:

sudo dpkg -i google-chrome-beta_current_i386.deb and failed 

Why suffer urself, double click the deb and it would tell u which dependencies are missing and just download then and ur set

---

### Post by iggy pop on 2010-01-21
I have also got my downloads to go to the Desktop. I have also double left-clicked on the .deb package but with no success. When i have double left-clicked on a .deb package a little white disk appears with three black dots racing around inside the white disk and after awhile it disappears and then nothing?

I really do like using Ubuntu 9.10 but if this is going to continually happen i might as well get rid of Ubuntu now.

Thanks for the reply

---

### Post by snowpine on 2010-01-21
> **iggy pop said:**
> I have also got my downloads to go to the Desktop. I have also double left-clicked on the .deb package but with no success. When i have double left-clicked on a .deb package a little white disk appears with three black dots racing around inside the white disk and after awhile it disappears and then nothing?

I really do like using Ubuntu 9.10 but if this is going to continually happen i might as well get rid of Ubuntu now.

Thanks for the reply

If you run the command from the terminal, you will get detailed error messages that you can use to debug. Since you aren't sharing these errors with us, I can't really help. :)

---

### Post by blackened on 2010-01-21
> **iggy pop said:**
> ...I really do like using Ubuntu 9.10 but if this is going to continually happen i might as well get rid of Ubuntu now.

Thanks for the reply

Echoing what snowpine has already said, it's impossible for us to offer anything but commiseration if you won't post the terminal output that resulted from you using dpkg. Re-enter the command exactly as you did before, but this time cut and paste the result into your next post, preferably wrapped in code tags for readability.

---

### Post by iggy pop on 2010-01-21
Went back to the terminal and typed in exactly what i did earlier and it installed? I now have Google Chrome. Thanks for all the replies

---

### Post by steveneddy on 2010-01-21
> **iggy pop said:**
> I like using Ubuntu 9.10 but getting really fed up now. Having failed miserably to install the latest version of the Opera browser 10.10 despite all the  help from forum members. I tried this time to install Google's browser "Chrome"  and once again failed miserably.

I downloaded the .deb package, opened a terminal and typed: cd Desktop
I then typed: "ls" to make sure the package was there and finally i typed:

sudo dpkg -i google-chrome-beta_current_i386.deb and failed 

I think it about time i ditched Ubuntu 9.10

Are you running a 32 bit or 64 bit version of Ubuntu?

The file you are trying to install are 32 bit files.

Here is an easy way to install Chrome that involves some terminal work, but it is easy, just copy and past the commands and follow the instructions.

This will take care of the dependencies, update automatically when update manager runs and get you to the end of this quest.

Just a side note:

Stop giving up so easily. You are in a new computing environment and things are different here than in the Windows world.

If you just don't get it and want to go back to Windows, that is your choice. Using is a choice that we all have made and the learning curve will be steep at first.

Take a deep breath, relax and just go slow. Post a thread asking for help without telling us that you might as well quit will get a lot of flamers telling you to just quit.

I will post the instructions here for you and others to get Chrome installed the easy way:

We want to open a specific tect file. Open a terminal and copy and past these commands in there:

```
sudo gedit /etc/apt/sources.list
```

you must enter your password because these are "administrator" files, or root files.

You are using karmic, so scroll to the bottom of that text file and enter these two lines:

again, just copy and paste:

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
```

Save and exit the file.

Now we need a key to authenticate your PC to the server. In terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
```

When that finishes do this in terminal:

```
sudo apt-get update
```

this will update the package manager in Ubuntu.

then finally

```
sudo apt-get install chromium-browser
```

You will find it installed and the launcher will be in

Applications --> Internet --> Chrome

Good luck and post back here if you have any issues.

These instructions were copied from this web site:

[http://www.ubuntugeek.com/install-chromium-google-chrome-web-browser-in-ubuntu.html](http://www.ubuntugeek.com/install-chromium-google-chrome-web-browser-in-ubuntu.html)

Which I found using this Google search:

[http://www.google.com/search?hl=en&source=hp&q=google+chrome+ppa&aq=f&aql=&aqi=g-p3g7&oq=](http://www.google.com/search?hl=en&source=hp&q=google+chrome+ppa&aq=f&aql=&aqi=g-p3g7&oq=)
:popcorn:

---

### Post by steveneddy on 2010-01-21
> **iggy pop said:**
> Went back to the terminal and typed in exactly what i did earlier and it installed? I now have Google Chrome. Thanks for all the replies

I see it worked for you already performing the previous command.

That's great.

Please make note of the links in my sig for further instructions on many different subjects.

Glad it worked for you!

---

### Post by Sir Jasper on 2010-01-21
Hi again,

Excellent news. I have spent lots of time tweaking (Xubuntu in my case) and installing programs and gathering data and I have made a quite few mistakes, but if clones or images (and possibly backups as well) are taken then mistakes may be easily rectified.

My regards

---

### Post by Dougie187 on 2010-01-21
Glad it's working.

---

