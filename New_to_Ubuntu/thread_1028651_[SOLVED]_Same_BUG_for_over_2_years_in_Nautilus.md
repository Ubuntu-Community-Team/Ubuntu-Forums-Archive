---
title: "[SOLVED] Same BUG for over 2 years in Nautilus"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Kellemora on 2009-01-02
Hi Gang

Besides myself having a MAJOR ISSUE with Nautilus Bugs, I've seen posts back as far as two years ago talking about the same Bugs.

Yet I see no information anywhere that anyone is working on trying to resolve the problems with Nautilus.

There are workarounds to get around these BUGS, but they are a royal pain in the backside to have to do 40 times a day!

Once again, I've spent over 7 hours trying to get Nautilus to work properly.  Rebooted one machine over 35 times with no success.

It would be nice to know someone is actually looking into the problem with Nautilus!  
Rather than the problems being ignored year after year after year!

And NO the problem is NOT Samba, NOT the smb.conf file, not the Networking, the problem is directly WITH the Nautilus file browser.  It flat out don't work properly, and when it don't work properly, we lose a whole day of work as EVERYTHING must be done MANUALLY.  Eight computers times Five users = 40 times a day a single file must be mounted MANUALLY and if each user is dealing with three or four files per day, the number of times they must be mounted manually quickly jumps to over 120 times per day that the work must be done MANUALLY due to a Major BUG in Nautilus.

Even though CentOS has little to no support on their beginner issues, at least it works properly, once set up and when one needs it to work.  Ubuntu works three to four days in a row, then won't work, sometimes 3 cold boots will get Nautilus working again.  Other times, you can keep rebooting all day and it won't work.  Next day, it might work fine again.

THIS is a VERY SERIOUS PROBLEM!!!!!
Why is it NOT being worked on for over TWO YEARS NOW?????

TTUL
Gary

---

### Post by LowSky on 2009-01-02
maybe you should post the issue on [https://launchpad.net/](https://launchpad.net/)

also are you trying to mount a file or share it? What exactly is the bug you really dont explain that. we can t hepl without more info

have you tried using a dffeernt file manager?

---

### Post by Kellemora on 2009-01-02
Hi Low Sky

I've reiterated the complete problem numerous times.

Nautilus will work fine for a week or two, then suddenly not show any of the shared files or folders anymore.

You CAN Ping all the machines.
You CAN type smbtree in a command line and ALL of the shares appear there just fine.
You CAN go to Go/Location and type the IP address to make them appear manually.

But when they stop appearing in Nautilus, it sometimes takes 3 cold boots to get them back, if they will come back at all that day.  If not, 50 cold reboots won't bring them back until tomorrow, then all will be fine again for a week or so.

This is a Hard Wired Network that functions properly!
No changes have been made between when Nautilus works right and when it don't.  It has a MIND OF ITs OWN as far as when it will work and when it won't.

I've gone back over two years in searching for answers and find the exact same problem listed by NUMEROUS others.

The Issue is STILL UNRESOLVED!  Plain and simple!

Now, if someone can't get Worlds of Doom to play in WINE, a solution will be coming down the pike in about a week or less.
Or if some MP3 player won't work, it will be fixed in only a couple of days.

But something as SERIOUS as a MAJOR BUG in Nautilus just goes on unresolved year after year after year!

If networking WORKS and Samba WORKS, and you can access your files every way except through Nautilus unless you do it manually.  Then the problem MUST lie with Nautilus!

And NOTHING you can change elsewhere is going to FIX the problem with Nautilus, only mess everything up so nothing works until restored back to the way it was before Nautilus made you think the network was down.

I have 8 computers here, 6 of them running Ubuntu.  The configuration files are IDENTICAL except for machine specific changes.  If everything works FINE for a few weeks, then suddenly one machine cannot see the network through Nautilus for a day or two, but all the rest can.  OR if everything has been working fine for a month or more, then suddenly NONE of the Ubuntu machines can see shares through Nautilus.  But they can Ping, they can see the shares in smbtree and they can access them and mount them Manually.
Where would YOU say the problem lies?
If NOT with Nautilus, then where?

Is there some other Program that can be used besides Nautilus?
Besides a web browser of course!

I'm peeved because NOBODY is working on this ongoing for too long issue!!!!!

TTUL
Gary

---

### Post by steeleyuk on 2009-01-02
Maybe you could ask for a refund.

Are the same people who were having problems two years ago still having the same problems? Are the bug reports up to date and relative to the current version of Nautilus? Have bugs been filed on the GNOME bugtracker as well as Launchpad? Have you considered trying to fix it yourself?

I can understand you're frustration, bugs which persist, even after being reported and confirmed are a pain. Though capitals and more than 15 exclamation marks won't get it solved.

---

### Post by dwasifar on 2009-01-02
Try THUNAR!!!  It may HELP YOU!!!!!!

Oh, sorry - your agitation is contagious.  Try Thunar and see if that helps.  

```
sudo apt-get install thunar
```

If you have the same problem with Thunar, then Nautilus is not the issue.

---

### Post by chrisod on 2009-01-02
> Maybe you could ask for a refund

Nice one :)

---

### Post by Kellemora on 2009-01-02
Hi DW

I loaded XFE and ROX and neither of them have the problem!

All the shares show up in both of them just fine.

WHEN the shares show up in Nautilus, it works just fine too!
I've been slowly moving and resorting files into a new file server for the last week, no problems.

Then last night Nautilus decided to go belly up again!
I got all the machines up and running properly again, except this one that I use the most.

My three cold boot trick didn't work this time, and when it don't, 50 boots won't fix it.
However, if I shut down overnight, by tomorrow, Nautilus will hopefully be working again.

Everything usually goes along just fine until we get some upgrade or update or security update, then Nautilus stops finding the shares again.

For ME, it means instead of being off work on Saturday, I will have to WORK all day Saturday to catch up with the work that didn't get done today as planned, due to the Bugs in Nautilus!

Since I started using Ubuntu at work, I often burn the midnight oil due to problems and 90% of those are directly related to Nautilus not showing the shares and having to manually mount every single folder I need to check, move or whatever.

So YES, it's very frustrating and I do get quite POed about it!

If it worked all week, it should have worked today too!

And it seems it always happens when I'm already swamped the most!

I'm very seriously thinking about dropping Ubuntu and moving over to CentOS.  It has no support, but at least it usually works right once you figure out their backwards methods of doing things.

TTUL
Gary

---

### Post by chrisod on 2009-01-02
If Ubuntu doesn't work for you then you should use a different OS. However, you rants here are wasted electrons. We aren't the Nautilus development team.

---

### Post by infinitejones on 2009-01-02
Have you tried using NFS instead of Samba? I appreciate there may be a reason why you can't, but here's a great how-to...

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

It takes about two minutes per machine to set up the /etc/exports and /etc/fstab files and I've never had a problem with it, ever, using Nautilus.

---

### Post by PmDematagoda on 2009-01-02
As mentioned previously, we aren't the Nautilus development team. If you seriously believe that the culprit is Nautilus then you should *report* this bug yourself to them either through Launchpad(If it is Ubuntu-specific) or through their own Bug tracker(If it is not Ubuntu-specific).

By the way, is this [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=530394") similar to what you have?

---

### Post by Kellemora on 2009-01-02
Hi IJ

I still have 2 XP machines here on-line & 6 Ubuntu machines!

As soon as we are RID of the last two Mickey$oft machines, I will use NFS!

Thank You

TTUL
Gary

---

### Post by Kellemora on 2009-01-02
Hi PmD

I thought Nautilus WAS an Ubuntu program!

It's shown in Synaptic WITH Both the Ubuntu Logo in front of it and the Ubuntu name WITHIN the description of Nautilus.

I noticed most of the listings DO NOT have the Ubuntu Logo, some have the Logo, some have the Logo and the Ubuntu name associated with them.  Those without the logo or name I assumed were 3rd party programs available to Ubuntu users in the repositories.

If I see a Chevrolet Logo on a car, I don't ASSUME it's a FORD!
However lately I can probably assume it's made in China, hi hi.....

About the Bug Report, I'm not using wireless so am not switching between different LAN methods.  But the resultant problem that particular bug mentioned is identical in what I see.  What goes on under the hood I have no idea.

But I did pick up something to give a try to see what happens, although it seems like a cold boot up would give the same result.

Is it safe to try $ killall gvfsd-smb-browse ?????

I'm already trying stopping and restarting the network, stopping and restarting Samba, and rebooting.

My IP numbers are NOT static, but they have remained the same on each machine now for 3 months.

If I can PING each machine using their IP number.
If they show up correctly, none missing using smbtree in terminal.
And I can manually mount each share using Go/Location.
Then they should appear when I hit Places/Network......

If not, what setting needs to be changed, and where?

I'm new to Linux and newer to Ubuntu, only 3 months under my belt is all.  Can pretty much figure out how to do things on my own now, but only up to a point.

I've read more man pages and wiki's than I have customers orders in trying to convert my office over to Ubuntu successfully.

I've even considered paying for Ubuntu Support!
But the folks there are more honest than I realized!
They don't know what to do either!

TTUL
Gary

---

### Post by dwasifar on 2009-01-02
> **Kellemora said:**
> I thought Nautilus WAS an Ubuntu program!

It's shown in Synaptic WITH Both the Ubuntu Logo in front of it and the Ubuntu name WITHIN the description of Nautilus.

I noticed most of the listings DO NOT have the Ubuntu Logo, some have the Logo, some have the Logo and the Ubuntu name associated with them.  Those without the logo or name I assumed were 3rd party programs available to Ubuntu users in the repositories.

Not exactly.  When you see an entry in Synaptic with "ubuntu" embedded in its name, this usually means the package contains some ubuntu customization.  Often the customization is just about how or where the package installs itself, or trivial details of appearance.  Nautilus, specifically, is not an invention or creation of Ubuntu.  Like most things you find in Linux distributions, it's an independent project and can be found in many, many distros.

> **Kellemora said:**
> If I see a Chevrolet Logo on a car, I don't ASSUME it's a FORD!

Bad analogy.  :)  Doubly so because it's quite common to see what is basically the same car with a different nameplate.  

> **Kellemora said:**
> If not, what setting needs to be changed, and where?

I think the first setting you need to change is to turn down the "strident and demanding" knob on your keyboard before you post questions.  :)  :)  :)

Okay, seriously.  If I understand what you are trying to do, you have a local network of machines you are trying to convert to Ubuntu, and you want them all to see each other's shares; correct so far?  Using Samba, the shares are intermittently dropping off.  Right?  Further, you are connecting these shares using the GUI tools and expecting them to be more permanent than they are.  If I have any of that wrong, please correct me.

If I were in your situation, these are the things I'd try:

1) Stop using Samba to network one Linux machine to another.  Use nfs, that's what it's for.  Samba is an emulation of Windows SMB; there's no good reason to use it if you're not interfacing with a Windows box.  You can still use Samba on the same machine as nfs if you need to communicate with a Windows network too; but use nfs between Linux boxes.

2) Set your router up to assign static IPs to your machines by MAC ID.  Yes, I know you say that the IP assignments have not changed for some time - as far as you know.  But your problem might be related to when your router's DHCP server renews the leases on the addresses.  Granted that is a long shot, but setting static IPs eliminates this as a potential cause.

3) Define any shares you want persistently mounted in the machine's /etc/fstab file.  There are plenty of howtos about this if you search the forums.

4) Consider setting aside one machine to act as a file server, and have everyone else connect just to that, rather than all connecting to each other.  It's much more consistent and easy to manage.  You can give each user a "share" folder on the server and mount it permanently on their machine in /etc/fstab (see above).

We do all wish you luck on this, really, and there are plenty of people who will help if they can.  But please temper your sense of outrage.  Nautilus is a well-established package, integral to most distributions that use Gnome, so it's unlikely that a really major bug would slip through with no one caring.  It's far more likely that you have some configuration problem that just appears to be a Nautilus bug.  This is not to say that it's trivial or unimportant; we would all like to see you solve it.  But it's not likely to be what you think it is, and it doesn't help to get mad.

---

### Post by gn2 on 2009-01-03
> **Kellemora said:**
> 
I've even considered paying for Ubuntu Support!
But the folks there are more honest than I realized!
They don't know what to do either!

TTUL
Gary

The folks here do know what to do, the solution to your problem has already been posted in this thread.

(in the first reply)

---

### Post by Kellemora on 2009-01-03
Hi Dwasifar

Sorry about getting so grumpy!
Losing my weekends and burning the midnight oil tends to put one on edge!

FWIW, I am in the process of building a new File Server, just so we don't have to look to all the other machines.  I've set it up considerably differently, file system wise that is, than everyone is used to, which means resorting all of our data into new folders.  A major undertaking to start with!  Being more complicated with Nautilus acting up just when I set aside time to do the work of moving things around.

One of the reasons I AM building a file server is so that I can automount the file servers primary working folders to each computer and do away with each person having to connect to the drives on certain computers for their data.

I even had thoughts of going to a Main Server for everything, but I'm not afraid to admit that I'm not smart enough to take that plunge yet!
What I'm calling a File Server is just a computer that I dumbed down to the bare essentials, but still with a GUI for my sake, hi hi.  Installed two 500 gig hard drives internal, and two external 500 gig drives for the mirror of the internal drives.  The external drives are then mirrored off-site in case the place burns down or gets robbed, whatever.

I DID NOT know I could use BOTH smb and nfs on the same machine at the same time.  So that was a HELPFUL RESPONSE to me!

You pretty much pegged my layout!  I have one XP-Pro machine that I use for my company accounting.  It's NOT usually on-line.
But am working with a couple of Linux based accounting programs to see which one I will switch over too.  Wanted to do this at the first of the year but I'm still uncertain about which program I will chose.  When I do and everything is running smoothly XP will be gone from that machine too.  That machine I do not count in my mention of 6 Ubuntu and 2 XP machines.
The two XP machines are Front Office for POS and to run Doze only hardware I purchased a long time ago.  As those items are replaced, they WILL be Linux compatibles or they won't be replaced.

Before I started building the file server (which is in EXT3 format by the way), which already has most of our things on it already as I speak.  Here is how our office used to operate.
I used all of my older slower computers for the purpose of holding hard drives for file storage.  They were divided up fairly well.  One computer held client graphics, another the files that were under construction and client text data, and the third one the completed pamphlets, newsletters, etc.
So, when someone was working on a pamphlet for example, they needed to draw the clients images from one computer, text data submitted for this issue from a second computer, store their work back onto that computer, different drive, and when the job was finished it got put on yet another computer.  Each of those computers internal drives were mirrored to externals, then the externals were mirrored off-site.  Mirrored because I hate backup sets.  It's like RAID 1 without a RAID controller to die!

With the file server, everyone only needs to look to ONE Location for all the files, which will stop a LOT of headaches.

I did play with Edubuntu for a short time, only to find it wouldn't work for me here.

I have tried static IP numbers for the LAN, still had the same problem with Nautilus not seeing the shares from time to time.

Once I learned Nautilus was NOT an Ubuntu owned program I did place a bug report on Launchpad.
Of an interesting note, there is a BUG in the Nautilus Bug Report system also.  You hit the button, it compiles the data to make the report, then sends you to a non-existent web page so it cannot make the report it was set up by the designers to do.

In other words, it doesn't appear they are keeping up with even the basics of that program.

However, I'm going to digress on blaming Nautilus any more either.  fce and rox was working just fine as I said!  But this morning, from THIS machine, none of them was working.  All the other machines here are working fine though, and they can see this machine too.  But fce didn't find the shares this morning either.  Unless I entered the IP number manually.  That's something that has not happened before today.  But all the shares show up in smbtree just fine, so the network is obviously up and running.

My thoughts, based on a bug report I was directed to regarding wireless networks, is that there must be a location (I don't know about yet) where server or IP information is stored for Nautilus to work.  In any case, I rebooted and fce and rox again work, Nautilus don't, when using Places/Network that is.
It Does See and show the Windows Network Icon and when I click on that it does show the Icon for my WORKGROUP.  But when I click on that, NOTHING.  Normally, all the shares show up along with the page that shows Windows Network on the opening page.

I've had two IT guys from a major company (really major company) take a look see and they too could find nothing wrong with my configuration files.  But they were not that familiar with Ubuntu, but worked with Samba everyday.  Most of the machines in their company are Windows machines, their servers are UNIX.
They don't understand why when all the machines are set up alike, it works for 3 or 4 days then stops for a day or two on one of the machines, only to start back up a day later and work fine for another 3 or 4 days.  It's never the same machine that decides to take a day or two off either, it's totally random.  But when MY machine acts up, especially when I'm already swamped with work and burning the midnight oil because of it.  Yeppers, I get grumpy.  So sorry about that!

Thanks for you help!  I'm going to try that nfs you mentioned since all of the NECESSARY machines here are Ubuntu now as it is.
Front office don't need to see back here, but we do need to access their daily data quite often.

Enjoy the New Year my friend!

TTUL
Gary

---

### Post by dwasifar on 2009-01-05
> **Kellemora said:**
> 
I have tried static IP numbers for the LAN, still had the same problem with Nautilus not seeing the shares from time to time.
How did you go about that?  At the router, or at each individual machine?

On my network I have the IPs assigned at the router.  DHCP is running, but the router is configured to assign most machines a specific IP according to the network card's MAC ID.  The machines themselves still pick up their IPs from DHCP rather than having static IPs locally assigned, but because the router is set up the way it is, their IPs remain constant.

If your router allows this, and you haven't tried it that way yet, see if it helps.  I would do it for every machine that shares resources on the network.

---

### Post by TransitMan on 2009-01-05
A thought here.
Instead of assigning static IP's from the router, give each computer a static IP physically, thereby eliminating the router from handing out IP's, static or otherwise.
Keep DHCP enabled, but limited to say 5 to 10 added machines as needed.
Going this route, you will have IP's on all the machines, and be able to connect to them via the router without the router handing out the IP's.
As far as Nautlius goes, I don't use it to browse my home network. I use Konqueror which works quite well. While you may be a fan of GNOME, installing Konqueror is as simple as going to Synaptic and choosing it and installing. It will come with some KDE libraries, but in the end it might make you life more enjoyable.
Give these ideas some thought.

---

### Post by cb951303 on 2009-01-05
For me, giving local IPs to all computers and than bookmarking smb://LOCAL.IP works all the time. Working through smb:/// is PITA. It only works when it feels like it.

---

### Post by dwasifar on 2009-01-05
> **TransitMan said:**
> Instead of assigning static IP's from the router, give each computer a static IP physically, thereby eliminating the router from handing out IP's, static or otherwise.
It's hard to be completely sure from what he wrote, but I believe the OP has already tried it that way.  That's why I am suggesting doing it from the router instead, to see if he has any better luck.

---

### Post by TransitMan on 2009-01-05
While I won't start a "what did he say", as I to tried to make sense of how he assigned IP's, he has marked this as solved.

Now I would like to know how he solved the problem.

---

### Post by nandemonai on 2009-01-05
Just a thought.. but why not auto mount the shares using scripts rather than relying on discovery?

I used to do the same thing when I was using samba shares (all nfs now) and it worked a treat.

My 2c.

---

### Post by crjackson on 2009-01-05
> **TransitMan said:**
> While I won't start a "what did he say", as I to tried to make sense of how he assigned IP's, he has marked this as solved.

Now I would like to know how he solved the problem.

Yes. Please tell us how you solved the problem.

---

### Post by Kellemora on 2009-01-05
Problem is NOT Solved!

I only marked THIS THREAD as Solved in light of a clearer Post that takes it's place.

TTUL
Gary

---

### Post by crjackson on 2009-01-05
> **Kellemora said:**
> Problem is NOT Solved!

I only marked THIS THREAD as Solved in light of a clearer Post that takes it's place.

TTUL
Gary

Gotcha - I started having problems with nautilus responding after heavy disk activity. Click on a location and nothing happens for several minutes. The behavior continues throughout unless you reboot the machine.

I was hoping you were going to recommend a different file manager that had no such issues.  In fact, I may just try kubuntu and see what happens.  Thanks for the response.

---

### Post by Kellemora on 2009-01-06
HI crj

I switched to wicd I think it's called, but I don't remember why or what that change was for anymore now.  I've got like umpteen zillions irons in the fire this past couple of days and everything has become a blur.

I have a new file server and moving files to it, in different order and system.  I figured while making the change, to update the system to a better filing system.  I think I bit off more than I could chew at once, hi hi..........

Then things that should work just fine, don't!

But I'm learning, the long slow hard way, hi hi........

TTUL
Gary

---

### Post by tjwilli on 2009-02-21
> **Kellemora said:**
> 

But I did pick up something to give a try to see what happens, although it seems like a cold boot up would give the same result.

Is it safe to try $ killall gvfsd-smb-browse ?????

I'm already trying stopping and restarting the network, stopping and restarting Samba, and rebooting.


Gary
FWIW, I just stumbled upon killing the gvfs-smb-browse process. I've had the same issue you describe, where sometime the shares are there, sometimes not. The last few times this has happened, I killed the gvfsd-smb-browse process from the System Monitor, and when I went to the Window workgroup shares, they were all there.****

---

### Post by Kellemora on 2009-02-21
Hi TJW

Glad to hear something worked for you!

Now that I've set up a Data File Server, I have mount on each computer in fstab to place the main shared folder named file-server placed on each desktop on boot-up.

It basically has the same effect as opening nautilus then hitting Go/Location IP# and the shares show that way.

Out of curiosity though, I still check Places/Network about every other day and shares are no longer showing on any of the Ubuntu computers.  But with all of our documents now centrally located, we don't have to jump around to the different computers anymore.

I also toyed around with a few things with the smb.conf file but it made no difference either, just lowered the security level is all, so I put everything back the way it was.

I've been so darn busy I really haven't had much time to play with settings, just trying to keep up with the workload of late.

With Ubuntu, things go a whole lot faster and smoother than they ever did on the Doze, despite the few bugs here and there, hi hi.........

And since mounting the file-server on each desktop eliminated typing in IP numbers things are going even quicker now than ever before.

I don't know if this has anything to do with anything, but I've got a 64 bit computer now with Ubuntu 64 bit loaded on it, and ever since bringing this computer into the working network group, no shares have shown up since in Places/Network on any Ubuntu computer, they show up fine on the two doze machines up front though.  Makes no sense!

Good Luck my friend!

TTUL
Gary

---

### Post by tjwilli on 2009-02-23
I spoke too soon. The other day I got the problem again, killed gvfsd-smb-browse, and tried to go to the network shares again. Nothing. Killed all gvfsd* processes. Still nothing.  I'm thinking I may have a firewall issue on the Windows side, but I'm not sure.
:(

---

### Post by Kellemora on 2009-02-23
Hi TJ

I had a certain ritual I used a couple of months ago, but only because it was working for me, and I even thought I figured out the reason it WAS working back then too.

See if this makes sense to you?

Samba does not normally LOOK at the smb.conf file when you boot up!
Instead it looks at the /var/lib/samba location that contains a binary version of the smb.conf file.  Not humanly editable.

When you boot up cold, samba looks at /var/lib/samba for it's info.
BUT, if you boot up twice in quick succession, it says ut oh, wonder why my owner did that, maybe I should read the smb.conf file this time.
It does and everything seems to work right until you reboot again.
Then it's back to reading the /var/lib/samba configuration again.

Here comes my three boot trick.  If you boot up again a THIRD time in quick succession, samba takes the smb.conf file and rewrites the /var/lib/samba configuration with the changes made to smb.conf

Then after that, it works properly, and this usually lasts until the NEXT upgrade comes down the pike and you install it.  And also there is the BUG with Nautilus not showing shares in Places/Network.

I'm no programmer, don't understand whats under the hood, but I have eyes and ears so to speak and can say what I see seems to be happening.

I filed bug reports giving my scenario above which was duplicable every time shares would not show up for me on all the machines.

However, a couple of upgrades came down the pike and it seems the three boot method no longer worked and the only problems I was having was with Nautilus Places/Network, Go/Location always has worked for me.

Now, since I got the new 64 bit computers, shares do not show on ANY machine here, except the DOZE machines without using Go/Location IP method.  Shares just don't appear in Places/Network at all anymore.

It could also be that we RETIRED one of the machines too......
There is a possibility that somehow during set-up, the machine we removed appointed itself as HOST.  In the old days one needed ONE HOST and all the rest clients.  But I have NOT known this to be true at least for a Decade if not longer.  I've never set a host at all, just set up simple file and print sharing and everything worked, no matter which machines were added to or pulled from the LAN......

I do think it is interesting that smbtree shows all the shares, no problem, and the Doze machines can see the shares, no problem, but not a single Ubuntu machine can see shares through Places/Network anymore, I must use Go/Location and the machines IP number I need to access to see all the shares on that machine.  And smbfs cannot be installed.  If it is 1/3 of the shares, give or take, will not appear.

So for me going a data file server route and mounting the primary file during boot on each machine has been the best way to go.  It just works without problems now, so I don't mess with it anymore!

TTUL
Gary

---

