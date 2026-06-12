---
title: "Kubuntu:  How to mount NFS share?"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by theosib on 2006-11-21
I know how to mount an NFS share via the command line.  But I was wondering, since we're using these nice GUIs like KDE and stuff, what is the GUI way to do it?  I figured out how to share something out easily enough.  But from the System Settings, I can't find a way to mount a remote share.  From Konqueror, there's a way to mount shares, but the options do not include NFS.

So, how do you do it?

---

### Post by FrodoB on 2006-11-21
[http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html)

---

### Post by ajm2005 on 2006-12-10
> **FrodoB said:**
> [http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html)

this doesn't answer his question.

he is asking how to access NFS without mounting via the command line.

I.E., how do you access NFS via the file navigator.

In KDE, you are supposed to be able to access NFS with the Konqueror browser, using the io slave nfs:// however this has never worked for me. I always get an error mesdsage "authorization failed" and "authentication not supported".

---

### Post by sanicki on 2007-06-05
> **ajm2005 said:**
> In KDE, you are supposed to be able to access NFS with the Konqueror browser, using the io slave nfs:// however this has never worked for me.

Using Feisty and I am having the same issue. Am I doing it wrong? nfs://<server ip>/<share path>?

---

### Post by Yfrwlf on 2007-11-09
I tried with Dolphin and I get the "authorization failed" error too, and this is just a guess because I'm still a nooblet-in-training but NFS shares are probably picky and have what I think are normal Unix/Linux security mechanisms in place, so you possibly have to 1) create a user account on the machine that's trying to be accessed so that user can come into it (using the same name, I guess, and maybe password too?), and 2) have permissions set for the files that user is trying to access to allow them to access it.  But I could be wrong, need to try it out. :)  The only reason Samba works without hassle is it already has it's own user set up, so perhaps it'd be nice if NFS was as easy by default unless you wanted it more secure.

Or, you can just use Samba instead if you don't understand any of that for easier network file browsing, and leave NFS for more secure file sharing (even though Samba can be made more secure too).

Or you can just use scp, ftp, or http or something. ;)

---

### Post by Yfrwlf on 2007-11-09
Oh, and they say on this thread here that there is no announce feature in the NFS protocol so yes, NFS is apparently the very secure file sharing method and perhaps faster because of it's stripped-down capabilities but I dunno.  So, no NFS browsing, looks like you have to access it directly, at least the machine if not the shared folder as well.

[http://forums.fedoraforum.org/showthread.php?t=20937](http://forums.fedoraforum.org/showthread.php?t=20937)

---

### Post by Eiríkr on 2008-01-02
> **Yfrwlf said:**
> Oh, and they say on this thread here that there is no announce feature in the NFS protocol so yes, NFS is apparently the very secure file sharing method and perhaps faster because of it's stripped-down capabilities but I dunno.  So, no NFS browsing, looks like you have to access it directly, at least the machine if not the shared folder as well.

[http://forums.fedoraforum.org/showthread.php?t=20937](http://forums.fedoraforum.org/showthread.php?t=20937)

You need to set up your zeroconf / bonjour / avahi daemon configuration to announce your NFS shares if you want them to be browseable.  Have a look at this other form thread for ideas on how to do that:

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

Cheers,

Eiríkr

PS -- This other thread also has lots of good info:

[http://ubuntuforums.org/showthread.php?t=523928](http://ubuntuforums.org/showthread.php?t=523928)

---

### Post by Yfrwlf on 2008-01-04
> **Eiríkr said:**
> You need to set up your zeroconf / bonjour / avahi daemon configuration to announce your NFS shares if you want them to be browseable.  Have a look at this other form thread for ideas on how to do that:

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

Cheers,

Eiríkr

PS -- This other thread also has lots of good info:

[http://ubuntuforums.org/showthread.php?t=523928](http://ubuntuforums.org/showthread.php?t=523928)

Interesting, thanks!  It might be neat if Ubuntu, since it allows NFS sharing, to set it up to broadcast NFS shares by default, or to give the option to do so easily.  Might be a good thing to add to the GUI *shrug*

But I have to ask, what are the advantages and disadvantages of using either system?  Samba is set up for broadcasting and everything by default, so I've been mostly using that.  I know it's definitely not the traditional Unix way though. ;)  I was told NFS was faster for file transfer speed, but I haven't compared the two yet.

---

### Post by Eiríkr on 2008-02-23
> **Yfrwlf said:**
> Interesting, thanks!  It might be neat if Ubuntu, since it allows NFS sharing, to set it up to broadcast NFS shares by default, or to give the option to do so easily.  Might be a good thing to add to the GUI *shrug*

I agree that something like this as a GUI config tool would be nice; my general impression is that the Avahi project is still quite young though, given the lack of any GUI tools and the paucity of documentation, so perhaps we can hope for some GUI goodness in months to come.  :)

> **Yfrwlf said:**
> But I have to ask, what are the advantages and disadvantages of using either system?  Samba is set up for broadcasting and everything by default, so I've been mostly using that.  I know it's definitely not the traditional Unix way though. ;)  I was told NFS was faster for file transfer speed, but I haven't compared the two yet.

I don't know about speed, but given that NFS in general is leaner than SMB, I wouldn't be surprised if NFS were indeed faster.  As for which one to use, the general rule of thumb is to use the sharing server best suited to your client machines -- so SMB for Windows clients, and NFS for Unixy clients.  I think this has to do with what the client is expecting in terms of filesystem options; SMB emulates how Windows filesystems work, and is therefore suited to Win->Lin connections.  While SMB can also be made to work for Lin->Lin sharing, the additional overhead of all that Windows nuttiness can sometimes get in the way -- I ran into issues myself when I was trying to run chmod and do other Unixy operations on server-side files from the client, and found that I couldn't (both sides were Ubuntu machines; though it's entirely possible my smb.conf had some option I didn't fully understand that prevented this).  I also couldn't get SMB to work cleanly to serve up files to my Mac iBook, but (finally) had success with NFS.  YMMV.  :)

Incidentally, if you haven't had any success yet with setting up Avahi for your NFS shares, have a look [post=4387032]over here[/post] where I finally got around to writing up a bit of a HOWTO (aimed specifically at Ubuntu -> Mac OSX NFS sharing, but applicable to other Lin->Lin setups as well).

Cheers,

Eiríkr

---

### Post by Yfrwlf on 2008-02-27
> **Eiríkr said:**
> Incidentally, if you haven't had any success yet with setting up Avahi for your NFS shares, have a look [post=4387032]over here[/post] where I finally got around to writing up a bit of a HOWTO (aimed specifically at Ubuntu -> Mac OSX NFS sharing, but applicable to other Lin->Lin setups as well).

Cheers,

Eiríkr

Cool, thank you, I'm surprised to hear you had problems with OS X and Samba though, as I always assumed OS X could detect Samba shares out of the box, and that if Windows could see Ubuntu, then surely OS X would too or so I thought.

I would seem like Avahi is something that might be nice to merge with NFS somehow or include by default along with it, so that NFS sharing is easier.  I'd imagine though that SMB is of course the main focus though, and perhaps it's adequate enough that "normal users" are fine using it, and NFS is more left to system administrators who care about speed among other things the most.

---

### Post by Eiríkr on 2008-02-27
Yeah, there's something clearly wrong with my Samba setup, as Windows *can't* see my Xubuntu file server.  I can map drives just fine, but running [font=courier]net view[/font] from a terminal on the XP box never seems to show my Xubuntu machine.  Perhaps relatedly, though the workgroup folder shows up in the Network pane on my Mac, it's always empty.  I finally figured out that I needed to use [font=courier]-t cifs[/font] and my server's IP address instead of hostname, and I could manually mount on the Mac, but by the time I'd gotten that far, I already had NFS up and running.  :)

The Samba quirks have only been a minor inconvenience so far, but I'm getting more and more curious as to what's wrong.  Might be time to start a thread of my own.  

Glad the Avahi stuff might come in handy.  It looks like the Linux Avahi project is still pretty young, and while I agree it would be great to have more integration and GUI-ness, it'll probably be a little while before anything like that is available.  It was hard enough simply trying to find info on what the service config files were supposed to look like!  :shock:

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-03-01
> Yeah, there's something clearly wrong with my Samba setup, as Windows *can't* see my Xubuntu file server. I can map drives just fine, but running net view from a terminal on the XP box never seems to show my Xubuntu machine. 

Fixed the issue!  I'd forgotten that I'd set up my Xubuntu network mask to be 192.168.255.255, while my Winbox was 192.168.10.255.  Even once I figured out the difference, it took me a while to realize it was the issue, as I'd (apparently mistakenly) understood 192.168.255.255 to be a superset of 192.168.10.255, whereas judging from the behaviour I was having it's clearly *not*.  Once I switched my server's networking config to use the same more specific network mask, Bob's your uncle and it's working perfectly.  :D

Now to figure out why it's not showing up correctly on the iBook.  The workgroup name shows up in the Network pane, but it's empty...  :confused:

---

