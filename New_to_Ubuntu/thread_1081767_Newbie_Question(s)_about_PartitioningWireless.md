---
title: "Newbie Question(s) about Partitioning/Wireless"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Gossamer8 on 2009-02-26
Greetings all!

So a friend of mine switched to Ubuntu and got me interested in the idea. I've been reading up on how to switch, and beginner guides, etc - and I'm pretty sure I want to start off with dual boot. I figured this was a good way to see what I'm "missing" on the Ubuntu side, and keep access to things like Windows based games I still like to play.

I have a dual core PC, so my hard drive is already separated into two, 80GB partitions. My question mainly is whether I should move the things I have saved on my partition without the Windows OS (D:/), mainly photos and iTunes mp4 files, back to the side with Windows (C:/), and shrink that side down to just what it needs to store what it has right now ... and then install Ubuntu on D:/ and give it lots of space - or if I'm fine to just leave it divided 80/80, and put Ubuntu on D:/?

Ideally, one day, I'd like to just be running one OS ... likely Ubuntu ;), but for now I want to keep a bare bones Windows, mostly for my games I still enjoy. I'm just not sure exactly how to set myself up for what I want to do. Any tips are greatly appreciated!

And my tiny little 2nd question is related to wireless. I'm pretty sure my Linksys card IS supported ... but how do I make sure I have everything set up to get my card up and running right away when I'm working in Ubuntu? Should I download the Linux driver to a flash drive and install it that way? Of all the devices I have that one is the biggest deal to me - I'm a 'net junkie! So I want to be sure I know exactly how to get that working right away after install. 

Thanks!

~ Gossy ~

---

### Post by sailthesea on 2009-02-26
Hi 
 If you just want to try things out you can do it two ways:
1 Create a live cd and boot it up BUT it may not work your wireless and other bits and pieces
2 Easier (I found anyway) Use Wubi and install 8.10 within windows and then you really will see how things work I did this a while back and found no problems in fact I'm still dual booting that way now

 There can be a few niggles with wireless but if it doesn't work out uninstall and try again 
 Good Luck

---

### Post by wlraider70 on 2009-02-26
There is a way that you can access your windows partition files form Ubuntu, so i would just leave them where they are.

as for how, i don't know.

---

### Post by Gossamer8 on 2009-02-26
Thanks for the suggestions ... but I'm ideally going for the best performance along with this too - and from what I read in the Ubuntu Pocket Guide, that is posted in one of the stickies here, it seems the best of both worlds I can get is creating a partition for Ubuntu, and just choosing at boot up time which I want to go into. It seems like running Ubuntu IN Windows is going to ruin the performance/point for me ... my intention really is to wind up just using Ubuntu in some form or other - but to start with I want to preserve the windows area for a few things I'm worried I won't be able to get working on the Ubuntu side, but don't need constant access to anyway.

So really my issue is whether I should play around with moving the files, and if/how I should shrink down the Windows partition. Also, what steps I need to take to make sure the wireless works on the Ubuntu side.

---

### Post by sailthesea on 2009-02-26
Well you've done your reading so you will have a good idea what to do if you want alter your partition Yes back up and shrink your windows partition 
 I take it your using vista? Otherwise it can get complicated You will have to use Gparted or similar Partitioning during install is fiddly
 My original suggestion Wubi within windows is only to test things out re your hardware If it all works go for the full install if it doesn't you haven't made any permanent changes My setup is working on an old machine that I don,t demand much from
 Run Wubi as a test is what I'm saying
Post some specs and you'll get a lot more response
Jump in and don't be afraid

---

### Post by lindsay7 on 2009-02-26
I just did all the things you are talking about doing. If you run the live cd ubuntu, you will be able to setup and see if you wireless card works and is compatable. You then can do whatever you want as far as the dual boot goes.  When you do the Ubuntu install form the live cd, it will walk you thru the partition process and will not do anything until you confirm that you are ready to install ubuntu.  Be cautious however because when you get to the point of acually partitioning you hard drive for the final act of installation, the program will do the partition and it can not be undone unless you back all the way out of the install program and use windows or some other program to set the partitions back to where they were.  You will get a warraning during the installation telling you this will happen, so just careful.  The good news is, if you make a mistake and you are not happy with somethng, you can repartition and formate under windows and try again.  My hard drive was in two partitions like yours and what I did was to get into windows and extend my windows partion to use the whole drive. Then I let or used the Ubuntu install program to setup the dual boot partition as I wanted. You just slide the bar on this install screen to set the size of the partitions you want  for the dual boot. It was very easy that way and took the guess work out of all of this.

---

### Post by Gossamer8 on 2009-02-26
Sailthesea - Aaaahhhh I gotcha now :) I thought you were talking about the option to always run Ubuntu as a virtual machine IN windows - and though my computer specs are pretty decent, I figured that would sort of diminish the "experience" of having this bright and shiny new OS. But you're totally right, I should definitely run it the way you said to test out compatability! I'm definitely going to do that. And yes, I am running Vista, so hopefully that will avoid issues.

Lindsay7 - Thanks so much for the reply!!! I wasn't sure if during the dual boot set up it'd walk me through the partitioning stuff the way you described it or not. I read that it "walks you through it", but not whether it had options for sizing, etc. Guess I shouldn't be so surprised at how easy they make the install ;). 

I'm definitely going to back up all my data I'd die if I lost (mp3s, photos, docs, etc) before I do anything - so I'm not too worried after that about partitioning "going wrong". And now that I know it'll let me pick the sizing during install I think I'm good to go with that!

---

### Post by sailthesea on 2009-02-26
Good man!
 You'll know after a couple of hours if its all working 
 Go for it coz you you won't do any harm

You'll love it!
WELCOME

---

### Post by Gossamer8 on 2009-02-27
I'm all excited. I don't really have time to fiddle with it tonight but I'm already planning when I'll have time to sit and take care of everything. It's like I'll have a new computer all over again! Exciting!

---

### Post by theozzlives on 2009-02-27
I'd say stick the Live CD in, click on Network Manager to see if your network is listed. If it is, either WUBI or Dual Boot, if not there's still hope (depends on if you want to spend the time and research). These forums are very helpful. I've never found a Windows so helpful. You gotta BUY the OS, then PAY for support with Windows.

---

### Post by sailthesea on 2009-02-27
Well let us know how you get on
I felt exactly the same way when I discovered the new world of Ubuntu just be careful, it doesn't do to go crashing about in terminal and getting excited doing stuff Beware of thinking ubuntu is like windows its not 
 Its better
Have fun

---

### Post by sailthesea on 2009-02-27
He's good to go go go

---

### Post by booshire on 2009-02-27
I have a really thoughtful question for you, what is the wireless card? Even if you cannot find a direct driver for the card, you can still find the chipset (their website or using program like hw32). Ubuntu 8.10 contains much more driver support inherently, and has ndiswrapper on the disk if you want to try and re-use windows drivers. As with anything you do on the computer, research before changing.

---

### Post by lindsay7 on 2009-02-27
[http://en.wikipedia.org/wiki/Ndiswrapper](http://en.wikipedia.org/wiki/Ndiswrapper)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Read these, good info.

---

### Post by Gossamer8 on 2009-02-28
The card, I'm pretty sure, is a Linksys WMP54G. Honestly I stuck the card in there so many years ago I've forgotten - and Windows does little to inform me beyond telling me it's Linksys (unless there is some way I don't know of besides doing a looksy via device manager whathaveyou) - and I know I have the box for it somewhere, but that requires rifling through my computer box of boxes (yes, I save all my boxes lol) which I haven't had the desire to do yet. I should have some time tomorrow to do computer fiddling, and will definitely find out for sure then.

---

### Post by villain_s_deeds on 2009-02-28
I've been a linux newbie on and off for 2 years now.  My linksys wireless didn't work until recently when I installed Ubuntu Studio 7.10.  At first I was reluctant to do this, since I had to actually install it before using (I don't have a liveCD for it), but I am sure glad to have finally given in.

---

