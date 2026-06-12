---
title: "Newbie with networking frustration"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by jstevans on 2008-09-18
Hi all,

First, just so you know I'm not trying to waste people's time, I have searched these forums and the web for help, found a lot of information, none of it has solved my problems.  If I've missed something brain dead obvious please forgive the foolish question.

Second, I have a lot of networking and PC experience, all flavors of Windows from 1.0 onward and Mac from OS 7 onward.

Third, I tried Ubuntu a couple years ago and ended up giving up, too little time available to work with it and too frustrating.  I have recently come into possession of a spare PC and figured I'd give Ubuntu another try both for my education and to see if it really was as easy and powerful as people have been saying.

With that preamble out of the way, here's my two-fold problem - a) my Ubuntu machine cannot "see" my Windows 2000 and Windows XP machines and b) my Windows machines cannot see the Ubuntu machine.

Here's what I think I know:
[LIST]
[*]Samba is running on the Linux PC
[*]When I use the Ubuntu machine's Nautilus and enter 192.168.1.105 Nautilus opens that Windows XP machine just fine, I can browse its shared folders, etc.
[*]Using “Places &#8594; Connect to server” and entering the name of one of my Windows machines produces an error message “Can't display location "smb://livingroompc/"  
[*] Similarly, using “Places &#8594; Connect to server” and entering smb://192.168.1.101, the IP address for that PC, produces the same error message.  
[*]Entering smb://192.168.1.101 into Firefox or Opera produces a blank browser screen, no error message
[*] The Windows machine CANNOT even see the Linux machine no matter what I do, even a search for computers within Windows File Explorer
[*] The Windows machine CAN ping the Linux machine
[/LIST]

I have followed numerous pieces of advice from this forum and others.  
[LIST]
[*] One suggested I use Ubuntu "System -> Admin -> Network" to change the name of the workgroup to match my home network.  I did, no change from the Windows machines, they still cannot see the Linux PC
[*] Another said I needed to edit a file whose name I cannot remember so as to set my Ubuntu to the same workgroup as my Windows PCs.  I did, that didn't help the Windows machines see the Ubuntu either.
[*] Yet another said "You have no entries in /etc/hosts" but didn't explain how to resolve that.
[/LIST]

I'm stuck and frustrated, it really should not be this hard.  I know how to get various Windows machines and Macs to talk to each other on a home network, have done it many times.  

So, to the question - can someone help me out with some tips or maybe a link to a tutorial that speaks in simple English (one post said something about [fnmb] being broken without explaining what that was, where to find it, or how to make it right - useless to me).

Somehow I think I'm missing something incredibly obvious and when someone explains it to me I'll be stunned at my incompetence.  But right now I'm just frustrated at spending 4-5 hours over three evenings trying to get what I consider basic functions to work.

I'd be most grateful for your help.  I hope the above gave you enough information to do so

Jay

---

### Post by Another Monkey on 2008-09-20
You are not alone.  I too am going spare with networking.  I have, basically, an identical situation.  Two computers (Windows XPsp3 desktop, Ubuntu 8.04 laptop).

Both connected to the same router, on the same subnet, same workgroup, similar IPs (only last digit is different).

I have switched off all firewalls and still no success.  Whilst //192.168.32.xx/someShare works on both, I can't navigate to them.  Network in Ubuntu File Browser shows me the laptop (as you would expect) and the Windows Network icon.  Clicking on the icon brings up nothing.  Ubuntu cannot see the desktop this way, onlz by IP or "Connect to server".

On Windows I just get an error when trying to access the workgroup, yet when I use the IP address to navigate to the Ubuntu laptop, it appears correctly in the Explorer browser tree.

I think I have read every guide here and on the net and nothing seems to fix the networking problem.

The Windows firewall (McAfee) trusts the local network, log no exceptions and there is no change when I switch it off.  NetBIOS is enabled, services running (Computer Browser, Network Location, Server etc), I also disabled the Windows Firewall/ICF service.  No change.

Samba is installed an appears to be fine.  I can create shares, and see them on the Ubuntu laptop using File Browser.  Using direct IP connection, the Windows machine can see them too.

They will just not list each other under "Windows Network" or the workgroup.

The really annoying things is that when I take my laptop into work (a Windows Network) it works perfectly.  It sees all servers, all shares and will let me access them (after login).

Obviously I have something wrong at home - but what?  Could it be the router?  It's a Belkin F5D7632uk4 V1.0.  I've had a look, but there seems to be no trickery there.  It is running a firewall as well, but switching that off seems to have no effect.

It's driving me nuts!

A bit of help though.  To edit hosts, do this (gkedit in Kubuntu I think)
```
sudo gedit /etc/hosts
```

Then add an entry for each PC (they'll need fixed IPs for this to work) e.g.
192.168.0.321 MyOtherComputer
192.168.0.112 SomethingElse.AnotherDomian

**BUT**, you (we!) should not need to do this.  The computers *SHOULD* resolve each other's names/IPs on the same network without it.  If it's all working......*sigh*

---

### Post by quad71 on 2008-09-20
Okay, I'm going to pile on here and vent some similar frustration. I, too, am having similar problems and no success at finding a solution. I have an openSUSE Linux machine in my basement fuctioning as a Samba and Apache server and I have a mixture of WindowsXP, Visa(!),WinME(!!) and my Ubuntu laptop and all talk to each other via Samba except my Ubuntu laptop. 

If I know the IP address, I can browse other Windows machines from my Ubuntu laptop via Nautilus. I can likewise browse my Ubuntu laptop from a Windows machine if I know the IP. I just can't use the names nor will they show up in Ubuntu though Places->Network. All that shows up there are SFTP servers - my SUSE server and my Ubutu laptop. Nor will the Ubuntu machine show up in Windows "Network Places".

I'm with the last post - it shouldn't be this complicated. I have tried several Linux distributions and so far like Ubuntu best because it works best "out-of-the-box". What few that didn't work OTB I fixed with relative ease. This, however, I can't figure out. openSUSE and Fedora required no tweaking at all to get networked. 

Just as an added note, I use an openSUSE machine for a server at work and it has worked flawlessly for 2 years now in harmony with 15 other Windows machines (Win98 thru XP). My Ubuntu laptop will not work there, either unless I use the IP addresses.

Help! Please!

---

### Post by Another Monkey on 2008-09-21
I know Ubuntu works on a Windows network, because it is happy enough at work (which has proper domain controllers etc).  It's just at home that I cannot get it to function.

And no one seems to know the answer. :(

---

### Post by jstevans on 2008-09-22
Thanks for the replies, it's nice to know I'm not alone and that the problem lies, at least in some measure, in Ubuntu's complexity.

So hey folks - can anyone out there offer a troubleshooting walk through for those of us who are actually pretty experienced and really believe we have done everything right - yet, find that our networking is still not working?

Please!

---

### Post by Iowan on 2008-09-22
Firewalls can be a potential problem.  Ubuntu may need to have Winbind installed (and maybe smbfs) - I'll see if I can find the links.  It's also possible that installing Samba-server and setting up a share might make it visible.

Here's one [link]("http://ubuntuforums.org/showthread.php?t=891876").

---

### Post by jstevans on 2008-09-23
Thanks for your help.

In my case Samba is definitely installed.  

Also, as mentioned in my initial post, my Linux machine can "see" the Windows PCs if, and only if, I send it there by entering the intended machine's IP address.

J

---

### Post by Another Monkey on 2008-09-23
This is deeply strange.  I decided to sit down again and do combat with the windows network.  I was sure that the fault was a firewall, router setting, something.

I did two things at once, so I have no idea which worked (stupid).  But...
1) I opened the TCP/IP properties on Windows, went to the advanced tab and made sure that NetBIOS was enabled (not at default).
2) I fired up a Windows VMWare image.

After this - the network worked.  The workgroup showed as populated and the Ubuntu lappy listed the other PCs correctly. But neither Windows unit showed the Ubuntu lappy.  Once navigated to via IP, the Windows PC listed it in the workgroup and seemed happy to accept it.  The virtual one refused.  It could ping the laptop, but would not connect.  

I then shut the image down.

After some time, Ubuntu stopped showing the PC in the "windows network" and the windows Pc showed the laptop in the workgroup, although it did not list itself 8which strikes me as very strange).

So I got a tiny bit further, but still have problems.  Could I have Samba set up wrongly?  Have I simply forgotten to do something?  Could some ports be getting blocked?  Even though the firewalls trust the local network.

Does this new behaviour give any who knows about networking any clues?

---

### Post by quad71 on 2008-09-23
Okay, here's another clue for someone to chew on. I did two things, not sure which thing did what:

I installed WinBind per someon's suggestion, which appears to have done nothing for me, I'm not sure. I gave up and tried again today, this time plugging in via ethernet to transfer some video files. I did my usual workaround by using the IP of the machine I was connecting to. While I waited for the files to copy, I looked into Places->Network and  all my PCs were listed there and all accesable as they should be! So I restarted when my files were done to be sure it wasn't a fluke or that connecting manually didn't make it happen. Sure enough, it still worked after restart - all was happy.

So I switch back to wireless to see what happens - broken again. I can't see any other PCs in Ubuntu nor can I see my Ubuntu laptop on any other PCs. I can still access shares via IP address, so this seems to rule out a firewall issue(?). So I switch back to wired and all is happy again.

Any ideas on what to check with these bits of info added?

---

### Post by Another Monkey on 2008-09-24
Wireless.  This is my set-up too.  Wired Windows PC, wireless laptop.

I can't recall the specifics, but apparently this is normal behaviour on some routers; and it should be possible to change it.

I'll try the lappy on a wired connection tonight (it was wired in the office where it worked) and see what happens.

I have dug through all my router settings and can't see what I am missing.  Does anyone know (or can find a link to) what the router may be blocking?

I have a Belkin router btw.

---

### Post by jstevans on 2008-09-24
I'm glad we're working on this though I remain perplexed as to a) why Ubuntu Linux is so darned mystifying and b) why we're not getting some help from more qualified minds than ours.

As for my setup:
[LIST]
[*]All PCs are wired in, no wireless in use
[*]TCP/IP is on for all Windows machines
[*]My Ubuntu machines shows the Windows Network icon but clicking on that brings me to a blank window, no Windows machines displayed
[*]The Windows Network does not display the name of my Windows network (HOME)
[*]The Windows Network does not display any properties when queried
[/LIST]

I'm really wondering why I don't give up and go back to Windows 2000.  It may not be as good as Linux on a theoretical basis but at least I can get it to work!

Are there any experts out there who could help us work through this?  The web is awash with postings from people with networking frustrations trying to integrate their Linux systems into existing Windows networks.

---

### Post by Another Monkey on 2008-09-24
I know - there's literally hundreds of threads on this and no apparent resolution.  And nothing in the docs that I can find.

---

### Post by jstevans on 2008-09-24
I am experienced enough to know that Windows networking can be a horrible task.  I had a small problem getting one of my children's Windows Vista Home Edition laptop into the network.  

But this mess with Ubuntu is incredible.  If the Linux folks really want this to take over the world then configuring it needs to be familiar enough so people like we can easily it.  I'm not asking for it to be so easy that my 88 year old mother can do it.  I'm just asking that ti be easy enough that someone who can comfortably configure a network with multiple versions of Windows and Mac OS can integrate an Ubuntu PC.

Better yet, why not just have the installer ask me if I want to interconnect with a Windows network and then automatically turn on Samba and whatever else I need to make that happen?  That'd be the smart solution.

OK, end of rant.  But PLEASE - isn't there an Ubuntu wizard out there who'd be willing to help us out?

---

### Post by Michl on 2008-09-24
Well, this propbably isn't going to be vert helpful. But
for what it is worth, I haven't had major problems with networking since Feisty, and in my home network we have 5 computers conntected with ubuntu, XP and even 98.  In Heron 
I just clicked on Places -> Network, and there are all the computers.  Sometimes it takes a while and I need to click 2 or
3 times more before they all appear, but they all do.

In any case, it helps to install 
```
system-congif-samba
```
and using the gui share a file on each linux computer.
Do the same on windows boxes in the windoze way.

Also, make sure the network names are the same everywhere.
In linux edit the samba configuration file:

```
sudo nano /etc/samba/smb.conf
```

Scroll down to:

> workgroup = MSHOME

and change MSHOME to whatever you like. Now hit ctrl-x and press y and then restart samba

```
sudo /etc/init.d/samba restart
```

Maybe some of this helps.

---

### Post by jstevans on 2008-09-24
Thanks for the suggestion.  I walked through it and this is the resulting file (My home network is unimaginatively named "HOME"):

[global]
netbios name = Samba24
server string = CAD architects, Stockholm. East 32nd st, 34th floor
workgroup = HOME
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 8

I'm not sure why "Stockholm" and some of the other things are in here but I didn't tweak them so I guess they're intended.

Making this edit did not either a) allow my Linux machine to see the Windows PCs nor b) enable the Windows machines to see the Linux PC.

But, I am grateful for the suggestion and welcome any and all help.

Thanks again.

---

### Post by quad71 on 2008-09-24
Okay, I'm going to backtrack a few posts here and adress a comment by Another Monkey in Re to "doing battle with Windows netorking." My suggestion is to leave you Windows machines alone, especially if they (it) works already. All my Win machines talk nicely to each other, so I take the "if-it-ain't-broke, don't-fix-it" approach to them.

As for our routers being the culprit, I agree it sounds like a possibilty, but I've looked and tweaked and experimented there a dozen times to no avail. I have 2 Linksys wireless routers, one is configured as my gateway to the net and as my DHCP server, the other as a simple router to cover some wi-fi dead spots around my house. No matter which I connect to wirelessly, they behave the same. Wired connection all seems to work happily.

---

### Post by jstevans on 2008-09-24
I strongly agree with not changing the Windows machines.  Mine all talk to each other just fine, and to Macs when one of my kids' friends brings one over.  I have a mix of Windows versions including 2000 Professional, XP Professional, Vista Home, and XP Home.  

It is hard to imagine that the problem is my Windows machines though I'm willing to be surprised.  The same goes for my router - wired or wireless.

I've been doing all kids of tech support for 40 years (hey, my first tool was a rattle I used to fix my crib) and all that training in diagnosing problems says it's an Ubuntu setup issue.

And my research on the web says this is a problem shared by lots and lots of people.  It's time to get it fixed in the setup process or explained in the doc.

---

### Post by quad71 on 2008-09-24
server string = CAD architects, Stockholm. East 32nd st, 34th floor

This is the human-readable text that appears next to the host name on other machines - this can be whatever you want - "Another Monkey's banana" would work just fine here if you wanted. In the Window's "network neighborhood" or "network places", depending on the OS,"Another Monkey's banana" would appear in the description field beside the Linux machine's host name.

I'm not sure why we're messing around with Samba config as it appears to work as long as we use IP addresses. Somewhere the Ubuntu machine isn't resolving the host names of the other machines. It will, of course, affect how the other networked machines "see" the Ubuntu machine, so I guess I can where we're going with that....just thinking out loud here.......

---

### Post by Another Monkey on 2008-09-24
I have just tried it through a wired connection - no joy.  I guess I am just going to have to live with the fact that there is something borked with the network settings (either Windows, Samba or both) and that I am too dumb to spot it.

Windows only works when I start another instance in VMware.  Surely a machine should be able to see itself (and its shares) in a workgroup?

---

### Post by jstevans on 2008-09-25
The deafening silence here seems to indicate we are yet again on our own and that a solution to this problem we, and endless others, face is not forthcoming.

I confess to thinking that maybe Linux really is "the emperor's new clothes" rather than a genuine solution for the desktop.

---

### Post by quad71 on 2008-09-25
Well, I'm not sure I'd go quite that far. At this point, I could be Windows-free were there 3 things in Ubuntu - iTunes, MS Money or Quicken, and functional networking. As for everything else, I'm happy. I'm impressed with the stability and functionality of it and it's simply more fun to use than Windows. It's just too bad I have to jump through flaming hoops to talk to other machines, access iTunes, and do  my finances.

---

### Post by Landie_UK on 2008-09-26
I have been having the same type of problems as you guys as well. I did find some really good tutorials on youtube, I actually got Ubuntu to access win XP shared folders and got the XP PC to see My Ubuntu folder but was unable to get permission to access it. I am reinstalling Ubuntu right now as I found in the tutorials that I dont have "system > administrator > shared folders". It jumps from "services" to "synaptic package manager" this makes it hard to follow tutorials. Also i couldn't get the smdpasswd to work either which is also needed.

Her's a link to 1 tutorial. [http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Hope this helps

---

### Post by Onesimus on 2008-09-26
Hi,  I thought I would enter the arena.  I am about to setup my home network, and have not yet had any experience, however, this issue was covered in the fullcircle magazine (Issue 6)

[http://fullcirclemagazine.org/downloads/]("http://fullcirclemagazine.org/downloads/")

Hope this helps.

---

### Post by jstevans on 2008-09-26
Hi Onesimus

I like your screen name - "profitable" as I recall.

Thanks for the lead to the magazine article.  I just downloaded it, will give it a go later this afternoon.

J

---

### Post by jstevans on 2008-09-26
Hi quad71,

I find the absence of networking so huge that it's hard to say "as for everything else, I'm happy."  It's a bit like saying my new car has a great interior, wonderful air conditioning, and a stunning exterior finish - now, if only it had a transmission so I could actually go somewhere!  I'm just not going to buy that car!

This networking thing is a huge problem.  Maybe this group can keep working on it and help deliver a genuine solution.

J

---

### Post by Planter on 2008-09-26
For what it's worth, here is my two cents. I am involved with my third try to make Ubuntu work. My experience mirrors that of the others who have posted here. I simply cannot get Ubuntu to see or use my network printer or the other computer on the network. I tried so many different suggestions to modify this, that or the other entry in my smb.conf file that I lost track of what I had changed. Eventually the file was so screwed up I had to erase it and replace it with the original from the setup disk. I have a home network with a WinXP machine and a Vista machine. They talk to each other, exchange files and use a remote printer with no problems. When I boot into Ubuntu the fun begins. I even went to Kubuntu, which has a very nice interface, but is buggy. Some of the applications in Kubuntu crash my system and it doesn't network either.

Also I am not an inexperienced newby either. My computer experience goes back to the punch card days of the 1960's. I did some programming on DOS machines in the 1980's. Also I once operated a ham radio station in my home. Built the transmitter out of parts, designed and built longwire and dipole antennas, all of which worked.

Somebody needs to fix Ubuntu's networking.

---

### Post by Another Monkey on 2008-09-26
Windows and Ubuntu networking does work, and I have it working in the office as a zero-config (i.e. no changes).  All I need to do is provide the credentials and it works.

So I know for 100% certainty that it is possible.

It's at home it is driving me spare.
It could be my Windows set up (I need to launch a Windows machine in VMware to make Windows networking viable).  So there is probably something stupid in my main PC.  What that is, I have no idea.  NetBIOS etc all look fine.

Once that VMWare is running - workgroups etc. are fine.  Without that VMWare up, Windows just errors.

It could be, of course, that there is something up with my Samba settings and the home PC.  What that could be I also have no idea, as the laptop is fine in the office.  They will work fine given an IP, e.g. "smb://192.168.x.y/" or "\\192.168.a.b" in Windows.  They just refuse to see each other in a Workgroup without the VMWare image running.

As it all works with the VMWare image up, I can discount firewalls, router, cables, wifi card etc.  With the VMWare image down, it does not work without going direct via IP.

If I get time at the weekend (unlikely, I have to work) I'll check all the networking settings again; bit by tedious bit.

Does **anyone** have any clue why this behaviour would be?

---

### Post by jstevans on 2008-09-26
The VM phenomenon seems to have significance - now, if we only knew what was different about it versus running the same Windows machine without VM Ware.

A friend has promised me some software that might be of assistance.  At this point I'd dump Ubuntu in a moment but I don't have a spare licensed copy of Windows for the new machine I was given (sans OS - obviously).

Plus, it's somewhat a matter of pride here - I'm not ready to let a dumb machine and an even stupider OS beat me!

---

### Post by Another Monkey on 2008-09-26
I think the VMware image is acting as a "master" for the workgroup.  Or something like that, I don't think it's anything magic about VMWare.

Obviously there is a difference between the image and the host.  If I get tme, I'll check it out.

I don't think this is the fault of Ubuntu (or Smaba, or Linux) per se; just incomplete docs.

Or maybe I was an eejit with my Windows setup.......

---

### Post by jstevans on 2008-09-26
Hmmm, the "master" issue is interesting.  My understanding is that in a peer-to-peer Windows network (one w/o a domain controller) "finding" machines can be pretty funky.  Maybe the VM is acting as a master.  Can we determine if that's why your implementation is working?

---

### Post by Landie_UK on 2008-09-26
I found this link in another thread followed it through and got my Ubuntu to access Wifeys XP shared folders just fine, she can see my secondary hard drive but can't access it yet and I can't set share options in Nautilus get permission denied message. I am happy I am getting some progress at least I am Half way there.


A big Thank You to who ever posted the link it was a great help. 
Here is the link.

[http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.htm](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.htm)

---

### Post by quad71 on 2008-09-26
Good point. I guess since I can at least network via SMB with IP addresses, I have at least some form of "transmission". To carry on the analogy, I guess I'm having to stop, get out and my lock my front hubs, and then get back in and drive on. We shouldn't have to do that any more to get 4WD.

Now I'm lost. I have no idea what VMware is or what it does, so I'm no help there. 

I'm still leaning toward something outside of Samba or the Windows machines since it seems to work via IP's. My Windows and SUSE, and Mac machines work together, just not with my Ubuntu laptop.

What resolves names? There's a daemon running on my SUSE machine called nmbd. I use SWAT on it to configure Samba on it and I've had to start/restart nmbd on occasion to get my networking going, but I don't see it in Ubuntu. Is is called something else? I thought maybe WinBind could be a culprit but it's not running on my SUSE machine and it works happily w/o it.

I'll check out the videos and suggestions above and report back later...thanks for the input.

---

### Post by quad71 on 2008-09-26
.

---

### Post by jstevans on 2008-09-27
OK, I'm still trying to get this working and am grateful for the contributions.  The following is a question I'm embarrassed to ask but need to: if Samba is running on my Ubuntu machine should I see it listed in the "Processes" page of the System Monitor? 

If you can't guess, I'm asking because I don't see it listed and I'm thinking that may be what is amiss.

When I restart Samba via Terminal here's what I get:

[COLOR="Red"]stevan@Ubuntu:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                       start-stop-daemon: warning: failed to kill 6243: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ] 
stevan@Ubuntu:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                       start-stop-daemon: warning: failed to kill 7985: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ] 
stevan@Ubuntu:~$ 
[/COLOR]
How do I determine if Samba is really running?  Must it be listed in the "Processes" page of the System Monitor?

Oh, and if Samba should be showing in the Processes listing can anyone tell me what might be wrong, why it's not actually launching?

Thanks.

Ahhh, the mystery!  The adventure!

J

---

### Post by Iowan on 2008-09-27
Samba (server components) show up (via **ps -ax**) as **smbd** and **nmbd**.

---

### Post by jstevans on 2008-09-27
I may be making some progress here after searching some other posts.  I'm 99% sure Samba is not starting.  

My log.nmbd log says:
[COLOR="Red"][2008/09/27 11:24:05, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/27 11:24:05, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
[2008/09/27 11:24:05, 0] nmbd/nmbd.c:main(795)
  ERROR: Failed when creating subnet lists. Exiting.
[2008/09/27 11:26:57, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/27 11:26:57, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
[2008/09/27 11:26:57, 0] nmbd/nmbd.c:main(795)
  ERROR: Failed when creating subnet lists. Exiting.[/COLOR]

And the log.smbd file says 
[COLOR="RoyalBlue"][2008/09/27 11:24:05, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/27 11:26:57, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008[/COLOR]

I confess to not knowing what the interaction is between smbd and nmbd but it's clear that at least nmbd isn't starting.

Any insights as to how I fix nmbd's problem with subnets and get this baby chugging?

J

---

### Post by jstevans on 2008-09-27
Thanks Iowan.

I believe your comment "Samba (server components) show up (via ps -ax) as smbd and nmbd" means that if I look in the Processes section of System Monitor I MUST be seeing smbd AND nmbd if Samba is actually running.

True?

Sorry for this question but I wasn't 100% sure about your shorthand so I thought I'd check.

J

---

### Post by Iowan on 2008-09-27
Sorry about shorthand... I'm @ Panera on PDA and don't type well with stylus.  I must confess, I haven't read entire thread.  **ps** would be via terminal (not System Monitor). Dunno if BOTH processes must run.  Sometimes there will be multiple instantances of one component or the other.  Usually the "failed to start" is a problem in smb.conf.

---

### Post by jstevans on 2008-09-27
Just in case it's helpful in diagnosing my problem, here is my smb.conf

[COLOR="Red"][global]
	netbios name = Samba24
	server string = CAD architects, Stockholm. East 32nd st, 34th floor
	workgroup = home
	security = user username map = /etc/samba/smbusers
	hosts allow = 127. 192.168.0.
	interfaces = 127.0.0.1/8 192.168.0.0/24
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	printcap name = /etc/printcap
;	load printers = yes
	cups options = raw
;	printing = cups
	guest account = avahi
	log file = /var/log/samba/samba.log
	max log size = 1000
;	null passwords = no
	username level = 8
	password level = 8
;	encrypt passwords = yes
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
	preferred master = no
;	domain logons = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
;	time server = no
	name resolve order = wins lmhosts bcast
	wins support = yes
	wins server = 
;	wins proxy = no
	dns proxy = no
;	preserve case = yes
;	short preserve case = yes
	client use spnego = no
	client signing = no
	client schannel = no
;	server signing = no
	server schannel = no
;	nt pipe support = yes
;	nt status support = yes
	allow trusted domains = no
	obey pam restrictions = yes
	enable spoolss = yes
;	client plaintext auth = no
;	disable netbios = no
	follow symlinks = no
	update encrypted = yes
;	pam password change = no
	passwd chat timeout = 120
;	hostname lookups = no
;	smb passwd file = /etc/samba/smbpasswd
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete user script = /usr/sbin/userdel '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	machine password timeout = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind use default domain = yes
	winbind separator = @
	winbind cache time = 360
	winbind trusted domains only = yes
	winbind nested groups = no
	winbind nss info = no
;	winbind refresh tickets = no
;	winbind offline logon = no
	guest ok = yes

[homes]
	comment = Home Directories
	path = /home
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = no
;	available = yes
	browseable = no
;	guest ok = no
;	printable = no
	locking = no
	create mode = 0600
	directory mask = 0700

[printers]
	comment = All Printers
	path = /var/spool/samba
;	browseable = yes
;	writable = no
;	guest ok = no
	printable = yes
	share modes = no
	locking = no

[pdf-documents]
	path = /home/pdf-documents
	comment = Converted PDF Documents
;	available = yes
;	browseable = yes
	writeable = yes
	guest ok = yes

[pdf-printer]
	path = /tmp
	comment = PDF Printer Service
	printable = yes
	guest ok = yes
	use client driver = yes
	printing = bsd
	print command = /usr/bin/gsambadpdf %s %u
	lpq command = 
	lprm command = 
[test]
path = /home/USERNAME/Desktop/test
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes[/COLOR]

Questions:
1.  Is the conf set up properly to allow my Ubuntu machine to "see" my iwndows PCs and vice versa?
2.  Should "guest OK" be set to yes if I want to allow guest users?
3.  Should wins support = yes?
4. Should wins server = ?
5. Should wins proxy = no?

Thanks,

J

---

### Post by Iowan on 2008-09-27
> # NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors.Gotta say, I don't understand "new" Samba nearly as well as pre-Hardy versions.  [Here]("http://ubuntuforums.org/showthread.php?t=891876") is a thread with some potential solutions.  I saw another thread that suggested "removing" Winbind made the network faster.  Your smb.conf seems pretty busy - might be able to pare it down to see what works.  I make a backup before making wholesale changes - then when I screw it up, there's a safety net.

---

### Post by quad71 on 2008-09-27
This may to obvious, but I'll ask anyway. Did you check "System->Admin->Services and see if "File sharing(Samba)" was checked? Sounds like smb isn't starting at bootup. You might also check your logs (var/logs/samba) for some clues. Wins support makes your machine a client, the other option makes it a server - both can't be yes. I have them all commented out, so try that and see.....

I installed SWAT and it gives me a good status of smb and nmb. I'm a bit confused though because it doesn't give me all the options SWAT gives me on other Linux machines give me, such as configuration options, start/restart, etc. I think I'm on a wild goose chase.....

---

### Post by jstevans on 2008-09-27
Your question isn't "way too obvious" at all.  I had no idea "File sharing (Samba)" needed to be checked.  However, it isn't even an option on my system, probably due to Samba not having started because of the "nmdb" problem mentioned above in this thread.  

I'm thinking that if I can get nmdb to run then Samba will start properly and at least some of my problems will be resolved. 

Then again, sometimes I'm wrong (at least - according to my kids).

Still hoping for some help on nmdb being unable to launch.

As for SWAT - how to I install that?  I'm running Gnome (the Ubuntu default desktop).  I tried "add applications" and searched for SWAT to no avail.

Thanks,

J

---

### Post by Iowan on 2008-09-27
> **jstevans said:**
> As for SWAT - how to I install that?  I'm running Gnome (the Ubuntu default desktop).  I tried "add applications" and searched for SWAT to no avail.Look under System>Administration>Synaptic Package Manager. 
I looked under **man samba** to learn:>        nmbd( 8 )
          The  nmbd  daemon provides NetBIOS nameservice and browsing support.
          The configuration file for this daemon is described in smb.conf(5)
Run **testparms** to see if something is amiss in smb.conf.

According to my "young-un", sometimes I'm NOT wrong...

---

### Post by jstevans on 2008-09-27
Thanks for yet another tip.

I think I installed SWAT via the System>Administration>Synaptic Package Managed.  Now, if I could only find it so I can run it!  Yikes, this is a lot of work!!  But, I'm pretty determined.

One post said:
[COLOR="Red"]   To  launch  SWAT  just  run  your  favorite web browser and point it at "http://localhost:901/".
[/COLOR]
I did and was rewarded with the famous:
[COLOR="RoyalBlue"]Failed to Connect
Firefox can't establish a connection to the server at localhost.[/COLOR]

So, please tell the struggling newbie how to run SWAT.

Also, and equally embarrassing to need to ask, HOW do I run testparms?  I wandered a few forum postings and, while many spoke about testparms, none said how to run it.  I even did a search through the file system and the Synaptic Package Manager - no joy.

---

### Post by Iowan on 2008-09-27
> **jstevans said:**
>  HOW do I run testparms?  THAT one I can help with...
Open a terminal (Under Applications>Accessories on my Gutsy machine) - or CTRL-ALT-F1. Simply type in **testparm** and hit ENTER.  The command I mentioned earlier (**ps -ax**) would have been entered through a terminal.

BTW, if you use CTRL-ALT-F1 to get a terminal, use CTRL-ALT-F7 to get back to desktop.

---

### Post by jstevans on 2008-09-27
Thanks, that got testparm to run which produced the following which I believe means my smg.conf is fine - true?

[COLOR="Red"]Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-docs]"
Processing section "[pdf-printer]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
[/COLOR]
Since it nicely suggested that I "Press enter to see a dump of your service definitions" I did just that and received this:
[COLOR="Blue"][global]
	workgroup = HOME
	netbios name = SAMBA24
	server string = CAD architects, Stockholm. East 32nd st, 34th floor
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = avahi
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	password level = 8
	username level = 8
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = /etc/printcap
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	preferred master = No
	local master = No
	domain master = No
	dns proxy = No
	wins support = Yes
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	guest ok = Yes
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	share modes = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = No
	locking = No
	share modes = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	locking = No
	share modes = No

[pdf-docs]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	printable = Yes
	printing = bsd
	print command = /usr/bin/gsambadpdf %s %u
	lpq command = 
	use client driver = Yes

[test]
	path = /ho[/COLOR]

So tell me, is this level of pain common in an Ubuntu installation?

J

---

### Post by quad71 on 2008-09-27
I have felt less pain w/ ubuntu than other Linux installs, but then again I've tried only 3. This one issue has almost overtaken the dozen or so issues I've had with other distributions, though.

To run swat, you first need to reboot after install. After that, you run it in a web browser (firefox works fine) by typing "http://localhost:901". You'll be prompted for a username and password, which is typically "root" and associated password.

It didn't do me much good except to tell me that smb and nmbd was running, which a command in a terminal probably could have accomplished that. It doesn't provide the pull-down menu options and help for samba.config like it does in other Linux ditributions, I assume because it conflicts with ubuntu's samba configuration panel or something. I don't know. SWAT is completely broken in the current version of openSUSE (11.0), which is why I abandoned that OS and tried Ubuntu.

Anybody know if ubuntu has a firewall,and if so, how do you modify it (programs, interfaces, etc.)? I'm back to checking my interfaces. My networking works as-advertised as long as I'm plugged in, but not wirelessly. Something about the wireless interface not letting me access the network via names - ip's only. Very strange.

---

### Post by quad71 on 2008-09-27
Fixed my swat issue.....didn't have password set for "root" user. I have a single user system, and my login is the super user, so until now, I havn't needed to use root. Long story short, you MUST login as root to get all the options in swat. If "root" username doesn't work, try setting the password for "root" user in users/groups control panel. There may be another way of doing this, but this is the only way I know to do it.....

---

### Post by Another Monkey on 2008-09-28
So I compared my VMWare image to the desktop PC and spotted some differences.  I made everything the same and still no joy.  I note that when running "ipconfig /all" the desktop PC reports and "unknown" Node Type.  So far all efforts to correct that have failed.

The Ubuntu laptop is now unable to see any either Windows esystem, even with the VMWare image running.  Going direct via IP still works from Ubuntu, but not from Windows.  "ping" still works in both directions.

I am seeing errors in the nmdb log, are they significant?
```
  Packet send failed to 192.168.32.255(137) ERRNO=Operation not permitted
[2008/09/28 12:49:19, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.32.255 port 137 failed
[2008/09/28 12:49:19, 0] nmbd/nmbd_nameregister.c:register_name(514)
  register_name: Failed to send packet trying to register name JGROUP<1e>
[2008/09/28 12:49:19, 0] libsmb/nmblib.c:send_udp(793)
  Packet send failed to 192.168.32.255(138) ERRNO=Operation not permitted
[2008/09/28 13:16:13, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/09/28 13:16:16, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/28 13:22:05, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server MR-NILSSON is now a local master browser for workgroup JGROUP on subnet 192.168.32.5
  
  *****
```

log.smdb shows this
```
[2008/09/28 12:48:04, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/28 13:16:16, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/28 13:16:17, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/09/28 13:16:17, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/09/28 13:16:17, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/09/28 13:16:17, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```

I have no idea why it's trying to contact 192.168.32.255 as there is no PC on the address.  I also have no idea why it thinks it's on subnet 192.168.32.5 as it should be on subnet 255.255.255.0 (just like the Windows boxes).  Where do I check this?

Following earlier comments, I installed SWAT, set the root password, rebooted and this is what I see when I click on "View"
```
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/09/28 13:51:43

[global]
	workgroup = JGROUP
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[homes]
	comment = Home Directories

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

After the reboot - this is all that is in log.nmdb.  Why is it trying to contact a non-existant IP?
```
[2008/09/28 13:42:08, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/09/28 13:42:11, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/28 13:43:07, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/09/28 13:44:12, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/09/28 13:44:12, 0] nmbd/nmbd_subnetdb.c:create_subnets(190)
  create_subnets: No local interfaces !
[2008/09/28 13:44:12, 0] nmbd/nmbd_subnetdb.c:create_subnets(191)
  create_subnets: Waiting for an interface to appear ...
[2008/09/28 13:48:12, 0] libsmb/nmblib.c:send_udp(793)
  Packet send failed to 192.168.32.255(137) ERRNO=Operation not permitted
[2008/09/28 13:48:12, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.32.255 port 137 failed
[2008/09/28 13:48:12, 0] nmbd/nmbd_nameregister.c:register_name(514)
  register_name: Failed to send packet trying to register name MR-NILSSON<20>
[2008/09/28 13:48:12, 0] libsmb/nmblib.c:send_udp(793)
  Packet send failed to 192.168.32.255(137) ERRNO=Operation not permitted
[2008/09/28 13:48:12, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.32.255 port 137 failed
[2008/09/28 13:48:12, 0] nmbd/nmbd_nameregister.c:register_name(514)
  register_name: Failed to send packet trying to register name MR-NILSSON<03>
[2008/09/28 13:48:12, 0] libsmb/nmblib.c:send_udp(793)
  Packet send failed to 192.168.32.255(137) ERRNO=Operation not permitted
[2008/09/28 13:48:12, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.32.255 port 137 failed
[2008/09/28 13:48:12, 0] nmbd/nmbd_nameregister.c:register_name(514)
  register_name: Failed to send packet trying to register name MR-NILSSON<00>
[2008/09/28 13:48:12, 0] libsmb/nmblib.c:send_udp(793)
  Packet send failed to 192.168.32.255(137) ERRNO=Operation not permitted
[2008/09/28 13:48:12, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.32.255 port 137 failed
[2008/09/28 13:48:12, 0] nmbd/nmbd_nameregister.c:register_name(514)
  register_name: Failed to send packet trying to register name JGROUP<00>
[2008/09/28 13:48:12, 0] libsmb/nmblib.c:send_udp(793)
  Packet send failed to 192.168.32.255(137) ERRNO=Operation not permitted
[2008/09/28 13:48:12, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.32.255 port 137 failed
[2008/09/28 13:48:12, 0] nmbd/nmbd_nameregister.c:register_name(514)
  register_name: Failed to send packet trying to register name JGROUP<1e>
```

This is driving me insane!

---

### Post by quad71 on 2008-09-28
Check your network card configuration. If it is set to manual, you may have a strange subnet mask or even bizarre IP address. If your network is not using static IPs, your Ubuntu machine should be in "roaming" mode and not manual. I'm curious as to why you're at 192.168.32.xxx. Are all your machines on .32.xxx? That could be an issue...not sure. Unless you've changed it, most routers come with 192.168.1.xxx as the default local IP address range for DHCP. Your Windows boxes may be on one segment and your Ubuntu box another. Not being familiar with how your network is set up, I'm just throwing some things out there....

---

### Post by Another Monkey on 2008-09-28
My home network is 192.168.32.x, are IPs in this range a problem?  I am in "roaming mode" and connecting to my home network.

This is the result of "ifconfig"
```
wlan1     Link encap:Ethernet  HWaddr 00:1f:1f:05:b4:53  
          inet addr:192.168.32.5  Bcast:192.168.32.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe05:b453/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:913086 (891.6 KB)  TX bytes:124206 (121.2 KB)
```

That is what I would expect to see and matches up to "ipconfig" on Windows.  Although I am still puzzled by the IP for bcast.  But as I haven't changed anything, I guess it is correct.  I assume all the failures I see in log.nmbd are these broadcasts.  Odd that they only seem to work with the VMWare image running.

I wonder if there is  something wrong with my Windows PC?  As this would, I guess, explain the error I get when trying to access the workgroup from Windows without the VMWare image running.  But I am at a loss as to what to check in Windows or Ubuntu!

---

### Post by quad71 on 2008-09-28
The IP range is fine, as long as they are all the same range (.32.xyz). I don't think that's an issue then. As for the broadcast, that is normal I think, as I see the same except mine is .1.255. If you can ping the other machines and you can access the internet, I would think your hardware is configured correctly, then. Don't want to lead you down the wrong path. Sounds like you're okay there.

---

### Post by Another Monkey on 2008-09-28
I am 99% sure my Ubuntu laptop is fine (it works at the office).

I think it is my Windows desktop, as that only functions without error with the VMWare image up.  I have read that the virtual VMWare adaptors can cause issues, so I disabled them.  No joy.

I think I will give up on fiddling with Ubuntu for a while and look more into my Windows set-up.  I'll see if I can borrow a Windows lappy to see how that behaves at home on it's own.  If it works OK and see's itself - I know for sure that it's my Windows PC being screwy.

---

### Post by eschatologicalhumor on 2008-09-28
I didn't read the entire thread, only the first and last page, but this is how I got it to work:

First, both computers are wireless.

Shared the folder on the remote pc (Windows)
On the Ubuntu laptop, Places > Connect to Server and entered the ip address of the Windows box, then under 'Folder' below, put the name of the folder.

That's it. Voila.

This is the first time I've ever tried to setup networking with Ubuntu, and the first time with Windows/Ubuntu.

Now I have to get my wired Ubuntu desktop to be seen by this laptop and I'm all set.

---

### Post by eschatologicalhumor on 2008-09-28
Tested, and proved.

Same method as above worked for my wired Ubuntu box.

---

### Post by Another Monkey on 2008-09-28
Connect to server from Ubuntu works from me, always has.
Going direct via the IP works too (both ways).

Navigating via the File Browser or Windows Explorer fails.
That is my problem.  I wan to be able to navigate just like I would on a Windows network and I *know* this is possible as I can do it in the office, or if I bring up a separate Windows instance in VMWare.

Can you navigate to your Ubuntu box from your Windows one, only using Explorer?

---

### Post by eschatologicalhumor on 2008-09-28
> **Another Monkey said:**
> Connect to server from Ubuntu works from me, always has.
Going direct via the IP works too (both ways).

Navigating via the File Browser or Windows Explorer fails.
That is my problem.  I wan to be able to navigate just like I would on a Windows network and I *know* this is possible as I can do it in the office, or if I bring up a separate Windows instance in VMWare.

Can you navigate to your Ubuntu box from your Windows one, only using Explorer?
I haven't tried the reverse, accessing the Ubuntu box from Windows only because there isn't any media on this laptop to access. This was a test for a project in progress; I'm creating a remote media server with an Epia VIA C3 motherboard for the bedroom.

But when I connect TO the Windows box or my Ubuntu desktop from the Ubuntu laptop, it auto-mounts the share folder and the File Browser opens instantly.

---

### Post by eschatologicalhumor on 2008-09-28
Anybody having sound issues?

I get NO sound from movies on either box I connect to.

Anyone else having this issue?

---

### Post by Another Monkey on 2008-09-29
<rant deleted>

I (almost) have it working at the office.  Ubuntu 8.04 cleanly reinstalled.
Attached to Windows maintained network (no changes to network settings allowed, Ubuntu **must **comply).
System updates installed.
Vanilla install of samba, smbfs, system-config-smaba and smbnetfs (not sure I need that last one).
Opened "Samba" under "Administration"
Preferences/Settings and gave it a workgroup name (it is the only box on the workgroup).
Left security at default.
Created a share, allowed all users to see it (read only).
Rebooted.
Navigated by IP once, and now Windows seems to work (very, very slow to display in Windows though).
Ubuntu cannot see any Windows shares though.

Note: bar the workgroup name and share, this is a **clean **install.  Do I need to add any accounts to assist the Windows boxes in browsing?  No I need to add accounts or soemthing to Samba?  I need to compare what I have to what i have at home I gues....at least at home I can share (even if the PCs refuse to see each other).

I'd call this progress in one direction.  Why would the Windows display be so slow?  Why can Ubuntu now not see any shares?  They exist and are open to all (well, a test one is...).

Once I get Ubuntu showing up consistently at work and at home, the next trick is to add some security to the shares.

Part of my rant still hoklds - getting Ubuntu to operate on a Windows network is way, way too hard.

---

### Post by Another Monkey on 2008-09-30
I just found this: [http://www.itwire.com/content/view/19728/1162/](http://www.itwire.com/content/view/19728/1162/)
Seems that Hardy is fundamentally broken and I have spent an age banging my head against something that will **never** work. 

More here:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)
[http://bugzilla.gnome.org/show_bug.cgi?id=522494](http://bugzilla.gnome.org/show_bug.cgi?id=522494)

Anyone know when this bug will be fixed (or how I can find out)?

---

### Post by Falkengeist on 2008-09-30
I tried the current and previous distributions of Ubuntu and was never fully able to resolve the Windows network display and access issues. I did find a Linux solution though. Try using the Xandros distribution.  It does not have all of these problems and it it very easy to use.

---

### Post by quad71 on 2008-10-01
Okay, so this is a known bug, broken and can't be fixed by the average joe schmuckatelly. So why on earth hasn't anybody on the Ubuntu team pointed this out? Almost a week of banging heads and not only did no one offer help, they didn't even bother to say it wasn't fixable! Thanks a lot.

---

### Post by *B* on 2008-10-02
Ok, I'll throw my 2 cents in here. 

I have 5 computers in my home. All 5 have XP Pro fully updated. 2 of those (a laptop and one desktop) are dual-boot systems with Ubuntu (also fully updated). 

After much reading and trial and error, I finally got the 2 Ubuntu systems setup where they saw and connected to the XP boxes and the shares on them... great. I could even play movies across the network, I was a happy camper. The only problem was, the XP machines could not access the Ubuntu machines and their shares. The Ubuntu machines would show up in XP, with the other XP boxes, and would even have something like Samba 3.02 behind it or something, but I could never access those machines from a XP machine. 

I didnt like it, but lived with it. Fast forward to a couple months ago. After an update of some sort to Ubuntu, now if I have any Ubuntu machine booted up..... my other XP boxes cant even access each other. I get the "WORKGROUP is not accessible" error. As soon as I shut the Ubuntu machine off, or boot it to XP, my XP machines can access each other again perfectly.

Also, now in my Ubuntu file manager, when I click "Network" it will then show "Windows Network" and then "WORKGROUP". But now (unlike before the update) when you click on "WORKGROUP" nothing comes up, it doesnt see anything. If I physically type in the address of one of the shares on an XP box (smb://192.168.x.x/shared/) it will easily display that share. I had to go through and create shortcuts for every share I had and list the IP address and share name to get my Ubuntu boxes to connect to the XP boxes now.

It is getting aggravating. 

So, in conclusion:

1. My XP Boxes cant see or connect to my Ubuntu boxes.
2. When one or both of my Ubuntu boxes are booted up, my XP network is totally hosed and I cant even see or connect to the other XP boxes.
3. Connecting to the netowrk through the file browser no longer works as it did before, and I had to make seperate launchers for each XP share to now access them.

---

### Post by haydnc on 2008-10-02
I no longer have any Windows machines active on my network so I can't test any of this out, but when I did I had them all talking windows <-> ubuntu so it might be worth checking these things out and seeing if they sort you out at all: 

(also apologies if I cover things you've already done - just doing this from memory of what I did)

Check that winbind and samba are installed:

System - Administration - Synaptic Package Manager
Search for winbind and select to install
Search for samba and select to install

**Note:** From memory winbind is what translates the machines IP address into human readable text so you'd no longer need to use smb://192.168.32.5 when browsing to/from the ubuntu machine you could use smb://mymachine instead. Or \\192.168.32.5 = \\mymachine if coming in from windows.

Edit the file /etc/nsswitch.conf by adding 'wins' to it so that the line that says:
hosts: files dns (there may be other things on this line)
now reads
hosts: files dns (whatever else is on that line) wins

(I'm guessing with all the work on this you've all done you're totally okay with editing files owned by 'root'. If I'm wrong about that let me know.)

Edit the /etc/samba/smb.conf file so that the line that says:
security = user
becomes 
security = share

**Note:** People may complain about this as it is less secure, but it means you don't need to have local user accounts for anyone/everone who wants to access shares on the ubuntu machine. If there is an easier way, please let me know it. This change sets it up so that access rights on any given file or directory are the ones used by the person accessing the file over the network. Let me know if that needs further explanation.

At the bottom of the smb.conf file your shares are defined, an example from your file is:
[homes]
comment = Home Directories
path = /home
read only = no
; available = yes
; browseable = yes
; guest ok = no
; printable = no
share modes = no
locking = no

If I were going to share a directory that was sitting in my home drive I would use:
[MyShare]
comment = the share i set up
path = /home/haydnc/shareddir
read only = no
available = yes
browseable = yes
guest ok = yes

Then I would make certain that under my home directory 'sharedir' exists and has 777 permissions set on it. (chmod 777 sharedir -R)
I am sure that there are easier ways to set this up, but I've been doing it from the command line so long I never bothered to learn the easier ways.

~~~

Once all that is done I think you need to restart some services:
```
sudo /etc/init.d/networking restart
sudo /etc/init.d/samba restart

```

I think those are the right codes - you could just reboot instead.

I think that was it for the basic setup. You should be able to browse to the Ubuntu machine from the windows machine:
\\ubuntumachine
and get a list of the shares active on the ubuntu machine

Or browse to the windows machine from the ubuntu machine:
smb://windowsmachine

If that doesn't work try using ping to test that traffic is going both ways - I did have massive problems getting windows firewalls, both built in and third party, to let communication travel to/from other machines on my network. Simple test for that is to briefly disable firewalls and try again.

As far as browsing from the windows machine using "My Network Places". It does work, you just need to make sure your workgroup in the smb.conf file matches your home network name. You've said in an earlier post that it does, so that shouldn't be a problem. You should theoretically see the ubuntu machine listed under the workgroup name.

Browsing back the other way works too... from memory the only thing I had problems with was the Home - Connect to server  option. I seem to remember that not working at all well.

~~~

Sorry for the huge post - hopefully something in there will help you all out a bit if you've not given up and left already. I guess I should check out these forums a little more often.

I'll keep an eye on this thread and give what troubleshooting help I can. For the record I'm using Ubuntu 8.04.1 at the moment and while there were some problems with networking becoming 'broken' via some of the Ubuntu updates I've never found it to be a huge problem to network windows and Ubuntu machines. Except when I was still on beta versions of Ubuntu, but that's not too unexpected really.

~~~~ 
Edit: before I forget, you might ask why this stuff - particularly the winbind bit isn't enabled by default. Others have asked and apparently the answer is that winbind is under the universe (therefore not free - or community maintained only or something like that) repositories. For this reason its not a default part of Ubuntu no matter how much we might like it otherwise.

---

### Post by *B* on 2008-10-03
Just a quick note to say THANK YOU for taking the time to post this! The additions to the nsswitch and smbconf did away with 2 of my problems. My XP machines can now see and access my Ubuntu machines/shares, and also when one/both of the Ubuntu machines are booted, my XP machines can communicate fine now. 

Now, down to the last problem of not being able to go further than "Network/Windows Network/Workgroup" in Nautilus. I still have to access the computers on the network with shortcuts I made specifically to shares. Just like in XP, I used to be able to click "Workgroup" and see all the computers that were currently logged on, then click them and see/access the shares for each computer. Now when I click Workgroup it shows no computers at all. 

I DO know though that if this is a wrong setting, it was caused by an update. This worked for the longest time, and then all of the sudden stopped after an update a while back.

Thanks again!

---

### Post by *B* on 2008-10-05
well, I guess I spoke too soon. The fix you mentioned alleviated 2 of my 3 problems on my Dekstop, but the Laptop still has the same issues. I cant even see it from an XP box, or the Desktop (whether booted to Ubuntu or XP). I can see the other XP boxes from my laptop (when its booted to Ubuntu) but it doesnt even show up to the XP boxes.

Setting up a simple home network should NOT be this hard.

---

### Post by haydnc on 2008-10-05
Just to confirm the issues you're now having, before we go trying to come up with fixes for them:

**First**, on your desktop when booted into Ubuntu:
If you browse to: Places - Network - Windows Network - Workgroup you have no (Windows?) machines listed?

Please confirm whether you can browse to the windows machine(s) directly by using 
smb://<windows machine name> and get a list of shares on the windows machine, or even 
smb://<windows machine name>/<share name> to see the contents of a windows machine share. 

This is just so that I can confirm that the problem isn't caused by the shares on the windows machines not being accessible at all. 

From memory I don't ever have to browse down through Places - Network - Windows Network - Workgroup because any machines on my network with active shares appear at the very top level and can be seen the second I go to Places - Network. And I do definitely have one windows XP machine on my network that I'd forgotten about, so I can confirm that this holds true for that one.

**Second** when the laptop is booted into Ubuntu it doesn't show up at all on the other machines, whether they're booted into Windows or Ubuntu? 

Please confirm that you've checked the /etc/nsswitch.conf and /etc/samba/smb.conf on the laptop (as per the earlier post), you've got samba and winbind installed. If you could also let me know what methods you've tried to use to access the laptop from the XP machines that didn't work. 

i.e. were you just trying to access the laptop via its name \\<laptopname> from the windows machine(s) or did you also try via IP address \\192.168.1.whatever-the-laptops-ip-address-is

Do you experience the same problem(s) when deliberately turning off any firewalls you've got running on the windows machine, both third party and built in windows firewall?

If the desktop is booted to Ubuntu **and** the laptop is booted to Ubuntu can they see each other at all?

~~~

Please, let me know and I'll see what I can do to come up with answers for you. For whatever its worth to you, in the past - once I had the basic networking issues sorted out on my Ubuntu machines - every time I had a problem it was related to the windows machines firewall or the windows machine failure to update its network view.

I won't tell you that it's always been easy getting the Ubuntu side of the network right. Once an update I installed broke networking entirely, and I know I still don't have things set up the best way possible, using the security = share option alone makes sure of that... I can just assure you that once it has been sorted out on one Ubuntu machine the same formula tends to work on all the other ones too and once **that** has been done the problem tends to lie on the Windows side - for me that usually is caused by their firewalls killing all internal network traffic.

---

### Post by conorturton on 2008-10-05
> **quad71 said:**
> Okay, so this is a known bug, broken and can't be fixed by the average joe schmuckatelly. So why on earth hasn't anybody on the Ubuntu team pointed this out? Almost a week of banging heads and not only did no one offer help, they didn't even bother to say it wasn't fixable! Thanks a lot.

Because if they did, they'd have to admit that they broke something which was working absolutely fine in 7.10. Sadly, you're banging your head against the "Microsoft is evil" brigade. As long as you can see Linux machines, they don't give a toss about Windows ones. Welcome to the Linux fanboi elitism.:(

---

### Post by *B* on 2008-10-06
[QUOTE=]Originally Posted by **haydnc**
Just to confirm the issues you're now having, before we go trying to come up with fixes for them:

**First**, on your desktop when booted into Ubuntu:
If you browse to: Places - Network - Windows Network - Workgroup you have no (Windows?) machines listed?[/QUOTE]
Correct. If I type in **192.168.1.X/shared** it will take me to the shared folder named "shared" on that XP machine. If I just type in the IP address, it wont show me the shared folders on that machine. I have to physically type in the exact address and name of the share.

[QUOTE=]Please confirm whether you can browse to the windows machine(s) directly by using 
smb://<windows machine name> and get a list of shares on the windows machine, or even 
smb://<windows machine name>/<share name> to see the contents of a windows machine share.[/QUOTE] 
no to the first part, yes to the second part (explained above).

[QUOTE=]This is just so that I can confirm that the problem isn't caused by the shares on the windows machines not being accessible at all. [/QUOTE]
Understood, but not the case. If it was the XP machines, I couldnt access them with the Ubuntu desktop. Its not a firewall issue. I run static IP's and have rules written specifically for the IP addys on my LAN. The Ubuntu Laptop cant see, or be seen. A XP firewall could block incoming access (if not set right) from the Ubuntu laptop, but it could still be seen, and that wouldnt keep that same XP machine from seeing the Ubuntu laptop.
.
[QUOTE=]From memory I don't ever have to browse down through Places - Network - Windows Network - Workgroup because any machines on my network with active shares appear at the very top level and can be seen the second I go to Places - Network. And I do definitely have one windows XP machine on my network that I'd forgotten about, so I can confirm that this holds true for that one.
I never had to either till after I ran some updates a while back. When I would browse to places/network it listed all the boxes currently booted on the LAN.

**Second** when the laptop is booted into Ubuntu it doesn't show up at all on the other machines, whether they're booted into Windows or Ubuntu? [/QUOTE]
correct, nor can **it** see **them**

[QUOTE=]Please confirm that you've checked the /etc/nsswitch.conf and /etc/samba/smb.conf on the laptop (as per the earlier post), you've got samba and winbind installed. If you could also let me know what methods you've tried to use to access the laptop from the XP machines that didn't work. [/QUOTE]
To avoid a lengthy post, I have IM'd you a copy of both conf files. Both these files are exactly the same on the desktop (other than the computer name) and work perfectly. Samba & winbind are installed. If they arent running, Im not aware of it, nor would I know why they arent. Ive tried accessing the Ubuntu laptop from the XP machines by both going through network neighborhood (the Ubuntu laptop isnt listed even though the ubuntu desktop is listed <b>and</b> accessible) and I have tried typing the IP addy & share name of the ubuntu laptop, into the address bar and it still comes up with nothing. When desktop and laptop are **both** booted to ubuntu, the laptop sees nothing (XP boxes or ubuntu desktop) and no boxes (ubuntu or XP) can see the laptop through any methods.

[QUOTE=]i.e. were you just trying to access the laptop via its name \\<laptopname> from the windows machine(s) or did you also try via IP address \\192.168.1.whatever-the-laptops-ip-address-is[/QUOTE]
both

[QUOTE=]Do you experience the same problem(s) when deliberately turning off any firewalls you've got running on the windows machine, both third party and built in windows firewall?[/QUOTE]
yes

[QUOTE=]If the desktop is booted to Ubuntu **and** the laptop is booted to Ubuntu can they see each other at all?[/QUOTE]
no. The desktop can see the XP machines and they can see it, but nothing sees the laptop, nor can it see anything.
~~~

[QUOTE=]Please, let me know and I'll see what I can do to come up with answers for you. For whatever its worth to you, in the past - once I had the basic networking issues sorted out on my Ubuntu machines - every time I had a problem it was related to the windows machines firewall or the windows machine failure to update its network view.

I won't tell you that it's always been easy getting the Ubuntu side of the network right. Once an update I installed broke networking entirely, and I know I still don't have things set up the best way possible, using the security = share option alone makes sure of that... I can just assure you that once it has been sorted out on one Ubuntu machine the same formula tends to work on all the other ones too and once **that** has been done the problem tends to lie on the Windows side - for me that usually is caused by their firewalls killing all internal network traffic.[/QUOTE]

All I know is its not a firewall issue. The might keep the Ubuntu boxes from accessing the XP boxes, you could still see them listed in the network list as they boot up and register on the network. It also wouldnt be affecting the 2 ubuntu boxes communicating.

Ive had updates hose up my network before. Ive had it hose up my bluetooth, my wireless (recently hosed it up and had it set auto @ 1mb/sec connection rate) and no telling what other things IM forgetting off the top of my head. It got to the point I almost trashed linux and gave up. But, Im stubborn, so I didnt. It sucks having your system and settings screwed all the time updating though.

I DO want to thank you very much for taking time to read the thread and help if you can, its very much appreciated!

--------------------------------------------------------------------------------------------

**UPDATE:**
Just for grins & giggles I decided to take my laptop into the office and plug it into my swicth and use a wired connection. Guess what? When I booted the laptop into Ubuntu, it saw the other boxes and was able to access the shares on them (ubuntu and XP both) and they (ubuntu and XP) could see the laptop and access the shares on it. 

**But** as soon as I unplugged it fromt he switch and went back to using a wireless connection only, I was back in the same boat with the same results.... cant see anything and nothing can see the laptop when in ubuntu..... what the hell? Im wondering if the update that screwed up the connection speed of my wireless did something else. It works fine for internet.

---

### Post by haydnc on 2008-10-06
Having seen that last update you posted I'm inclined to agree that the problem is a wireless networking one and you've actually got your core networking setup as right as it needs to be. That's particularly true in light of your statement that something recently messed up your wireless networking in a big way. 

I've picked up a thing or two for getting networking working, but I have to tell you I've had virtually no issues with wireless networking ever. I've been one of those lucky ones that it worked out of the box for every time since I first got a machine with wireless capability. Unfortunately for you that means I've got very few tips or tricks for how you might fix your network visibility issues if it is solely a wireless networking issue.

I do believe a number of other people have had problems with the default network manager (NM-Applet) in the past so if you search the forums and/or hit up Google for some answers you'll probably be able to turn up more effective advice on the subject than any I can give.

That said, what I can do if you'd like is post the content of my nsswitch.conf and the important bits of my smb.conf files if you think it'd help. They are subtly different to the ones you sent me via PM. I just don't believe that there is anything in them that would cause your laptop to show up on a wired network when it doesn't on a wireless one.

Apologies if I'm thrashing an already dead topic there, but if you're having success on your wired network adapter and not on the wireless one is there any way that something somewhere is killing data transfer to/from your wireless network card? Something in your router setup perhaps, or perhaps the setup on the W-NIC its self? It would seem to be the more logical explanation.

---

### Post by *B* on 2008-10-07
I agree, its something in the wireless setup, but its in Ubuntu, not my hardware. I use a Belkin router as an AP only, and it works perfectly when booted to XP(internet & LAN both). As I said, the wireless works great where the internet is concerned in Ubuntu, I just cant see/connect to the LAN.

Especially, as discussed, when you consider an update awhile back screwed up a LOT of people's RT2500 connections. Mine was one of those, and I came here and found out quickly what had happened. My (and others) speed got set to a 1mb/sec default connection rate.

I dont use Network Manager. I couldnt even type a single character in it, so I removed it.

Thanks again for your help.

---

### Post by theDaveTheRave on 2008-10-08
Hi guys,

You seem to be strugling rather a lot, I must admit it had me struck dumm for a while also.

firstly, check out this forum post by Stormbringer.
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

I then realised that in the samba installation there needs to be an extra "bit" to enable windows to see the linux desktop, I found that this link explained what I needed to get, I think it was <smbfs>, Ah yes after a short search I found the page, here is a short snippet

> 
The Samba metapackage is not necessary on clients to:

    *

      Access shared folders, drives and printers on a Windows computer (that is, act as a client with Windows servers), you only need the smbfs plugin. See MountWindowsSharesPermanently
    * Have your Windows computer use (via a network) a printer that is attached to a Linux computer. CUPS can be configured to make the printer accessible to the network.
    *

      Share directories between two Linux computers. You can use NFS or setup an SSH server on one computer and access it from other computers using an scp or sftp client, or Places > Connect to... > SSH in Ubuntu. See [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)


and here is the [full documentation.]("https://help.ubuntu.com/community/SettingUpSamba")

Personally I have a different issue relating to fixed IP addresses, when I use the <network settings> dialogue to set the details of the fixed IP and server details, the networking fails!

I hope I have been able to add to both the solution and add some more to a horrible problem for linux / ubuntu!

Dave

Edit 1:

Sorry just realised something I had forgotten.

you need to edit the etc/hosts file with the IP address and computer names so as to be able to ping a computer by it's name, this is the copy on the pc I am using at my research post.
> 
myersdav@bibe:~$ more /etc/hosts
127.0.0.1       localhost.localdomain           localhost
192.168.206.78  bibe.univ-rouen.fr              bibe

# Serveurs infographie
192.168.206.40  zeus.univ-rouen.fr              zeus
192.168.206.81  moustique.univ-rouen.fr         moustique
192.168.206.83  mouche.univ-rouen.fr            mouche

# Serveurs impression
192.168.206.80  vulcain.univ-rouen.fr           vulcain
192.168.206.42  grenouille.univ-rouen.fr        grenouille
myersdav@bibe:~$


Also I just found this on network config on the UbuntuDocs site, I don't know if it will be helpfull or not, here is the [link]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html")

---

### Post by *B* on 2008-10-08
theDaveTheRave: Hot DAMN I could kiss you! As soon as I read about the hosts file, I remembered I hadnt edited it on my laptop.... and THAT did the trick! My lappy now is visible when connected to the LAN wirelessly. 

NOW, here is my question....(and not just for Dave).... it worked before.... what I dont get is why I had to edit the hosts file after all this time? And, if that was the culprit, why did it work when connected via hard wire to the LAN? It boggles the mind I tell ya lol.

OK, I lied..... two questions....... why in the hell did ALL the tutorials I read ages ago tell me to install the full Samba metapackage in order to network with WIndows machines, when all that was needed was a plugin? Thats ridiculous. Networking should NOT be this hard to setup, or maintain.

Now, if I can just get my Ubuntu machines to display the shares of the the other computers. I still have to use my shortcuts I made as sometimes the browser displays the computers and then their contents, and sometimes it doesnt.

THANKS AGAIN!

---

### Post by theDaveTheRave on 2008-10-08
*B*

Glad to be of service.

regarding your /etc/hosts file, I think, but could be wrong, that you may be able to set this to be different for different locations, hence when you go to work everything works fine etc.

Try copying the various setup files when you are in a known good location

so you will want:

/etc/hosts
etc/network/interfaces

and I'll look up the other and get back to you!!! but I think they are in the links I posted earlier.

TTFN

Dave

---

### Post by duanyang on 2008-10-08
Hi I installed ubuntu 8.04 on my HP dv6707us notebook as dual boot. I have problem to connect to internet in ubuntu (but with window vista it is fine). 

it uses atheros AR242x 802.11abg wireless PCI express adapter and 
it uses nVidia MCP67 ethernet interface. At home i have a dynamic ip connection (optimum/comcast cable) to internet. 

I have done quite some digging in this forum. i have downloaded net5211.inf driver. i have downloaded ndiswrapper (compiled and installed). somehow neither wireless nor wired connection works now. 

when i use duso lshw -C network and i see: 
the wireless driver is ndiswrapper+net5211
the ethernet interface: driver=forcedeth. 

in System->administration->network, i see both interface. i set dhcp correctly. in System->administration->hardware drivers, i have enabled both Atheros hardware access layer (HAL) and suppor for atheros 802.11 wireless LAN cards. 

Anyone has suggestion how to sort this out? i am a newbie to ubuntu. i have spent quite some hours but without success. 

thank you very much,
Dan
p.s. the notebook worked for networking when using static ip in another location a few days ago.

---

### Post by theDaveTheRave on 2008-10-10
duanyang

I'm surprised that there are no other forums that have been able to solve your problem!

I'm no expert of wireless, but this should help you find out what you need to be able to do a better search, or maybee solve your problem?

run this command
> 
iwlist scan


it should return details of any network devices that support scanning, unsurprisingly most of them wont. at the moment I can't paste a sample output, but is should contain details similar to the following

> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:18:01:EF:D2:70
                    ESSID:"yourESSID"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    


If you get a response similar to that then you are almost there with the wireless

try entering
> 
sudo if[COLOR="Red"]down[/COLOR] [COLOR="Blue"]ath0[/COLOR]

replace [COLOR="Blue"]ath0[/COLOR] with the name of your interface that was supporting scanning.

This will have brought [COLOR="Red"]down[/COLOR] the interface, so now you want to start it [COLOR="Red"]up[/COLOR] again
> 
sudo if[COLOR="Red"]up[/COLOR] [COLOR="Blue"]ath0[/COLOR]


This may have solved your networking problem, but you should know as you will get a string of errors regarding your wireless device being unreachable or similar.

if you haven't solved the problem still, and I get the feeling that is going to be unlikely! you need to make sure of the chip set of your device

> 
lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       [COLOR="Blue"]description: Wireless interface
       product: *_AR5416 802.11abgn Wireless PCI Adapter_*
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wifi0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 [/COLOR]module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.2 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes


The higlighted section is the part that will confirm you are using the chipset you think you are.

sorry I can't be of much more service, good luck.

Dave

---

### Post by theDaveTheRave on 2008-10-21
Hi again all.

After much searching I have found out the following and been able to set a static IP and stuff.

here is how I did it. If you find this helpfull please say as I'm contemplating puting it in the <HOWTO> section.

So here goes.

-------------a quick howto-------- tell me if this works for you please.

All the terminals where I work are on a static IP system, as there is essential data that need to be shared between the computers.

Before I arrived the team had built a rather nice terminal that was to ultimately become a source for all thier shared data. They attempted to run a variety of Linux flavours on the terminal with the required static IP, so as they would then still be able to easily access from external sites.

I suggested that I examine why they couldn't get a static IP to work on this "soon to be a server" by showing how to do it on my Ubuntu Laptop.

First attempts where a dismal failure, each time the details were entered into Network manager, networking failed immediately! I hunted high an low on the internet for a solution, from my understanding there was either an issue with the connection to the correct DHCP name server or something wrong with the network mask.

Here is a diagram of how my network is.

Now the strange thing here is that the PC is a windows XP terminal (not for long though if I have my way), and running the <ipconfig> command on this terminal give the following information.

> 
Configuration IP de Windows





        Nom de l'hôte . . . . . . . . . . : Anticlimax


        Suffixe DNS principal . . . . . . : 


        Type de nœud . . . . . . . . . . : Inconnu


        Routage IP activé . . . . . . . . : Non


        Proxy WINS activé . . . . . . . . : Non





Carte Ethernet Connexion au réseau local:





        Suffixe DNS propre à la connexion : 


        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Controller


        Adresse physique . . . . . . . . .: 00-1D-09-0A-44-8D


        DHCP activé. . . . . . . . . . . : Non


 [color="blue"]       Adresse IP. . . . . . . . .*. . . : 134.157.195.42


        Masque de sous-réseau . . .*. . . : 255.255.255.0


        Passerelle par défaut . . .*. . . : 134.157.195.126


        Serveurs DNS . . . . . . . . . .  : 134.157.0.129
[/color]




As you can probably tell I work in France!

Now running ifconfig on my ubuntu terminal 
> 
davem@Dartagnan:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:19:7d:40:b8:c0  
          inet6 addr: fe80::219:7dff:fe40:b8c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[color = "blue"]eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:134.157.195.83  Bcast:134.157.195.127  Mask:255.255.255.128
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
[/color]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78699 (76.8 KB)  TX bytes:78699 (76.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-40-B8-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26011 errors:0 dropped:0 overruns:0 frame:16292
          TX packets:6150 errors:35 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:4716117 (4.4 MB)  TX bytes:279792 (273.2 KB)
          Interrupt:18 



now I wasn't entirely sure on the DNS server that I was hooked into, on a further search on the internet (don't you just love googe) I found this site

and it gave me a way to find the required detail.

It is apparently hidden in a file that will relate to the dhclient, so we need to have a search for this file with the following

> 
davem@Dartagnan:~$ locate dhclient
/etc/dhcp3/dhclient-enter-hooks.d
/etc/dhcp3/dhclient-exit-hooks.d
/etc/dhcp3/dhclient.conf
/etc/dhcp3/dhclient-enter-hooks.d/avahi-autoipd
/etc/dhcp3/dhclient-enter-hooks.d/debug
/etc/dhcp3/dhclient-enter-hooks.d/samba
/etc/dhcp3/dhclient-exit-hooks.d/debug
/etc/dhcp3/dhclient-exit-hooks.d/ntpdate
/etc/dhcp3/dhclient-exit-hooks.d/whereami
/etc/dhcp3/dhclient-exit-hooks.d/zzz_avahi-autoipd
/etc/dhcp3/dhclient-exit-hooks.d/zzzz_dhcdbd
/lib/dhcp3-client/call-dhclient-script
/sbin/dhclient
/sbin/dhclient-script
/sbin/dhclient3
/usr/share/man/ja/man5/dhclient.conf.5.gz
/usr/share/man/ja/man5/dhclient.leases.5.gz
/usr/share/man/ja/man8/dhclient-script.8.gz
/usr/share/man/ja/man8/dhclient.8.gz
/usr/share/man/man5/dhclient.conf.5.gz
/usr/share/man/man5/dhclient.leases.5.gz
/usr/share/man/man8/dhclient-script.8.gz
/usr/share/man/man8/dhclient.8.gz
/usr/share/man/man8/dhclient3.8.gz
[color="blue"]/var/lib/dhcp3/dhclient.ath0.leases
/var/lib/dhcp3/dhclient.eth0.leases [/color]
/var/lib/dhcp3/dhclient.leases
/var/lib/whereami/dhclient3.ath0
/var/lib/whereami/dhclient3.eth0
davem@Dartagnan:~$ 


we now need to look into the suspect files, in my case the eht0 file (as I am in a hard wired connection - I assume that if I had a wireless router I would look into the ath0, so here is my current file.

> 
davem@Dartagnan:~$ more /var/lib/dhcp3/dhclient.eth0.leases
lease {
  interface "eth0";
  fixed-address 134.157.195.83;
  server-name "";
  option subnet-mask 255.255.255.128;
  option dhcp-lease-time 3564;
  option routers 134.157.195.126;
  option dhcp-message-type 5;
  option dhcp-server-identifier 134.157.195.99;
  option domain-name-servers 134.157.0.129;
  option host-name "Dartagnon";
  option domain-name "local";
  renew 2 2008/10/21 07:15:13;
  rebind 2 2008/10/21 07:37:38;
  expire 2 2008/10/21 07:45:04;
}
lease {
  interface "eth0";
  fixed-address 134.157.195.83;
  server-name "";
  [color="red"]option subnet-mask 255.255.255.128;[/color]
  option dhcp-lease-time 3564;
  option routers 134.157.195.126;
  option dhcp-message-type 5;
  option dhcp-server-identifier 134.157.195.99;
  option domain-name-servers 134.157.0.129;
  option host-name "Dartagnon";
  option domain-name "local";
  renew 2 2008/10/21 06:54:46;
  rebind 2 2008/10/21 06:54:46;
  expire 2 2008/10/21 06:54:46;
}
davem@Dartagnan:~$


Now the important part, and this is where my previous experience caused my internet connection to break, is in red. The subnet mask, this controls the possible IP addresses that the terminal can hold. For some reason the XP terminal has a different mask (admitedly only the last set of digits are changed from ".0" on XP to ".128" on Ubuntu) - if someone can explain why this is I will be truly grateful!

So now we can set out static IP, either via the Network Manager GUI or via the file directly.

Via Network Manager.

Obviously you will have started network manager, unlocked it with your admin password, and selected your eth0 connection. Now you need to click the <properties> button

You now have the options for setting the various IP settings, obviously first off you need to change the <configuration> selection to "Static IP address" and then enter in the details into the required sections as dictated by your </var/lib/dhcp3/dhclient.eth0.leases> file.

Hopefully that should give you success? remember to save the location details, and then whenever you are on this location you will need to change your network location to this location.

Via the file directly.

Nework manager actually causes a change in the </etc/network/interfaces> file that is as the following

> 
davem@Dartagnan:~$ more /etc/network/interfaces
auto lo

iface lo inet loopback




iface ath0 inet dhcp
wireless-key ********
wireless-essid BIBOU





[color="blue"]iface eth0 inet static
address 134.157.195.83
netmask 255.255.255.128
gateway 134.157.195.126[/color]

auto eth0
davem@Dartagnan:~$ 


The important details in this file is the first line stating [color="blue"]iface eth0 inet static[/color]. Appart from that ensuring the details for the address, netmask and gateway are as reported in the </var/lib/dhcp3/dhclient.eth0.leases> file, you will notice that you do not need to have the DHCP server details in the file, I guess the network will automatically ask for this from the DHCP server, wherever it is.

So assuming someone changes the address of the server (eg. an office move causing a new subnet network to be created for the departmet), your system should still ask for the same IP address from the new DHCP server (allthough for all intents this is the "same" machine, its IP address may have changed!).

Proviso to this help file.

I'm no network admin or Linux guru, if you have a problem I will try to help, but I don't know if this will work with wireless cards or not.... although we do have a wireless network here at my office!

a quick recap.

usefull files / commands are:

[COLOR="DeepSkyBlue"]/etc/network/interfaces[/COLOR] - self explanatory!
[COLOR="DeepSkyBlue"]/var/lib/dhcp3/dhclient.eth0.leases[/COLOR] (however this may be different in your system, you will possibly need to do a <[COLOR="SeaGreen"]locate dhclient[/COLOR]> to find your particular file.
[COLOR="SeaGreen"]ifconfig[/COLOR] - to show all your networking interfaces details.
[COLOR="SeaGreen"]iwlist scan[/COLOR] - will show all available wireless networks.
[COLOR="SeaGreen"]route[/COLOR]to show your IP tables, the information in here is also repeated in dhlient.leases file
[COLOR="SeaGreen"]traceroute [IP address][/COLOR] - will show the various server etc that a <[COLOR="SeaGreen"]ping[/COLOR]> command would pass through on its way to the IP Address

Well I hope this information is of assistance to everyone out there

Dave

---

### Post by chefhossein@verizon.net on 2008-10-21
The easiest way to for Ubuntu machine to see Vista use Terminal

type: code: nautilus smb://xxx.xxx.x.xxx   this being your vista ip
it takes you to File Browser you are going see nothing,but put a slash / in front of the ip address and put the name your shared folder name exactly the way is in you Vista shared folder in my case "public" it prompts to log on put the id and password.
this should work. please after getting in that shared folder in Vista, Bookmark it so you do not have to do this every time.

---

### Post by haydnc on 2008-10-21
> ***B* said:**
> theDaveTheRave: Hot DAMN I could kiss you! As soon as I read about the hosts file, I remembered I hadnt edited it on my laptop.... and THAT did the trick! My lappy now is visible when connected to the LAN wirelessly. 

So what exactly did you need to change in your hosts file to make it visible where it wasn't before? I wouldn't think it would be necessary to manually add the IP's and names of all the other machines on your network, particularly if you're using DHCP so did you have to modify something specific to the laptop its self?

> ***B* said:**
> OK, I lied..... two questions....... why in the hell did ALL the tutorials I read ages ago tell me to install the full Samba metapackage in order to network with WIndows machines, when all that was needed was a plugin? Thats ridiculous. Networking should NOT be this hard to setup, or maintain.

I can only speak for myself, but since hard drive space has not been an issue for me since back when I was using Windows 95 I never bothered to work out if only a bit of Samba was needed to do what I wanted. It was always just easy to install samba as a whole. Call me lazy or spoiled by modern hard drive sizes if you want, you'd probably be right. ;)

---

### Post by theDaveTheRave on 2008-10-22
hi all,

from haydnc
> So what exactly did you need to change in your hosts file to make it visible where it wasn't before? I wouldn't think it would be necessary to manually add the IP's and names of all the other machines on your network, particularly if you're using DHCP so did you have to modify something specific to the laptop its self?

I don't think this is so much an issue with the /etc/hosts file as for the machine to be able to get a host name quickly and easily from the IP address. Personally I find it easier (on the first occasion at least) to be able to put in the address of a shared folder as //nameOfComputer/folder...blah..blah..blah...  than to have to use //someHorribleIPAddressThatICanNeverRemember/....

Other wise I think you have a valid point, that said however.... on my network here I can only see the shared folder on the machine that lives in my /etc/hosts file.... so I suspect it may be a config requirement, unless you have access to the "server" to be able to see all the potential subfolders (or in this case the shared folders on various machines).

Basically, I'm not sure why they are needed, but if they are there things seem to happen a lot more easily than if they aren't! I will check this shortly on the new server I have just set up!

Dave

---

### Post by anachronon on 2009-01-01
I don't know if anyone is still following this thread.  But, just in case, I now have the same problem.  I have a WinXP laptop that I was connecting wirelessly to a Linux PC.  I was using the connection to access a parallel-port printer that is connected to the PC.  It was made through Samba, and for a year, it worked great.

Then, sometime around the end of November, the connection just quit working.  I have been pulling my hair out, ever since.  There seems to be no solution.  All of the settings were the same as when it was working!  What changed?  Could the cause be an update gone bad?

About the only odd thing I found, is that I can ping the Linux PC from the WinXP laptop.  Yet, I can NOT ping the WinXP laptop from the Linux PC!  How is that possible?  Is that even my problem.

The other odd thing is that, suddenly, I can't seem to open the permissions on the Samba share folder.  "sudo chmod 777" seems to do no good.  According to the properties listed in the file browser, access is still restricted to root.

Has anyone found any answers?  I am desperate.  I need to be able to use my printer from my laptop!

---

### Post by Gnostabuntu on 2009-01-06
This problem definitely seems to be reoccurring, Did you try configuring your samba file? I'd Check out this site real quick and give it another try ((Man>CPU))
[http://www.go2linux.org/how-to-install-samba-on-linux-with-swat]("http://www.go2linux.org/how-to-install-samba-on-linux-with-swat")

Hollar back if this helped!

---

### Post by anachronon on 2009-01-11
> **Gnostabuntu said:**
> This problem definitely seems to be reoccurring, Did you try configuring your samba file? I'd Check out this site real quick and give it another try ((Man>CPU))
[http://www.go2linux.org/how-to-install-samba-on-linux-with-swat]("http://www.go2linux.org/how-to-install-samba-on-linux-with-swat")

Hollar back if this helped!
Yes, I reconfigured everything, both on Linux and Windoze.  I also double-checked my configurations, assuming that something might have been changed.  No Luck.  I even reinstalled a few settings.  Still no luck.

For those interested, there is also a good Samba set-up and configuring tutorial on this forum:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

