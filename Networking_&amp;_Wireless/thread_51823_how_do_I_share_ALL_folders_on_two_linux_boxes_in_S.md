---
title: "how do I share ALL folders on two linux boxes in SAMBA"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by arjay1 on 2005-07-25
Question says it all - how do I get two kubuntu boxes to share ALL folders on both machines with each other, using samba.  At the moment I keep adding folders to smb.conf but it is a PITA.  There must be an easier way?

TIA

---

### Post by grim42 on 2005-07-25
[QUOTE=arjay1]Question says it all - how do I get two kubuntu boxes to share ALL folders on both machines with each other, using samba.  At the moment I keep adding folders to smb.conf but it is a PITA.  There must be an easier way?

TIA[/QUOTE]
 Try putting everything you want shared in one folder, and sharing that?

---

### Post by wrtrdood on 2005-07-25
Personally, with two Linux boxen I wouldn't use Samba for this.  NFS works well and is not that hard to set up.  That being said, you are using M$ terminology here.  When you say "all folders" what precisely do you mean?  Surely you are not trying to make every root level folder accessible, are you.  Or are you referring to sharing "home" level user directories?

Perhaps the difficulty comes from the directory level at which your "shares" are being defined.  Even so, yes, you must configure each directory you wish to be seen by others on both systems.  There's really no other alternative.  There are some tools available to make this somewhat easier but it's still a bit tedious.  There is no simple "file manager" share-this-folder option if that's what you're looking for.

A possible alternative is to define a single share point, as suggested but not by putting everything in one directory.  You could create a single directory such as **public**, define it only in smb.conf then create symbolic links (using the ln command) to all the other points in only that directory.  That way you would not have to touch smb.conf again but merely add new links as the need arises.

---

### Post by arjay1 on 2005-07-25
Thanks for the advice.  Yes, I DO want to share pretty well everything unless you can advise how else to do things like, for example:  I want to make a change to my /etc/samba/smb.conf file - then I want to save a new copy of the smb.conf to the other machine (100 yards away and four floors down in a different building).

I don't want to have to walk up and down stairs with a floppy in one hand and an oxygen mask in another everytime I want to change something on the other machine that is not in my home directory!!??  The only other way I can see of doing it is to copy every file I change to a temp directory in /home on one machine, then copy it over to the other's /home - then get myself over to the other machine - repeat the process - and delete all the temp files.

Unless - of course - you know different!.....

---

### Post by majikstreet on 2005-07-25
[QUOTE=arjay1]Thanks for the advice.  Yes, I DO want to share pretty well everything unless you can advise how else to do things like, for example:  I want to make a change to my /etc/samba/smb.conf file - then I want to save a new copy of the smb.conf to the other machine (100 yards away and four floors down in a different building).

I don't want to have to walk up and down stairs with a floppy in one hand and an oxygen mask in another everytime I want to change something on the other machine that is not in my home directory!!??  The only other way I can see of doing it is to copy every file I change to a temp directory in /home on one machine, then copy it over to the other's /home - then get myself over to the other machine - repeat the process - and delete all the temp files.

Unless - of course - you know different!.....[/QUOTE]
 if you want to change something on another machine, use ssh. (can't help with ssh since I'm in a dilema with ssh now!)

---

### Post by wrtrdood on 2005-07-25
Ah.  This sounds more like you just need to keep directories in sync between the two systems.  Is that right?  If that's the case, you might want to consider looking at rsync.  It's an included utility.  Have a look at the man pages for rsync and you may find a way to simplify this process.  I've used it in the past to maintain updates between servers and though it can be difficult to set up at first, it does work quite well in making sure everything stays synchronized.

If you would rather maintain manual control of updating files, there are much easier ways of doing that on Linux systems than running back and forth between systems.  For one thing, you can copy files easily between systems using scp.  It works exceptionally well and since it uses ssh, can be quite secure.  It's also possible to configure ssh so that you don't need a password and in this situation it would be just like copying a file from one directory to another on the same machine.  Speaking of ssh, is there some compelling reason you would need to be moving physically from one system to the other?  You do realize that you can log on to the other machine from the one your using by simply using ssh, right?  In fact, it's possible to set the DISPLAY environment variable to point to the X display on your local system and run graphical tools as if you were in front of the other machine.  I say possible because there are some changes required to get X to let you do that but it can be done.  

Just trying to come up with some ideas here for making your life easier  :)

---

### Post by sonny on 2005-07-25
Why don't you mkae links to the files you want to share into your /home directory?, that way you just share your /home and just put some links to the other folder. 
Just an other sugesstion.

---

### Post by arjay1 on 2005-07-26
Hey - amazing set of suggestions - what a helpful bunch of people you are.  Thanks to everyone.  I should have explained that I am a newbie to linux and even newer to kubuntu.  For example, I had never heard of ssh, rsync or scp (I know, I know) but will look them up and do some reading.  

I have used remote desktop in Windows ever since it was introduced so I know the general theory about that.  However, you can make all directories available in Windows very easily.  I presumed that if I logged on to one machine from the other using some linux software, that I would have the same problem as I do now - only having access to a limited set of directories.  I obviously have some homework to do.

BTW - I did post to this forum asking a couple of questions about nfs but got no reply.  Posting on a Sunday was probably a mistake - very few readers and the board has moved on a long way since then.  I really just wanted to know if nfs and samba can co-exist ok on the same machines and same network (I have to keep dual boot to XP on at least one machine for various reasons).  Perhaps one of you could enlighten me.  In the meantime I'm off to man pages to do some research.

Thanks again to everyone.

---

### Post by wrtrdood on 2005-07-26
You're welcome.  Always willing to help make Linux attractive to new people.  :) 

Yes.  Samba and NFS can easily coexist.  You should know that Samba is really only needed if you intend to access resources between Linux boxen and Windows.  Linux does not need it.

  NFS provides something very similar and has been used in Unix for quite some time.  It has its own set of problems but generally works pretty well.  Let us know if you need help setting it up.

---

### Post by skyboy on 2005-07-27
wrtrdood >> For the Graphical remote connection, kubuntu comes with Krdc and Krfb (respectively K remote desktop connection and K remote desktop control)  which make it really easy  to display the remote computer "as if you were in front of the other machine". I use it everyday ;) and I didnt need to modify anything in my xorg.conf nor in Xserver.
And yes rsync is great for synchronising several Linux-Box's

---

### Post by wrtrdood on 2005-07-27
> For the Graphical remote connection, kubuntu comes with Krdc and Krfb 

Indeed.  There's also FreeNX (and I see where it may be integrated into the software you mention) and VNC.  Still, setting up X to to allow connections (listentcp and xhost) and using *export DISPLAY=192.168.1.1:1* strikes me as a very easy way to accomplish nearly the same thing.  It works great with servers.  :wink:

---

### Post by arjay1 on 2005-07-28
skyboy - I tried to set up krfb and krdc and failed miserably.  I used krfb to setup an invitation complete with ip address (didn't realise it also needed the screen number!) and password.  Then rushed off to the other machine to try it out.  I entered the address in krdc but it hung in the authentification stage.  Never got the chance to enter the password.  Do I have to enable something in ip tables?

I can access some shares already via samba but that won't allow me to share hidden directories which is where i need to get sometimes.  

Very frustrating because if I boot both machines in Win XP (they are dual boot) I get access immediately and rdc works "out of the box".

---

