---
title: "Samba in Feisty: Please Work Out-of-the-box!!!!!!"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by Yfrwlf on 2007-01-19
This is a suggestion thread, not a problem thread, as I don't know where else to post suggestions. :)

Samba in Feisty Fawn Requirements:  A guest account, so no having to hassle with user names and passwords for others to see your files, and make things read-only by default.  Basically, user friendly easy file sharing!!!  Samba is very powerful, so if you want to give complex permissions then you can do that, but by default for beginner users just wanting to share out some files so others on the network can see them whether from Windows, Mac, or Linux, that is what needs to happen.

Ubuntu supposedly has instant easy file share *viewing* out of the box (though it currently doesn't work for me for some unknown reason), but file sharing needs to be that easy as well.  That would rock.  Am I right or wrong?  OK I'm done. :biggrin:

---

### Post by Enverex on 2007-01-20
System >> Administration >> File Sharing.

What's the problem exactly?

---

### Post by Yfrwlf on 2007-01-20
> **Enverex said:**
> System >> Administration >> File Sharing.

What's the problem exactly?

You mean, it's supposed to? :shock:

There is no System > Administration > File Sharing, but there is "Shared Folders", but no one can see those.  You're seriously saying that it's supposed to be really easy to share out files as well???  I wonder why mine isn't working then :?

---

### Post by Enverex on 2007-01-20
> **Yfrwlf said:**
> You mean, it's supposed to? :shock:

There is no System > Administration > File Sharing, but there is "Shared Folders", but no one can see those.  You're seriously saying that it's supposed to be really easy to share out files as well???  I wonder why mine isn't working then :?

They should be able to see them, yes (sorry for the folder name, I'm on Feisty so I had to guess the name off the top of my head). What machines are you trying to access the folders with? Also, do they show up if you type "smbtree" in a terminal?

---

### Post by juve on 2007-02-08
simple non-restrictive SAMBA out of the box !
Very good idea !!!

I'm on Edgy, smbtree works fine and shows all shares in the Network.

Ubuntu can access Windows,
Windows can access other Windows,
but Windows can't access Ubuntu without a password. 

That's very bad and should not be the default behavior for a Desktop-PC

---

### Post by Yfrwlf on 2007-02-08
> **juve said:**
> simple non-restrictive SAMBA out of the box !
Very good idea !!!

I'm on Edgy, smbtree works fine and shows all shares in the Network.

Ubuntu can access Windows,
Windows can access other Windows,
but Windows can't access Ubuntu without a password. 

That's very bad and should not be the default behavior for a Desktop-PC

Agreed, that is something I have noticed that is still the default.  Windows by default doesn't password protect shares.  I think the Ubuntu share window at the very least needs to have a password option where you can specify a password for your shares globally, just for that share, have no password globally, or no password for just that share.  Having those options for new users I think would be totally kickath. ^^

---

### Post by juve on 2007-02-11
agreed !

Atm in edgy, it is not possible to achieve default windows-behavior without messing around in smb.conf.

There's another problem before samba will work out of the box: Firestarter
You have to enable SMB for your LAN and you have to edit your /etc/firestarter/inbound/setup to allow response to netbios name broadcasts from the local network. Otherwise the Ubuntu-machine won't see the winboxes.
```
#at line 13:
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT
```[SIZE=1]At least if this addition is not a security risk, like many users i just blindly added it.[/SIZE]

---

### Post by Yfrwlf on 2007-02-20
You can't just allow a certain port to get through?  Samba is a defined option in Firestarter's ports, so by allowing it through it should fix that right?  I'm not sure how to enable Samba for my LAN, I have it installed is all, and it's running, but I'm still not showing other compies in the network browser.

So ya, it would be nice if Samba share browsing was enabled by default in Feisty.  If it's a security risk then Samba should be made to me more secure, hopefully, in the future. :)  It's just, in order for normal computer-unsavvy users to be able to view shares and find Samba printers to add so they can print to them, Samba needs to be browsable.  Most people don't know how to find out computer IPs, and most won't know how to manually add the printer name and it's host computer's IP, so browsing would make things that much better for Ubuntu's success on the desktop.

---

### Post by dmizer on 2007-02-21
let's have a little perspective here.

samba is NOT the end all and be all of file sharing protocols.  there are loads, mac has one which windows cannot connect to, linux has one that windows cannot connect to without some MAJOR work.  and that's only three that i'm aware of, i'm sure sun systems has one that's proprietary to them ... and who knows what else.

and that doesn't even include universal protocols like ftp, and http (both of which linux can easily serve up, but i wouldn't trust windows to do this).

samba is NOT a native file sharing application for linux, and really ... it's a testament to how versatile linux is that linux is actually able to communicate with your windows computers, despite the fact that it may be painful.  also, because samba is a windows native file sharing protocol, the only people who can make it more secure is windows developers.

but this is not the only thing causing you this "problem".  when you look at the difference between linux and windows, you're looking at a fundamental difference in security perspective.  while you may find it annoying to enter a password to gain access to a shared file folder, think about it next time you take your laptop to a mobile point, and your windows machine just lets whoever has the desire to browse your shares unchallenged.

in linux, samba CAN be configured with options which will allow unrestricted windows like access to your shares, but howto's don't include these options as a general rule because of a more restrictive and safer outlook held in the linux community regarding networking computers.

remember ... if your computers can talk to each other without restriction, so can someone else's.  windows default "security" is something like leaving all the doors open (not just unlocked ... but standing wide open) on your house and expecting only family to walk in.  while this may save you from having to fish your keys out of your pocket each time you come home, you would frequently end up with nasty surprises upon your return.

so to sum up:
1) please remember that samba is NOT a native linux app, and realize that it will require more effort because of this.

2) upon serious and informed consideration, if your needs truly do not require password protection, this can be configured, and the answers are on this forum.

---

### Post by mozetti on 2007-02-21
> **juve said:**
> simple non-restrictive SAMBA out of the box !
Very good idea !!!

I'm on Edgy, smbtree works fine and shows all shares in the Network.

Ubuntu can access Windows,
Windows can access other Windows,
but Windows can't access Ubuntu without a password. 

That's very bad and should not be the default behavior for a Desktop-PC

This is one of the most misguided and uninformed posts I've seen on this site.

---

### Post by Yfrwlf on 2007-02-23
This is the kind of attitude that Microsoft Vista takes for it's so-called "security", and the kind of attitude that can hold Linux back from competing on the desktop.  Let me explain...

> **dmizer said:**
> while you may find it annoying to enter a password to gain access to a shared file folder, think about it next time you take your laptop to a mobile point, and your windows machine just lets whoever has the desire to browse your shares unchallenged.

You think a password should be the be-all end-all in "security"?  Certainly not.  Sharing files to everyone and not placing passwords upon it would allow anyone to browse your files "unchallenged" yes, and that's the entire point.  It is very possible to make a bunch of files read-only to anyone, or accessible to a smaller group of users or whatever you choose, and still be secure.  Again, if users want to share files to *anyone* as read-only, without requiring a password, it should be possible to do so and still be secure.  If they run into problems then they can start requiring a password, or restrict the access, or whatever kind of attack is being waged on their machine, the developers of the sharing software will hopefully be able to patch that problem without forcing all users from then on out to have to use passwords.  To not require passwords but to be able to share read-only files while remaining secure may be a challenge, yes, but that doesn't mean that that kind of sharing is wrong, or impossible to do securely.

Windows has lots of holes in it, lots of security flaws.  The Vista method of security is to give users more warnings about doing certain things.  This is not actually fixing the problem, it's not making these holes less penetrable, it's keeping the user "in-line".  While this method may be appropriate to a degree, at least until solutions can be found, it is most likely overlooking ways in which the software can be made better to improve security.  Security is partly the user's responsibility always, yes, but the software is definitely not immune from fault.

Your argument is "this is the way it's always done in Linux", the kind of conservative attitude that you can't afford to hang onto with technology unless it is *definitely* necessary, and I don't think that is ever 100% the case.  My argument is "Does it have to be, or can you make Samba secure enough so you don't have to require passwords?"

But enough of that, it all comes down to this people: If users can have an easier time of doing things while still remaining mostly secure or ideally very secure of course, because the software is secure enough to allow that, they should do it.  If they aren't, then more restrictions certainly need to be there.  We can all agree on that.  Is Samba secure enough to allow read-only sharing of files without requiring passwords?  No clue.  If it isn't, then for now we need passwords, which brings me to my second point on this thread:

Samba file sharing in Ubuntu needs to give the option for easily specifying passwords or no password, if it's secure enough to share with no password, in which case read-only could be highly recommended or whatnot.

"1) please remember that samba is NOT a native linux app, and realize that it will require more effort because of this."

Yeah, I fully realize that, and realize what I'm asking.  I'm still asking for it though.  The reason is because in my opinion in order for Linux to become more attractive to users and thus developers too so that Linux users like me and you will have more software available for us to use, it needs to be used by more people.  Right now, allowing users to comfortably switch from Windows to Linux is one of the most important goals in order to achieve this due to the US at least being a mostly Microsoft dominated nation.  That means making Samba work well, easily, and securely.  This is not the most important thing on earth for Linux by far heh, but it is a good goal to accomplish along the way IMO.

"2) upon serious and informed consideration, if your needs truly do not require password protection, this can be configured, and the answers are on this forum."

That's correct, but I don't think users that don't know about manually configuring samba.conf or whatnot should have to come to this forum just to learn how to do it.  I think all the options to allow them to share their own files on their own network at the very least, and in a secure way, should be made available through the GUI.  I'm not going into the arguments for why a GUI is better for beginners, because hopefully that's obvious to you already, so my reason for wanting this should also be obvious.

Right now sharing files is available by right clicking on a folder and selecting share.  However, I have yet to see anywhere about password options.  I think beginners are going to be a little confused when they share out files and try to access them from another machine and are prompted for a password when they never specified one to begin with.

I hope the developers of Ubuntu are aware of these challenges and can meet them, and if my suggestions help them to do so then awesome. ^^

---

### Post by dmizer on 2007-02-24
no, i think you've mistaken me in many aspects.  i do not believe that the answer to security lies in the software.  software can be easily cracked no matter how secure it's made.  just look at how quickly one person was able to break the encryption for hddvd and another to crack bluewave.

my position on security stems from the knowledge that it takes far more than secure software to make a computer secure.  it takes ACTIVE participation on the part of the user.  non-password protected read only shares are easily configured, and are by far and away more secure than non-password protected read/write shares.  but people want read/write capability to their shares.

the sad fact is that many uninformed users (windows, and linux or otherwise) are unhappy with how their system works unless it is completely insecure.  that is:
> wide open read/write shares on the entire system because it's too much of a pain to have to remember to save the file in a specific folder
> running as administrator so changes can easily be made, and software can be easily installed.
> running wireless with no wep because it's too difficult to set up and so on.

by far and away, the biggest reason for the lack of security in the personal computer market (again ... windows or linux or otherwise) is due in large part to uneducated users.

> Your argument is "this is the way it's always done in Linux", the kind of conservative attitude that you can't afford to hang onto with technology unless it is *definitely* necessary [...]

no ... i said nothing even remotely close to "this is the way it's always done in linux".  i said there is a fundamental difference in security perspective when comparing linux and windows.  this perspective comes from an experienced and informed development team, and from an experienced and informed user base.  what's more ... when considering how pivotal computers are to today's society, and when considering how many varieties of in-routes there are, i suggest that an aggressive security outlook is essential.  this attitude is independent of operating system.  it doesn't matter what os you use ... if your system CAN be compromised, it most likely WILL be compromised.

you see ... windows CAN be made tolerably secure.  sure, windows is also full of holes; but more importantly, windows user public is full of holes. it takes a huge amount of knowledge and work to make a windows system secure.  it takes effort that the windows public is both too unwilling to perform, and too uninformed to be able to perform in order to create a windows computer you can trust.  but linux works exactly the opposite.  you must work to make the system not secure.  anyone can pick up and install a relatively secure ubuntu operating system out of the box.  but it takes effort and hard work to make ubuntu as insecure as windows is upon its install ... and you're kidding yourself is you think that ubuntu can't be made to function as completely and totally insecure as windows.

to me, you seem to be saying that it is preferable to be insecure because of a usability standpoint&#65292;and that seems to me to be (at best) misguided. sure, non password protected READ ONLY shares are (for the most part) perfectly secure.  but that's not what the public wants, they want to make changes too.  further, they want to make changes globally ... and from remote ... and from the world wide web.  when given the opportunity users invariably opt for the system that's insecure because it's "easier to use".

i do so clearly remember a time when it was perfectly safe to leave your front door unlocked all the time, or car unlocked (even idling in the parking lot when it's cold).  but no one complains about the fact that they must use their keys to open doors now, and no one complains that auto manufactures should make cars un-stealable without having to use keys.  they are painfully aware of the problems and dangers that threaten a home these days.  and they are aware that the first line of defense is a locked door.  but they are NOT aware of the problems and dangers that threaten their computers.

my argument is that it is painfully obvious (given the perspective of the user) that an aggressive security philosophy, and user education are the only ways to combat the growing menace, and password protection is a small but important piece of that security and education.

---

### Post by ChrisG_UK on 2007-02-26
I've been trawing these forums for a while looking for answers to samba problems, and what I see is lots and lots of people having a tough time getting their Ubuntu boxes to cooperate with Windows file sharing. That's a real shame.

I believe lots of people, like myself, see Vista as a wake-up call to look at alternatives like Ubuntu, but cooperation with Windows is a necessary evil while we make the transition. The easier it is, the more people will successfully make the switch. Security is a detail that I'm sure can be worked out. The important thing is to make it easier.

Ubuntu is close to being a very real challenger to Windows, and integration with Windows file sharing is one of very few barriers. It needs to work easily with Windows shares "out of the box", i.e. all done with a few mouse clicks.

Well, that's my two pence worth. Take it or leave it.

---

### Post by Yfrwlf on 2007-02-26
> **ChrisG_UK said:**
> I've been trawing these forums for a while looking for answers to samba problems, and what I see is lots and lots of people having a tough time getting their Ubuntu boxes to cooperate with Windows file sharing. That's a real shame.

I believe lots of people, like myself, see Vista as a wake-up call to look at alternatives like Ubuntu, but cooperation with Windows is a necessary evil while we make the transition. The easier it is, the more people will successfully make the switch. Security is a detail that I'm sure can be worked out. The important thing is to make it easier.

Ubuntu is close to being a very real challenger to Windows, and integration with Windows file sharing is one of very few barriers. It needs to work easily with Windows shares "out of the box", i.e. all done with a few mouse clicks.

Well, that's my two pence worth. Take it or leave it.

That was all I was trying to say really, too.  I agree with you dmizer that security is very important, and I'm not trying to make Linux work the exact same way as Windows, especially if it's an insecure way.  Whatever choices need to be made to keep Ubuntu secure so be it, but whatever it is it needs to work easily and be enabled easily, "out of the box".

This is luckily now a mute point it seems at least to some degree, because Ubuntu Feisty seems to work out of the box at least for browsing.  In Feisty, if you go to browse windows networks in Nautilus, all the Windows shares on my network showed up.  This, IMO, seems to be a great improvement over Edgy.  I hope the printer utility that they end up putting in Feisty if it isn't already will also allow browsing for Samba printers over the network as well to make adding them easy for beginners.

I have yet to try sharing out directories in Feisty, so I don't know if that has changed any or if they made it easier to specify a password or whatnot without editing a smb.conf file.  If passwords need to continue to be required even for read-only shares, so be it, but at least make it an option and the password definable through the GUI for noobs would be my suggestion to the developers, though they are probably aware of this already.

Go go Ubuntumobile!

---

### Post by dmizer on 2007-02-26
> If passwords need to continue to be required even for read-only shares, so be it, but at least make it an option and the password definable through the GUI for noobs would be my suggestion to the developers, though they are probably aware of this already.
not trying to beat a dead horse, but this is not how things work.

you see, the username and password for shares are that of the remote computer, not the ubuntu computer.  you must add the windows computer's username and password as a user on your ubuntu computer.  and this can be done with the add user gui utility or with the smbpasswd utility in the cli like so:
```
sudo useradd -s /bin/true windowsuser
sudo smbpasswd -L -a windowsuser
sudo smbpasswd -L -e windowsuser
```

password protected shares work exactly the same way in windows.

---

### Post by jlsheehan on 2007-02-28
Whilst I don't like the idea of having my home directory readable by default, I do think that easy fast sharing of files out-of-the-box would be a nice feature.

Mac OSX provides a "Drop Box" to easily share documents on your PC and Windows has the "Shared Documents" folder enabled by default for the same reason.

It would be nice to easily enable the Samba guest account on a directory but to do it without a password you need security=share, which is currently not the default.

Samba share level security, however, still needs a user associated with each share in order to set the share level password, an elaborate annoyance in order to share something based on password only (or lack thereof).

Perhaps Samba 4 will provide some easier solution.  Or there is always the old trick of installing apache and creating a /home/<username>/public_html directory which can then be read by anyone who goes to http://<your-ip-address>/~<username>/

Jeff

---

### Post by Yfrwlf on 2007-03-08
<rant>
Thanks dmizer for the correction, I'm ignant still ;)

Jeff, I've also used Apache for sharing files before like that, it's a good way.  Also, the Firefox extension AllPeers is a useful way to share files with other Firefox users.

I do agree with you though that there should still be an easy, secure way of sharing files at least as read-only.  There is no security risk for that, otherwise you're calling Apache a security risk too since that's all it does.  If Samba is secure and could be configured to do that, then that'd be great.

If users wanted upload access, or read/write access, a password-only security model would be less secure than one requiring users be set up so that the normal Linux user permissions could then be used.  Otherwise you'd be open to dictionary password attacks and such.

I dunno, that's the limit of my knowledge really, but I do understand that Linux permissions are set up to enforce security, that it seems to be a pretty secure model, but it needs a polished easy interface for new users, whatever is necessary to keep security *and* ease of use.  If you try to claim that ease of use = insecure, then your security model is a failure.  Obviously Linux can't rely upon complexity to be secure, because then once it gets popular it will be known and easy to crack.  So with that aside, what needs to be done then is, like I said, giving it a facelift to be easily accessible to users.

So lets say you are going to use the fairly secure normal Samba sharing model.  Now, how can you make it user friendly?  Lets see, dmizer you say that it needs to have the Windows user set up with the same name on the Linux machine as well.  So, in the share folder dialogue box that pops up, how about putting in a User Access option.  Under that, state that only the users listed will have access to the share, and to make sure the name is exactly the same as the user on the other computer.  Or put that dialogue in the share folder window, and have the button link to the users control app.

Something like that.  It's a very simple question, really.  Just ask: Can a user who doesn't know anything about file sharing do it?  The knee-jerk reaction from some is "they shouldn't be using a computer if they don't already know how to use a computer" um no, the computer is there to compute for them and at the very least should help them so they CAN EASILY accomplish what they need to accomplish.  The computer is for them, not for someone who already knows it.  For both advanced, and beginner alike.  Why are Macs so easy to use?  Because they are easy to understand, mostly.  Users shouldn't have to run to forums to learn how to use their computer.  It should just work, and get out of the way, so they can use their computer for the thiings they need it for.  I like messing around on the command line, I do a lot of things that most people won't do that are "advanced", running several different headless servers, etc.  I love the power of Linux, don't get me wrong, it's incredible.  However, this is for beginners, to guide them and teach them, so Linux can take the desktop market from Microsoft.  Something long, long overdue.  To do that, it needs to break a few traditional molds, like that user friendliness is bad, or that closed source can't be run on open source.  You can have ease of use and still have power under the hood if you need it.  You can run closed source apps and drivers on your system, it doesn't stop open source apps from competing or being run instead, in fact it will make them compete even harder, which is good for both OSS and CSS.

OK way too long, sorry. :)
</rant>

---

### Post by airtonix on 2007-03-26
yeah like dmizer says.....learn ssh. nuff said. (its even intergrated with nautilus)

---

### Post by Yfrwlf on 2007-04-07
Oh I have, and you're welcome to use what you like obviously, but you've missed the point entirely.  This isn't Slackware.  This is Ubuntu, for "normal" users, not SSH-using users like you and me.  We are a minority compared to the vast majority of desktop users, so to make it easy for them we need things like this.  Do you think your grandma is going to start SSHing into her Beowulf cluster to manually setup cron jobs and iptables?  Probably not.  This point is now mute though since the developers have added a few additional tools for "easy file sharing" to Feisty.  One of them actually looks eerily similar to the exact way I described what it could be like in this thread.  Maybe they are watching and listening after all ;)  I'm going to thank them after the final release of Feisty, after I figure out how to use the thing, since it's integration into the rest of the system and Nautilus is unknown to me at the moment.  Seems like now there are almost too many file sharing tools, but just getting them out there was a great first step at least.  Yay for Ubuntu!  =D>

---

