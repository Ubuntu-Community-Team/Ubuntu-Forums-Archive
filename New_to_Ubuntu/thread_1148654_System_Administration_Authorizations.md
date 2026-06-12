---
title: "System Administration Authorizations"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by marianlibrarian on 2009-05-04
I tried to find an answer in the forums and the documentation but was overwhelmed by the stuff from the forum and could find no mention in the documentation.

I have a public access computer. I have an administrators user id (me) and another user id for patrons. There are very few restrictions that can be set up when creating a new user. So I found under System / Administration / Authorizations what I thought was my solution. It seems to be able to block users from doing stuff. So I selected my patron user and blocked it from using an item called ubuntu tweak. So that only the librarian super user can have access to it.

Well, even though I am looking at it right now. When I am logged in as patron, I can do anything I want. including screw up the desk top by moving and or deleting the menus and panels. 

so far my only solution when they do this is to reinstall unbuntu which takes a long time and I have 5 computers to take care of.

How do I stop a low end user from having the same privileges as an administrative super user???

I know an ignorant nubee as myself is so aggravating but I have been working on this all morning and I guess I can't see the forest for the trees. I really have tried to read through the online documentation and searched the forum and I found fragments of info but nothing that made sense.

Anyway, thanks for your help.

---

### Post by NESFreak on 2009-05-04
> **marianlibrarian said:**
> I tried to find an answer in the forums and the documentation but was overwhelmed by the stuff from the forum and could find no mention in the documentation.

I have a public access computer. I have an administrators user id (me) and another user id for patrons. There are very few restrictions that can be set up when creating a new user. So I found under System / Administration / Authorizations what I thought was my solution. It seems to be able to block users from doing stuff. So I selected my patron user and blocked it from using an item called ubuntu tweak. So that only the librarian super user can have access to it.

Well, even though I am looking at it right now. When I am logged in as patron, I can do anything I want. including screw up the desk top by moving and or deleting the menus and panels. 

so far my only solution when they do this is to reinstall unbuntu which takes a long time and I have 5 computers to take care of.

How do I stop a low end user from having the same privileges as an administrative super user???

I know an ignorant nubee as myself is so aggravating but I have been working on this all morning and I guess I can't see the forest for the trees. I really have tried to read through the online documentation and searched the forum and I found fragments of info but nothing that made sense.

Anyway, thanks for your help.

Have no experience with it myself, but shouldn't this be what you're looking for?
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

---

### Post by llamabr on 2009-05-04
[http://ubuntuforums.org/showthread.php?t=338980&highlight=kiosk+cafe](http://ubuntuforums.org/showthread.php?t=338980&highlight=kiosk+cafe)

---

### Post by Didius Falco on 2009-05-04
One more for the list:

[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)


I hope it helps...

---

### Post by bodhi.zazen on 2009-05-04
> **llamabr said:**
> [http://ubuntuforums.org/showthread.php?t=338980&highlight=kiosk+cafe](http://ubuntuforums.org/showthread.php?t=338980&highlight=kiosk+cafe)

How about a direct link : [http://developer.kde.org/documentation/tutorials/kiosk/index.html](http://developer.kde.org/documentation/tutorials/kiosk/index.html)

KDE Kiosk FTW :)

For gnome see : [http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

---

### Post by marianlibrarian on 2009-05-04
I clicked on help when I had the System Administration Authorizations screen open and the Welcome to the Ubuntu Help Center screen appeared. So I typed in Authorizations in the search field and the following appeared:
> Search results for "authorizations"

Gnome Display Manager Reference Manual
    ... one, they have
            access to the x server authorization directory.  it must be able to
            read an...
Vinagre Manual
    ...acilitates the identification,
                and authorization of computers and users via authentication serv...
Ubuntu Server Guide
    ...e systems depend on ldap for authentication, 
        authorization, mail, etc. it is a good idea to setup a 
        red...
polkit-auth manual page
    Manage authorizations


I clicked on the first link and this appeared:
> 3.3.&#8195;The GDM User

        For security reasons a dedicated user and group id are required for
        proper operation!  The need to be able to write Xauth files is why user
        "nobody" is not appropriate for gdm.
 
        The GDM daemon normally runs as root, as does the slave.  However GDM
        should also have a dedicated user id and a group id which it uses for
        its graphical interfaces such as gdmgreeter and
        gdmlogin.  These are configured via the
        User and Group
        configuration options in the GDM configuration files.  The user and
        group should be created before running "make install".  By
        default GDM assumes the user and the group are called "gdm". 
      
        This userid is used to run the GDM GUI programs required for login.
        All functionality that requires root authority is done by the GDM
        daemon process.  This design ensures that if the GUI programs are
        somehow exploited, only the dedicated user privileges are available.
      
        It should however be noted that the GDM user and group have some
        privileges that make them somewhat dangerous.  For one, they have
        access to the X server authorization directory.  It must be able to
        read and write Xauth keys to <var>/lib/gdm.
        This directory should have root:gdm ownership and 1770 permissions.
        Running "make install" will set this directory to these
        values.  The GDM daemon process will reset this directory to proper
        ownership/permissions if it is somehow not set properly.
      
        The danger is that someone who gains the GDM user/group privileges can
        then connect to any session.  So you should not, under any
        circumstances, make this some user/group which may be easy to get
        access to, such as the user nobody.  Users who
        gain access to the "gdm" user could also modify the Xauth
        keys causing Denial-Of-Service attacks.  Also if a person gains the
        ability to run programs as the user "gdm", it would be
        possible to snoop on running GDM processes, including usernames and
        passwords as they are being typed in.  
      
        Distributions and system administrators using GDM are expected to setup
        the dedicated user properly.  It is recommended that this userid be
        configured to disallow login and to not have a default shell.
        Distributions and system administrators should set up the filesystem to
        ensure that the GDM user does not have read or write access to
        sensitiv


My head just exploded and my brains are on the floor

---

### Post by Didius Falco on 2009-05-04
Don't worry, soon enough you'll be telling your staff ```
sudo get me a sandwich
```

It still doesn't work on my wife though... <G>

---

### Post by pastalavista on 2009-05-04
Have you tried removing the listing in the Applications menu? You could even remove the whole menu and just put icons for allowed apps on the desktop. I know it wouldn't stop a linux-savvy power user but it would cut way down on misuse from the normal users.

edit: Or you could use the 'Guest session' for patrons and that way everything they do will only affect their current session... just some thoughts

---

### Post by marianlibrarian on 2009-05-04
sudo get me a sandwich
:P

I just missed lunch too. 

I just tried to read through some of the documentation in the links above and while my staff is putting my brain back in my head, I'll try and explain what I am trying to do:

I have an "administrative" user which is the librarian and when I set this user up, I made sure that all privileges were checked.

I have a "patron" user which is the patron and when I set this user up, I checked only the privileges like access external storage devices, use audio devices, use CD ROM drives, use floppy drives were the only privileges checked.

My problem is that these "privileges" still allow a patron to have access to moving and or deleting panels on the desktop and other destructive things. 

I thought that "Authorizations" would control this. For example: Opening up the Authorization window and selecting "Ubuntu-Tweak" and then going to the area that has Explicit Authorizations and selecting the Block button and then selecting the Patron user id and seeing it on the list with the word "Blocked by Librarian" beside it --- Does not block this user from this application.

Do I have to shut down or reboot or something for this to take effect? I didn't do that.

---

### Post by marianlibrarian on 2009-05-04
> **pastalavista said:**
> Have you tried removing the listing in the Applications menu? You could even remove the whole menu and just put icons for allowed apps on the desktop. I know it wouldn't stop a linux-savvy power user but it would cut way down on misuse from the normal users.

edit: Or you could use the 'Guest session' for patrons and that way everything they do will only affect their current session... just some thoughts

I did put just the icons for internet, word processor, and spread sheet on the desk top. That made it easy for the patron who just wants to nicely use the computer and go away. We have several patrons (alot actually) who have lost their jobs and if they are fortunate enough to get unemployment they have to log into their account with the state unemployment agency on a weekly basis. These are some very frustrated folks and our computers are different because they are not winders and they just click away on things and then freeze it up and then they go away. And I get to hear it from the next patron and then I get to clean it up as best I can. 

Since just setting up a user with the four privileges I mentioned before is not enough... Please tell me --- What is a "Guest Session"?????????

... The Parental Guide mentioned earler is nice but 99.9% of our users are adults.

---

### Post by Didius Falco on 2009-05-04
If it doesn't seem to be taking effect, reboot.

I think I may have the solution you are looking for though. I was just in another thread with a Kubuntu user, and it made me think of this: KDE has a Kiosk Mode, with what appears to be a very easy gui to administer the system.

Here are a few sites to get you started.

[http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)

[http://jriddell.org/programs/kiosk-article.html](http://jriddell.org/programs/kiosk-article.html)

[http://www.downloadsquad.com/2008/04/04/flipping-the-linux-switch-control-freaks-meet-kde-kiosk/](http://www.downloadsquad.com/2008/04/04/flipping-the-linux-switch-control-freaks-meet-kde-kiosk/)

[http://developer.kde.org/documentation/tutorials/kiosk/index.html](http://developer.kde.org/documentation/tutorials/kiosk/index.html)

Tell your staff to keep that brain-scooper handy! Seriously, this looks like it could do a good bit of what you need. You'll still have to do a bit of file permission settings, etc., but it should ease the pain quite a bit.

If this does turn out to be your solution, I'd recommend that you do a couple of things. These are all just things that occur to me - I am not a SysAdmin, nor am I anywhere near to being a Guru. I might, maybe, be qualified to be the guy that does the dishes for the real Guru's, if they are in a good mood.

That said:

1. Get all your pcs on the same version. It'll just make your life that much easier.

2. After you get it all set up, back it up, to make restoring a lot easier. There is a tool in Synaptic Package Manager called RemasterSys that will let you burn a restorable CD/DVD of your installation. It has a gui that makes it easy to use.

3. If you go with KDE, I'd uninstall  the Gnome desktop, lest some wiseacre come in and switch it to Gnome and wreak havoc. This may be completely unnecessary - again, I am not a SysAdmin or a Guru. If I'm wrong about this, at least I'll have erred on the side of caution...

4. And if elected...whew, that always happens when my posts get too long!! ;)

---

### Post by marianlibrarian on 2009-05-04
Hi Didius Falco!

Oh darn. I didn't read number 3. My staff are goofing off and didn't screw my head back on right.

Ok now I'm back. - How do you go from gnome to kde?

> [I]I saw references to the Kiosk thing and this is where I get lost. Is there a difference between KDE and Gnome? If I am understanding what I am reading (oh no) then what runs as a KDE thing will not be ok in a Gnome environment??

I am pretty sure that Hardy Heron is Gnome? 

Heavens sometimes I can be such an idiot.[/I]

---

### Post by pastalavista on 2009-05-04
OK, sorry. I hadn't noticed that you were using Hardy and Dapper. In Intrepid (8.10) and Jaunty (9.04) there is an option in the user switcher applet for a "Guest Session" which is completely user only (no admin) and temporary. It is a basic session which has only user allowed apps and no ability to permanantly save anything except to removable media. When logged out and back in, it reverts to the original basic desktop.

---

### Post by Didius Falco on 2009-05-04
Ubuntu has a number of desktop environments it can run under. Ubuntu comes with Gnome as the default desktop. Kubuntu comes with KDE as the default.  There is also Xubuntu, which uses XFCE desktop.

They are all the same system underneath, the Desktop is just the GUI that overlays them. They are all interchangable as well; Ubuntu users can install the KDE desktop and/or the XFCE desktop.

Think of them as different outfits, that all have the same person under them.

You can install any of them through the Synaptic Package Manager.

First, read through the Kiosk info and see if that's an approach you'd like to take. If it is, just about anyone here can walk you through the installation.

Actually, here is a website that you can use to compare them. It's not going to be one of those head-spinning, brain-exploding things - the person who put the site together both knows his stuff and has a knack for setting it out simply enough to make it all seem easy.

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

Look in the menus on the left at that page, under "playing around" and it'll explain the different desktop managers. The link I gave you is a comparison between Gnome and KDE.

BTW, I didn't mean to confuse you more...sorry about the brains...<G>

---

### Post by marianlibrarian on 2009-05-04
Thanks for the information. I don't know why I was fussing about my head exploding because I only have one brain cell left anyway.

Here is an example: This morning I spent the better part of it upgrading one our five public access computers to Hardy Heron from Dapper Drake. Two patrons used it and a third one sat down and we found out that the top panel is gone and that the minimize, maximise and close icons are gone from the windows and god only knows what else. but right now it is unusable. Only 3 people used it and now I have to start all over again.

It looks like the kiosk thing is the only way that I can go and have the minimum in usable computers.

Library abuse is nationwide. It's just that I am the director and my job means that I have to clean toilets and understand the workings of Ubuntu and know the dewey decimal system and present all this with a smile. I said staff ... well there is me and one other lady full time and one part time person. neither of them know anything about computers. One of the perks of living in the DEEP RURAL Southern United States.

I had a hard time explaining that Ubuntu was not a scary word. Anyway, thanks for your help and after I get through scrubbing and vacuuming and dusting, I'll see about tackling these computers.
:)

---

