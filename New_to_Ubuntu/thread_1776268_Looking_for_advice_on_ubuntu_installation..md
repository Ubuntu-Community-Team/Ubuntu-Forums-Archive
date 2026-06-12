---
title: "Looking for advice on ubuntu installation."
date: 2011-06-05
forum: New to Ubuntu
---

### Post by organizedkaos on 2011-06-05
Hello everyone.
 
I am currently using ubuntu 10 (I believe) in virtual box on my vista box. The reason for this is because I compile android sources and kernels as a hobby of mine.
 
I want to completely install ubuntu as my primary operating system but there are things that I still use in windows and I am not sure if ubuntu can sufficiently replace everything I do in windows. I would like it to.
 
My uses on my vista box are as follows:
 
- media server: I currently stream music and movies to my ps3 and vista laptop
- music editing: I currently use fruity loops studio for music creation, goldwave for audio editing and conversion, mp3tag for media tag editing, and almost all of my music files are wma
- movies: I sometimes copy dvd movies either onto dvds or convert them to wmv/avi/divx etc. and store them on my hard drive for streaming
- school: I am currently taking college courses online and my courses will only work with internet explorer. Firefox isn't even supported, go figure. I also rely heavily on msoffice for my assignments and I had to pay for the software. 
- internet: I browse the net to all kinds of sites and forums. I am assuming something like google chrome or firefox will be sufficient for that task but I don't know if I need to do anything extra to insure I have an internet connection.
- security: I currently use windows firewall and microsoft security essentials. I have had luck with this setup whereas my computer has not had any random shutdowns/reboots, blue error screens etc. I just don't know what kind of security I need to look into for ubuntu as far as viruses, attacks, etc.
- remote access: I currently have my vista box setup to allow remote desktop connection when I am away from home. Does ubuntu/linux offer something like this?
 
I apologize for a such a long post and I am sure I am forgetting something. I just want to see if I can truly replace my windows environment with linux/ubuntu and keep the functionality of my windows environment. I no longer want to use virtual machines or if I have to, I want to keep the use of virtual machines to a minimum.
 
Is this possible for me to do? Am I hoping for too much? Thank you to any solid response any one can give in helping me find the right path to completely migrate over to linux/ubuntu.

---

### Post by ikt on 2011-06-05
Just going to respond to the ones I can:

> **organizedkaos said:**
> 
- school: I am currently taking college courses online and my courses will only work with internet explorer. Firefox isn't even supported, go figure. I also rely heavily on msoffice for my assignments and I had to pay for the software. 

Are the assignments you're doing completely incompatible with libreoffice? Most assignments I do are pretty basic word documents. Also I would send an email to your college about compatibility with firefox, not being compatible with browsers beyond IE is shocking, I can't believe it's still happening in 2011.


> **organizedkaos said:**
> 
- internet: I browse the net to all kinds of sites and forums. I am assuming something like google chrome or firefox will be sufficient for that task but I don't know if I need to do anything extra to insure I have an internet connection.

How do you connect to the internet?

> **organizedkaos said:**
> 
- security: I currently use windows firewall and microsoft security essentials. I have had luck with this setup whereas my computer has not had any random shutdowns/reboots, blue error screens etc. I just don't know what kind of security I need to look into for ubuntu as far as viruses, attacks, etc.

Ubuntu has no services listening by default, so a firewall is kind of useless, it does have a few you can install though, there's also very limited malware available for ubuntu, since you install a majority of your software from the ubuntu software centre, getting malware is fairly difficult. It's one of the major insecurities in using windows, you're expected to get your software from random binaries on the internet.


> **organizedkaos said:**
> 
- remote access: I currently have my vista box setup to allow remote desktop connection when I am away from home. Does ubuntu/linux offer something like this?

Definitely, ssh/rdp/vnc are all there.

---

### Post by organizedkaos on 2011-06-05
> **ikt said:**
>  
Are the assignments you're doing completely incompatible with libreoffice? Most assignments I do are pretty basic word documents. Also I would send an email to your college about compatibility with firefox, not being compatible with browsers beyond IE is shocking, I can't believe it's still happening in 2011.

 
I'm not sure with libreoffice. Alot of my assignments actually use a handful of the office apps such as powerpoint, excel, word, and access. I also use ms projects (I think that's what it's called) for my project management courses. I have sent a handful of emails about the browser support issue with no response so that kind of sucks right there.
 
> **ikt said:**
>  
How do you connect to the internet? 

 
I connect using a netgear wireless usb dongle and I have an intel onboard network card. My question was mainly do I have to do anything extra to insure my onboard network card as well as the wireless dongle will work right away. Such as when windows installs drivers and such for those devices, does ubuntu have the same ability?
 
This is a fairly old computer that serves its purpose in the uses I stated in my first post. I am wanting to migrate because my virtualbox ubuntu environment is losing space and since I spend most time in there anyways I figured it would just be better if I get rid of windows and stick to ubuntu. However these are the issues I am currently faced with the decision to migrate.
 
Thank you for you answers so far. I really appreciate it.

---

### Post by sidzen on 2011-06-05
" - school: I am currently taking college courses online and my courses will only work with internet explorer. Firefox isn't even supported, go figure. I also rely heavily on msoffice for my assignments and I had to pay for the software."
[I]
This denotes dual-boot would be best, for now, IMHO.[/I]

See -- [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

[EasyBCD]("http://neosmart.net/dl.php?id=1") makes things even easier.

---

### Post by organizedkaos on 2011-06-05
sidzen,
 
Thank you for your response. I have tried the dual-boot method last year and while it may seem like the most viable solution it is not, IMO, for me.
 
I am a heavy multitasker and being able to compile android sources and kernels in the background while I do my school work is a really great time saver for me.
 
I do this currently with virtualbox but as you can imagine that taxes my system a bit more than if I were using one single operating system.
 
I am open to using whatever software is linux compatible to replace its windows counterparts, I just have had no luck finding them especially when I read things such as "you would need to install these libraries" or "you can compile it for your build" or things of that nature. 
 
I know I may sound a bit too "silly" and I am trying not to be. 
 
I believe WINE is some sort of emulator and if that is the case I can see myself using that to run internet explorer in ubuntu...if that will work.
 
Solutions like that I am open to as long as it gets me to my goal of replacing windows while retaining my functionality needs.
 
Thank you for your response.

---

### Post by ikt on 2011-06-05
to me it just looks like one of those situations where you're locked in, it's the same for me with world of warcraft, it's just not the same using wine and I pretty much have to use windows, funnily enough this is what microsoft rely on for a majority of their income, the whole you're locked in and can't get away from us software design :/

---

### Post by organizedkaos on 2011-06-05
> **ikt said:**
> to me it just looks like one of those situations where you're locked in, it's the same for me with world of warcraft, it's just not the same using wine and I pretty much have to use windows, funnily enough this is what microsoft rely on for a majority of their income, the whole you're locked in and can't get away from us software design :/
 
Yes, this is what it feels like most of the time.  Which is another reason why I am trying to make the switch to ubuntu.
 
I will keep doing my research though and hopefully others can lend some advice on how to completely replace my windows installation.
 
Thank you.

---

### Post by sidzen on 2011-06-08
> **organizedkaos said:**
> sidzen,
. . . 
I am open to using whatever software is linux compatible to replace its windows counterparts, I just have had no luck finding them especially when I read things such as "you would need to install these libraries" or "you can compile it for your build" or things of that nature. 
 
I know I may sound a bit too "silly" and I am trying not to be. 
 . . . 
Thank you for your response.

See the [Linux Alternative Project]("http://www.linuxalt.com/")
Also, techiMoe's exposition on Jason Lambert's 
[[SIZE=3]Installing Software in GNU/Linux[/SIZE]]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html")
is very useful.

Looks like you're stuck with virtualbox for now -- but never stop learning how to become 
[Pane-Free]("http://www.pane-free-geek.org/")!

---

### Post by fabricator4 on 2011-06-08
> **organizedkaos said:**
> Yes, this is what it feels like most of the time.  Which is another reason why I am trying to make the switch to ubuntu.
 
I will keep doing my research though and hopefully others can lend some advice on how to completely replace my windows installation.
 
Thank you.

Why not switch it completely around? Run Native Ubuntu (I like to recommend 10.04 LTS, unless you need later hardware compatibility or like your OS experience to be "exciting") and run Windows in VirtualBox.  Since you're already comfortable with VB you might find doing it the other way around a good solution.  That way, you have the compatibility of a native Windows install but can easily and (probably) very quickly learn to migrate most of your applicatons to a real OS ;-)

The VB in the repostitory is the OSE (Open Source Edition) and does not have USB support.  You would need to get the PUEL (Personal Use Evaluatino License) from Oracle (USB 1.1) along with the extension pack (USB 2.0).  The installation is quite simple.

I wish I'd listened to recommendations for VB under Ubuntu a long time ago.

Chris.

---

### Post by Mark Phelps on 2011-06-09
My suggestion is that you rethink dual-boot -- but as a means of testing out the usability of the Linux Alternative to MS Windows.

In my own experience, Wine was a complete waste of time.  And, given that you need to use Window apps that do NOT work with Wine (i.e., MS Project), you would also be wasting your time considering it.

Realize, that the more you depend on the fine details of how MS apps work, the greater the learning curve will be switching over to ANY Linux distro, not just Ubuntu.  So, some things will work differently; other things just might not work at all.

A true dual-boot is really the best option for trying out Ubuntu to see just how much of your stuff you can continue to do well with Ubuntu and its apps.  This way, you can experiment with converting over to Linux, while at the same time, having the ability to fallback into the MS Windows world to get stuff done.

As to switching the Virtual setup -- IMHO, this really depends on WHICH of the two OS environments you need to use the most.  THAT one should be your Real environment; the other one (the one less used) should be your Virtual environment.

But ... these are all just my opinion.

---

### Post by organizedkaos on 2011-06-12
> **sidzen said:**
> See the [Linux Alternative Project]("http://www.linuxalt.com/")
Also, techiMoe's exposition on Jason Lambert's 
[[SIZE=3]Installing Software in GNU/Linux[/SIZE]]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html")
is very useful.
 
Looks like you're stuck with virtualbox for now -- but never stop learning how to become 
[Pane-Free]("http://www.pane-free-geek.org/")!
 
Links have been noted and are on my to-read list.  Thank you for the help on those.
 
> **fabricator4 said:**
> Why not switch it completely around? Run Native Ubuntu (I like to recommend 10.04 LTS, unless you need later hardware compatibility or like your OS experience to be "exciting") and run Windows in VirtualBox. Since you're already comfortable with VB you might find doing it the other way around a good solution. That way, you have the compatibility of a native Windows install but can easily and (probably) very quickly learn to migrate most of your applicatons to a real OS ;-)
 
The VB in the repostitory is the OSE (Open Source Edition) and does not have USB support. You would need to get the PUEL (Personal Use Evaluatino License) from Oracle (USB 1.1) along with the extension pack (USB 2.0). The installation is quite simple.
 
I wish I'd listened to recommendations for VB under Ubuntu a long time ago.
 
Chris.
 
I had played with that idea too and fortunately my vb does have usb support.  I know this because while my vista is my host and ubuntu is in vb I am able to connect my htc device to my ubuntu vb and it will mount the sdcard in my vb so I'm not worried about that.  Again, this is an idea I have considered, I just want to cover all bases before making a close to final decision.
 
> **Mark Phelps said:**
> My suggestion is that you rethink dual-boot -- but as a means of testing out the usability of the Linux Alternative to MS Windows.
 
In my own experience, Wine was a complete waste of time. And, given that you need to use Window apps that do NOT work with Wine (i.e., MS Project), you would also be wasting your time considering it.
 
Realize, that the more you depend on the fine details of how MS apps work, the greater the learning curve will be switching over to ANY Linux distro, not just Ubuntu. So, some things will work differently; other things just might not work at all.
 
A true dual-boot is really the best option for trying out Ubuntu to see just how much of your stuff you can continue to do well with Ubuntu and its apps. This way, you can experiment with converting over to Linux, while at the same time, having the ability to fallback into the MS Windows world to get stuff done.
 
As to switching the Virtual setup -- IMHO, this really depends on WHICH of the two OS environments you need to use the most. THAT one should be your Real environment; the other one (the one less used) should be your Virtual environment.
 
But ... these are all just my opinion.
 
Thank you for the advice on WINE.  I know now to just stay away from that.  While I am not downplaying the true dual boot method, for me it just adds time to wait on between booting one system over the other especially when switching.  At least with the vb option I can go between host and vm in the same session.  As for making the os I need the most the host, I really just want to make ubuntu my primary os all the time and only rely on windows for when it's needed.  Other than the microsoft products, the other things I depend on it for are media streaming, media creation and editing, and media compatibility.
 
I have actually started looking for a linux server option that will allow me to (like windows server, I know I'm sad) install a virtualization server.  If I can find that then I can be able to find the best of both worlds.
 
Thank you again for all your responses.  They help me get one step closer to breaking these "window panes".

---

### Post by organizedkaos on 2011-06-26
Ok, I am going to pull the trigger very very soon (within the next day or two) in making ubuntu my main os and just running windows in virtual box.
 
My last question is has anyone had any luck mounting ntfs drives as rw and not losing any data?
 
I need to be able to mount my existing ntfs drives until I can replace them with higher capacity drives.
 
Thanks again.

---

### Post by nzjethro on 2011-06-26
> My last question is has anyone had any luck mounting ntfs drives as rw and not losing any data?

I have three ntfs partitions mounted for read-write, and an external mounted too. No problems what so ever. With internal HDDs (i.e. other partitions) you can mount them when you install. Otherwise, most externals will automount, and at a stretch you can add them to fstab to ensure they automount.

---

### Post by dFlyer on 2011-06-26
Your ntfs should auto mount without a problem. I use ntfs for my external backup drives and have never lost any files as of yet and I've been using ubuntu since 2006 as my only os.

---

### Post by organizedkaos on 2011-06-27
Thanks for the responses guys.  It's good to know that my existing ntfs drives (which hold all my non os files) can be mounted in ubuntu without a hitch.  
 
I'm still sorting out the list of windows apps I need to keep and then I want to start the ubuntu installation either tonight or tomorrow.
 
Thanks once again everyone who responded here.

---

### Post by organizedkaos on 2011-06-28
Just want to report that I am now running my host on ubuntu 10.04.

Install went without a hitch after having some issues with ubuntu not seeing the hard drive I wanted to install to.  

Diskutility (not minding spelling right now) did the trick when I needed to add the mbr to my newly formatted and completely empty hard drive and Gparted worked well for making the necessary partitions for the install (primary partitions swap, /, /home).

Now I'm finding OpenOffice.org to be extremely versatile in opening all my previous ms office documents (spreadsheets, powerpoint, and word so far).  Even the description in synaptic says it's a near drop in replacement for ms office and so far it's looking I ***might*** not need to run "winblows" in a virtual machine.

The only thing I can't get to work are my music files which, because of using ms for so long, are encoded in wma9.

totem, vlc, mplayer, and banshee all have problems opening wma9.  Vlc says it needs "windows media audio 9 decoder" and mplayer/totem give me "internal data stream error".

I have installed the medibuntu repo and installed the gstreamer plugins and everything else I found that suggests how to get wma to play but no luck so far.  

So now as it stands ubuntu is doing very well at replacing my ms environment almost completely.  

The only two things I need to work out is wma playback (which I'm thinking I may have to re-convert them back to mp3) and file streaming to my ps3.  If I can figure these two things out, I don't think I will go back to ms anymore.

Thanks everyone for your help in this thread.

---

### Post by rewyllys on 2011-06-28
> **organizedkaos said:**
> Just want to report that I am now running my host on ubuntu 10.04.

Install went without a hitch after having some issues with ubuntu not seeing the hard drive I wanted to install to.  

Diskutility (not minding spelling right now) did the trick when I needed to add the mbr to my newly formatted and completely empty hard drive and Gparted worked well for making the necessary partitions for the install (primary partitions swap, /, /home).

Now I'm finding OpenOffice.org to be extremely versatile in opening all my previous ms office documents (spreadsheets, powerpoint, and word so far).  Even the description in synaptic says it's a near drop in replacement for ms office and so far it's looking I ***might*** not need to run "winblows" in a virtual machine.

The only thing I can't get to work are my music files which, because of using ms for so long, are encoded in wma9.

totem, vlc, mplayer, and banshee all have problems opening wma9.  Vlc says it needs "windows media audio 9 decoder" and mplayer/totem give me "internal data stream error".

I have installed the medibuntu repo and installed the gstreamer plugins and everything else I found that suggests how to get wma to play but no luck so far.  

So now as it stands ubuntu is doing very well at replacing my ms environment almost completely.  

The only two things I need to work out is wma playback (which I'm thinking I may have to re-convert them back to mp3) and file streaming to my ps3.  If I can figure these two things out, I don't think I will go back to ms anymore.

Thanks everyone for your help in this thread.
Congratulations, both on your goal and on making such good progress toward it!:)

I'd like to recommend that you adopt LibreOffice instead of OpenOffice.  LibreOffice already has taken some steps beyond OO in their respective latest versions, e.g., wrt to reading and writing ".docx" files.

Good luck with finding a solution to your wma9 problem; sorry I can't offer any help.

---

### Post by organizedkaos on 2011-06-28
@rewyllys

Don't sweat it.  Everything I got in this thread was very helpful. 

Thanks for the tip on libreoffice.  I noticed only one thing that OOo can't do with my old excel spreadsheet and that's run my vb macros that I set up on my sheets.

I was researching installing ms office in wine but I will look into libreoffice first.  

Many thanks again to all who lent a helpful response in this thread.

---

### Post by andrew.46 on 2011-06-29
> **organizedkaos said:**
> 
The only thing I can't get to work are my music files which, because of using ms for so long, are encoded in wma9.

totem, vlc, mplayer, and banshee all have problems opening wma9.  Vlc says it needs "windows media audio 9 decoder" and mplayer/totem give me "internal data stream error".

I have installed the medibuntu repo and installed the gstreamer plugins and everything else I found that suggests how to get wma to play but no luck so far. 

Seems a little odd as vlc and MPlayer should be able to play most wma9 files. Can you post one of the troublesome files somewhere?

---

### Post by organizedkaos on 2011-06-29
> **andrew.46 said:**
> Seems a little odd as vlc and MPlayer should be able to play most wma9 files. Can you post one of the troublesome files somewhere?

I'm not worried about it anymore.  I just went ahead and installed xp pro sp3 in virtualbox.  Libreoffice couldn't run my excel macros (I use my worksheets alot) and just to get the streaming up only took windows media player.  

Overall though I am actually spending more time in ubuntu (host) than xp (guest).  

I have only gone into xp just to set it up and make sure my excel sheets are still working.  

Everything is working great now.  Now I just need to finish setting up my android dev environment in ubuntu :(

---

### Post by Ozymandias_117 on 2011-06-29
You can stream to your ps3 with a program called "uShare" - I've personally only used it for streaming to a 360, but it worked great and it's supposed to work with the ps3 as well.

---

### Post by Nekrose483 on 2011-06-29
use IE4LINUX... my freshman year of college.. i took a math cource... the professor assigned the hormwork online...

it only worked with IE.... so i looked it up. IE4LINUX.. i think its called IE4LIN.. idk. check it out. or.. try wine... then open a terminal and type "winetricks"... something will pop up.. it should be on there. lol.. goodluck...


oh, and i also use FL studio to produce music.. i'm actually dual booting windows 7 just to do that.. but  i'm trying to look up differant programs... nekrose.decuir(at)gmail.com

contact me and i'll send some links your way. i dont have the links for the one i'm using right now.

---

### Post by organizedkaos on 2011-06-30
> **Ozymandias_117 said:**
> You can stream to your ps3 with a program called "uShare" - I've personally only used it for streaming to a 360, but it worked great and it's supposed to work with the ps3 as well.

Awesome, I'm going to check that out and see if it can handle my streaming straight from ubuntu.  Thanks for the tip.

EDIT:  From your tip I found mediatomb and installed that.  Works perfectly now.  Thanks again.

> **Nekrose483 said:**
> use IE4LINUX... my freshman year of college.. i took a math cource... the professor assigned the hormwork online...

it only worked with IE.... so i looked it up. IE4LINUX.. i think its called IE4LIN.. idk. check it out. or.. try wine... then open a terminal and type "winetricks"... something will pop up.. it should be on there. lol.. goodluck...


oh, and i also use FL studio to produce music.. i'm actually dual booting windows 7 just to do that.. but  i'm trying to look up differant programs... nekrose.decuir(at)gmail.com

contact me and i'll send some links your way. i dont have the links for the one i'm using right now.

XP Pro in virtualbox is doing a great job handling my windows needs right now and it's running fast so that's a plus.

I have already migrated my fl studio environment over to my 2 year old laptop since it doesn't leave the house anymore.  

Overall I think I have pretty much covered everything I needed to with the help from the responses in this thread.

I didn't even look for alternatives to my fl studio.  Once you get used to it it just makes music creation that much faster.  :)

---

