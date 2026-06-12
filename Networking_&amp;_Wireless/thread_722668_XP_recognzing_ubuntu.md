---
title: "XP recognzing ubuntu"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by oerllikon on 2008-03-12
ok, im sure there are several posts about this, but i couldnt find any that did me much good. i was wondering what i needed to do to. thanks

---

### Post by handydan918 on 2008-03-12
> **oerllikon said:**
> ok, im sure there are several posts about this, but i couldnt find any that did me much good. i was wondering what i needed to do to. thanks

Ummm...maybe post a question?

---

### Post by konungursvia on 2008-03-12
I don't let my Xp see my linux drives, but do let my ubuntu see my ntfs drives. This I feel is most secure. You never know what the hell is out there in the wild on your windows systems, and it's nice to have your own private fortress called linux. Don't bother letting windows see ubuntu.

---

### Post by Eiríkr on 2008-03-12
While totally isolating Linux from Windows is a lovely idea, there are many possible situations where that's functionally impossible due to various usage requirements and constraints.  And if you're stuck using Windows, you're actually probably better off using Ubuntu as your file server, and setting up ClamAV or some other security program to make regular scans of the Ubuntu drive(s).  

And I'll ditto Handydan here and say that asking a question is probably a better way to start than simply saying "I don't know what to do (and can't be bothered to search very much)", which is really what your post sounds like.  :-|  Without a more directed question, we really don't know what you're talking about -- you could very well be looking for advice on visual recognition processing software for a Windows-vs-Ubuntu robotic slapdown, for all we can tell.  :confused:

Cheers,

Eiríkr

---

### Post by oerllikon on 2008-04-04
> **handydan918 said:**
> Ummm...maybe post a question?

well, that was in the title.....
thanks for the help though. ill just leave it. i can save stuff from my linux machine to my xp machine
well, what it boils down to is, how do i get my XP machine to recognize my ubuntu computer. i already have them networked, with samba installed, and i can save things on my xp machine from my ubuntu one, but i would like it the other way around, since i dont know when my xp machine will finally crash, or become useless

---

### Post by Eiríkr on 2008-04-04
Okay, here's something we can work with!  :)

By "with samba installed", I assume you mean the package named "samba" for serving (i.e. setting up shares on an Ubuntu machine), rather than just the "smbclient" and "smbfs" packages for acting as a client (i.e. accessing shares on Windows machines).  If all you've done is install Samba, you won't have any actual shares configured -- so there will be nothing on your Ubuntu machine that you'll be able to see from the Windows machine.  I'm a bit old-school myself and can walk you through how to set up a share via a text editor -- if you need help with the GUI, someone else will have to answer.  ;)

So, open up a terminal, and type the following to open you Samba configuration file for editing:
```
sudo gedit /etc/samba/smb.conf
```

If you've got the default conf file that comes with a fresh Samba install, you'll see an awful lot of lines that begin with either a **_#_** or a **_;_** -- any line in a Samba conf file beginning with either of these symbols is treated as a comment and ignored by the Samba daemon process (smbd) when reading the file.  This is called "commenting out".  For now, we'll ignore these lines.

Find the line in the [global] section that says:
```
workgroup = SOMETHING
```

Make sure that the SOMETHING text matches the name of your workgroup as seen on the Windows machines.  This is usually just the default WORKGROUP, but could be anything.  The key is that the names match on the Windows and Ubuntu machines.  

Next, we'll add a share definition.  This is a super-simple setup just to get you started.  Scroll down to the bottom of the smb.conf file, and add the following lines.  Replace the caps with the path to the directory you want to share.  
```
[share]
   path = /PATH/TO/SHARE
   read only = no
```

We're done with your conf file, so save it and quit gedit.

Now we need to add your Ubuntu username to the Samba password file.  Without this step, you won't be able to log on to your Samba share.  Open a terminal and type in the following.  Replace the caps with your Ubuntu username, and then enter whatever password you want in the prompt that appears.
```
sudo smbpasswd -a USERNAME
```

Once you've done all this, restart your Samba server:
```
sudo /etc/init.d/samba restart
```
This makes sure that all your new settings are used by the server.  Now go to your XP machine, open Explorer, and type the following into the address bar, replacing the caps as appropriate:
```
\\SERVERNAME\share
```

You should be good to go after this.  If you run into any problems, let us know *exactly* what your symptoms are, and post the contents of your smb.conf file, and we'll go from there.

Hope this helps,

Eiríkr

PS -- Sometimes folks find that entering the server name in Explorer fails out; if this happens, try replacing SERVERNAME with the IP address of your Samba share.

---

