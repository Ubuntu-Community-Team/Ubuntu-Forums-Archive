---
title: "samba question"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by benner on 2008-08-25
i just did a fresh install on my work machine. i open the network, select the correct one, it lists all the machines on the network fine.  when i select the server ('warehouse') where everything is, nautilus comes up with nothing--just blank.  i had other machines that worked fine out of the box, so i am not familiar with how to configure anything here. i did a search and am still working on it, but if anyone can help me out, i would appreciate it. our network manager is suspicious of me for installing linux and i will have to go back to (horrible!) vista if i can't get this sorted quickly.  thanks in advance...

---

### Post by bab1 on 2008-08-26
> **benner said:**
> i just did a fresh install on my work machine. ...
Are you saying that you installed Ubuntu and are now trying to browse for shares on a Windows network?

If so, you need to install "smbfs". This is the client used to browse for the shares.  From the terminal:```
sudo apt-get install smbfs
``` This should install the client and the needed dependencies.

Samba is a server to allow Windows clients to access files on a Ubuntu host.

---

### Post by Iowan on 2008-08-27
There is (was?) a [gvfs bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903") that doesn't allow viewing just the server - you need //server/share.

[Here]("http://ubuntuforums.org/showthread.php?t=895054") is the thread where I found the link.

---

### Post by benner on 2008-08-30
thanks. but it didn't work.  still blank. i installed the tools. i edited the config. nothing yet.

---

### Post by benner on 2008-09-08
still nothing? again, when i installed ubuntu last year, the network appeared and i was easily able to select the machine i wanted to access. i had a login/password set up in windows to access the network. when i installed ubuntu, i created an account with the same login/password and voila!

now, i can't access anything. i am a teacher, test-driving ubuntu in my classroom, still trying to convince the administration to stop pirating all their software and to try making the switch. but my students and the other teachers depend on having access to network drives.

this should be a no-brainer. if i can't solve this, i don't have a chance. please help.

---

### Post by gregphil on 2008-09-08
Long standing bug(s):

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351)

---

### Post by benner on 2008-09-10
unbelievable that this bug has been around so long. so if i understand correctly, no one can view windows shares out of the box in hardy because of a bug that has been around for 6 months? i've installed on 7 machines recently and none of them can browse network folders. the folders all appear empty. there must be a million people using ubuntu machines on windows networks. are we all having the same issue?

---

### Post by gregphil on 2008-09-10
Yep, thats the state of things.  

At least the gnome developers have finally realized their gvfs library needs fixing:

[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

---

### Post by babarehner on 2008-09-30
interesting about the Samba question. I also am a teacher with a classroom of ubuntus installed on top of Virtual PC 2007. The temporary workaround I am using is a web server with http upload- that way students can get their files up and down. This allows all students access to files they need but I coded the http uploader to only give them access to their own directory. Also Windows Server 2003 has an option for Linux/Unix but I have not gotten around to checking it yet, Good luck

---

### Post by benner on 2008-10-29
i now have the intrepid RC running (fresh install) and still have the same problem.  2 things are keeping me from switching full time on my work machine and installing in my classroom:

1) we have no access to our files on the network

2) i can't connect to any of the NEC projectors in the school, wired or wireless.
(here's my thread on that one:)
[http://ubuntuforums.org/showthread.php?t=957170](http://ubuntuforums.org/showthread.php?t=957170)

no luck so far on the forum here with either of these issues.  any help will e appreciated and will lead to 17 new grade 5 ubuntu users.  your assistance will be appreciated...

---

### Post by dmizer on 2008-10-29
NEC projectors ... no idea there.

As for connecting to the network shares, please see the second link in my sig.

---

### Post by HDTimeshifter on 2008-11-01
So they didn't fix this bug in 8.10?  I just upgraded on Oct. 30 and still get a blank folder when I try to browse my Vista share.  I have a network with a Vista laptop and an XP server and an old XP desktop as well as my main Ubuntu PC.  The laptop will stay with Vista, but I'd like to reformat the server with Ubuntu and possibly the desktop with Ubuntu if everything works fine in Virtual Box on my Ubuntu PC.  The plan is to do everything through my main Ubuntu PC, but if I can't access my Vista laptop, I have to keep XP on either the server or desktop in order to access the Vista laptop for backups, etc.

I tried the following procedure: [http://blogs.zdnet.com/Bott/?p=238](http://blogs.zdnet.com/Bott/?p=238) but when I tried to make the link, got "Operation not permitted" error:
link /mnt/vista_public ./vista_public

Maybe if I can just get the link command to work?

---

### Post by rstewartmailacct on 2008-11-01
Hi, 

I also have tried SMB4K and it has errors.  Anyone get this to work on Intrepid?  It also did work on Feisty because I have a box with Feisty that I haven't upgraded.

Thanks

---

### Post by dmizer on 2008-11-01
> **HDTimeshifter said:**
> So they didn't fix this bug in 8.10?  I just upgraded on Oct. 30 and still get a blank folder when I try to browse my Vista share.  I have a network with a Vista laptop and an XP server and an old XP desktop as well as my main Ubuntu PC.  The laptop will stay with Vista, but I'd like to reformat the server with Ubuntu and possibly the desktop with Ubuntu if everything works fine in Virtual Box on my Ubuntu PC.  The plan is to do everything through my main Ubuntu PC, but if I can't access my Vista laptop, I have to keep XP on either the server or desktop in order to access the Vista laptop for backups, etc.

I tried the following procedure: [http://blogs.zdnet.com/Bott/?p=238](http://blogs.zdnet.com/Bott/?p=238) but when I tried to make the link, got "Operation not permitted" error:
link /mnt/vista_public ./vista_public

Maybe if I can just get the link command to work?

If you are able to access shares on the other XP computers, but not Vista, the problem is most likely Vista rather than Ubuntu.

---

### Post by bab1 on 2008-11-01
I don't think Vista is broken.  It does use a stronger encryption scheme ie; ntlmv2

See if [**[COLOR="Red"]this[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=954691") helps.

Edit: Here is another [**[COLOR="Red"]reference[/COLOR]**]("http://lists.samba.org/archive/samba-technical/2007-February/051456.html")

---

### Post by jonandrews on 2008-11-02
So many people have added to this post that there is obviously a real problem. All I can add to the debate is that is not present on ALL installations. I have done two clean installations of 8.10 on different machines in support of updating my networking guide:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

Both installations have worked fine, exactly as described in the guide for 8.10 / XP networking.

In the past, I have seen this 'blank' response to clicking on a shared XP folder as an intermittent problem, but not since 7.04, I think.

---

### Post by bab1 on 2008-11-02
@jonandrews,

> Both installations have worked fine, exactly as described in the guide for 8.10 / XP networking.

This problem is related to MS Vista.  With Vista MS upgraded their login encryption scheme.  You can upgrade XP to the Vista encryption.  That is what my posts point out.

---

### Post by jonandrews on 2008-11-02
@Bab 1
Point taken.  I did do trials with 7.10 and Vista networking with no problems, but I've not tried with later versions of Ubuntu. I don't use vista day-to-day, so I'll have to set up a vista machine and see if I can duplicate the issue with 8.10.

---

### Post by jonandrews on 2008-11-08
Further to the earlier comments that the 'blank' response error is confined to Vista , by luck I was asked to set up a brand new Vista Home Premium SP1 pc for a friend, so I added it to my network to test with Unbuntu 8.10. 
In the Vista 'Network & Sharing centre' I had the following settings:  Network Discovery = on, Workgroup=Workgroup, File Sharing=on, Public Folder Sharing=on, password protect sharing =off.   
I have to report that I had no problems at all, with Vista, XP, & Ubuntu 8.10 pc's able to fully access files on each other normally. So, I guess I go back to the comment that all I can add to the debate is that the problem is not present on ALL installations.

---

