---
title: "Getting an application packaged"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by alexcckll on 2009-04-08
OK - I'm part of the audiovisual team at my local church, we use EasyWorship to display lyrics etc during services.

EasyWorship is currently a Win32 application, we use it on XP/Vista on the church kit.

Suppose that the manufacturers (Softouch Inc) released a version of EasyWorship for Linux in the future?  I would not feel comfortable installing *anything* except via Synaptic or apt-get.. and would not feel comfortable straying from Canonical's repositories. 

The application is likely to be commercial (currently a licenced app that one buys).

I run a preinstalled instance of Ubuntu 8.04LTS on a Lenovo Thinkpad - and am pretty new to Linux.. so would not know how to troubleshoot issues that came out of installing unknown or untrusted code.

I am also used to corporate IT environments, where software goes through an AppAdd process (packaged for target builds).

My question is... if said putative Linux version of EasyWorship was released, how would I go about requesting the application be packaged for Ubuntu, so that eventually I could apt-get the application, buy and enter a licence key etc?

---

### Post by Rocket2DMn on 2009-04-08
I moved your post to a new thread.

You typically only find FOSS (Free and Open Source Software) in the Ubuntu repositories.  There are a few exceptions in the multiverse repository which aren't entirely free-as-in-freedom but they are free-as-in-beer (you don't have to pay for them).  For programs that are purchased from a third party vendor, which is what EasyWorship sounds like, you would have to get a linux installer from the vendor.  It would not be made available in Ubuntu repositories.

If they were to release a linux version, the chances are it would be closed-source (not open source), so they would give you a binary installer.  All you could do is talk to the vendor to see if or request that that program be compatible with Ubuntu and other Debian-based linux distributions.

---

### Post by alexcckll on 2009-04-09
Umm - I understood that some commercial software such as VMWare Desktop, Citrix ICA clients etc are in some other repository - I believe it's called the Partner repo?

EG  - stuff mentioned here - [http://www.ubuntu.com/products/softwarecatalogue](http://www.ubuntu.com/products/softwarecatalogue)  - By no stretch of the imagination could you call IBM DB2 "open".

How would I go about initiating the requests so that Easyworship could be AppAdded to the Ubuntu platform?

---

### Post by Rocket2DMn on 2009-04-09
I'm not entirely sure on how Partner Repositories work, but this is also an option.  However, this requires more coordination between Ubuntu's parent company, Canonical, and the third party vendor in question.  The software has to be tested and approved for use on an Ubuntu system and are approved for support by the vendor.

You would need to go through the appropriate contact channels with the company that supports EasyWorship - you may need to ask their help desk for details about that.  Hopefully somebody there knows what it is that you are talking about, but no guarantees.

---

### Post by alexcckll on 2009-04-10
Thanks for that; I'd really be looking to use software that was certified for the OS.  So... next port of call would be to wait until the Linux version became available.. then formally contact both the vendor and Canonical?

---

### Post by k3lt01 on 2009-04-10
Or you could just use Lyricue which is in the repositories already. :guitar:

---

### Post by alexcckll on 2009-04-10
Slight problem.  Cross-compatibility; church runs EW on Windows.  Running Easyworship on my Ubuntu instance (preinstalled, remember) would then enable me to prepare .ews schedule files at home and either email them or whack 'em on a USB thumbdrive.

Same as the old days of WordPerfect on DOS/Win/UNIX....

---

### Post by k3lt01 on 2009-04-10
Another option is you prepare the aformentioned file and use your laptop to put it up on the screen as a trial. You could save your church money in the various license fees (my guess is you also have a Virus scanner etc which also have yearly subscription fees) and introduce them to an OS which is free from all of that.

---

### Post by alexcckll on 2009-04-10
Slight problem - it doesn't do integrated Powerpoint/OpenOffice import-and-present-from-schedule yet, or integrated DVD playback... from the schedule file.  Different Bible versions (Message, NIV, KJV, NASB etc); CCLI integration; integrated video playback from WITHIN the app.

And the 2nd monitor stuff isn't easy for a relative beginner to Linux.. so it was more being able to work with an already-installed base.

The advantage it DOES have is proper separation from the database substrate..

---

### Post by alexcckll on 2009-05-04
OK - I did see some app that appears to be GPL3 licenced...

Get_IPlayer - goes off, grabs and reformats IPlayer streams for alternate players and doesn't require mucking about with Adobe AIR - which would preclude me until 2012 (staying LTS-LTS as that's what my vendor certifies)..

Available here - [http://linuxcentre.net/getiplayer/](http://linuxcentre.net/getiplayer/)

I'm not about to risk breaking my machine by installing independent apps.. would prefer as a relatively new user ot just go get them from the repos.

As I'm not sure about the Enhancement process - was it best for me to raise the support request... [https://answers.edge.launchpad.net/ubuntu/+question/69845](https://answers.edge.launchpad.net/ubuntu/+question/69845) ?

Thanks, 

Alex

---

### Post by Taiwo on 2009-05-05
Can anyone please show me how to install Lyricue on Jaunty. Thanks

---

### Post by SentientFluid on 2009-05-05
> **alexcckll said:**
> OK - I did see some app that appears to be GPL3 licenced...

Get_IPlayer - goes off, grabs and reformats IPlayer streams for alternate players and doesn't require mucking about with Adobe AIR - which would preclude me until 2012 (staying LTS-LTS as that's what my vendor certifies)..

Available here - [http://linuxcentre.net/getiplayer/](http://linuxcentre.net/getiplayer/)

I'm not about to risk breaking my machine by installing independent apps.. would prefer as a relatively new user ot just go get them from the repos.

As I'm not sure about the Enhancement process - was it best for me to raise the support request... [https://answers.edge.launchpad.net/ubuntu/+question/69845](https://answers.edge.launchpad.net/ubuntu/+question/69845) ?

Thanks, 

Alex

Have you tested running it in Wine?

---

### Post by alexcckll on 2009-05-05
> **SentientFluid said:**
> Have you tested running it in Wine?
It has a .deb and source available.  hence asking Release Management to evaluate it to be AppAdded.

I'm not willing to take the risk of installing code outside the repos.. I don't know if it'll break my machine.

---

### Post by SentientFluid on 2009-05-05
> **alexcckll said:**
> It has a .deb and source available.  hence asking Release Management to evaluate it to be AppAdded.

I'm not willing to take the risk of installing code outside the repos.. I don't know if it'll break my machine.

As a general rule of thumb, there's nothing wrong with adding software from outside the Ubuntu repositories *so long as you trust the source.*  If you don't trust the source then don't install it.  My opinion is that if it's a commercially available program that you've used and liked on another system, then chances are the Linux port is just as good.  Assuming the company is the one who created the port, that is.

---

### Post by alexcckll on 2009-05-06
Yeah - except I was not enquiring about EasyWorship.  The query is regarding this Get_Iplayer application.

I AM NOT A DEVELOPER.  Therefore, I wouldn't really know what to look for in order to make sure it's safe to install etc.  Instead - I trust Release Management to handle it.

Is a basic end-user the correct person to raise an Enhancement Request in order to get an app out there in the wild evaluated for Ubuntu inclusion and release?  Or should I save up the £250 for a year's paid support, then phone Canonical?

---

