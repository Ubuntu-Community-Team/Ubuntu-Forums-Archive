---
title: "Need a tutorial for SAMBA/LDAP Advanced features..."
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by spliner on 2008-02-08
I've been reading through the forums for the last couple of months, and have finally been able to set up my SAMBA PDC with an LDAP backend thanks to everyone here and especially to Richard at [http://www.rrcomputerconsulting.com](http://www.rrcomputerconsulting.com) (I highly recommend his tutuorials for beginners).

Now, I need to set up some of the advanced features that Richard didn't cover in his tutorial.  I'm still reading and sifting through the forums, so if it's been covered in detail, please forgive the repeat questions!

My network consists of the following:

1 PDC (SAMBA + LDAP) - Up and running now, doing authentication only (Ubuntu 7.10 Server)

40 Workstations - Windows XP Pro

2 Workstations - Windows Vista Business

1 Network Printer (Savin C3535)

I need to have several things working before I add all the workstations to the domain controller:

1)  Remote storage of the My Documents folder.  I've been experimenting with this, and I think I have it working just fine, but it required some changes on the XP box I was working with.  How do I do this automatically with a logon script?
2)  Logon scripts.. how?  I assume there's a setting in the smb.conf, but I'm still somehat confused about what to change in there since I'm using LDAP as well.  The PDC is working thanks to Richard's guide, but there are things commented out in the smb.conf file that look to me like it shouldn't be (like domain logins = yes).  I need to map drives, relocated both their My Documents folder and their e-mail store folder to their home directory on the server each time they log in.
3)  Roaming profiles.. since the My Documents folder and e-mail folders are going to be located on the server.. how do I activate this features so they can move anywhere in the network and have their files/programs?
4)  What about programs that don't save their data in My Documents?  How do I store their data on the server so that they work with the roaming profiles?
5)  I have a 10/100BT network... is that going to handle 40 roaming profiles at once?  Or is it going to slow to a crawl?  Should I forget roaming profiles and just stick with the My Documents folder and/or the e-mail store being on the server?
6)  After following Richard's tutorial, the server itself is slow resolving DNS names.  It works, but it's slow.  Since I used the server's IP address for it's first nameserver (as the tutorial instructed) it's almost as if it hangs on it for a couple of seconds and then goes on to my ISP's nameserver which is second in my list.  How do I make Bind9 become a real DNS server so that it can also resolve names on the Internet and not just on the local network?  Workstations are not resolving at all at this point unless I add in a secondary DNS server from the ISP in their config.

I think that's about it for the moment. I will be happy to write all of this into one huge guide once it is finished and post it for everyone.  I'm taking notes and writing the guide as I go.

---

### Post by spliner on 2008-02-11
For those of you who came across this post, and would like to see the progress of a tutorial like this, written by Richard over at [www.rrcomputerconsulting.com](www.rrcomputerconsulting.com), hop on over to this thread and enjoy!

[http://ubuntuforums.org/showthread.php?t=640760]("http://ubuntuforums.org/showthread.php?t=640760")

---

