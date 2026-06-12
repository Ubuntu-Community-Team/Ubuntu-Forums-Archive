---
title: "video chat on ubuntu"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by geekyhawkes on 2009-04-25
Im running 9.04 (which is excellent) but the only thing im missing since windows is msn & audio/video.  pidgin doesnt support video chat and for some reason amsn dies everytime i try to sign in.  msn wont install under wine so i guess im asking what are my options?

Thanks for any help

---

### Post by mangurt on 2009-04-25
I don't think there's that many options for video chat with linux.  The only one I know of is skype.

---

### Post by spiderbatdad on 2009-04-25
gyachi for yahoo. Also isnt there emesene in synaptic package manager? I have not tried emesene. Gyachi works very well.

Since Intrepid there has been a problem with the libv4l-0 It was necessary for many of us to use a special command to get video support programs to run. The command is one of the following:```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so amsn
or
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so amsn
```run that in your terminal. If it works for you, you can use insructions here to create a launcher for the command: [http://ubuntuforums.org/showthread.php?t=1026188](http://ubuntuforums.org/showthread.php?t=1026188)

---

### Post by geekyhawkes on 2009-04-25
Thanks for the terminal tip, but sadly everytime i click login from amsn it crashed out and the terminal window reports back segmentation fault.  Can anyone give me anymore tips, or a clue how to fix the segmentation fault?

---

### Post by NightwishFan on 2009-04-25
I think kopete supports video chat...

As for segment fault that is serious business. Try to reinstall it.

I think there are other MSN programs, search synaptic perhaps.

---

### Post by shagy on 2009-04-25
You could try [Ekiga.]("http://www.gnomemeeting.org/") I once tried it but was with an older version of Ubuntu but could not handle it. I think I will talk to a friend, who has Ubuntu, to see if I you can get it working. Skype works for me because I have a cetified by Skype headphone. Maybe it will work with other headphones too.

---

### Post by llamabr on 2009-04-25
> **mangurt said:**
> I don't think there's that many options for video chat with linux.  The only one I know of is skype.

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

Scroll down to #5 in the don't section.

To the OP, of course this is possible.  Which do you want, yahoo, im, msn, icq?

---

### Post by geekyhawkes on 2009-04-25
msn is what i am after.  I have tried installing amsn a couple of times and on 2 machines but the same happens, it must not work with 9.04 is all i can think...

---

### Post by llamabr on 2009-04-25
I just installed it just fine.  What sort of machine do you have?  And how are you installing it?  I just did so with apt, and it installed fine.

---

### Post by geekyhawkes on 2009-04-29
Sorry, i should have been more clear, i want to video with other msn users.  I have tried running msn 7.5 installer under wine with no luck and amsn keeps crashing out with the segmentation fault mentioned above.  From what i can see emsn doesnt support video either?

---

### Post by Judgegeo on 2009-04-29
> **geekyhawkes said:**
> Sorry, i should have been more clear, i want to video with other msn users.  I have tried running msn 7.5 installer under wine with no luck and amsn keeps crashing out with the segmentation fault mentioned above.  From what i can see emsn doesnt support video either?

aMSN works under 9.04 fine. You could try virtulization, or check [http://appdb.winehq.org/](http://appdb.winehq.org/).

---

### Post by 3rdalbum on 2009-04-29
> **NightwishFan said:**
> I think kopete supports video chat...

It supports video, but not audio.

> **NightwishFan said:**
> As for segment fault that is serious business. Try to reinstall it.

1. Segmentation Fault really just means "the program crashed".

2. Reinstalling software does nothing; it's not like the program binary gets wear and tear from use. In some cases, deleting the program's user settings in ~/.*programname* can help, but I don't think that will solve the OP's problem either.

---

### Post by Kosimo on 2009-04-29
aMSN is an excellent program (a bit ugly) which actually support almost all MSN features, including videoconference.

Give it a try! Is on official Ubuntu repositories

---

### Post by NightwishFan on 2009-04-29
> **3rdalbum said:**
> It supports video, but not audio.



1. Segmentation Fault really just means "the program crashed".

2. Reinstalling software does nothing; it's not like the program binary gets wear and tear from use. In some cases, deleting the program's user settings in ~/.*programname* can help, but I don't think that will solve the OP's problem either.

1. I know that.

2. I was offering a suggestion. I thank you for trying to inform me, but I do not need corrected. I meant perhaps if it seg-faulted he might have other problems, or an bad installation cd.

---

### Post by geekyhawkes on 2009-04-29
Ive tried amsn but it keeps crashing, if someone can give me a clue how to stop this then il press on!   Virtualbox is an issue but it seems overkill for what i am trying to achieve.  

As far as wine, i have not been able to get a working version on msn installed under wine so any help would be well received.

Thanks guys..

---

### Post by NightwishFan on 2009-04-30
I am not really qualified to help debug amsn. If I had some more spare time I could try in any case.

Try running amsn from a terminal.

The command should be amsn, if not simple use the tab key to autocomplete.

The terminal might state why the error is occurring.

---

### Post by geekyhawkes on 2009-05-02
Thanks for the help.  I have just reinstalled amsn and ran it from the terminal.  The program runs fine until i try to connect or click auto update.  Then it "crashes" with the terminal reporting the segmentation fault.  

I can access all of the menus fine offline, and the program seems stable but the issue seems to be whenever i ask it to contact the internet.

Any thoughts?

---

### Post by geekyhawkes on 2009-05-02
Not sure if this means anything to someone, but i tried amsn -help from termnial and had the following reported back

 --:        Pass all remaining arguments through to script
    (processing arguments in argv variable)
    invoked from within
"load /usr/lib/libtk8.5.so.0 Tk"
    ("package ifneeded Tk 8.5.6" script)
    invoked from within
"package require Tk"
    (file "/usr/bin/amsn" line 48)


This might mean nothing, im still getting to grips with ubuntu

---

### Post by NightwishFan on 2009-05-02
I wish I could help you more. I am bumping this in the hope a guru will spot you.

---

### Post by Claus7 on 2009-05-02
Hello,

amsn 0.97.2 is supposed to be stable, yet it lacks many good features amsn for linux should have. Try this:
[http://www.amsn-project.net/forums/viewtopic.php?t=6448](http://www.amsn-project.net/forums/viewtopic.php?t=6448)

and see if it is working. I have no stable sound clips, I cannot call someone, someone else can call me, and I can hear sound from them, they cannot hear me. Also I cannot adjust the camera settings as I was able to do in previous versions. Have in mind that one week ago I wasn't able to hear anyone, so I think that in the final version of 0.98 these will be fixed. It's high time this is fully supported, because it is under development for a long time now.

I would avoid 0.97 versions even if they are in the repos. They are far inferior than their 0.98 counterpart and according to KaKaRoTo 0.98 is unstable only in the new features. As for ugliness that someone mentioned, I think that it is more eye candy even from the original msn! They have done a very nice job, and installing it from the link I provide you, you will have a lot of options to customize it as you like. 

Well done to amsn devs and the guys bringing the svn version one click away to ubuntu. Have in mind that it is under development so till the final release it might be a little bit buggy. 

I would not think of using another disto for msn. And jaunty has the right tools that it can compile amsn with all the arsenal available.

Regards!

---

### Post by geekyhawkes on 2009-05-04
just installed 0.98 amsn and no different!  Any way i can find out what is going on with it?  I do have an xp VM installed but it is way overkill to launch xp just for a working video version of MSN!

---

### Post by Claus7 on 2009-05-04
Hello,

have you removed the previous installation before doing so, in order to avoid conflicts with previous versions? Other than that I can advice you to see the logs that amsn produces, yet the amsn forum might be more ideal about that. You can open a kind of terminal, which gives information about amsn, yet I had come across with that years ago. Do you face any problems with other applications or is it only amsn?

Regards!

---

### Post by geekyhawkes on 2009-05-06
Yes removed previous version and the settings folder @home.  Everything else is working fine, just amsn that crashes out.  Wierd.  Thanks for the help i will do a bit more research at the amsn forum.

---

### Post by castudil on 2009-05-07
Hey geekyhawkes, maybe this info is helpful to you.

This week my wife was complaining that amsn didn't work on her machine. 

The problem:

The specific problem was not a crash, but the program was stalled when she wanted to connect to her account.

First attempt:

I tried to uninstall it and reinstall it via apt-get, but this didn't work.


My solution: 

Below the login and password boxes appear a text in blue that says something like "remove account" or "delete profile". I delete the account setting and re-entered and voila! amsn working again. don't know what caused the problem though.

---

