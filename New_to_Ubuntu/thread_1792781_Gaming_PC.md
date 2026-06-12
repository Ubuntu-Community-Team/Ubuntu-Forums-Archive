---
title: "Gaming PC"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by MerlinCoder on 2011-06-28
Hey everyone. 
 
I have a gaming PC. It's pretty powerful and  doesn't have a problem running anything on the market. I've been  struggling with Windows Vista for about a year now and have to devote so  much of my time to fixing viruses, removing spyware blah blah blah I'm  sure you get it and don't need me to repeat all the issues... 
 
Well,  it gives me such a headache with all the problems I get and I really do  want to make the switch to Ubuntu as I have used it before, but I can't  really justify losing all my games. 
 
Well, I was talking to a  friend today who mentioned that Ubuntu has a VM system, much like  windows 7. I don't really know much about this. Just imagine if I  completely wiped off windows and replaced it with Ubuntu and WINE and a  vista VM. When running the windows games, will it be at least 70~80% as  good as a fresh Vista install? Obviously I really can't imagine it ever  being 100% as good, and I'm not expecting that, but a little drop in  speed would be nothing compared to all the headaches I'd save with virus  removal. 
 
Oh, just in case your interested, the game I'm running the most is League of Legends.

Many thanks!

---

### Post by e79 on 2011-06-28
Running games in a virtual machine is definitely not comparable as playing it straight of your hardware, sometime they won't even lauch as the virtual drivers are not ready yet for such tasks. To build virtual machines, you would need something as [VirtualBox]("http://www.virtualbox.org/") (there is many virtualization solutions, just mentioning one free here)

As for running League Of Legends on WINE you should be able to do it following this post

[http://eu.leagueoflegends.com/board/showthread.php?t=2384](http://eu.leagueoflegends.com/board/showthread.php?t=2384)

Hope this helps

---

### Post by MerlinCoder on 2011-06-28
Ahh I see. I was wondering if a VM could emulate the CMOS and work as if it was just another instance of your computer booting up. If theres all kinds of emulation going on in the background it probably isn't worth it when I could just dual boot...Sorry I really should have researched it a little before posting.

---

### Post by e79 on 2011-06-28
> **MerlinCoder said:**
> Ahh I see. I was wondering if a VM could emulate the CMOS and work as if it was just another instance of your computer booting up. If theres all kinds of emulation going on in the background it probably isn't worth it when I could just dual boot...

Dual Booting would be your best bet unless WINE can run it, for now.

> Sorry I really should have researched it a little before posting.
No sweat, we're here for that  :p

Hope this helps

---

### Post by travisHAZE on 2011-06-28
I've played with Wine for just one game, Neverwinter Nights, and it runs better on Ubuntu w/ Wine than with Vista on this crappy laptop. 

Try dual-booting first, keep Vista for just the games, then Ubuntu to try and see how they all run under Wine. Wine works fairly well at running Windows programs (And it's not an emulator!)

Thus far I've got Photoshop CS1 installed through Wine, Neverwinter Nights and attempting to get 3ds Max to function with my specs, but it doesn't look like it will.


Just be prepared for a total shock from the fresh switch to Ubuntu from Vista, I'm still adjusting.
Your best friend will quickly become the Terminals, as it runs quicker than the GUI does
[Ctrl] + [Alt] + F1-F6 give you different terminals, [Ctrl] + [Alt] + F7 returns you to GUI

---

### Post by MerlinCoder on 2011-06-28
Will the VM work quite well for 2D applications? Such as Visual Studios?

---

### Post by dFlyer on 2011-06-28
Needless to say if your a gamer, it's best to dual boot and keep you windows. You can use wine for a lot of stuff including games, but most gamers I know stick with windows for the games, unless you can find it native to linux.

---

### Post by Terl on 2011-06-28
> **MerlinCoder said:**
> Will the VM work quite well for 2D applications? Such as Visual Studios?

Most likely it would but why would you want to do that?  Seriously, the best thing is if you want to run windows apps the best way to do it is in windows.  And if you want to develop for windows (Visual studio) why wouldn't you want to run windows?

I did not want to give up my games or go through the hassle of setting up Wine (and not all games work well in Wine anyway) so I dual boot.  No shame in it...my laptops though are pure Ubuntu.

---

### Post by MerlinCoder on 2011-06-30
> **Terl said:**
> Most likely it would but why would you want to do that?  Seriously, the best thing is if you want to run windows apps the best way to do it is in windows.  And if you want to develop for windows (Visual studio) why wouldn't you want to run windows?


One of the main reasons I want to switch out of windows is to keep me motivated. If all my games are sitting there waiting for me, its hard to keep working on a project haha!

I use Visual Studios for SDL development and have had things written in it compile for macs and linux os. The main reason I'd like to stick with it is because the tools are debug features are quite good and I've been disappointed with some of the alternatives such as Dev C++. Of course, its more laziness on my part of finding, installing and setting up a new IDE. But I do get your point.

---

### Post by ellaivarios on 2011-06-30
Running games through a Virtual Box inside any GNU/Linux distribution, not just Ubuntu is folly. Performance will drop at least by half, and more than likely your graphics card and audio capabilities will not be used, but a generic video and audio card is simulated by the Virtual machine. Playing simple games would not be a problem, but I would not try to play Crysis or Farcry or any of those resource-hungry games.

GNU/Linux, and in particular the distribution known as Ubuntu, are not nearly as far as Windows in the gaming industry, plus they use OpenGL instead of DirectX to render graphics, and although OpenGL is better and free, well Microsoft has its ten little fingers and toes tickling the noses of every game developer to use DirectX, so there are incompatibilities. As an alternative you can download use "Supreme Super Gamer.iso" a Linux based Gaming distribution with many games (it's about 8GB). Search in Google.

My advice is to dual boot Ubuntu and just keep Windows for gaming. Besides, you will probably need Windows if you are not a computer code & script-writing geek. Aside from the trivial issue of being able to play games, GNU/Linux Operating Systems cannot run important serious applications that people need for their profession, such QuarkXpress or Indesign, or Photoshop (the Linux alternatives Scribus and Gimp, respectively, being severely inferior). Anyway, the fact that you have viruses and malware means you are a very sloppy computer user that downloads garbage and visits shady websites... sorry to slap you with the truth pal. Having a gaming PC means does not necessarily imply that you should have viruses on your computer. It just means more than likely you have cracked games which you haven't paid for or you visit sketchy sites, or both. I have never used an antivirus or a firewall in my entire life and I have never had a virus or a trojan or any malware for that matter of the likes of it to my knowledge at least. 

My advice to you, if you prefer to download illegal pirated stuff, would be to invest in a Sandbox. (Don't try to download a cracked/hacked version off a torrent like you did with the rest of the stuff you downloaded and gave you all those viruses...c'mon... you'll end up with the same problems again) A Sandbox is basically what it says: it creates a memory box for an application/program so that while you run it, the application has no access to other memory processes or files and is self-contained, so if it has a virus, well more than likely it will not infect your computer -- more than likely, but not definitely. The other better, but more time-consuming alternative is to open suspicious downloads in a Windows VirtualBox (even within Windows) and run an antivirus.

Don't listen to all the urban legends that there are no viruses or trojans for GNU/Linux. Of course there are. It's just that first of all there aren't too many GNU/Linux users, and secondly the root is protected...although I think that's kind of stupid too... it'll bite us all in the butt like in a Sci-Fi movie, because the root belongs/is owned by the system itself... One of the easiest ways to steal your friend's password in Linux, because users type it in like a million times each session, is to create an application and upon installation it pops up a window that looks just like the prompt the operating system pops up asking for your password. (who's gonna check you right of wa? You think everyone sits and reads code every moment of the day?) LOL To make it more robust in capturing someone's password, you can make it give an "incorrect password" on the first time the user inputs it, in case there is a typo LOL, so the user types it in more carefully. Then have the program send this info to you in an e-mail or something, and have the program code erase itself for this function after it completes the job. You know how easy it is to make something like this in Linux? If you want you can make sure this program duplicates itself upon copy transfers to other computer systems. That would be a virus, and completely undetectable, actually. (just throwing out ideas I guess...). WHat I'm trying to tell you is that having crap infecting your computer is more than often due to user choice, not because some hacker wants to deliberately get you. Trust me, no firewall or antivirus will prevent a hacker from entering your system if they know what they are doing and you are a worthy target...

What most people don't understand is that most viruses and trojans are marketing gimmicks by the very same companies that make antivirus software products...otherwise they would be out of business. You think some clown-geek sits there in front of his computer and just makes a virus that destroys everyone's computer for no reason or purpose? The only true reason for someone to sit down and write of a virus or a trojan or a worm for that matter, is to OBTAIN INFORMATION or make your computer a zombie so he or she can control it and use it to commit cyber crime. An easy way to get people's credit cards or e-mail passwords (were most credit card information is usually stored by dumb users) is through really sought-after programs, such as your favorite newly released game -- it's free to download, because statistically, the dude who cracked it will more than likely get twenty times more money than what the poor programmers got working three years to make it, just by getting access to people's personal data, such as Identification and credit card info... There was a 19-year old guy in my neighborhood in Greece who got caught for having hacked in Interpol, the CIA and the FBIa... and this valuable info would fetch a lot of money from the people who are the enemies of these agencies. Moreover, this guy would create spybots on thousands of computers, essentially making your and my computer a zombie that he could use to commit other crimes, like steal people's credit card info. ..He was using Linux... (oops) 

By the way, if you want to install Ubuntu, download version 10.04. Don't even think about 11.04. It's the Vista of GNU/Linux. It's garbage, because they trashed Gnome for Unity, and running Compiz on it is a pain in the butt. Basically, with the Unity desktop manager, instead of having menus and buttons like you are used to for accessing programs, you only search for everything - that's it, no menus no nothing. Now unless you are brain damaged like the clown who thought of designing this, you probably remember visual paths more than the name of the thing you are trying to find... but of course all the Linux Gurus and Ubuntu fanatics will tell you everyone remembers things like "synaptic" -- or "IBus" and of course they know WTF these programs/utilities do... especially if they are new users to Ubuntu... they will  know what to search for... and sure enough if they don't know these applications/utilities exist...they will not use them.. but who cares? The way Ubuntu is going with this Unity thing it is turning itself into ten times more idiot-proof than MacOS... and about a hundred times more frustrating. (yeah you can switch to "classic gnome" at login... but it's still incompatible/buggy with Compiz...

SO, here's the summary after my rant:
1.DUAL BOOT WINDOWS & UBUNTU
2.USE WINDOWS FOR GAMING
3.STOP DOWNLOADING CRAP & STOP VISITING SKETCHY WEBSITES.
4.WINE MAY OR MAY NOT WORK FOR RUNNING GAMES, AND MOST OF THE TIME YOU WILL HAVE PROBLEMS, i.e. CRASHES, BUGS, STALLING, ETC FOR COMPLICATED AND GRAPHICALLY INTENSE APPLICATIONS/GAMES. TRY IT - IF IT WORKS, YOU ARE LUCKY. IF NOT, TOUGH LUCK.

---

### Post by FormatSeize on 2011-06-30
> **ellaivarios said:**
>  My advice is to dual boot Ubuntu and just keep Windows for gaming. Besides, you will probably need Windows if you are not a computer code & script-writing geek.
Not necessarily (and you are scaring the noobs away). Something like KDE can be run without any knowledge of terminals and all that cryptic stuff. I read the other day a testimonial about using KDE for years without having to delve into all of these things. Though, he is an artist of some sort, as he talked a lot about using Gimp, or something.
 
I will say, though, that you do come across those that ask things like "why do you have to be a computer programmer to use Linux" or "is there a GUI that can do that," so there are those that are turned off at the terminal prompt aspect of it. 
 
> **ellaivarios said:**
> What most people don't understand is that most viruses and trojans are marketing gimmicks by the very same companies that make antivirus software products...otherwise they would be out of business. You think some clown-geek sits there in front of his computer and just makes a virus that destroys everyone's computer for no reason or purpose?
... yeah. That's what I always thought, it was just someone that was bored and malicious at the same time, and happened to be in front of a computer. 
 
> **ellaivarios said:**
> By the way, if you want to install Ubuntu, download version 10.04. Don't even think about 11.04. It's the Vista of GNU/Linux. It's garbage, because they trashed Gnome for Unity, and running Compiz on it is a pain in the butt. Basically, with the Unity desktop manager, instead of having menus and buttons like you are used to for accessing programs, you only search for everything - that's it, no menus no nothing. Now unless you are brain damaged like the clown who thought of designing this, you probably remember visual paths more than the name of the thing you are trying to find... but of course all the Linux Gurus and Ubuntu fanatics will tell you everyone remembers things like "synaptic" -- or "IBus" and of course they know WTF these programs/utilities do... especially if they are new users to Ubuntu... they will know what to search for... and sure enough if they don't know these applications/utilities exist...they will not use them.. but who cares? The way Ubuntu is going with this Unity thing it is turning itself into ten times more idiot-proof than MacOS... and about a hundred times more frustrating. (yeah you can switch to "classic gnome" at login... but it's still incompatible/buggy with Compiz...
I completely agree with this. I was doing a little internet research the other day because I was wondering why there was a sudden shift to Unity in the first place, especially since all you ever hear about is how it crashes, how it was "not ready", and how Gnome is an afterthought in 11.04 (generally for hardware issues). It turns out that there was some sort of disagreement between Canonical and the people that make GNOME, or something. I didn't get all the details. I starting reading a multi-part journal entry by a guy that says he used to hold a high position in GNOME, which he is telling the story of what happened. But it turns out that all of the journal entries aren't finished yet (which was dissapointing after an hour of reading it).

---

### Post by MerlinCoder on 2011-06-30
Thanks for the advice (albeit quite insulting).

My last virus came from a java applet that I ran through a webpage, and spyware is generally from ignorance on my part, installing a new theme or something...I don't crack software or use torrents. I enjoy video games, and make sure that I support the creators.
Occasionally I will try and find ebooks for free, and often end up at a dodgy location. 

We make mistakes. Windows, and indeed likely Linux, can be unforgiving if something is accidentally installed.

---

