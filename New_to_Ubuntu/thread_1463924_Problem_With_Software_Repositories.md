---
title: "Problem With Software Repositories"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-27
From time to time I go into Synaptic and type down commonly used Linux programs. I even watch people on youtube giving tutorials on some of this stuff and their Synaptic Package Manager seems to pull up "songbird" (as an example) but if I type "songbird" into my synaptic, it only comes up with "pidgin" (which I don't want). [COLOR=DarkRed]But that's only an example. I found a pain-in-the-but-round-about-way of getting it.[COLOR=Black]

Now... I'm experiencing the same problem again, and I just can't help but feel things would be going so much easier if it were all just in the Repositories... Is there a way for me to add more repositories to synaptic? If so, how?

I know that you need to refresh your Synaptic on a regular basis and check for updates. That's not the problem. I do that once every few hours (it seems).

Right now I'm trying to get Kdenlive. Fortunately, Synaptic DOES have Kdenlive, but I keep pulling up a glitchy version that doesn't even work. And it's version 5.5 or something... the current version, correct me if I'm wrong, is 7.7. So I've tried going to [http://www.kdenlive.org/](http://www.kdenlive.org/) but that's got to be one of the worst websites I've ever been on. You'd think clicking "Download" would do something, but... it just gives weird instructions that I don't even understand because it's evidently not working for me.

I've successfully installed some kdenlive stuff but what winds up happening is when I place it under my user folder it still doesn't work.

So... there's gotta be an easier way.
[/COLOR][/COLOR]

---

### Post by dannyboy79 on 2010-04-27
have you enabled the multiverse, universe, and proposed repositories? it's within one of the pulldown menu's within synaptic. don't know if songbird is even in the repo's though. i just checked my lucid repo's and it's not in there. if you're running karmic, you can add this ppa for songbird:
[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)
don't forget to update after each time you add a new repo. good luck

---

### Post by Merk42 on 2010-04-27
Yes there's a way to add more repositories.
As for how easy it is, that depends on how cooperative the other end (in this case KDENLive) is.

If you go the download section where it talks about Ubuntu packages that's exactly referring to adding more repositories.

The instructions may not make sense because it seems they're assuming you're using KDE, and I'm assuming you're using GNOME.
[list=1]   [*]go to System Menu > Software Sources > Third-Party Software;
   [*]click add and paste this line in:
      ppa:sunab/ppa If you are using KDE 4.3
      ppa:sunab/sunab2 If you are using KDE 4.4 WARNING: this is an "unstable" ppa updated weekly with svn trunk of Kdenlive and MLT
   [*]close software source and click reload.
[/list]
Translated for GNOME
[list=1]   [*]go to System > Administration > Software Sources > Other Software Tab;
   [*]click add and paste this line in:
      ppa:sunab/ppa If you are using KDE 4.3 
      ppa:sunab/sunab2 If you are using KDE 4.4 WARNING: this is an "unstable" ppa updated weekly with svn trunk of Kdenlive and MLT
(you're using GNOME, which is neither, so stick with the first option)
   [*]close
[*]Reopen synaptic and reload and find kdenlive to install
[/list]

---

### Post by orphanlast on 2010-04-27
[Merk42]("http://ubuntuforums.org/member.php?u=314897")
It seems like some of this is working. Kdenlive 7.7.1 is showing up, but when I try to makr it for instillation it sates the following: 

> 

COULD NOT MARK ALL PACKAGES FOR INSTALLATION OR UPGRADE
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

(>=4:4.6.2-0ubuntu3~karmic1~ppa1) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: libqtgui4 (>=4:4.6.2-0ubuntu3~karmic1~ppa1) but 4.5.3really4.5.2-0ubuntu1 is to be installed
  Depends: melt (>=0.5) but 0.4.4-2build1 is to be installed
  Depends: libmlt-data (>=0.5) but 0.4.4-2build1 is to be installed




I'm trying to follow what you've said to the letter. (I have Gnome... I think. I'm operating Ubuntu)

From that information right there, is there anything that you can suggest me to do in order to get things flowing from this point?

---

### Post by orphanlast on 2010-04-28
Just an update for everyone. I'm not just twiddling my thumbs and toes like a mangy mutt (5 points for those that know where that phrase comes from). 

I regularly do independent research on my own and I'm currently here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) ... ... ... even though I'm hugely the opposite of a fan when it comes to help.ubuntu.com ... I know they're doing their best, but sometimes they just waste hours and hours and hours and hours and hours and hours and hours and hours and hours and hours of your time.

But anyways, I AM learning quite a bit from this page and I think anyone just starting out and wants to know anything about software repositories (which you all should) better take a look and read this entire page.

I'm still having troubles but if I wind up resolving the issue on my own, I'll let everyone know how I managed this.

---

### Post by orphanlast on 2010-04-28
Okay, so now I know how to navigate through the menus dealing with software repositories... but I have no idea where I'd go to find a new repository so that I could add one, much less find one that's compatible.

At the end of that Help.ubuntu.com page that I supplied, it gave me this link [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/) and I assumed it was a list of different repositories I could add, but when I try to add them... doing something like "deb http://packages.ubuntu.com/dapper/admin/" it's just not working... 

I'm a noob, so if that's freakin' stupid, I'm sorry.

Anyways -- I've gone to brainstorm.ubuntu.com and posted how I think this could be improved, especially for a noob like myself. If you're interested in taking a look, have at it. It's right here.

[http://brainstorm.ubuntu.com/idea/24345/](http://brainstorm.ubuntu.com/idea/24345/)

This is like shopping for the shop BEFORE you shop for your programs. It's kind of annoying because it's as though there's no "SHOP" for the shops... Unless anyone can direct me to a website or something that just has a long list of functioning repositories for Ubuntu that I can just copy and past into there... that would be pretty cool.

---

### Post by dannyboy79 on 2010-04-28
the main approved repositories are already listed within the repositories selection in ubuntu synaptic! if you enable those and still don't find the software you need already packaged for ubuntu, you have to search for it yourself. either on getdeb or using google to find .deb's (this is no guarentee that it'll work with ubuntu), best option would be is to get the source and compile it yourself.

You're asking something that is almost unaccomplishable.

You want a repository to add to ubuntu for every phathomable linux software out there? The vast amount of available software approved to work with ubuntu is either already in an approved repo or within a ppa that someone created because they wanted to provide the software already packaged for the masses. anything else, you do the leg work and hunt down the source and compile it yourself.

Don't know what else you want?

---

### Post by CatKiller on 2010-04-28
> **orphanlast said:**
> So... there's gotta be an easier way.  Kdenlive is in the Universe repository. 7.1 for Karmic, 7.7 for Lucid (released tomorrow).  System -> Administration -> Software Sources -> Community maintained Open Source software (universe) to enable the Universe repository. No need to mess about with PPAs.

---

### Post by orphanlast on 2010-04-28
>  System -> Administration -> Software Sources -> Community maintained Open Source software (universe) to enable the Universe repository. No need to mess about with PPAs.

Okay, I'm able to follow you from SYSTEM all the way down to SOFTWARE SOURCES... but I'm not finding a menue, button, or tab called Community Maintained Open Source Software.

---

### Post by todak on 2010-04-28
> **orphanlast said:**
> Okay, I'm able to follow you from SYSTEM all the way down to SOFTWARE SOURCES... but I'm not finding a menue, button, or tab called Community Maintained Open Source Software.

Check the box next to the line that I have highlighted for you.

---

### Post by oldsoundguy on 2010-04-28
The easiest way .. no adding individual lines and cutting and pasting:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
download/install/run ... then

update.

It will NOT add PPA sources .. those DO have to be added by you if you want to risk the software that is on the site .. some PPA sources are rock solid .. some are running Alphas and Betas that are not quite stable all the time .. do your research!

---

### Post by orphanlast on 2010-04-28
> **todak said:**
> Check the box next to the line that I have highlighted for you.

Oh yeah. Did that yesterday. Thanks!

> **oldsoundguy said:**
> The easiest way .. no adding individual lines and cutting and pasting:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
download/install/run ... then

update. 

Woah... So Tweak... if I'm understanding this, it's like Synaptic. I don't add repositories to synaptic... I download repositories as separate programs. Is that right? Or is it both? ... It looks like it's more than just a repository... The computer recognizes it as "A SYNAPTIC".

Man... this isn't getting any easier. When I go to the update manager check the update and press the UPDATE button it states the following: 

"COULD NOT APPLY CHANGES! 
FIX BROKEN PACKAGES FIRST."

When I click "Close" on that pop up. it says the following: 

"UPDATE SUCCESSFUL"

... Kinda Ironic.

I'm honestly impressed with this thing, it's just confusing me because it's constantly telling me that updates have been successful but if I go to that update manager it just keeps saying that the update is successful. Some of what I've described happens to be in some of my attachments.

>  It will NOT add PPA sources .. those DO have to be added by you if you want to risk the software that is on the site .. some PPA sources are rock solid .. some are running Alphas and Betas that are not quite stable all the time .. do your research!I appreciate you're help. Lol, but there's so much Jargon. What do you mean by PPA. I genuinely googled around. I even went onto a Linux Questionair Wiki and they said PPA doesn't exist and the only thing that I can find as a definition is: "  Parallel Port Adapter" but we're obviously not talking about a computer cord.

But what I'm gleaning from this last paragraph of yours is that you're basically telling me to be selective with the programs I pick and maybe you're even saying that if I want to expand the software repository then I'm basically on my own. Tweak won't help with that.

---

### Post by alexcckll on 2010-04-28
Orphanist, 

The term PPA in this context means something like "Personal Package Archive".

Personally, I'm still sticking to the standard repositories.  As a beginner, or as a basic user, it might be best for you to do the same, and submit Needs-Packaging requests for the apps you would like to see available for Ubuntu.

Thoughts?

---

### Post by orphanlast on 2010-04-28
> **alexcckll said:**
> Orphanist, 

The term PPA in this context means something like "Personal Package Archive".

Personally, I'm still sticking to the standard repositories.  As a beginner, or as a basic user, it might be best for you to do the same, and submit Needs-Packaging requests for the apps you would like to see available for Ubuntu.

Thoughts?

Normally I'd agree... but there's just some programs that I can't seem to get any other way. Kdenlive, for example, doesn't even show up in my synaptic. In fact, the version of Tweak that was in my Synaptic was version 3 when it looks like it's up to version 5.

I refresh Synaptic all the time and I tell it to mark all updates but it doesn't seem to update anything or expand its repository at all...

---

### Post by orphanlast on 2010-04-28
> **alexcckll said:**
> Orphanist, 

The term PPA in this context means something like "Personal Package Archive".

Personally, I'm still sticking to the standard repositories.  As a beginner, or as a basic user, it might be best for you to do the same, and submit Needs-Packaging requests for the apps you would like to see available for Ubuntu.

Thoughts?

I agree... but I really want to learn all that there is about this Operating System and be really competent with it. I also don't see all sorts of programs in my Synaptic, but I see it in other people's.

Kdenlive, for example, seems to be nearly impossible to get any other way (their website has you go through some HUGE hassle). If a website has a "download page" they should just have a big button that says "DOWNLOAD" and that's the end of the story.

My Synaptic seems to be mentally retarded in that I press on the "check updates" and "refresh" daily and yet its latest version of Tweak was version 3, when the latest version is version 5.

The standard repositories don't seem to update or add any more...

This whole process needs an overhaul. It doesn't make sense as to why everyone somehow managed to make this so complicated.

Sorry... Firefox didn't post my original response until now... weird.

---

### Post by Bradtek on 2010-04-29
> **orphanlast said:**
> 

This whole process needs an overhaul. It doesn't make sense as to why everyone somehow managed to make this so complicated.

It seems it is only so complicated to you.

I just checked and it is in the Universe repository on my 10.04 install
its as complicated as selecting and clicking apply.

Please consider that it is you the end user that has complicated things by not following instructions correctly or at some stage making a mistake that has made it now complicated to rectify.

---

### Post by orphanlast on 2010-04-29
AHA!!! I figured it out. tweak wasn't updating because I needed to go to software sources (as shown in my first attachment) and then make sure that all the check marks were checked. I hadn't done ANYTHING to my sources list except for play with Tweak, so I figured if I would check those, then everything would be updated.

As for me getting Kdelive to work. My problem was looking at this page and being stupid at the same time [http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages)

One of my attachments has the key part highlighted. I actually put both of those Software repositories in there. So I'm assuming that the system was conflicting with itself and so Synaptic was unable to mark anything for installation because two repositories were trying to make the same command or something....

So once I removed both of them and tried one or the other -- TAH DAH!!!

Wow, and it took me two days to figure that one out.

(The only reason why I'm telling you all this is for two reasons. First, I want you all to know that you haven't wasted your time, and Second, I know there will be other people doing a lot of googling and they'll be trying to find this same information and if I don't say it, these people will be left in the lurch making my same mistake and possibly throw their hands up in the air and never forgive Ubuntu and go to MS Windows.

---

### Post by orphanlast on 2010-04-29
> **Bradtek said:**
> It seems it is only so complicated to you.

I just checked and it is in the Universe repository on my 10.04 install
its as complicated as selecting and clicking apply. 

No it wasn't. When I went to Synaptic originally, Synapic only had a VERY outdated version of Kdenlive. I'd mark and apply and have it installed but the stupid thing wouldn't work. Even the developers of Kdenlive admit that their older versions of Kdenlive have undergone some serious problems, have not been updated, and thus won't work.

So I wanted to get the up-to-date version. This got me to go to the Kdenlive website. I didn't understand their instructions (Most especially since I didn't even know that I could expand or add completely different repositories or how I would even do that... so the instructions looked like gibberish to the layman). 

So I did more research and didn't find much. I came here. Asked for help. Based off of what people were telling me, I had kind of a starting point to know what I should be googling for. I learned a little more about the process of adding repositories and how to add them (but not where to find them, unfortunately... I still don't know where to find repositories... it's like shopping for a shop).

After a while I got discouraged and I went on autopilot mode. I'd just listen to what someone here had to say and I'd try it out and that's how I got Ubuntu Tweak, and it's awesome.

Then I got pissed off at Ubuntu (as I often times do) and decided that I needed to figure this out or at least pout at the kdenlive.com site thinking "why the hell didn't they just place a download button like so many other websites." (Which I still don't know why they didn't but oh well.)

But I read the instructions, noticed they were the same instructions that someone else had given me in this thread. And thought that maybe if I were to have both repositories listed, then that might cause problems. I looked at the list and lo and behold I saw two repositories under the same name and tinkered with it.

So there was a lot more to getting Synapic to get it...

I'm sure the next version of Ubuntu will have everything up to date and it's coming out within... an hour of me posting this. lol. But, what happens when 10.04 gets aged and I start experiencing the same thing... all the software in the repository starts aging with it...

... Nah... I want to know how to update it myself. I can't just wait for the next version to come out every time I find a program that's out dated.

>  Please consider that it is you the end user that has complicated things by not following instructions correctly or at some stage making a mistake that has made it now complicated to rectify.

Yeah... I see my mistake. I still think it's overly complicated. Why can't we have a list of all the repositories and give them a 1-5 star rating. Those that have 4,000 people having rated one repository as reliable, I think it's safe to say that you could add that one... rather than search blindly for repositories and randomly adding one to another... just having your fingers crossed that the sucker will work or that the software will be reliable.

---

### Post by orphanlast on 2010-04-29
I don't know what the big deal is... I'm a noob. I'll admit it. That's my most of my, undoubtably irritating, threads are on absolute beginner talk. Of course I'm going to over complicate stuff. I hardly even know how Ubuntu functions.

Lol... and what do you know... even the newer version of Kdenlive freezes... at least it's able to play two seconds of the clip I want to edit. That's a step in the right direction.

---

### Post by Bradtek on 2010-04-29
Doing it yourself is the only way to be sure it gets done and done the way you want it and this is how many Free & Open Source apps get created.
Someone needs an app to do something so they create it, then release it as open source so others can use and or improve it.
Unlike the Micro$soft world where you pay for something and expect it to work or have it fixed, the Linux and FOSS world you get something for nothing and are expected to learn how to use it or at least not post complaints when it doesn't work. You help by reporting bugs and or posting soloutions.

Pleas feel free to compile and manage a list of repositories and their ratings.

As you are having so much trouble with this one application, has it occurred to you to try a different video editor ?

I'm not sure what the current situation is with Video Editors in Linux as I haven't needed to use one other than Avidemux to convert a few videos.

---

### Post by CatKiller on 2010-04-29
> **orphanlast said:**
> The standard repositories don't seem to update or add any more...


This is a feature, not a bug. Ubuntu is deliberately set up to use fixed collections of software packages which are tested together. The particular versions of each package are set at feature-freeze, which happens some time before release to allow testing to occur. The only updates that you get are security updates and bug fixes. This approach means that all the software is necessarily dated, but only by a maximum of seven months or so. As a complement to this approach, you can add other repositories for more up-to-date software, although the newer version will not have been tested in conjunction with all the other software that you might have installed. This includes backports, which are versions for *release*+1 made available for *release*.

There are distros that have a rolling release approach, but Ubuntu isn't one of them.

---

### Post by dannyboy79 on 2010-04-29
> **orphanlast said:**
> AHA!!! I figured it out. tweak wasn't updating because I needed to go to software sources (as shown in my first attachment) and then make sure that all the check marks were checked. I hadn't done ANYTHING to my sources list except for play with Tweak, so I figured if I would check those, then everything would be updated.
are you using lucid or karmic? either way I don't know what the whole 2 days of posting was all about as if you re-read post #2 you'd see that I gave you the answer you needed immediately. I don't have any ppa's or any weird unapproved repo's added to my sources and when I do
sudo aptitude show kdenlive
i get back this:
0.7.7.1-0ubuntu1
it's located in the universe repo under the graphics section.

you're a noob, and we all were at some point but you do know how to read I trust. you could've saved yourself a whole mess of time as well as others if you had just read post #2

---

### Post by orphanlast on 2010-04-29
> **dannyboy79 said:**
> are you using lucid or karmic? either way I don't know what the whole 2 days of posting was all about as if you re-read post #2 you'd see that I gave you the answer you needed immediately. 

Sometimes people can get an answer to the question but they won't understand it... or the answer doesn't work because it's implemented wrong... which both happened to be the case here. I also kept everyone in the loop as to what I was doing and what has been the problem. And I was trying to find out what was going on.

I DID follow your advice.

>  I don't have any ppa's or any weird unapproved repo's added to my sources and when I do
sudo aptitude show kdenlive
i get back this:
0.7.7.1-0ubuntu1
it's located in the universe repo under the graphics section.

you're a noob, and we all were at some point but you do know how to read I trust. you could've saved yourself a whole mess of time as well as others if you had just read post #2

I can read. It's been a lot of reading.

And I don't know what to tell you but kdenlive 7.7 wasn't coming up in my Synaptic. It just simply and absolutely wasn't. I know this because I was reading what Synaptic was saying.

---

