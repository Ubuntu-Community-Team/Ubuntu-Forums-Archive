---
title: "Skype problems - or whey Ubuntu still has a long way to go"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-18
Don't get me wrong...I am a BIG fan of Ubuntu. I have been using it for almost a year. It is ideal for somebody like me who has geeky tendencies......BUT....

I convinced my wife to move to Ubuntu...that worked great. Now she wants Skype on her PC. She is on 8.10. I downloaded Skype using Synaptic..red face...it does not work...the Log In Screen has the Sign In button greyed out...and the options only gives one tab and that is the advanced one.

I will download it from the website I said to her....it is probably a problem with the repository....what do you know same problem. My wife was not amused. She had set it up herself in Windows.

So, anybody know what is wrong with the Skype program that I have downloaded. I just cannot get it to work. Skype works fine on my machine.

It does not really matter if the problem is Skype or Ubuntu, people are going to see it a big barrier...it just reinforces the geeky nature of Linux and why it is not for ordinary folk. The most common application really need to work right out of the box for people to be convinced that it is worth moving over to Ubuntu.

Help!

---

### Post by jpoRS on 2009-03-18
Pidgin has Skype, does that work for you or do you have the same grey-out issue?

wheyUbuntu does have a long way to go.  Though I hear Curd will be ready for beta soon [/bad joke]

jim

---

### Post by kaixi on 2009-03-18
I tried Skype 2.0 with video call support on my Dell laptop (running Intrepid). The interface was very simple but everything worked fine.

I pulled the package from [www.skype.com/download/skype/linux/](www.skype.com/download/skype/linux/)

---

### Post by dunbrokin on 2009-03-18
> **kaixi said:**
> I tried Skype 2.0 with video call support on my Dell laptop (running Intrepid). The interface was very simple but everything worked fine.

I pulled the package from [www.skype.com/download/skype/linux/](www.skype.com/download/skype/linux/)

That is where I got it from....it does download...but as I said, the sign in is greyed out for some reason.

---

### Post by dunbrokin on 2009-03-18
> **jpoRS said:**
> Pidgin has Skype, does that work for you or do you have the same grey-out issue?


jim

Her machine does not have Skype in the drop down menu....nor does mine...it has lots of stuff but not Skype...unless it is called something else.

---

### Post by desperado665 on 2009-03-18
When I first start Skype, the sign in button is grayed out, but after inputting a few characters into the password box, it becomes available and works fine. Also be sure to set your playback and capture devices to ALSA, as Skype has issues with PulseAudio.

---

### Post by jflaker on 2009-03-18
Ubuntu is more than ready for Prime-Time.

When you reference "Hey, there is no programs/support for X-ThirdPary-service/hardware", that isn't the fault of Linux, that is the fault of the service provider or hardware manufacturer who refuses to see or refuses to acknowledge the existence of other than Windows.

In the long run, it hurts the service provider or hardware manufacturer as their sales fall off because of lack of support.

just my 2 cents.

---

### Post by dunbrokin on 2009-03-18
It does not stop being greyed out no matter how many characters you enter.

All capture devises etc set to ALSA....

---

### Post by dunbrokin on 2009-03-18
> **jflaker said:**
> Ubuntu is more than ready for Prime-Time.

When you reference "Hey, there is no programs/support for X-ThirdPary-service/hardware", that isn't the fault of Linux, that is the fault of the service provider or hardware manufacturer who refuses to see or refuses to acknowledge the existence of other than Windows.

In the long run, it hurts the service provider or hardware manufacturer as their sales fall off because of lack of support.

just my 2 cents.

Like I say, it does not matter whose fault it is...the general public just sees a problem...and they will take it on....geeky people will...that is the difference....this problem really brought it home to me. In theory you are right Ubuntu is ready and capable...but in practice it is not.

---

### Post by anewguy on 2009-03-18
Since the last time I installed Skype I have a different computer so I'm using an old PIII system for Ubuntu.  I am running 8.10.  I tried installing via Synaptic, but it came up with an error box about several things needing to be installed (a lot started with libv4) but said these packages were unstable and would not be installed, so it wouldn't install Skype.

I then followed the download to Skype itself and downloaded the Linux version for Ubuntu - noting that it did NOT go up to 8.10.  Upon trying to use package manager to install it, a box came up saying "An older version is available in a software channel.  generally you are recommended to install the version from the software channel, since it is usually better supported.".  I then went ahead with the install of what was downloaded, not some other version.  It had to download 3 packages - libausio2, libqt4-core and another that I missed before it closed the window.  I seem to remember libqt4-core being one of the packages that Synaptic did not want to install saying it was instable.  At any rate, it did install, and Skype shows under Applications/Internet.  I started it and it came right up with the login screen and let me login.  I don't have speakers or a microphone or a headset hooked up to that computer, so I then removed Skype.

Not sure why it's not working for you - when you tried via Synaptic did it give you the same error box?  When you installed from the direct download, did it tell you to use a different version from a software channel?  Did you use such a version or continue on with the regular install?

I would suggest you remove Skype (sudo apt-get remove skype  followed by sudo apt-get autoremove).

Then re-download the package from Skype - be sure to select the Ubuntu version even though it only goes up through 8.04.  Then double-click on the package to install it.

Let us know what happens.

dave :)

---

### Post by desperado665 on 2009-03-18
I'm using 8.10. I installed Skype v.2 using Ubuntu Tweak and have no issues what-so-ever using it.

---

### Post by ashwat on 2009-03-18
> **desperado665 said:**
> I'm using 8.10. I installed Skype v.2 using Ubuntu Tweak and have no issues what-so-ever using it.

I do understand your pleasure that Skype works for you but it is these kind of replies that put newbies off. What they are searching are for someone to understand their problem and try to find a solution that they are able to comprehend and execute as required, not a " Works for me buddy, you must be a loser not to have it work" type one liners. The guy is probably all irritated trying to sort it out and wants to just smash the monitor. A little bit of "putting yourself in his shoes" type thinking would do a lot of help. 

And as for the problem, I had that happen to me when I first installed from deb from the website. I removed it and tried again and this time it seemed to work. Since I am a newbie myself, I do not exactly know what fixed it; all I have to say is that, it got fixed.

---

### Post by stchman on 2009-03-18
> **dunbrokin said:**
> Don't get me wrong...I am a BIG fan of Ubuntu. I have been using it for almost a year. It is ideal for somebody like me who has geeky tendencies......BUT....

I convinced my wife to move to Ubuntu...that worked great. Now she wants Skype on her PC. She is on 8.10. I downloaded Skype using Synaptic..red face...it does not work...the Log In Screen has the Sign In button greyed out...and the options only gives one tab and that is the advanced one.

I will download it from the website I said to her....it is probably a problem with the repository....what do you know same problem. My wife was not amused. She had set it up herself in Windows.

So, anybody know what is wrong with the Skype program that I have downloaded. I just cannot get it to work. Skype works fine on my machine.

It does not really matter if the problem is Skype or Ubuntu, people are going to see it a big barrier...it just reinforces the geeky nature of Linux and why it is not for ordinary folk. The most common application really need to work right out of the box for people to be convinced that it is worth moving over to Ubuntu.

Help!

So you have made this judgment based solely on one program?  Skype?

I guess we can say the same thing about Windows as it won't run K3b.  Big barrier that needs to be overcome.

FYI, Skype is not in the Ubuntu repositories.

You can get the latest Linux version from Skype website or Medibuntu.

---

### Post by stchman on 2009-03-18
> **dunbrokin said:**
> Like I say, it does not matter whose fault it is...the general public just sees a problem...and they will take it on....geeky people will...that is the difference....this problem really brought it home to me. In theory you are right Ubuntu is ready and capable...but in practice it is not.

So we can say both Windows and Ubutnu have a long way to go as they can't run the entire iLife suite?

No matter that the apps were written for OS X, the public will see it as a problem.

---

### Post by desperado665 on 2009-03-18
> **ashwat said:**
> I do understand your pleasure that Skype works for you but it is these kind of replies that put newbies off. What they are searching are for someone to understand their problem and try to find a solution that they are able to comprehend and execute as required, not a " Works for me buddy, you must be a loser not to have it work" type one liners. The guy is probably all irritated trying to sort it out and wants to just smash the monitor. A little bit of "putting yourself in his shoes" type thinking would do a lot of help. 

Ok, I apologize for the post sounding a little "stand-offish", but if you look at my other response in this thread, you would see that I was only making comment as to how I got mine to work and nothing more. We are all here to impart what knowledge we have to those that seek answers. I was only trying to be helpful.

---

### Post by ashwat on 2009-03-18
> **desperado665 said:**
> Ok, I apologize for the post sounding a little "stand-offish", but if you look at my other response in this thread, you would see that I was only making comment as to how I got mine to work and nothing more.

No offense meant mate. It is just that I am seeing way too many responses in a similar dismissive tone. Either that or you need to switch over to a native linux app, forget your roots start afresh type mumbojumbo. Help us through our baby steps and we shall be ever grateful to the community. As it is, it is a steep learning curve for most, makes no sense in responding in such a way.

---

### Post by dndrich on 2009-03-18
I am a bit of a newbie, but I run Skype no problem on a Dell Mini 9 with Ubuntu 8.10.  I would try removing all vestiges of what you have installed so far.  Make sure no hidden files exist in your home directory.  Use control-h to find those files.  Now, Skype is definitely in the repositories, but it is in the medibuntu repositories.  There are numerous threads on how to install medibuntu repositories.  Google psychocats linux and you will get a really nice site about how to do that.  Then install via the repositories.  It is up to version 2 which does work well with full video support for a web cam.  Next, configure skype for audio.  There is a good thread on that at [http://www.ubuntumini.com/2009/01/skype-on-dell-mini-9.html](http://www.ubuntumini.com/2009/01/skype-on-dell-mini-9.html)  This also has instructions on medibuntu.  Should work well.  See if this helps.

---

### Post by Miljet on 2009-03-18
I'm sure that you will find plenty of help in these forums. You start out belittling Ubuntu in the title, and then snap at the people who respond to your post.

Perhaps when someone states that the program is working on their machine, they are really offering to compare configuration files to find the problem.

---

### Post by HermanAB on 2009-03-18
When all else fails, download the Static Linked version from Skype.  It is completely self contained and works purrrfectly.

Cheers,

Herman

---

### Post by dunbrokin on 2009-03-18
> **HermanAB said:**
> When all else fails, download the Static Linked version from Skype.  It is completely self contained and works purrrfectly.

Cheers,

Herman

I did and it didn't....which is why I commented that Ubuntu (despite the numerous protests here) is not ready for the main stream....I can follow all these instructions and get it to work...and so can most of the people who commented here....but my wife cannot do that...nor has she any interest in doing that (again unlike most people on this forum)..and, at the end of the day, she (and people like her) are the ones who will determine if Ubuntu is ready for the mainstream....not the rest of us.

---

### Post by dunbrokin on 2009-03-18
> **Miljet said:**
> I'm sure that you will find plenty of help in these forums. You start out belittling Ubuntu in the title, and then snap at the people who respond to your post.

Perhaps when someone states that the program is working on their machine, they are really offering to compare configuration files to find the problem.

Dude, I did not snap anybody, nor belittle Ubuntu.....check the thread.

---

### Post by dunbrokin on 2009-03-18
> **stchman said:**
> So you have made this judgment based solely on one program?  Skype?

I guess we can say the same thing about Windows as it won't run K3b.  Big barrier that needs to be overcome.

FYI, Skype is not in the Ubuntu repositories.

You can get the latest Linux version from Skype website or Medibuntu.

Why all this religious zeal? Read what I said. My wife (and people like her) are the ones making these decisions...not you or I....we are just on the sidelines cheering for our team. But if we attack everybody who makes a comment like "our team needs more training to beat the top team" as being a traitor then we have already lost. We need a more positive attitude to face up the problems we have...and we need to work hard at helping people to get started with the "must have" applications. Deprecating comments and non specific help comments only help to reinforce the idea that Ubuntu is for nuts and geeks.

Negative comments are helpful in showing us where our weaknesses are...attack the weaknesses and not the messenger...What are people like my wife etc going to think about Ubuntu etc if they see threads like this? Think before you vent...and give specific helpful instructions...otherwise you have no place on a forum like this...you just help push our cause backwards (sorry, stchman, that was not directed at you personally...but at the general attitude you find amongst the zealots)

---

### Post by dunbrokin on 2009-03-18
> **anewguy said:**
> 

I then followed the download to Skype itself and downloaded the Linux version for Ubuntu - noting that it did NOT go up to 8.10.  Upon trying to use package manager to install it, a box came up saying "An older version is available in a software channel.  generally you are recommended to install the version from the software channel, since it is usually better supported.".  I then went ahead with the install of what was downloaded, not some other version.  It had to download 3 packages - libausio2, libqt4-core and another that I missed before it closed the window.  

Thanks Dave, very useful advice...however it did not work I fully removed Skype as suggested and then installed it via Tweak, as suggested elsewhere, I did not have any problems with Synaptic ...other than libausio2 is not in the repository.

In short, no further forward...still greyed out sign in...and still only one option tab as before.

---

### Post by presence1960 on 2009-03-18
> **dunbrokin said:**
> Why all this religious zeal? Read what I said. My wife (and people like her) are the ones making these decisions...not you or I....we are just on the sidelines cheering for our team. But if we attack everybody who makes a comment like "our team needs more training to beat the top team" as being a traitor then we have already lost. We need a more positive attitude to face up the problems we have...and we need to work hard at helping people to get started with the "must have" applications. Deprecating comments and non specific help comments only help to reinforce the idea that Ubuntu is for nuts and geeks.

Negative comments are helpful in showing us where our weaknesses are...attack the weaknesses and not the messenger...What are people like my wife etc going to think about Ubuntu etc if they see threads like this? Think before you vent...and give specific helpful instructions...otherwise you have no place on a forum like this...you just help push our cause backwards (sorry, stchman, that was not directed at you personally...but at the general attitude you find amongst the zealots)

It does not matter how many people use Linux. That is not the reason it exists. It (for the most part) is not a commercial venture. As such it doesn't need to be in competition with anyone or anything. If you are like me - then **_just use Linux_**and be open to explain or help **_only when asked_**. That is the best thing I can do for Linux, it doesn't need me defending or promoting it.

---

### Post by LowSky on 2009-03-18
Hey stop bickering! Fighting solves nothing.

Ok....  I just installed Skype on my Ubuntu 64 bit machine using the medibuntu repos. Works fine. 
Only issue was setting sound, I just set it to pulse (I assume pulseaudio) and it works just fine.

No issues creating or using a screen name, nothing was greyed out.

---

### Post by dunbrokin on 2009-03-18
> **LowSky said:**
> Hey stop bickering! Fighting solves nothing.

Ok....  I just installed Skype on my Ubuntu 64 bit machine using the medibuntu repos. Works fine. 
Only issue was setting sound, I just set it to pulse (I assume pulseaudio) and it works just fine.

No issues creating or using a screen name, nothing was greyed out.

Sound advice...and thanks for that...but unfortunately it does not help me...

---

### Post by LowSky on 2009-03-18
clearly it doesn't but As Im saying a recent install and it works correctly, so clearly its not the current package but some other setting causing the issue oon your wifes machine.

did you try to completly remove skype and reinstall it. using a different method?

---

### Post by dunbrokin on 2009-03-18
> **LowSky said:**
> clearly it doesn't but As Im saying a recent install and it works correctly, so clearly its not the current package but some other setting causing the issue oon your wifes machine.

did you try to completly remove skype and reinstall it. using a different method?

Agreed, and I do appreciate the fact that you tried as this does rule out one avenue of approach - so thank you again.

Clearly, as you point out, it is a setting on my wife's machine...I did try twice removing and reinstalling by different methods ....but still the same problem. Thanks for your concern and interest.

---

### Post by dunbrokin on 2009-03-18
> **presence1960 said:**
> It does not matter how many people use Linux. That is not the reason it exists. It (for the most part) is not a commercial venture. As such it doesn't need to be in competition with anyone or anything. If you are like me - then **_just use Linux_**and be open to explain or help **_only when asked_**. That is the best thing I can do for Linux, it doesn't need me defending or promoting it.

A very sane and philosophical view....but one, I suspect, that not too many adhere to. Fortunately or unfortunately, depending on your view, we humans do like to convince others to join our team. Religion has no commercial purpose also, but it does not stop people wanting to recruit others. As you say, it does not really matter how many are saved as long as you are saved...but not many see it that way....but thank you for that sanity check.

---

### Post by cariboo on 2009-03-18
Have you tried installing Skype in a terminal using:

```
dpkg -i skype-debian_2.0.0.72-1_i386.deb
```

To see if there are any error messages. You will have to change the version to your own of course.

I would suggest you have a look at [this]("http:///help.ubuntu.com/community/Skype") page, as it may help.

Jim

---

### Post by Djalmahal on 2009-03-18
Hi, I had problems with skype I removed the skype from the skype homepage and installed skype-common and skype static from the medibuntu repositories, just google it. I did that on my laptop and on some of my friends when i put ubuntu on. In Skype itself on my computer default works for everything under options>sound devices but on the last install only pulseaudio worked.
Skype can be tricky but I always got it to work. The Medibuntu repositories have some proprietary codecs in them, but it seems to work, hope that helps your wife.
Andreas

---

### Post by anewguy on 2009-03-19
Does it let you enter in a username and password but leave the button greyed out?  Have you set up an account with Skype?

Dave :)

EDIT: While you are having this trouble with Skype, select applications/accessories/take screen shot and click the grag the whole desktop button and then Take Screenshot.  When you have that post it back here with the "image" button (it looks like a yellow box with a mountain and the sun in it).

---

### Post by gandaran on 2009-03-19
dunbrokin
skype uses qt4 libs (KDE) so it mite not always work perfectly in a gnome environment, for gnome users it's best to use the self contained static version, it integrates a little better, the static version is in the repositories if you add the medibuntu repository, open synaptic search for the static version and install this one not the other, also the one you download from skype is not the static version.

---

### Post by dunbrokin on 2009-03-19
> **cariboo907 said:**
> Have you tried installing Skype in a terminal using:

```
dpkg -i skype-debian_2.0.0.72-1_i386.deb
```

To see if there are any error messages. You will have to change the version to your own of course.


dpkg: error processing skype-debian_2.0.0.72-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-debian_2.0.0.72-1_i386.deb

---

### Post by dunbrokin on 2009-03-19
Thanks and apologies to all.....problems solved....ahem!....user error would you believe...](*,)

---

### Post by Helios1276 on 2009-03-19
> **dunbrokin said:**
> Thanks and apologies to all.....problems solved....ahem!....user error would you believe...](*,)

Skype problems - or why dunbrokin has a long way to go?;)

---

### Post by issih on 2009-03-19
First of all, if you start out saying that X isn't suitable for mainstream use because Y doesn't work, then people responding saying that Y does work is a perfectly acceptable response. As it refutes your implication that X is broken, and further suggest that something else is wrong in your case, not just straight software incompatibility.

Secondly, Y not working on one specific machine can be down to a million tiny things, other apps installed, a loose capacitor on the motherboard, a corrupt bios, a corrupt file, almost anything. Something not working on one specific machine can happen to any OS at any time, it means precisely nothing, except that you are unlucky. When it happens on nearly all machines, or all machines with a certain bit of software installed, then it is a problem with X.

Thirdly, often the problem is, as eventually found here, something simple, unrelated and quite often [pebcak]("http://en.wikipedia.org/wiki/PEBKAC"). I strongly advocate not attacking new users, and doing the best we can to help them on their terms, but the attitude adjustment here needs to happen on both sides. Linux has to be learnt on its terms, it isn't windows, and thinking it is will only slow down your progress and make you frustrated.

Forthly, advocating starting fresh and using linux solutions wherever possible is just sound advice, native programs are far easier to install, manage and are much less likely to have buggy features. This is linux, you will be happier if you do everything you can NOT to use windows programs. If there isn't a solution that will do what you need, then alright try and use wine, but please don't use it as a first port of call as you are not being fair. You can't judge Linux on how well it can run windows programs, judge it on its own terms.

Anyway, I'm glad you got it sorted out.

Hope that helps

---

### Post by dunbrokin on 2009-03-19
> **Helios1276 said:**
> Skype problems - or why dunbrokin has a long way to go?;)

Can't argue with that......and won't argue if we beat Wales.

---

### Post by dunbrokin on 2009-03-19
> **issih said:**
> First of all, if you start out saying that X isn't suitable for mainstream use because Y doesn't work, then people responding saying that Y does work is a perfectly acceptable response. As it refutes your implication that X is broken, and further suggest that something else is wrong in your case, not just straight software incompatibility.

Secondly, Y not working on one specific machine can be down to a million tiny things, other apps installed, a loose capacitor on the motherboard, a corrupt bios, a corrupt file, almost anything. Something not working on one specific machine can happen to any OS at any time, it means precisely nothing, except that you are unlucky. When it happens on nearly all machines, or all machines with a certain bit of software installed, then it is a problem with X.

Thirdly, often the problem is, as eventually found here, something simple, unrelated and quite often [pebcak]("http://en.wikipedia.org/wiki/PEBKAC"). I strongly advocate not attacking new users, and doing the best we can to help them on their terms, but the attitude adjustment here needs to happen on both sides. Linux has to be learnt on its terms, it isn't windows, and thinking it is will only slow down your progress and make you frustrated.

Forthly, advocating starting fresh and using linux solutions wherever possible is just sound advice, native programs are far easier to install, manage and are much less likely to have buggy features. This is linux, you will be happier if you do everything you can NOT to use windows programs. If there isn't a solution that will do what you need, then alright try and use wine, but please don't use it as a first port of call as you are not being fair. You can't judge Linux on how well it can run windows programs, judge it on its own terms.

Anyway, I'm glad you got it sorted out.

Hope that helps

I stand chastised...

---

### Post by issih on 2009-03-19
Chastised, hopefully not, just a bit more aware. No malice was meant in what I said. For every linux zealot that jumps to slam a new user unfairly there is a new user missing the point and blaming it on linux's lack of "user friendly" features, both sides need to stop looking for someone to blame, and stop antagonising each other.

The criticism, such as it was, is not just aimed at you, its aimed at many others, and (as you can see if you look at my post history) I am just as likely to criticise those who go looking to slam people that dare criticise linux.

Both sides need to try not to get so wound up, unfortunately, at the moment there appears to be a trend towards less tolerance, on both sides, which is sad, and should be fought against, that is all :)

Enjoy your skypiness

---

### Post by digital-daniel on 2009-03-21
I'd like some help on a similar problem.

I've got my webcam working in Cheese but in Skype it has horrible lines going through it. When I reduce the resolution to 320x240 in Cheese the lines appear there. Would it be possible that skype brings the resolution down and if I could increase it I'd have a better picture. Or should I try and find a different webcam driver.

Newbie: using Ibex, 

 lsusb
Bus 004 Device 002: ID 04e8:3272 Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:8519 OmniVision Technologies, Inc. OV519 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by tom56 on 2009-03-21
> **digital-daniel said:**
> I'd like some help on a similar problem.

I've got my webcam working in Cheese but in Skype it has horrible lines going through it. When I reduce the resolution to 320x240 in Cheese the lines appear there. Would it be possible that skype brings the resolution down and if I could increase it I'd have a better picture. Or should I try and find a different webcam driver.

Newbie: using Ibex, 

 lsusb
Bus 004 Device 002: ID 04e8:3272 Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:8519 OmniVision Technologies, Inc. OV519 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Start your own thread - your problem might not get noticed here. I personally can't help, but hopefully someone else can.

---

### Post by digital-daniel on 2009-03-21
Okay, thanks

---

