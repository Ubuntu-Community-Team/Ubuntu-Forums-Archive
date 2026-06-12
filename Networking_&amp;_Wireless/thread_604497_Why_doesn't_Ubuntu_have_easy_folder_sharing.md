---
title: "Why doesn't Ubuntu have easy folder sharing?"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by altu on 2007-11-06
Ok, we all know how to share folders in windows, no?

Right click - Share folder, you pick if you want it to be read only or not and that's finished. 

Why can't Ubuntu have something like this? Why do we have to fiddle with smb.conf every time? I'm not referring to big networks, this is just what I want for my small network at home.

I mean I have never seen a linux distro that manages this.  A few years ago I had to read a book on SAMBA just to learn how to share folders!!!! This is inconceivable.

If I were a complete newbie and I sumbled upon this problem I would be quite disappointed. 

And to make something clear: I'm all for security but I do not think things should be so complicated for my 3 computer network at home.

---

### Post by AndyCooll on 2007-11-06
Hmmm ...well I don't usually need to share folders in the way that you mention. However, I thought there  already was something for this (System > Preferences > Sharing, or something like that. I'm not at my Linux box at the moment). And I'm sure I've seen a "sharing" option when right clicking a folder and selecting preferences there was then the option to share. Perhaps that was just for folders in my home directory. As I mentioned I'm not at my Linux box at the moment, so feel free to correct me if I'm wrong.

:cool:

---

### Post by edm1 on 2007-11-06
> **altu said:**
> Ok, we all know how to share folders in windows, no?
Right click - Share folder, you pick if you want it to be read only or not and that's finished.

Have you tried doing exactly this in ubuntu?

---

### Post by netztier on 2007-11-06
> **altu said:**
> 
And to make something clear: I'm all for security but I do not think things should be so complicated for my 3 computer network at home.

Beg your pardon, sir (or madam, pick whatever applies...)

What is *not* easy about right-klicking a folder in your home directory, selecting "Share folder ..." giving your password - since this function needs admin rights - and then select the protocol to share your folder with?

Alternative: System -> Administration -> Shared Foldes and use the "add..." button?

best regards

Marc


PS: come to think of it - probably these features only become available once Samba's installed - I'd need to verifiy this. Granted, that might take a bit of tweaking of smb.conf - just as configuring your workgroup's name takes some digging in Windoze's Control Panel, too. But in that case, your rant is misplaced, as the functions you want are actually there. You should rant against samba's default configuration, not at the desktop environment's missing "Share Folder..." context menu.

---

### Post by timcredible on 2007-11-06
> **altu said:**
> Ok, we all know how to share folders in windows, no?

Right click - Share folder, you pick if you want it to be read only or not and that's finished. 


works the same way in linux.  you didn't try this before posting?

---

### Post by de_valentin on 2007-11-06
If it only was this easy. I did try the right-click on a folder share etc...and it does appear at the system> administration>shared folders. But that doesn't mean that it is visible from any other desktop on the network not even another gutsy. Even worse the entire desktop is not found on the network. 
Well there still is a way for me to share files and I'll tell you how it goes.

install xp on virtualbox using this [http://ubuntuforums.org/showthread.php?t=433359&highlight=install+virtualbox](http://ubuntuforums.org/showthread.php?t=433359&highlight=install+virtualbox)

then enable the file-sharing in xp and et-voila when xp is running in virtualbox it appears on every computer in the network as well as on the machine running the virtualbox. 

Off course I can acces all window shares on other desktops even without using vbox. So its kinda one way which, needless to say, should statistically mean half of all traffic:confused:

Edit: Oh and believe me i tried several howto's

---

### Post by maybeway36 on 2007-11-06
The problem is that most users don't need security, but they have no way of settigns the level to "share" and setting up an anonymous read/write folder without editing smb.conf.

---

### Post by altu on 2007-11-06
> **netztier said:**
> 

What is *not* easy about right-klicking a folder in your home directory, selecting "Share folder ..." giving your password - since this function needs admin rights - and then select the protocol to share your folder with?

... 

You should rant against samba's default configuration, not at the desktop environment's missing "Share Folder..." context menu.

Well I did just that. I installed Gusty clean. I right clicked on a folder (not in my home but a folder that I had created on a separate empty partition). I gave my password. A popup came on asking me to install SAMBA then a window opened with the option to share that folder. I chose SMB and read-only. OK. That was all. 

Result?

Computer is visible in Network Neighbourhood  but keeps aking me for username and password!!! I do not want to use a username and password. It is my problem if I don't care about security!!! 

It is true that SAMBA has the defaults this way and it is not Ubuntu's fault but **come on they should give you the option!!!** If the easiest most user frienly linux ever can't do this no wonder people who have not used linux before find it difficult. Ubuntu is not Arch or Slackware or Debian. Ubuntu should just work.

---

### Post by FreewheelinFrank on 2007-11-08
I've just spent the morning trying to figure out how to share files over a network in Ubuntu. 

I came across a lot of technical stuff about NFS, SSH, Samba.

Then I found this page.

Ah ha! Right click a folder and click share!

I had another Google for share folders in Ubuntu and found this:

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

I followed the guide and now I seem to be able to share files to and from Ubuntu machines across a network.

I also came across this guide:

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

It mentions editing smb.conf and setting up a samba password, which I didn't do.

When is it necessary too do that stuff? Ubuntu to Ubuntu sharing seems to be working without doing it. Is that necessary to share with Windows?

Is it better to use NFS for sharing between computers running Ubuntu? Is there a simple guide to setting up NFS sharing?

---

### Post by gigaferz on 2007-11-21
try that

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

samba is for a *nix computer in a windows network, nfs is supposed to be the *nix way to share files...

the sharing folders option IS there but , most likely will not work...

---

### Post by jivabill on 2007-11-21
Well, I read thru everything, tried the tutorial.  I am still stuck.  I agree 100% with the poster's critical remarks about the lack of good documentation for sharing.

I seem to have the typical problem:  I had a Win98SE machine and an XP Pro machine networked.  Worked absolutely perfectly.

Then after XP Pro committed suicide couple weeks ago (cpu useage error in registry) I was so pissed I loaded Gutsy on the machine.  I like Ubuntu, and mostly I like the docs.  But there is a gaping hole here in the area of networking.

I have the typical problem:  I set up the network by simply installing samba.  After that I could see and manipulate the files marked for sharing on the Win98SE machine.  BUT I could not see the folders marked for sharing on the Ubuntu machine.  Can't get past the request for a password.  More correctly, I can't figure out HOW to go about trying to see them.  So I did what was done on the 98 to XP system:  I mapped a network drive to make the connection to a sub folder that has all my stuff in the home folder on Ubuntu.

But, everytime I try to map the drive, it asks for a password.  I put in the password that I set up in samba configuration and I am told that the password is not correct.  So, totally stuck.  Works one way, don't work the other.  NOTHING I have found and I have spent a lot time looking has helped.

Since my background is 25 years in Mainframes and I was in charge of Standards and Docs in several big installations, I see a lack of proper docs here.

What to do?  M$oft docs are obtuse.  Ubuntu docs on the subject are non existent.  Too bad indeed.
Bill

---

