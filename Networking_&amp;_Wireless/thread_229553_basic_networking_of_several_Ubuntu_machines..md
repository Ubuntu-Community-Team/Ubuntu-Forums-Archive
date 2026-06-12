---
title: "basic networking of several Ubuntu machines."
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by em3raldxiii on 2006-08-04
Alrighty, as usual, I did some searching but couldn't find any difinitive answers to my question.  So here'goes ...
 
I have 4 Ubuntu machines (one's Kubuntu actually), all connected via D-Link DI604 router.  I have DHCP working just peachy keen, so I can connect to the internet just fine.  I also have one computer running a webserver ([www.anxietyofinfluence.ca]("http://www.anxietyofinfluence.ca")) which I have manually configured through my router to have a static IP on the network.
 
Now, two of these machines USED to be Windows machines, and as such still have NTFS drives on them.  I can happily access them on their host machines (I haven't enabled write on them though).
 
I also have Samba running, though in my inxpert way, I believe it is not 100% configured correctly.  And I am not even sure Samba is the best way to do what I am doing .... but maybe it is .... I don't know ...
 
So, with computer 'A', I can access the shared portions of computer 'B', but computer 'B' cannot access any part of computer 'A'.  Computer C and D do not count at this point (maybe later).  When I go through my network browser, the only option is "MSNetwork" ... which seems retarded to me since none of my computers use Windows any more.
 
The biggest issue I have is that I want Computer 'B' to be able to have READ access to the NTFS drive on Computer 'A', and the more transparent the better.  Ultimately, I want to be able to open GXINE or some other media player and have it automatically point to that drive.
 
All help and commentary is appreciated.  Thanks guys (and gals). :D
 
Mike

---

### Post by tkiesel on 2006-08-04
Technically Samba is still emulating a Windows style network, so you'll find things like Windows mentioned here and there. ;)

Go to Places->Network Servers on both of those machines and go ahead and double click on Windows Network.

You should see an icon for whatever workgroup you chose to put the machines in. If you see more than one, then some of your machines are set to be in different workgroups than others.  Consolidating them all into one will make things run more smoothly.

To set the workgroup up go to System->Administration->Shared folders  and click on properties of one of your shares. Then click the General settings button it offers.  There you'll find the workgroup.  Put your machines in the same workgroup. That'll simplify a few things right off.

This might allow A and B to see each other more easily now!

There are some other things you can do here and there to tweak Samba out. I've done some editing of /etc/samba/smb.conf on my computer and my wife's computer here and there, but with Ubuntu 6.06 maybe there'd be no need.

As for getting these shares to operate as transparently as possible, you'll want to set them up to automatically mount on boot. (One caveat here, if you want to do this and you're in the habit of using spaces in your share names, don't.  Switch em over to ye olde underscore.  Got_it? Sweet.)

Install smbfs in either Synaptic or the terminal
```
sudo aptitude install smbfs
```

Make a directory for a place to put the remote share. I've got my wife's music mounted at a directory called L'sTunes in my home directory.

Edit your /etc/fstab to add a line for the share.

```
//servername/sharename  /media/mountname  smbfs  username=administrator,password=password,fmask=777 ,dmask=777  0  0
```

Here's the anatomy of that line:

//servername/sharename  is the name of the remote machine and share that you're wanting to mount.  In my case the name of my wife's machine is glitter and the share name is shared_tunes, so it'd be  //glitter/shared_tunes

/media/mountname is the place you'll put the share. So /home/tkiesel/L'sTunes for me.

smbfs says it's a Samba filesystem

username=administrator,password=password,fmask=777 ,dmask=777 is a string that sets you up to have read/write rights.

the username and password are for the comp that has the share you're mounting. the fmask and dmask definte the rights of the share.

so for me username=lkiesel,password=******,fmask=777 ,dmask=777

[lkiesel there, not tkiesel.  Hard to tell, I know.] You see ***** there because I'm not gonna give you my wife's password. ;)

Putting it all together:

```
//glitter/shared_tunes /home/tkiesel/L'sTunes smbfs username=lkiesel,password=******,fmask=777 ,dmask=777  0  0
```

Put a line like that (altered for your situation of course) in /etc/fstab and then run ```
sudo mount -a
``` to mount it.

Then that share will transparently be a part of your filesystem and you can play music, movies, anything off of it with zero hassle.

Much love!
-T
bassist, middle school teacher, music fanatic

[Note: If you have a weird hangup/Gnome weirdness after rebooting when you've done the fstab mount thingie, check out the bug report in my sig. There's a little one line addition to /etc/network/interfaces that overcomes a bug in Dapper with automounting Samba shares. Until the bug gets (finally) fixed at least.]

---

### Post by christhemonkey on 2006-08-04
By the way, just thought id say em3raldxiii:
On your [www.anxietyofinfluence.ca](www.anxietyofinfluence.ca) site, the link to her myspace is broken.
Sends you to mysapce.com instead of myspace.com.
Just thought id let you know!

---

### Post by em3raldxiii on 2006-08-04
> **tkiesel said:**
> Technically Samba is still emulating a Windows style network, so you'll find things like Windows mentioned here and there. ;)
 
Go to Places->....]
 
Holy shamole, dude! You da man. As soon as I get home I am going to do some serious network adjustments. Thank you SO much for the incredibly detailed answer.
 
> **christhemonkey said:**
> By the way, just thought id say em3raldxiii:
On your [www.anxietyofinfluence.ca]("http://www.anxietyofinfluence.ca") site, the link to her myspace is broken.
Sends you to mysapce.com instead of myspace.com.
Just thought id let you know!
 
Thanks! I think it's the new way myspace handles their links, it seems they no longer allow direct linking to user pages? I dunno ... I'll go over it just to make sure.
 
*EDIT:  I just clicked it, and it worked for me.  Myspace is buggy though, so I wouldn't doubt that it would do it to you.  Try again a few times at different times of day and let me know what happens.*

---

### Post by christhemonkey on 2006-08-05
Hmm i tried again, but still the link on the left of the page tries to take me to [www.mysapce.com](www.mysapce.com)
Maybe its just my strange windows computer...

---

### Post by em3raldxiii on 2006-08-05
Very strange indeed.  I'm at work right now on a Win2KPro machine on a heavily firewalled network.  I went to the anxietyofinfluence website and clicked on the Myspace link on the left.  It took me to the Anxiety of Influence Myspace page, complete with auto-playing audio.
 
When you hover over the link, what address appears in your status bar?  (in Internet Explorer).  I am wondering if perhaps your computer has some kind of malware affecting it.  Try clearing your cache, history, and temp files etc etc, and try cranking up your security settings to max.

---

### Post by tkiesel on 2006-08-05
ONe of you is clicking the Myspace graphic link, the other one is clicking the "Check out our profile on Myspace!" text link.  The text link version is broken while the graphical one isn't. :)

Rock on,
-T

---

### Post by christhemonkey on 2006-08-05
O yes.
i see that now, thnks tkiesel

---

### Post by em3raldxiii on 2006-08-05
LOL good catch!  Haha.  I guess I should fix that when I get home, hey? One of these days I will configure my FTP server so I can do it from work ...

---

