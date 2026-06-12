---
title: "Repair Disks - How?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by nicnok on 2011-01-16
Any chance of setting out exactly how [in idiotspeak please] to create a set of recovery & repair disks for a lovely pc rescued from a skip?

---

### Post by drs305 on 2011-01-16
Your post was moved from another thread since you were not the OP and your post did not concern that poster's situation.

You will need to be more specific as to what you are trying to do, and which OS you are trying to back up. If it is Windows, you may have better success asking the question on a Windows forum. That being said, here is a link to Windows recovery disks. Note the page has a links to a commerical site but there are also torrent links which will allow downloading various Windows recovery disks (not just W7) for free (look carefully).
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by nicnok on 2011-01-16
As is obvious I'm very new to these forums so apologies, and certainly don't mind having the message moved,  but it bore directly on the post in the original thread [Paul820 in showthread.php?t=1668247] who said that 'option 1 was you must hold [or create?] recovery & repair disks (for your Ubuntu OS on the hard drive) as a very top priority' [if you are playing  with Ubuntu [Gparted]], but failed to give any detail of the process[es]. 

I realise my question is of more general application & this is very basic stuff, but some of us are almost beanless techless newbies, so an expanded explanation in idiotspeak of what Paul820 was on about or a link would be helpful.

Specifically I am slowly migrating to Ubuntu, running it on the skip pc, because I no longer trust MS since something in an imported Windows 7 file smashed my worn but comfortable Win ME [which is restored and running on the other pc].

I hold no system recovery & repair disks for the Ubuntu machine, though I have always assiduously backed up my working files to a USB stick periodically. So, thanks, but the Windows info is not what I was after.

Why would I need such disks when I can download the Ubuntu package quite simply? 
Is the answer that there's lots more going on inside the box than just Ubuntu?

---

### Post by cogier on 2011-01-16
I agree with your thought as to why you need this as you can download a live CD if needed.

The old drive you have, if it functions, will be reformatted by the Ubuntu installation if that is your plan.

---

### Post by Paul820 on 2011-01-16
@nicnok

I think you have gotten yourself a little confused regarding the other thread about rescue discs. The OP was saying he couldn't rescue his vista partition as his vista recovery partition was hidden.

**lisati** said it was his #2 priority to make recovery discs when he gets a new machine. Most new machines usually have rescue partitions and they are Windows. So i said that was my #1 priority as i have just bought a new machine that came with Windows 7 and the first thing i did was make the rescue discs for the OS, Windows recovery disc and drivers.

So you see, that is what i was replying to, sorry for the confusion.

If you want a rescue disc for Ubuntu there is one here, i havn't used it but maybe you might find it useful: [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Once again, sorry for the confusion.

---

### Post by drs305 on 2011-01-16
Ubuntu doesn't have 'recovery/repair' disks, although the LiveCD probably comes close in many users' minds.  

From the LiveCD you can either access your real system's files or 'chroot' into your real system, more or less allowing any commands you execute from the LiveCD to be performed on your actual installation.

This inevitably leads to discussions on how to back up your system. Most, but not all, of your customizations and all your data files within the Ubuntu partition probably reside in your /home folder (/home/username). 

Users employ various methods to back up and protect these settings and files. You can search for 'rysnc' and 'unison', two syncing apps. 

Another option is to have a separate /home partition. This doesn't back up the files, but it allows the user to retain customizations and data stored on the /home/username folder should the OS need to be reinstalled. This reinstallation is easily accomplished via the LiveCD and designating a separate /home partition is one of the install options.

One other thing I'll mention, though not directly related to backups, is some handy utility disks which can come in handy should the OS fail.

The SystemRescueCD, Gparted CD, Super Grub Disk are all mentioned from time to time on the Ubuntu forums. They allow booting from a CD/USB drive and allow the user to access the system files from either the command line or GUI. While a LiveCD can do many of the same tasks, each of the aforementioned has its advantages.

---

### Post by Paul820 on 2011-01-16
@nicnok

Having a large bean count doesn't necessarily make someone a techie. I know less about Ubuntu than most of the guys on here and they have less beans than me. Beans are rewarded for posts but that doesn't mean you have a lot of knowledge about Ubuntu. Most of mine were accumulated from the art forum where i spent a lot of my time a couple of years ago having general discusions with others on there. So, don't take no notice of bean counts ;)

---

### Post by nicnok on 2011-01-18
Thank you all for the useful chat. To mop up the points:
1 - Old drive will remain as MS Windows [another old pc - useful backstop - now slowly filling with photos]
2 - Paul820 - I see now the objective for the rescue mission was  different from my wondering why I needed it for my set-up: my confusion,  not your poor posting.
3 - Although not proud of my beanless  state I can live with it! ... but   techlessness is a real handicap trying [& failing] to make sense  of quite a lot of posts [though not this thread - thanks guys]
4 - drs305 - since I'm mostly on default settings & unpartitioned on  this drive I'll rely on the Live CD and regular file backups. This  conclusion strongly influenced by Ubuntu itself seeming to be very  stable and has recovered itself well when I've broken OO &  Evolution, so disaster seems unlikely or am I being over complementary?
re backups/ recovery: I seem to have lost the link that told me how to  archive old emails in Evoultion: what file load will Evolution tolerate  before I start getting problems? [had this once when Outlook Express  vampired all the RAM {I was told}] [oops, am I hijacking? - sorry?]

---

### Post by smurphy_it on 2011-01-18
You could try clonezilla.  It's similar to "Norton Ghost" and will backup your entire drive/partition(s).

I had to recently use it for a newly purchased Netbook, with no optical drive.

[http://clonezilla.org/](http://clonezilla.org/)

---

