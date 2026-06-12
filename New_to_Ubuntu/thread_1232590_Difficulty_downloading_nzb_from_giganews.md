---
title: "Difficulty downloading nzb from giganews"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Trinity1976 on 2009-08-05
Hi,

On Windows I've been using Newzbin to download from Giganews. Have been trying to find something to do the job in Ubuntu.

Tried Lottanzb but had no joy so tried sabnzbdplus. The application places the file in the queue but doesn't download. Looking at the error messages it's telling me there's a problem with the username or password.

This message sometimes comes up when I run over my usage limit, so I tried to log onto my account at [www.giganews.com](www.giganews.com) with my username and password, and it said the details were not valid. I got the password resent, checked it, tried again and still no joy.

So I went back into Windows and tried the same thing and it worked fine. So there is no problem with the username and password, but it won't let me log on while in Ubuntu, even though all I'm doing is going to the Giganews website in Firefox.

I assume this error is why Lottanzb won't work either, although it doesn't actually give a message, just gets as far as queuing the files, then stops.

Any ideas?

---

### Post by Mark Phelps on 2009-08-08
If you're asking for an NNTP news reader that works in Linux, check out PAN.  It's in the repos.

It looks and works a lot like the previous version of Forte's Agent Newsreader.

---

### Post by terry_gardener on 2009-08-08
i currently use hellanzb for my giganews account 
it is easy to setup 
i have attached the install script.
make it executable right click properties permissions tab and tick allow to be run as executable field.
double click icon and run in terminal 
6 options will appear 
click option 1 and press enter and accept the install of all the packages.
when finished double click the icon again and select option 2 and do the same accept to install packages. 
again double click the icon and select the option 3 and select to create config file. 
find the server and enter giganews details.
change the username and password to yours.
and change the connections to amount you have mine is 10. 
click save 
thats is 
to run it type hellanzb 
any nzb files placed in /home/username/.hellanzb/nzb/deamon.queue
will be downloaded...

---

### Post by terry_gardener on 2009-08-08
example helanzb config file attached.
just change the username and password section

---

### Post by themusicalduck on 2009-08-08
I use klibido, it works fine and is pretty easy to use.

---

