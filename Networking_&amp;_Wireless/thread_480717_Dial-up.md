---
title: "Dial-up"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Bartender on 2007-06-21
Did some dial-up testing on a brand-new Feisty install today.  Trying to find solutions for 2 of the problems that have come up fairly often in dial-up threads - the /etc/resolv.conf problem and a solution for installing gnome-ppp to a PC that can't get online.  The /etc/resolv guide definitely works.  So does the gnome-ppp d/l but I don't know if there's a newer version available.


**Create /etc/resolv.conf file**

The following was done on a brand-new copy of Ubuntu 7.04.   Xubuntu's file editor is a little different, not quite as automatic as Ubuntu's.  

Just so you know where the etc/resolv.conf file should be, go to Places>Computer>File System, then click on &#8220;etc&#8221; to display its contents.  Scroll down past the bright orange folders to the plain-looking files below.  You'll find no file between &#8220;rc.local&#8221; and &#8220;rmt&#8221;.  Close out of File System.
Click on Applications>Accessories>Terminal.  At the blinking cursor type (or better yet paste this command directly into your terminal)        

```
sudo touch /etc/resolv.conf
```

and click &#8220;Enter&#8221; key.  You'll be asked for your password.  Type it in and hit &#8220;Enter&#8221; again.  It'll seem like nothing happened.  All you'll see is a new line prompting you for input, just like the very first line when you opened the terminal.  Close out of terminal.
Now go back to File System, click on &#8220;etc&#8221;, scroll down and you'll find a new file &#8220;resolv.conf&#8221; in between &#8220;rc.local&#8221; and &#8220;rmt&#8221;.
Congratulations!  You've created an empty /etc/resolv.conf file.

**Install gnome-ppp**

Go online with any old Windows PC and find this site 
[http://packages.ubuntu.com/dapper/net/gnome-ppp](http://packages.ubuntu.com/dapper/net/gnome-ppp)  
Download the correct package for your situation.  i-386, PowerPC, or 64-bit.  I downloaded the i-386 version.  Notice this appears to be a version of gnome-ppp for Dapper.  I don't know if there's a newer version for Feisty but this one seems to work.  At least there weren't any errors.  I was not able to actually test it out because of our crappy ISP.

(EDIT:  Please see next post - more info regarding packages)

Download the package to your Windows desktop, then burn it to a CD.  
Pop the CD into your Ubuntu PC.  CD should spin up.  File Browser window appears, identifies &#8220;gnome-ppp_0.3.23-0ubuntu2_i386.deb&#8221;.  
Double-click on the package.  New window comes up.  This window should say : 
&#8220;Package: gnome-ppp&#8221;
&#8220;Status: All dependencies satisfied&#8221;

There's other text within the window, but I want you to make note of the package and status comments.

Click on &#8220;Install Package&#8221;.
Enter password.

The next step took almost 20 seconds on my old PIII 450MHz, so be patient if you're on an older PC.  The &#8220;Package Installer&#8221; window finally comes up and informs you of progress.  After a short time you'll get &#8220;Installation Finished&#8221;.
Close the active windows, go to Applications>Accessories>Internet and find &#8220;GNOME PPP&#8221;.  Congratulations again!  You've installed gnome-ppp to your Ubuntu PC!  It's easy to put an icon for gnome-ppp on the desktop from there.

(NOTE: Transferring gnome-ppp is easier with a thumb drive.  Copy the downloaded package to a thumb drive, go thru the Windows steps to release the thumb-drive, plug it into the Ubuntu PC, click on the icon that comes up on the desktop, save the gnome-ppp package to your desktop, then double-click on it to start the installation.  Don't forget to right-click on the thumb drive icon and "Eject" it before removing it from the Ubuntu PC)

The above addresses only two of the dozen or so stumbling blocks for dial-up users.  Please feel free to add any good stuff you've figured out.  Dial-up help is scattered all over the Ubuntu forums and I'd like to gather some of it together if possible!

---

### Post by Bartender on 2007-06-22
Whoops, there is a Feisty "gnome-ppp" package.
[http://packages.ubuntu.com/feisty/net/gnome-ppp](http://packages.ubuntu.com/feisty/net/gnome-ppp)

The package search is handy - didn't know about that!
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Bartender on 2007-07-06
I've always been a little put off by wvdial, but gave it a try today.
Fresh Feisty install as described above, with the blank /etc/resolv.conf file, gnome-ppp downloaded from a Windows PC and installed.
I didn't know if other things had to be done to make dial-up work, so I just tried it.

Went into terminal, typed 
```
sudo wvdialconf /etc/wvdial.conf
```
Entered password
wvdial cranked out a bunch of lines, indicating that it saw my 5686-03 US Robotics external Sportster on ttys0.

Then I typed into the open terminal line 
```
sudo gedit /etc/wvdial.conf
```
This opens the /etc/wvdial.conf file.

I only changed 3 lines.  To move the cursor up, down, left & right use your arrow keys, not the mouse.  Get the cursor to the line that says
"; Phone = " 
Remove the ";" and the space so that the word "Phone" is up against the left border.  Use your arrow key to place the cursor one space past the "=" and type in the number you use to dial your ISP.
It looked like this before 
; Phone =
you want it to look like this 
Phone = 5551212
One space on either side of "=", no spaces or dashes in the phone number.
(EDIT: I tried "*70,5551212" at a later date and that also worked.  *70 turns off call-waiting.  So wvdial can handle some variations) 
Follow the same rules as above to edit the Password line and the Username line.  Your ISP may want the domain as part of the username or they may not.  In other words it may be "linuxuser@isp.com" or it may just be "linuxuser".

Go to File>Save, or hit the Ctrl+S keys, to save the file.  You might want to close the terminal, open it, type ```
sudo gedit /etc/wvdial.conf
``` again, and make sure you did it right.

If your ISP cooperates with Linux, and if your modem is compatible with Linux, and if the modem was identified by wvdial, you should only have to open a terminal and type 
```
sudo wvdial
``` and wvdial will leap into action.  I got a quick log of what was happening, then when it indicated it was connected I went to Firefox and was online.  Whoo-hoo.
Don't close the terminal session that you used to dial!  Just bring it up when you want to disconnect, and type "Ctrl+C".  wvdial will close the connection.

More news on gnome-ppp.  Once I saw wvdial work, I opened gnome-ppp, checked the settings, entered my username/password/phone # and hit "Connect".  The first couple of times gnome-ppp stopped at "entering password".  I clicked the "Log" button.  It had stalled at a line that said "enter password" or something like that.  I closed gnome-ppp and tried again.  This time it said "Could not find modem".  I tried again and it dialed.  Tried again and it failed.  Tried again and it dialed.  I downloaded the Feisty gnome-ppp (remember in the first post I'd downloaded the Dapper version) to a thumb drive on my Windows PC.  Plugged the thumb drive into the Ubuntu PC and double-clicked on the file.  The Feisty package was numbered slightly differently than the Dapper package, but the Package Installer said they were the same.  I then tried 3X in a row to dial and never got a failed connect, so I'd suggest installing the appropriate gnome-ppp for your version of Ubuntu.

Good luck to all

---

### Post by kcamerud on 2007-07-07
Thanks.  I'm running 7.04 (it came as the backup OS  with my new e1505 and I was forced to reinstall after a password problem (I think 7.10 was preinstalled)) but I tried all your suggestions anyway.  No success yet.

---

### Post by _duncan_ on 2007-07-08
I prefer pppconfig instead of wvdial for fresh ubuntu installs for the following reasons:

1. No need to mess with /etc/resolv.conf file. This will be taken care of automatically by the setup program.

2. No editing of configuration files. The setup program will prompt the user for various info like phone number to dial, max connect speed, tone or pulse dialing, ISP user name, password, etc. and write these into a configuration file.

3. Just like wvdial, pppconfig comes with the default install, so there's no need to download anything from the repository.

4. User can close the terminal window after connecting using the pon command without breaking the connection. Disconnection can be done by opening a new terminal window later on and typing poff. With wvdial, closing the terminal window will result in disconnection.

So my usual process after installiing Ubuntu is to use pppconfig to achieve initial internet connection, update the package list, then install gnome-ppp from the ubuntu repo to have a GUI dialer.

Since the /etc/resolv.conf problem is already taken care of by pppconfig, it should be quite easy to get gnome-ppp working subsequently. Also, the user don't have to worry about which gnome-ppp versions to use since the package manager will match it to the ubuntu version installed.

Essentially, setting up dial-up internet connectivity with GUI dialer after a fresh install boils down to:

```
sudo pppconfig
pon
sudo aptitude update
sudo aptitude install gnome-ppp
poff
```

The code above assumes there is already a working modem in place. Users with winmodems will need to install the appropriate drivers and daemons before this.

---

### Post by Bartender on 2007-07-08
Duncan -
Thanks very much for the pppconfig guide!  That's exactly the sort of input I was hoping for.

I thought that gnome-ppp was a front-end for wvdial, so now I'm confused as to how pppconfig and gnome-ppp cooperate.  Does setting up pppconfig establish files in the right places so that gnome-ppp can use them?   I have a vague idea of how the various dial-up files interact, and most of that is probly wrong.

I'll have to try your method.  What if I've already done as described above (/etc.resolv, wvdial, gnome-ppp) and it worked?  Should I leave well enough alone?  Could configuring pppconfig mess with the existing dial-up files somehow?

---

### Post by _duncan_ on 2007-07-08
> Does setting up pppconfig establish files in the right places so that gnome-ppp can use them?

Not exactly. pppconfig solves the problem of /etc/resolv.conf, but they keep separate configuration files. So you still have to set up gnome-ppp after installation.

> I'll have to try your method. What if I've already done as described above (/etc.resolv, wvdial, gnome-ppp) and it worked? Should I leave well enough alone? Could configuring pppconfig mess with the existing dial-up files somehow?

I don't think so. I had pppconfig, wvdial, gnome-ppp and KPPP all working before with Edgy 6.10. But the true value of using pppconfig instead of wvdial is for fresh installs since it saves the user a lot of tinkering around with configuration files. After all, once gnome-ppp is set up properly, you probably won't be using these terminal-based dialers anyway.

---

### Post by Bartender on 2007-07-19
More notes on dial-up.

**Restart the PC before trying to use gnome-ppp or KPPP**  

Sorry if this is starting to sound like a diary instead of a guide, but I keep learning stuff too.  Yesterday I changed gnome-ppp in order to try dialing out at someone else's house.  Kept getting errors until I shut the machine off and restarted.  Then gnome-ppp dialed flawlessly.  So, restart the PC after first configuring, or editing, gnome-ppp.  Same goes for KPPP.

**Change pap-secrets and chap-secrets permissions**

Although wvdial and gnome-ppp seemed to be working on the test PC described above, I was getting two error messages in the logs, described in post #1 of this thread.
[http://ubuntuforums.org/showthread.php?t=376707&highlight=chmod+777+pap](http://ubuntuforums.org/showthread.php?t=376707&highlight=chmod+777+pap)

I followed the directions in post #2

First did this for pap, then again for chap with this code
```
sudo chmod 777 /etc/ppp/chap-secrets
```
and the error messages quit.

I have not entered the commands to change the permissions back to 644.  Will the error messages come back if I do?  Don't know, but I'm under the impression that it will work even if the messages about pap and chap being flaky re-surface.

---

### Post by Bartender on 2007-08-21
For those of you who are absolutely new to dial-up, I want to add some general thoughts.  Way I see it, there are three distinct hurdles to Linux dial-up.

#1 - Winmodems.  Just about every modem on the market nowadays is a winmodem.  A winmodem is a stripped-down device that passes some of the processing chores on to the CPU.  It can't do that without being able to talk to the CPU, and it can't talk to the CPU without drivers that allow it to use the operating system.  Since the whole world is on Windows, these cheap modems come with Windows-based drivers.
So, cheap modem + Windows = "winmodem".
If the modem manufacturers wrote Linux drivers this problem would go away.  I'm not sure if they could just write one set of drivers or if the myriad choices of Linux OS'es works against us in this matter.
You will see many threads referring to "scanmodem" and "linmodems" and etc.  These threads are all about people trying to make winmodems work under Linux.  It can and has been done, but every time I try to follow one of these threads my brain starts to melt.  I scrounged around for some used serial modems and these seem to work pretty well.  Serial modems are almost always full hardware modems that do all of the processing themselves.  Because of that, the "winmodem" problems go away.
Iif you have a new computer with no serial port there are a couple of options.  Find a serial/USB adapter cable (I can't guarantee that any cable will work; this does not appear to be a trouble-free solution) or find a USB external modem that works.  Be very careful if you go down that road.  Most USB externals don't work with Linux.  Some do.  I've been building a list, gleaned from forum success stories.  The Zoom 2985 and the Best Data 56USBSL have been reported to work.  Take that with a grain of salt :)

#2 - Linux dialer software.  Actually, it's unfamiliarity with Linux dialer software that creates the hurdle.  wvdial and ppp-config work well enuf for most of us, but until you figure out how they work it seems very hard.  
The previous posts within this thread only address Hurdle #2.

#3 - ISP's.  Most ISP's will work just fine with Linux.  If you call them and ask about "Linux support" they'll say "No" but that doesn't mean it won't work.  It just means they don't understand Linux themselves and don't see any benefit in getting up to speed on it.
Some ISP's require that you install proprietary software, and those are the ones that are most likely to   give you trouble.  I can tell you from personal experience that Juno is a pain.  It either doesn't work at all, or the connection crawls until they boot me off.  I was sure that PeoplePC was another one, but just read a thread recently that indicated success, so not sure about that now.

I hope this helps some folks to at least get a picture in their minds of how the dial-up problems break down.  At first it just seems like one big mess.  Try to dissect your situation into the 3 categories described above and see if that helps to make headway.

---

### Post by kcamerud on 2007-09-03
[http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=LIN4&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=LIN4&hidlang=en)

This is the link that dell support gave me though I am no back on broadband so I don't know if it works.

---

### Post by kcamerud on 2007-09-03
[http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=LIN4&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=LIN4&hidlang=en)

Sorry, the whole address didn't copy the first time.

---

### Post by Bartender on 2007-10-17
More dial-up notes.  For those who have an external serial modem and a newer PC with no serial port, try the Sabrent SBT-USC1M cable.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M)

Tried this on a desktop with Ubuntu 7.04 - GnomePPP detected the modem at /dev/ttyACMO

---

### Post by _duncan_ on 2007-10-26
Just installed Gutsy 7.10 on a separate partition, so now my test computer is a multi-boot of Feisty 7.04, Gutsy 7.10, openSUSE 10.3 and Fedora 7. Here are my initial findings on dial-up in Gutsy:

1. pppconfig still works like a charm.

2. the GUI dialer gnome-ppp seems a bit flaky. It can dial out and connect to my ISP, but the UI is stuck at the message "Connecting". Unless I click on the "Log" button, I wouldn't know if I'm really connected or not. Can browse and check email using it though so it's not a complete failure. On the other hand, it defeats the purpose of using a GUI dialer. :(

3. I did not try wvdial, but since gnome-ppp uses it at the back-end, it's reasonable to assume it can be made to work via CLI.

4. Will try KPPP after I finished configuring the system to my liking (vmware, java, flash, firefox plugins, etc). Not looking forward to downloading all those KDE library packages that KPPP requires though.

Hope this helps people contemplating on upgrading to Gutsy.


PS. KPPP works pretty well on my default Gutsy install with gnome desktop. It's a sizable download due to the large number of dependencies (a little less than 30 MB) but worth it IMO.

---

### Post by Bartender on 2007-11-01
30MB of data to get KPPP working under GNOME?
Wow
Duncan, you must believe that KPPP is superior to GNOME-PPP?  That's a lot of dependencies just to get KPPP going...

---

### Post by _duncan_ on 2007-11-01
> Duncan, you must believe that KPPP is superior to GNOME-PPP? That's a lot of dependencies just to get KPPP going...

At least for gutsy, it is definitely better than gnome-ppp. But to put things in perspective, I downloaded Ubuntu gutsy using dial-up (about 695 MB), so what's another 30 MB. :)

I understand where you're coming from though. I remember from an earlier conversation that your ISP cuts you off after 10-15 minutes. So downloading the required packages using synaptic package manager may be difficult

---

### Post by gonnoc on 2007-11-06
Thanks for this thread - very useful. But its the old catch 22. Need to get here so I can find a way to get here

Anyway after stumbling across some different connection methods came across these two excellent links which would have helped  - Ive suggested the info go into the distribution documentation

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)
and 
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Bartender on 2007-11-11
New info regarding packages -

BTW, my old test PC is now running Gutsy.  I don't know if that has a bearing on what I experienced or not.

Tried downloading KPPP, but it did not download as one usable package.  Dependencies were left behind.  I thought that was the whole concept behind the "packages" website  :confused:

Some packages will download with all dependencies, others won't.  And I don't know if this is something that gets fine-tuned with time?  A few months back I'm sure I downloaded the entire kde-desktop for Ubuntu 7.04 and it was ready to go - all dependencies in one download.

Gnome-PPP still works as a package if you already have Ubuntu installed.

---

### Post by _duncan_ on 2007-11-12
> Tried downloading KPPP, but it did not download as one usable package. Dependencies were left behind. I thought that was the whole concept behind the "packages" website.

the ubuntu "packages" website is for users to download individual packages. It lists dependencies but does not automatically download everything. The best way to download a package and all its dependencies is to use a package manager (e.g. Synaptic, apt-get, aptitude, etc.).

> Gnome-PPP still works as a package if you already have Ubuntu installed.

you mean, it doesn't freeze at "connecting" and refuse to iconify on the system tray? Weird, I've seen a lot of users complaining about it on this forum. Maybe I'll give it another shot.

---

### Post by Bartender on 2007-11-12
Hi, duncan -
All I meant was that if you have Ubuntu 7.10 and need to download gnome-ppp, the Gutsy gnome-ppp package does work.  You can download the package and it will install.
 
As far as how well or poorly it works once you've got it on the PC, I can't say.  Sounds like there are problems.  Since gnome-ppp has worked well enuf in the past, it might be one of those deals where it works just fine under 7.10 on some PC's and not on others?

---

### Post by _duncan_ on 2007-11-15
A little off-topic, but the following are useful tidbits I feel a dial-up user should know about ubuntu:

1. The synaptic package manager also acts as a download manager for unfinished / interrupted downloads. For example, if a user tries to install a package with 10 dependent packages, and for some reason the installation got interrupted while downloading the 3rd package, synaptic will start downloading from where it left off if the user tries to install the same package again.

2. The ubuntu package managers (synaptic, apt-get and aptitude) stores all downloaded packages into the folder /var/cache/apt/archives. This allows users to "stow away" these downloaded packages into another medium (another partition on the hard drive, burn to CD, thumb drive, etc.) and "reuse" these packages on another installation without having to download them all over again.

---

### Post by Bartender on 2007-11-15
duncan, it all helps and I appreciate it

I went into Synaptic, clicked on Settings, went into Sources>Third-Party Sources, and clicked on "Add CD-ROM".  Was prompted to drop in a CD, so I tossed in a freshly burned Kubuntu CD and it appeared to be added to the list of sources.

But when I went back to Synaptic and asked it to Search for KPPP it found nothing.  Then I asked it to search for the kubuntu-desktop and again got nothing.  It kept saying I had to Relaod but without an internet connection it was unable to do so.  I woulda thought it'd be able to recognize the CD without having to go online.  Don't know if I'm making some basic mistake?  Some of us dial-up users have access to broadband away from home, and it would be a handy trick to be able to add packages from a Kubuntu CD to an Ubuntu install or vice versa.

---

### Post by _duncan_ on 2007-11-16
It's possible to reload without internet connection, you just have to deselect those sources that require downloading from the internet. If I remember correctly, it's under Settings >> Repositories.

On the first tab, there is a section called "Downloadable from the internet". Make sure everything in there is UNCHECKED. Then try reloading again.

---

### Post by Bartender on 2007-11-16
OK, will do.  
I also read some stuff on the internet that maybe sorta indicated that an alternate install CD works better than a LiveCD as a 3rd party source?  I'm not even sure that's what I was reading.  :-?
Anyway, I downloaded Kubuntu alternate .iso while I had access to broadband and will try that too.

---

### Post by Bartender on 2007-11-17
Well, that didn't work.  It's probly more accurate to say that I couldn't figure it out...

I've got an Ubuntu 7.10 LiveCD, Kubuntu 7.10 alt install CD, and a Xubuntu 7.10 alt install CD.  Installed every one of them (one after the other, not all at once), then went into Synaptic and got them to recognize 3rd party CD's, then was unable every time to get Synaptic to use the CD.  In every OS Synaptic would give me messages about having to "Reload" and needing an internet connection, etc.  Felt like I was chasing my tail.  Tried unchecking all sources except the CD.  Didn't work.

Tried to get each OS to recognize the desktop packages (in Kubuntu, I asked Synaptic to look for "ubuntu-desktop", etc. etc.) but was unsuccessful.
In Ubuntu, tried to get Synaptic to see "KPPP" on the Kubuntu CD but no go.
In Xubuntu, tried the same things.  Spent some time in "Add/Remove" and was told that Amarok and KPPP wouldn't run on my system (i-386).  Both of these programs do run on this PC.  I saw them run within the last 24 hours.  :-?

Anyway

Kubuntu's KPPP dialer makes for the "easiest" way to get online with a fresh install.  I opened the terminal and typed 
```
sudo touch /etc/resolv.conf
``` 
then opened KPPP, set up the info, and got online (with Juno!) for a while.  Even reloaded the package information.  That took over an hour and one reconnect.  Pathetic.

Ubuntu really isn't much harder.  Either type in the same command as above, then set up wvdial, and/or follow duncan's directions for pppconfig.  I went with pppconfig and it worked fine.  Downloaded GNOME-PPP and that worked too.  

Didn't try to dial from Xubuntu but I'm sure pppconfig woulda worked.

It's a harsh world for dial-up users.  A raw install of Kub, Ub, or Xub is a diamond in the rough.  Each OS is missing things that you'll want.  Without a few hours in front of a broadband connection you're missing out.  

Kubuntu may be the most complete package for your basic needs, but it doesn't have GIMP or even Firefox!
I've never had any luck connecting to the Internet with Konqueror.

Ubuntu doesn't come with a good CD burn utility.  It needs Braseros or the KDE burner.

Xubuntu of course has the least programs and what's there is less developed.  The default media player, Totem, would only play the first track of a music CD.  I was probly doing something wrong.  It has Braseros as the burn utility, which I'm told is better than Ubuntu's default!  The latest Xub has OpenOffice Writer, which is much handier for communicating with Word users than Abi.

Somebody smarter than me could probly use all three CD's to concoct a decent installation.

---

### Post by _duncan_ on 2007-11-29
A fellow ubuntu user (gborzi) developed a lightweight system tray applet that works well with pon / poff. It assumes pppconfig was properly set up and uses its settings to connect and monitor dial-up ppp connections. Anyway, here's the link to the discussion:

[http://ubuntuforums.org/showthread.php?t=534709]("http://ubuntuforums.org/showthread.php?t=534709")

Been testing it past couple of days and seems stable enough for gutsy. Can be considered as a no-frills alternative to gnome-ppp and KPPP.  It's biggest selling point is size (about 12 KB download).

---

### Post by Bartender on 2007-11-30
duncan, thank you -
Again, a most useful find.  Will have to try that out.

**For dial-up users who have a thumb drive and access to broadband away from home**

Last night I tried again to get Ubuntu 7.10 to recognize and use a Kubuntu 7.10 alt install CD for packages.  This time I went into "Add/Remove Programs" (under the Applications tab) instead of opening Synaptic Package Manager.
In "Add/Remove" there's a box in the lower left corner for "Preferences".  This takes you to the same window as you would see in Synaptic, where you can get to the "3rd Party Resources".  I went thru it again.  Since unchecking all of the online repositories hadn't worked for me last time I did not uncheck them this time.  Just ignored the message that said something about "Unable to finish without a connection to the Internet" when it tried to Reload.
When finished, it added another line below the first one, showing that the Kubuntu CD was accepted as a 3rd Party Resource.  This didn't seem like progress, because I'd already gotten a Kubuntu CD into the 3rd Party list, but was unable to add anything from the "Add/Remove Programs" list.
However, this time when I clicked on KPPP in the "Add/Remove Programs" list, the CD spun up and the Package Manager did its thing.  Whoohoo.
I added Amarok and K3b.

Then I got out of Add/Remove and went into Synaptic.  "kubuntu-desktop" was present in the list of available programs.  It hadn't been before.  I installed that too. 

I don't know for sure what I did wrong the first time(s)... for anyone who wants to try this: 
(1) Use an alt-install CD instead of the LiveCD
(2) Go thru "Add/Remove" instead of Synaptic Package Manager when trying to get the CD recognized as a 3rd Party Resource.

Of course, this is only useful to those of you who have access to broadband away from home and can copy an entire alt-install download to a thumb drive.

---

### Post by Bartender on 2007-12-22
Supposedly Gnome-ppp has been patched?  In this thread 
[http://ubuntuforums.org/showthread.php?t=642287](http://ubuntuforums.org/showthread.php?t=642287)

Don't know what's involved in downloading/installing that .deb package...

Turns out it was easy peasy and Gnome-ppp now works in Gutsy just like it did in Feisty.

---

### Post by _duncan_ on 2008-04-29
Posting this from my new install of Hardy Heron 8.04. Here are some comments about dial-up:

1. The old reliable pppconfig works.

2. gnome-ppp (from the Ubuntu repo) works. This is a definite improvement over Gutsy 7.10. Bumped into some file permission issues for /dev/ttySL0, but this is easily solved by changing the permission. Not sure if this is an issue with gnome-ppp (wvdial), or with the way the modem driver was installed.

3. wvdial also works. Initially had the same problems as gnome-ppp (file permission), but was able to get it to work after the fix in 2.

So if you are on dial-up and having doubts about getting dial-up working in Hardy, go ahead and take the plunge. It's well worth it. As an added bonus, Firefox 3 that came with Hardy is a lot better than Firefox 2 of Gutsy.

---

### Post by Bartender on 2008-05-03
Hey, duncan, good to hear from you.  I wiped my install of 7.10 and installed 8.04 a few days ago.  Lots of nice little improvements here and there and no glitches of any import.
As you mention, pppconfig works just as well as before. 
I used that to dial frys.com (finally dumped Juno and got an ISP that works with Linux) and downloaded gnome-ppp from Synaptic.  Gnome-ppp worked like a champ for me, auto-detecting the USRobotics external modem on a serial-to-USB adapter at /dev/ttyACM0, something that I believe the previous gnome-ppp was unable to do.
I didn't have any permission problems, thankfully.

I did have one odd phenomena - Firefox was in off-line mode.  I've been online several times since upgrading to 8.04 via wireless and ethernet, so I don't know what the deal was there.  I found the box to uncheck under "File">"Work offline".  A minor glitch in FF3?

Dial-up still sucks but it feels a little faster than before.  Hard to say for sure...

---

### Post by _duncan_ on 2008-05-04
I'm back to using pppconfig and kppp. gnome-ppp only works for me if it's the first time to connect after booting. The file permission / resource busy error shows up the next time I invoke gnome-ppp and try to connect. Consequently, I have to reboot the system to use gnome-ppp again. Same problem with wvdial.

In contrast, pppconfig and kppp let me connect / disconnect as much as I want without requiring a reboot. Seems to me the problem is with wvdial. For some reason it doesn't free up its hold on the modem port before closing.

> I did have one odd phenomena - Firefox was in off-line mode. I've been online several times since upgrading to 8.04 via wireless and ethernet, so I don't know what the deal was there. I found the box to uncheck under "File">"Work offline". A minor glitch in FF3?

I don't think it's a firefox issue but an ubuntu networking issue. Evolution also suffers the same problem. These apps seem to be tied up to the networking icon on the notification area. If the icon is disabled, or is not connected, then firefox and evolution will start in offline-mode.

Your experience with wireless confirms my hunch. While on wireless, the network icon tells ubuntu you're connected, so firefox / evolution start in on-line mode. The icon isn't aware of the dial-up connection since we're not using "System > Networking" to connect, so it stays off-line.

I was able to override this before in Feisty, but had no luck with Gutsy, and now Hardy. Besides, I've gotten used to unchecking "File > Work Offline" everytime I start up Firefox, so it's no longer an issue with me.

> Dial-up still sucks but it feels a little faster than before. Hard to say for sure... 

What connection speed are you getting? I'm averaging 46-48 kbps in ubuntu (since breezy 5.10) compared to around 44 kbps in WinXP on the same machine. Connection is also very stable. Could it be your phone line?

---

### Post by Bartender on 2008-05-04
Yeah, we've definitely got problems with the copper between here and town.  Qwest has been lazy.  There are orange socks pulled over several of their little green junction boxes along our rural road, indicating problems inside.  Some of the socks have been out there in the weather for so long they're fading and falling apart.
I keep bugging Qwest about DSL but it's probably a lost cause...

I used to get about 28kbps with an Intel 536 internal modem on our Windows PC.    Because of my Linux experimentations, all Windows and Linux PC's now use US Robotics externals, which are capable of coaxing 37 to 40 kbps from the phone line.

---

### Post by _duncan_ on 2008-05-04
37 to 40 kbps isn't bad as long as connection is stable (no frequent disconnection).

Is wireless broadband not an option in your area? My understanding is this technology is dependent on line-of-sight between your location and the nearest cellular phone site (tower). So theoretically if cell phone signal is strong in your place, then wireless broadband ought to be possible.

I'll be switching to broadband soon. Just debating between wireless or DSL. Hardy is probably my last 700 MB .iso file download using dial-up! :)

BTW, did wireless work out-of-the box for you in Ubuntu? From what I can see on this forum, getting wireless to work can be just as troublesome as dial-up. That's why I'm leaning towards wired broadband instead of wireless.

P.S. Is that a new laptop you're brandishing in your sig? I recall seeing Pentium III before. :)

---

### Post by Bartender on 2008-05-05
We're 3 miles out of town on a rural road.  Whenever people visit I ask them to try their cell phones.  It's hit-and-miss.  No cable, no DSL; it's satellite or dial-up and satellite's too damn expensive.
Yes, it is a new laptop.  Got it a few months ago but forgot to update sig.  I bought it specifically because I was going nowhere with Linux and dial-up at home.  Broadband is available elsewhere so I had to get mobile. Access to broadband, even if it's not at home, has made a big difference!
After reading many threads on problems with laptops it appeared to me that buying a Centrino laptop might tilt the odds in my favor.  The Acer has Intel's newest wireless card (4965)and it works like a champ.  I think it detects and connects to wireless networks better than vista and with less fussing around.  Wireless has worked on several public hotspots and it worked just fine on my Dad's wireless network (he's got comcast cable and a Netgear wireless router).  The only thing that threw me was that Ubuntu wanted the WEP passphrase, not the long alphanumeric keycode.  I had no experience with encrypted networks and it took me a coupla days to figure that out.
I don't know if that's basically the same thing as these wireless services that run from cell towers, as you describe.  Does proprietary software create problems??

---

### Post by _duncan_ on 2008-05-05
> Does proprietary software create problems??
No, I don't think so. These services are usually OS-independent.

> After reading many threads on problems with laptops it appeared to me that buying a Centrino laptop might tilt the odds in my favor. The Acer has Intel's newest wireless card (4965)and it works like a champ. I think it detects and connects to wireless networks better than vista and with less fussing around.

Sounds like you made the right choice. Most of the horror stories I've seen involving wireless has to do with compiling drivers for wireless cards. Stuff like ndiswrapper, etc. Pretty much like the mess one has to go through with winmodems.


BTW, the wireless service I mentioned has an effective range of 1.5 miles from the nearest cell tower, so I doubt there'll be a company offering such service in your area in the immediate future.

---

### Post by Bartender on 2008-05-05
Yeah, it's easy to get confused with all the badging permutations.  Lots of lappies have the sticker noting Intel dual core Pentiums or Core 2 Duo's but if they don't specifically say "Centrino" it's probably a Broadcom card.
Who knows what's inside the AMD's.  I wasn't going to take the chance.

---

### Post by _duncan_ on 2008-05-06
I managed to fix the problem with Firefox and evolution starting in off-line mode. The fix involves disabling the network manager at start-up. This is done by creating 2 files with only the word "exit" in them:

```
sudo gedit /etc/default/NetworkManager
sudo gedit /etc/default/NetworkManagerDispatcher
```

After reboot, the pesky network icon no longer appears on the notification area, and Firefox / evolution now always starts in on-line mode.

-----------

Unfortunately this fix may not work for users who require the netowrk manager to establish internet connection (e.g. wireless, dial-up using System > Networking, etc.). They can still use this fix, but will have to delete those 2 files created and reboot to make use of the netowrk manager.

---

### Post by Diskdoc on 2008-06-09
Nice one about how to disable the network-applet! Before finding your notes in this thread I read [Bug #191889]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889") and decided to remove Network-applet completely, replacing it with [Wicd]("http://wicd.sourceforge.net/") and Gnome-PPP.

Gnome-PPP works wonderfully using the following .wvdial.conf:

> [Dialer Defaults]
Modem = /dev/ttyACM0
ISDN = off
Modem Type = USB Modem
Baud = 115200
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet.saunalahti","0.0.0.0",0,0
Init4 = 
Init5 = 
Init6 = 
Init7 = 
Init8 = 
Init9 = 
Phone = *99***1#
Phone1 = 
Phone2 = 
Phone3 = 
Phone4 = 
Dial Prefix = 
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = empty
Username = empty
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = on
;Minimize = off
;Dock = on
;Do NOT edit this file by hand!


Pidgin and Firefox now work without a hitch but I have yet to test connecting by ethernet or wireless.

---

