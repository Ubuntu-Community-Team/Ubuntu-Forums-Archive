---
title: "Accessing Windows Vista shares from Ubuntu"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by richbl on 2007-04-30
Hello all,

After much searching and head-scratching, I am still quite unable to access Vista shares from Ubuntu.

I'm aware that Vista now uses NTLMv2 where XP used NTLM/LM for authentication. However, it is also the case that Samba 3.x should also authenticate using NTLMv2. As I'm running Feisty, my Samba version is 3.0.24, and I've set client NTLMv2 auth = Yes in smb.conf.

So... my question is this: how do I successfully connect to a Vista share from Ubuntu?

Currently, here's what happens when I attempt to access a Vista (Home Premium, workgroup network) share:

Does: 
0) from Places, choose Network
1) choose server (e.g. Vista_box)
2) choose share (e.g. Rich)
3) share contents are correctly displayed
4) choose share folder (e.g. Documents on Rich share)
--error message displayed: Nautilus cannot display "smb://Vista_box/Rich/Documents"
--Documents folder icon is now changed into a text (generic) icon (?)

Should:
--be able to access smb://Vista_box/Rich/Documents.

Thanks.

rich

---

### Post by richbl on 2007-05-02
Bump...

Here is another way to ask my initial question, and an update on my research into the issue:

**Has anyone running Feisty had success correctly accessing Vista shares?**

Correctly is defined as with full NTLMv2 authentication.

I am aware of some partial solutions that have Vista degrade authentication to NTLM and/or LM. I personally haven't had luck with this solution (though it's really a stop-gap method of side-stepping the issue). On this last point, has anyone had success with Kerberbos authentication?

So far, my research of this issue has suggested the following:

[LIST]
[*]Native Vista authentication (NTLMv2) is incompatible with Samba 3.0.24 (shipped with Feisty). It *seems *that the upcoming Samba drop (3.0.25) *might *improve this problem, as noted in the 3.0.25rc3 Release Notes.

What's puzzling to me on this point is that my reading suggests that Samba 3.0.24 does indeed provide client NTLMv2 authentication. Clearly, I'm missing something here (either that, or the current implementation is incomplete or strangely incompatible with Vista).


[*]This issue is not immediately tied to Ubuntu inasmuch as it is a problem with Vista's new authentication defaults. Mac OSX users are evidently having similar problems.
[/LIST]

Any additional details or tidbits of information are much appreciated.

Thanks.

---

### Post by swells5 on 2007-05-03
you are not alone.
I have the identical problem with Vista Home Premium.
I have changed the registry value for LMcompatability from 3 to 1 - no change
I am with samba 3.0.22 dapper drake and have enabled NTLMv2 as directed at several sites found by googling.
I am sure that you are on the right track and I can not help you solve the problem yet, but hope that if more people show up with this issue we might get some help.
If you find the answer please post it here and I will do likewise.

---

### Post by clarke-pj on 2007-05-03
I'm having the same problem and done all the above but it seems to be nautilus is the problem.
I've just upgraded to Feisty but on edgy I just got the recurring login prompt.

As a temporary solution (hopefully) I'm using the following mount script

sudo mount -t smbfs -o username=<user>,password=<pwd> //<myVistaMachine>/<myshare> /mnt/vista

---

### Post by luckyaba on 2007-05-04
use cifs for the filesystem. i have my vista fileserver mounting on boot perfectly.

---

### Post by richbl on 2007-05-20
Just a quick update: it appears that at least part of the problem beyond the authentication issues already pointed out is that there's a new "feature" in Windows Vista that makes use of symlink-like structures called "junction points." A junction point is a redirection to an alternate file location. 

So, under Vista, the legacy "My Documents" folder is now hidden and a junction point created such that access to My Documents now points to the new Vista Documents folder. The same holds for any of the pre-Vista "My" folders (e.g. My Videos).

Interestingly, when any user (Windows or otherwise) attempts to directly access these junction points, a "permission denied" message is issued. See **[http://support.microsoft.com/kb/930128](http://support.microsoft.com/kb/930128)** for details on this issue.

Unfortunately, this new feature in Vista is confusing the current release of Samba (3.0.24) such that junction points are not identifiable, making it very difficult to discern whether Samba is looking at a junction point or a standard directory structure. See **[https://bugzilla.samba.org/show_bug.cgi?id=4557](https://bugzilla.samba.org/show_bug.cgi?id=4557)** for details on this Samba bug.

So, where does this put those of us who need to access Vista shares?

In my case, under Feisty, I'm unable to access Vista shares using Nautilus. This appears to be either a strict authentication issue (NTLMv2), or a combination of authentication issues and the junction point issue.

I *can* create a permanent mount point and access Vista shares using CIFS. 

Using CIFS resolves the authentication issue, but the junction point issue is still quite relevant, generating the error message:

[INDENT]**The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "My ___".**[/INDENT]

If anyone can shed any additional light on these issues, please advise.

Until then, I hope this helps.

---

### Post by funkyfreak on 2007-05-28
hey guys... I may be able to shed some light on this..although I cannot copy files from vista to kubuntu I can access my shares and play music files (thats all I've tried).  When I try to copy I get an error that the file doesn't exist. ?? I guess that is due to the above explination. 

Vista has new networking features... to allow access to the files on vista open the network & sharing center and:
1) make sure the network is set to 'Private' - **public will not allow network discovery**
2) Make sure that 'Password protected sharing' is off -** if turned on you have to have an account on the host machine to access**
3) Make sure the first 3 parts of the 'Network & Discovery' are turned on.  also ake sure the proper exceptions are allowed through the firewall if any is installed.

thats about all I did and then I opened the samba share folders and was able to browse and access all folders (sometimes was required to give vista user credentials) and play music... but I cannot copy them to my home folder.  I should also add that the share I am accessing are on a 2nd drive and my 'music' folder is vista is redirected to there...  maybe try sharing a different folder.

Hope this helps someone... and I hope someone can help me!! lol

also want to add that I am running a clean install of vista ultimate.. 

funkyfreak

---

### Post by ar3ac on 2007-06-18
I resolved recompiling on my feisty 

the "3.0.25" version of samba and the "libgnomevfs2" .

Now nautilus rocks accessing windows vista shares!!

bye,

Luca

---

### Post by hyapadi on 2007-06-21
> **ar3ac said:**
> I resolved recompiling on my feisty 

the "3.0.25" version of samba and the "libgnomevfs2" .

Now nautilus rocks accessing windows vista shares!!

bye,

Luca

So it seems the solution is as simple as update?

I wish they will update the repository soon so that I don't have to do recompiling.:)

---

### Post by rumour on 2007-07-19
> **ar3ac said:**
> I resolved recompiling on my feisty 

the "3.0.25" version of samba and the "libgnomevfs2" .

Now nautilus rocks accessing windows vista shares!!

bye,

Luca

Can you tell the steps involved .... thanx in advance

---

### Post by pyxu619 on 2007-08-02
> **ar3ac said:**
> I resolved recompiling on my feisty 

the "3.0.25" version of samba and the "libgnomevfs2" .

Now nautilus rocks accessing windows vista shares!!

bye,

Luca


Can you give a detail step-by-step process of recompiling samba and libgnomevfs2??

---

### Post by the_crowbar on 2007-08-09
I just upgraded Samba to 3.0.25. At the same time I upgraded my font rendering. Anyway, here is one way to upgrade Samba and gnome-vfs to support browsing Vista shares.
First setup a pbuilder environment by following steps 3, 4, and 5 from this thread:
[http://ubuntuforums.org/showthread.php?t=206382]("http://ubuntuforums.org/showthread.php?t=206382")

Create a work area for package build:
```
mkdir /tmp/work
```

Finish setting up the pbuilder environment:
```
sudo aptitude install cowdancer pbuilder
sudo cowbuilder --create
```

Download the required source files:
```
cd /tmp/work
apt-get source gnome-vfs2

```

I used the Samba 3.0.25 files from Gutsy. Here is the link to them:
[https://launchpad.net/ubuntu/gutsy/+source/samba/]("https://launchpad.net/ubuntu/gutsy/+source/samba/")
You need the three files near the top of the page. The names are: samba_3.0.25b-1ubuntu1.dsc, samba_3.0.25b.orig.tar.gz, samba_3.0.25b-1ubuntu1.diff.gz, 

Save these files in /tmp/work.

Now build the new samba package:
```
sudo cowbuilder --build samba_3.0.25b-1ubuntu1.dsc
```

Now install the new samba packages:
```

cd ~/pbuilder/result/
sudo dpkg -i libsmbclient_*.deb samba-common_*.deb smbclient_*.deb smbfs_*.deb

```

_After_ the samba packages are installed it is time to rebuild gnome-vfs2:
```

cd /tmp/work
sudo cowbuilder --build gnome-vfs2_2.18.1-0ubuntu1.dsc

```

Now install the new gnome-vfs2 packages
```

cd ~/pbuilder/result/
sudo dpkg -i libgnomevfs2-0_*.deb libgnomevfs2-bin_*.deb libgnomevfs2-common_*.deb libgnomevfs2-extra_*.deb

```

That is how I upgraded nautilus to be able to browse Windows Vista shares. There are other ways (dpkg-buildpackage, etc). Maybe someone with more experience with Ubuntu can recommend a better way.

---

### Post by swells5 on 2007-08-20
to install samba 3.0.25b on Ubuntu which works for window vista sharing:
go to [www.samba.org](www.samba.org)
scroll down untill you get to a link to "Samba 3.0.25b source code"
click this link to download - samba-3.0.25b.tar.gz
hopefully this will end up on your desktop as mine did
right click this file and chose "extract here" and a new file will appear on your desktop called - samba-3.0.25b

open a terminal window
type "sudo apt-get install build-essential" to make sure that you have the necessary programs to compile samba
when this is finished ( a few minutes) type "cd /home/your home folder name/Desktop" (mine is a capital D on Desktop)
type "cd samba-3.0.25b" then "cd source"

now you are ready to install samba so:
type "./configure"
lots of things will happen
when its done type " sudo make install"

after this I restarted my computer, I checked my /etc/samba/smb.conf file, which had not been changed, and when I opened nautilus, I had access to all the files on my Vista computer.

I hope this works for all
Steve
I tried it on another computer and this failed.
I reviewed my notes for the first computer and found that I had tried to install the .deb binaries prior to the above install.
So on the second computer, i went back to samba.org and scrolled down to the link - Binary_Packages download area.
I chose debian from the list and then "samba" and then "3"
I started at the top and clicked each package.
One install required libreadline4 be installed first, which I found by googling libreadline4 and installing that package.
then I continued installing each package that would install.
now both computers will browse my vista home premium computer shares.
Steve

---

### Post by dannyboy79 on 2007-08-20
it's not clear when to do steps 3, 4, 5 from the guide, so I went to do them and when I typed in the sudo nano ~/.pbuilder, it was blank, so I thought I had to install pbuilder and cowdancer first, well I did that and then the command regarding cowdancer is in the same box so I did that, then all of a sudden I see that it was looking for ~/.pbuilder file, then I realized I probably should have had one there with the contents from that above link. So I hit ctrl-c to stop that cowdancer command, then I went and followed steps 3, 4, 5, and now I am geting this error:
sudo cowbuilder --create
 -> Invoking pbuilder
/home/daniel/.pbuilderrc: line 28: unexpected EOF while looking for matching `"'


can anyone help please, I am sick of Nautilus Network browsing not working half the time. thank you. here is what my ~/.pbuilder file looks like
[http://www.pastebin.org/894](http://www.pastebin.org/894)

I would like to point out that I always thought that EOF meant that I either needed to hit enter so that it would create a new line that didn't have anythign on it OR that it was I did have an empty line on the end and that I needed to remove it by going to it and hitting backspace. I ahve tried both those and I still get that same error. Help please.

---

### Post by RDaneel623 on 2007-08-21
Hey Dannyboy, 

I had the same problem. After much trial and error I figured out what was wrong. When you used Nano to create the Pbuilderrc file you copied and pasted the code from the Howto guide. When you copy and pasted Nano put a line break in the following line: 

#OTHERMIRROR="deb ${MIRRORSITE} ${DISTRIBUTION}-updates ${COMPONENTS}|deb ${MIRRORSITE} ${DISTRIBUTION}-security ${COMPONENTS}"

There cannot be a line break, edit the file and make sure that that entire statement is on a single line. It'll work perfectly after that.

---

