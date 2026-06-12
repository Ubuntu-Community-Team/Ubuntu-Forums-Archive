---
title: "Removing a Virus in Ubuntu"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by roclin on 2009-03-10
I hear all the time that ubuntu has a hard time getting a virus. Well I get them to often. Is there a free scan and fix for my PC? IT WANTS TO SAVE TO FILE BUT WILL NOT LET ME OPEN IT. I'VE REINSTALLED 2 TIMES ALREADY AND NOW XP IS LOOKING GOOD ONCE AGAIN. AT LEAST I CAN FIND A PROGRAM THAT FIXES IT BUT FOR FIREFOX/UBUNTU...PROBLEM.

Email me at: [email]cgraysportron@juno.com[/email]
cgraysportron at juno.com

---

### Post by kidux on 2009-03-10
What virus are you getting? Also, download clamav (I think it's in the repo's) and scan with that. Also look for rootkithunter and scan with that.

---

### Post by roclin on 2009-03-10
It did not tell me his name.;)

---

### Post by roclin on 2009-03-10
rootkithunter  HOW DO i OPEN IT? IT GOES TO FILE BUT i DO NOT KNOW THE NEXT STEP.

---

### Post by cmay on 2009-03-10
when i read this i have to things on my mind. 
first do not put out your email adress on the net like this. 
it has been known to cause spam. 

second i wonder if you have the right permissions set for the files you are trying to open.  it seems very hard to many  to believe that you have a virus .

 i had a rootkit dropped once so i know it is possible to get compromised on a linux system.

i also know that when you resintall then there can be no virus on the new fresh install. 
if there was one in the first place you would have erased it from the harddisk by now if you resintalled twice.

---

### Post by roclin on 2009-03-10
> **kidux said:**
> what virus are you getting? Also, download clamav (i think it's in the repo's) and scan with that. Also look for rootkithunter and scan with that.

in the repo's?

---

### Post by roclin on 2009-03-10
> **cmay said:**
> when i read this i have to things on my mind. 
first do not put out your email adress on the net like this. 
it has been known to cause spam. 

second i wonder if you have the right permissions set for the files you are trying to open.  it seems very hard to many  to believe that you have a virus .

 i had a rootkit dropped once so i know it is possible to get compromised on a linux system.

i also know that when you resintall then there can be no virus on the new fresh install. 
if there was one in the first place you would have erased it from the harddisk by now if you resintalled twice.

right permissions

---

### Post by kansasnoob on 2009-03-10
How do you know you have a virus?

What exactly is wrong?

---

### Post by Tibuda on 2009-03-10
> **roclin said:**
> in the repo's?

Install [clamav,clamav-daemon,clamav-freshclam,clamtk and nautilus-clamscan]("apt:clamav,clamav-daemon,clamav-freshclam,clamtk,nautilus-clamscan") packages.

---

### Post by scottuss on 2009-03-10
Are you kidding? C'mon guys, The OP clearly doesn't have a virus, most likely doesn't have the correct application installed to open a certain file. In fact, after reading again, I get the impression he/she is trying to open a Windows application?

Firstly, what file are you trying to open or run? Secondly you DO NOT need to run a virus scan on Ubuntu. Getting a rootkit is a possibility but I find it VERY unlikely that this is the situation here. You can install rkhunter or chkrootkit to scan for these (you'll be clean no doubt)

I think you should probably read a few of the beginners guide sticky posts and/or do some Googling.

Jeez!

---

### Post by roclin on 2009-03-10
I must get it from some where after I reinstall. It shows up after a while.I went to my site at [www.weddingsbycharles.piczo.com](www.weddingsbycharles.piczo.com) and in my back office nothing works for me to redesign my site. Once in a while my screen goes haywire with many colores and stops.

---

### Post by lavinog on 2009-03-10
To install a virus scanner: click on applications>add/remove, in the search bar type virus and Virus Scanner should come up...select it (at this point I think it will tell you that you need to enable a repo...in this case click ok or yes)

Please explain how you know you have a virus.
Are you assuming that you have a virus because Ubuntu isn't behaving like windows does?

---

### Post by kansasnoob on 2009-03-10
Repo's are repositories. Go to System > Administration > Synaptic Package Manager. Click on Search and type clamav ......... although I see no need as long as you're using an email client with anti-virus.

But we need to know specifically what causes you to think you have a virus?

What's not working?

---

### Post by minsf on 2009-03-10
> **roclin said:**
>  NOW XP IS LOOKING GOOD ONCE AGAIN. 
so it seems that you dual boot XP and ubuntu, right?
did you get that virus while you were using xp or while you were using ubuntu? what are the symptoms- that is, how do you know that you got a virus?

---

### Post by kidux on 2009-03-10
> **scottuss said:**
> Are you kidding? C'mon guys, The OP clearly doesn't have a virus, most likely doesn't have the correct application installed to open a certain file. In fact, after reading again, I get the impression he/she is trying to open a Windows application?

Firstly, what file are you trying to open or run? Secondly you DO NOT need to run a virus scan on Ubuntu. Getting a rootkit is a possibility but I find it VERY unlikely that this is the situation here. You can install rkhunter or chkrootkit to scan for these (you'll be clean no doubt)

I think you should probably read a few of the beginners guide sticky posts and/or do some Googling.

Jeez!
Granted we all know he most likely doesn't have either, but having him run these programs as a newbie is good because it will show him that he is safe because that is the windows mentality which cannot be changed overnight. So have a little patience and humor him until he understands better.

---

### Post by lavinog on 2009-03-10
> **roclin said:**
> I must get it from some where after I reinstall. It shows up after a while.I went to my site at [www.weddingsbycharles.piczo.com](www.weddingsbycharles.piczo.com) and in my back office nothing works for me to redesign my site. Once in a while my screen goes haywire with many colores and stops.

That may be a video driver issue, or a flash issue...not a virus
What video card do you have?
are you running ubuntu 32bit or 64bit

---

### Post by kansasnoob on 2009-03-10
> **scottuss said:**
> Are you kidding? C'mon guys, The OP clearly doesn't have a virus, most likely doesn't have the correct application installed to open a certain file. In fact, after reading again, I get the impression he/she is trying to open a Windows application?

Firstly, what file are you trying to open or run? Secondly you DO NOT need to run a virus scan on Ubuntu. Getting a rootkit is a possibility but I find it VERY unlikely that this is the situation here. You can install rkhunter or chkrootkit to scan for these (you'll be clean no doubt)

I think you should probably read a few of the beginners guide sticky posts and/or do some Googling.

Jeez!

Sounds like something along those lines, but let's be patient.

---

### Post by roclin on 2009-03-10
> **lavinog said:**
> To install a virus scanner: click on applications>add/remove, in the search bar type virus and Virus Scanner should come up...select it (at this point I think it will tell you that you need to enable a repo...in this case click ok or yes)

Please explain how you know you have a virus.
Are you assuming that you have a virus because Ubuntu isn't behaving like windows does?   No, I understand the difference at times but it could be spyware too. I'll check.
It's like changing the channel on the old TV's along with missing info on my webpages in the back office.

---

### Post by lavinog on 2009-03-10
How to get quick responses on the forums: put the word 'Virus' in your title and your post will be read by practically everyone.

---

### Post by scottuss on 2009-03-10
> **kidux said:**
> Granted we all know he most likely doesn't have either, but having him run these programs as a newbie is good because it will show him that he is safe because that is the windows mentality which cannot be changed overnight. So have a little patience and humor him until he understands better.

Maybe so, but this is skirting around the actual problem that he has, and reasserting in his mind that he has a virus (which as you agree with me, he most likely does not)

I just want to get some more information as to EXACTLY what is happening and when so that I can try and give useful advice other than "install an AV" which I am certain in my own mind will not solve his problems.

But I agree that the Windows mentality cannot be changed overnight, and for that reason I will go along with what you say. :lolflag:

---

### Post by AusIV4 on 2009-03-10
Things like ClamAV aren't going to help. As others have stated, rootkit hunters may turn something up, but that's unlikely, particularly if you're not running an Open SSH port.

ClamAV scans files for *Windows* viruses. There aren't any known viruses to scan for on Linux. It's semi-plausible that some might be added in the future, but at the moment there are no Linux viruses to scan for.

Without more information on what is going wrong, we can't help, but I have really strong doubts that the problem is a virus.

---

### Post by bodhi.zazen on 2009-03-10
> **scottuss said:**
> Are you kidding? C'mon guys, The OP clearly doesn't have a virus, ...

+1

This is obviously an new user who does not know / understand the basics yet such as permissions, sudo, etc.

In addition s/he comes from windows, and thus assumes any and all problems are due to a virus (this too is probably wrong thinking, but it shows how much a problem viruses are on some OS).

So why are we jumping on the band wagon and talking about antivirus ?

Let's get back on topic :

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

And also 

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

@roclin : TYPING IN ALL CAPS IS CONSIDERED RUDE.  so please stop ;)

---

### Post by kansasnoob on 2009-03-10
> **roclin said:**
> I must get it from some where after I reinstall. It shows up after a while.I went to my site at [www.weddingsbycharles.piczo.com](www.weddingsbycharles.piczo.com) and in my back office nothing works for me to redesign my site. Once in a while my screen goes haywire with many colores and stops.

That all looks perfect to me. Quite a nice site BTW!

Maybe the Piczo - Quickie ad is messing around with things!

We need to know several things.

What browser are you using?

If Firefox what plugins/add-ons are installed?

---

### Post by roclin on 2009-03-10
I guess I expect when I want to do something it should be easy enough to understand. I do not have windows on my pc. I removed it 2 years ago because I hear ubunto was safer. It has and I want to thank everyone for there help. I put my junk email up and understand the safety factor but will check it later for help. Got to go to work but will be back to check this forum.

Thanks again.

---

### Post by roclin on 2009-03-10
> **kansasnoob said:**
> That all looks perfect to me. Quite a nice site BTW!

Maybe the Piczo - Quickie ad is messing around with things!

We need to know several things.

What browser are you using?

If Firefox what plugins/add-ons are installed?

I do not know how to find out. I just download everything.

---

### Post by roclin on 2009-03-10
> **bodhi.zazen said:**
> +1

This is obviously an new user who does not know / understand the basics yet such as permissions, sudo, etc.

In addition s/he comes from windows, and thus assumes any and all problems are due to a virus (this too is probably wrong thinking, but it shows how much a problem viruses are on some OS).

So why are we jumping on the band wagon and talking about antivirus ?

Let's get back on topic :

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

And also 

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

@roclin : TYPING IN ALL CAPS IS CONSIDERED RUDE.  so please stop ;)

Sorry for the "CAPS". I looked up and sent it before I realized it.

---

### Post by scottuss on 2009-03-10
Call me cynical but if this is the first major issue you've had in 2 years of using Ubuntu and you still don't know that you're not likely to have a virus... never mind.

---

### Post by linuxisevolution on 2009-03-10
Roclin, what problems are you encountering that makes you think you have a virus? Linux is 1000X more secure than Windows xp and if you got a virus than you must've purposely ran it with sudo.....

---

### Post by kansasnoob on 2009-03-10
I think this is something we can work through!

I can even play the video (quite nice I might add) after killing the pop-up!

---

### Post by JohnLM_the_Ghost on 2009-03-10
Ok... well it's all nice and stuff. What makes me wonder though **roclin** hasn't posted the actual problem in any one of the posts. I'm get the feeling we are dragged by our noses on purpose.

Just to be clear **roclin**... What does (or doesn't?) your PC do? And what you expect it to do?

---

### Post by cmay on 2009-03-10
> **JohnLM_the_Ghost said:**
> Ok... well it's all nice and stuff. What makes me wonder though **roclin** hasn't posted the actual problem in any one of the posts. I'm get the feeling we are dragged by our noses on purpose.

Just to be clear **roclin**... What does (or doesn't?) your PC do? And what you expect it to do?

if he post his own personal raw email on a forum and as he also just say "just download everything" i could get the feeling he really do not knows very much about computers. 

if he is dragging us around our noses then lets just hope he is actually using his own email account when he post it for everyone to see. all other scenarios would be kind of ugly.

---

### Post by kidux on 2009-03-10
> **scottuss said:**
> Call me cynical but if this is the first major issue you've had in 2 years of using Ubuntu and you still don't know that you're not likely to have a virus... never mind.
K, I'm gonna call BS on him with you here. Just saw the 2 year remark, nevermind what I said earlier, lol!

---

### Post by lavinog on 2009-03-10
> **JohnLM_the_Ghost said:**
> Ok... well it's all nice and stuff. What makes me wonder though **roclin** hasn't posted the actual problem in any one of the posts. I'm get the feeling we are dragged by our noses on purpose.

Just to be clear **roclin**... What does (or doesn't?) your PC do? And what you expect it to do?
[quote=roclin]I must get it from some where after I reinstall. It shows up after a while.I went to my site at [www.weddingsbycharles.piczo.com](www.weddingsbycharles.piczo.com) and in my back office nothing works for me to redesign my site. Once in a while my screen goes haywire with many colores and stops. [/quote]
[quote=roclin]It's like changing the channel on the old TV's along with missing info on my webpages in the back office. [/quote]

It sounds like he is getting a corrupted screen.
either due to a video driver bug, or flash bug...etc

@roclin: What version of Ubuntu are you using?
Have you been using the same version for the past 2 years or did you recently upgrade?

---

### Post by JoshuaRL on 2009-03-10
> **kidux said:**
> K, I'm gonna call BS on him with you here. Just saw the 2 year remark, nevermind what I said earlier, lol!

I'm leaning this way too.  If you ran for 2 years and are hosting your own website, then I find it a little hard to believe you wouldn't know how to troubleshoot this, at least to the point of being able to ask the right questions.

@ the OP:
That said, I think we should be willing to give you the benefit of the doubt.  Please post your graphics card, and when you go into System->Administration->Hardware Drivers do you see any proprietary drivers available?

---

### Post by chriskin on 2009-03-10
sorry for intruding in this thread so many posts after it started but...is it my idea or is the o.p. just lying? i mean come on now, 2 years and he doesn't know anything?

he either has no will to listen, like it seems in his responses, or he is a brand new user with the crazy windows mentality of "aaaaaaaaaaaa everything is dying, scream and it will get fixed by another" (or both)

---

### Post by hatten on 2009-03-10
whoa, a soap opera. Subscribing!
Will be interesting to see what the actual problems are, if there are any ^^

---

### Post by kansasnoob on 2009-03-10
I disagree with the negative comments. I suspect an end-user with something that was set up by someone else!

I further suspect that the pop-up ad created for his/her own site is a large part of the problem.

Many, many end-users have no clue what's wrong when something goes wrong! They just get mad and bang their heads on the keyboard.

Especially if it interferes with their ability to make money! And from what the OP said here I think this is their own site!

Check it out:

[http://www.weddingsbycharles.piczo.com/?cr=1](http://www.weddingsbycharles.piczo.com/?cr=1)

Looks good to me!

But laden with ads like:

[http://my.internetgiftpromotions.com/SplashPage.aspx?g=2ce6c5d8ab7648dcbe71391359c5839b&c=212&s=D371360&se=02](http://my.internetgiftpromotions.com/SplashPage.aspx?g=2ce6c5d8ab7648dcbe71391359c5839b&c=212&s=D371360&se=02)

If they're not ads the website owner authorized then he/she has a problem!

It seems like every time I click on it I get a new ad!

So, in the OP's mind it's Ubuntu's fault!

---

### Post by scottuss on 2009-03-10
> **kansasnoob said:**
> I disagree with the negative comments. I suspect an end-user with something that was set up by someone else!

I further suspect that the pop-up ad created for his/her own site is a large part of the problem.

Many, many end-users have no clue what's wrong when something goes wrong! They just get mad and bang their heads on the keyboard.

Especially if it interferes with their ability to make money! And from what the OP said here I think this is their own site!

Check it out:

[http://www.weddingsbycharles.piczo.com/?cr=1](http://www.weddingsbycharles.piczo.com/?cr=1)

Looks good to me!

But laden with ads like:

[http://my.internetgiftpromotions.com/SplashPage.aspx?g=2ce6c5d8ab7648dcbe71391359c5839b&c=212&s=D371360&se=02](http://my.internetgiftpromotions.com/SplashPage.aspx?g=2ce6c5d8ab7648dcbe71391359c5839b&c=212&s=D371360&se=02)

If they're not ads the website owner authorized then he/she has a problem!

It seems like every time I click on it I get a new ad!

So, in the OP's mind it's Ubuntu's fault!

Another cynical remark from me here... if the site is laden with ads, maybe this post was to get a few hits? He's been using Ubuntu for 2 years, knows that if he posts a thread title with the word "virus" in it he will get lots of attention and has a site with ads on. Far fetched? Maybe.

---

### Post by Bölvaður on 2009-03-10
Ok I may be the first one here to actually go deeper into the matter to analyze the problem.

> **roclin said:**
> 
It shows up after a while

Lets label this as "#1 : Description".
Can you provide us with as detailed description as possible (may be hard in some situation, but we take any information at all).

#2 : Time
After how long approximately does it take from when you turn on the pc until the problem starts.


> **roclin said:**
> 
I went to my site at [www.weddingsbycharles.piczo.com](www.weddingsbycharles.piczo.com) and in my back office nothing works for me to redesign my site.

#3 : Editing website
I am not familiar to how Piczo works (been looking at their site and screenshots of the editor to try figure out how they made it) and I have no idea why it wouldnt work.
When you are in the editor and you right click with your mouse on the editor, do you see "About Adobe Flash Player 10..."?


> **roclin said:**
> 
Once in a while my screen goes haywire with many colores and stops.
#4 : Display
For this we need to know what screencard you have got.
It can be done in the following way:
Application &#8594; Accessories &#8594; Terminal  and type: lspci
Copy the text that is shown in your post here. When you have copied the text into your post highlight the text with your mouse and press a button with the # sign on it (it will make [[SIZE="1"] [/SIZE]CODE][/[SIZE="1"] [/SIZE]CODE] around this text to identify it as a output from a command)

Then do the same to display the content of your xorg.conf file (it will tell us how your computer is controlling the graphical card)

Application &#8594; Accessories &#8594; Terminal  and type:* gedit /etc/X11/xorg.conf*
Also copy this text into your post, highlight it and press the # button again.


> **roclin said:**
> I must get it from some where after I reinstall.
This indicates hardware problem (computer part) or incomparability between the OS and the hardware. I can assure you that viruses in linux will behave in a different manner so your computer is very likely completely safe from them :)

I might be missing something but this is a good start to solve your problems.

---

### Post by Bölvaður on 2009-03-10
> **scottuss said:**
> Far fetched? Maybe.

Yes it is. The webservice that is hosting his website is called Piczo and by default they seem to put ads on the user's websites (which is the most common practice in the website hosting after paying high fees for storage).
According to other websites it is a very secure social network.

I really like roclin after reading his/her posts. It is very difficult for most people to get into computers like we have done and I feel it is our responsibility to help out if there is no one on his/her end that can help.

with that said I have an idea.

**Roclin**, are you able to contact some one that lives close to you that knows Linux? It is often easier to fix problems when facing the computer.

---

### Post by kansasnoob on 2009-03-10
> **Bölvaður said:**
> Yes it is. The webservice that is hosting his website is called Piczo and by default they seem to put ads on the user's websites (which is the most common practice in the website hosting after paying high fees for storage).
According to other websites it is a very secure social network.

I really like roclin after reading his/her posts. It is very difficult for most people to get into computers like we have done and I feel it is our responsibility to help out if there is no one on his/her end that can help.

with that said I have an idea.

**Roclin**, are you able to contact some one that lives close to you that knows Linux? It is often easier to fix problems when facing the computer.

+1! I don't think the OP was being dishonest or nefarious. I think something just went wrong! He/she mentioned multiple computers!

I think it was an, "oh crap, I can't operate my business without puters moment"! So they reached out for help, with an unhelpful amount of frustration. Been there and done that!

---

### Post by bodhi.zazen on 2009-03-10
I have been watching this thread and I think it is time to close it now.

@roclin: If you feel you still need assistance, please start a new thread and please be sure to use a descriptive title and a better description of your problem.

---

