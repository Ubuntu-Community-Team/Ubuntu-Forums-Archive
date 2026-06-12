---
title: "Totally bugged with Ubuntu: It sucks when u dual boot"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by bhatGanesh on 2009-01-11
Hi,
I always used VMware to install any linux os. There it used to work fine. I thought of installing it on my comp directly.
I have installed the Ubuntu ultimate- dual booted with Windows XP.
It was taking lot of time to boot, start.

I thought of trying out the different edition of Ubuntu.

When I installed the new one, it is worse then that. I am able to see only the pointer, nothing else.

I tried giving all the things which is suggested in the forums.
Nothing worked out.

Now started feeling, Windows is far better.
Being a developer, if I feel in this way, I am just wondering about the common man. :) owch.

Any suggestions? What would be the problem? I m planning to take out ubuntu from my system.. worst case windows re installation since ubuntu installs grub.

---

### Post by jimmy the saint on 2009-01-11
It sounds like you made up your mind already.  Sorry to hear that.  Linux is like anything else in that if you are unwilling to learn how to use it, it is unlikely to work for you.  Perhaps if you posted with a specific issue someone could help you.

---

### Post by howefield on 2009-01-11
> **bhatGanesh said:**
> Now started feeling, Windows is far better.
Being a developer, if I feel in this way, I am just wondering about the common man. :) owch.

To each his own, but what is the difference between the developer and the common man, precious little in your case I guess.

A little more info as to your problem and what you have tried to fix would help, but as a developer I guess you would know that.

---

### Post by Ripfox on 2009-01-11
I am a common man and so are you, and I like ubuntu far better. Ouch.

---

### Post by Bölvaður on 2009-01-11
From what I can see it is very simple. Something may perhaps be wrong and it is horrifyingly simple to correct it for anyone given the correct information. 


But as a joke (and to make this a more positive and upbeat thread) and because you are a developer.

This is my report on your thread:  (where everything will be looked at from a positive angle :))

> Title: Needs to become longer and less informative on the problem, too much details.

Details on the problem: It is very good to know there is "the pointer" and nothing else is there. It is very direct and doesn't bore the reader with long text about the cause of the problem like list of hardware, kernel version, what distro or what release, if anything has been tried to fix it or any other details that could indeed drown a perfectly happy clown in boring texts.

Misc: The over all feeling of the thread is very positive. It even have jokes like "It was taking lot of time to boot, start." :) very good punch line.:lolflag: And some of the sarcasm about him self was witty and pure as Belgium drinking water.
There needs to be small rephrasing or removal of the text on Windows being in his mind far better than Linux, as that might not be a popular thing to say on a Linux support forum without being ignored.

btw I really like some parts of Belgium, and lived there for more than a year not too long ago.

---

### Post by SunnyRabbiera on 2009-01-11
Try a fresh install of Windows XP sometime, instead of the ones the company gives you...

---

### Post by y6FgBn)~v on 2009-01-11
> **SunnyRabbiera said:**
> Try a fresh install of Windows XP sometime, instead of the ones the company gives you...

...and use whatever works for you. There is no wrong answer.

---

### Post by the.scarecrow on 2009-01-11
Being a common man and not a developer, installation of Ubuntu 8.04 was easy and quite straight forward. Perhaps that was because I read the instructions on how to do it rather than assume it would be the same as installing Windows.

People have really helped me on this forum, so try to have a positive attitude, after all would you want to help someone that was already angry and negative?

If you hold a sensible debate on this forum, it helps you and many others that can look at the thread in the future.

---

### Post by bhatGanesh on 2009-01-12
Thanks allot for your replies. I never expected this sort of very good reply from you people.I like to learn it. I feel that I can still dig into Ubuntu and install it. The problem is as follows

Note: I had installed the Ubuntu in VMWare. It works superb.

But when I installed the same in my local system( Ubuntu Ultimate), the starting time is very high as more than 5 minutes.

Then I thought of going for Ubuntu 8.10, it starts quickly, but i can see only mouse pointer.
I tried this,

apt-get install gnome-core

but it says, it is unable to locate the package.

Q1: What can fix this problem?
Q2:If I install UUltimate back, can we fine tune the start up time?
Q3: What would be the reason for slow response time? some threads says, it is due to time taken to mount the Windows partition. But I feel, all are the same ntfs partition, so it should not be a problem.

Looks like this happens only during dual boot.

I still want to have XP dual booted since I want to run some windows apps (Adobe products, bea products etc)
I have not tried Wine yet. Don't know how good it is when comes to performance, to run windows apps.

your help would be greatly appreciated.

---

### Post by piousp on 2009-01-12
> **pcybill said:**
> ...and use whatever works for you. There is no wrong answer.

Indeed no wrong answer, but there are better answers :p

---

### Post by piousp on 2009-01-12
> **bhatGanesh said:**
> 
Q3: What would be the reason for slow response time? some threads says, it is due to time taken to mount the Windows partition. But I feel, all are the same ntfs partition, so it should not be a problem.


Let me see if i understand you correctly. Did you install ubuntu using WUBI? Meaning, did you install it FROM WINDOWS?

---

### Post by LowSky on 2009-01-12
> **bhatGanesh said:**
> 
Then I thought of going for Ubuntu 8.10, it starts quickly, but i can see only mouse pointer.
I tried this,

apt-get install gnome-core

but it says, it is unable to locate the package.

Q1: What can fix this problem?
Q2:If I install UUltimate back, can we fine tune the start up time?
Q3: What would be the reason for slow response time? some threads says, it is due to time taken to mount the Windows partition. But I feel, all are the same ntfs partition, so it should not be a problem.



First , if you got only a mouse pointer how did you type the apt-get command
second you need sudo to install any app
third gnome-core isn't the package you need
forth if you need to the command would be
```

sudo apt-get install ubuntu-desktop
```

fifth: most likely if all you get is a mouse cursor you need to reset up your xorg config and that can be done from the grub menu by choosing recovery mode and choosing xfix

Sixth: In all my years of computing people who are developers know almost nothing of the operating system they use. You guys can write code for miles but try to get you to diagnose your own computer woes and it is like pulling teeth.

seventh: Ubuntu Ultimate is not a Canonical based version of Ubuntu, if you like that version so much your better off using Linux Mint which is similar and more stable. Or learn to install the need packages yourself in Ubuntu.

---

### Post by sadaruwan12 on 2009-01-12
Hi,
What I've to say is that you might be a developer but you're a common user when it comes to Linux. Why I say this is that from your post what I see is a person who doesn't like to read much and have trapped mined well I've seen this in many people who have used windows when they switch to Linux they think of a pre-built OS that have been bloated by unwanted softwares. I your case you say that you tried fix it but what did you fixed dahh....? I was turned to linux by accident in 1997 when windows had a strong hold over the market. I got my hands on a copy of Ubuntu v5.10 the installation of that was very easy from there on I've been using Ubuntu and other variety of distributions but I don't have any problems with that but every time I've a chance to learn some thing new I did that with outing for some gate to open up and show me a window back then I was a newbie how had no Idea about Linux but I managed to become who I'm to day in the world of linux by studying and talking to people. If you want to be a linux user be polite and try to think that you're not the center of the universe.And anther thing for a Linux user Google is the biggest and the best friend he/she can find. :lolflag:

---

### Post by bhatGanesh on 2009-01-12
Hi  @sadaruwan12,,
I appreciate your post, but reading it did not help me in any way.

Was your post is to help me?

Sorry for being arrogant in my answer.
I am not looking at linux as OS comes with unwanted softwares.
I m trying to build my skill sets with linux, rather I want to contribute going forward.

---

### Post by bhatGanesh on 2009-01-12
Hi,

Thanks allot for ur reply.

I did not install Ubuntu from windows.

I pressed Ctrl+Alt+F1 to get console.

Opening ubuntu in recovery mode, i tried. but dont know what exactly I need to do.

Can u please help me in that.
Or shell i try reinstalling it?

---

### Post by LowSky on 2009-01-12
Like I said boot into recovery mode from GRUB
Choose the option of XFIX

Or from Consol

sudo dpkg-reconfigure xserver-xorg

---

### Post by bhatGanesh on 2009-01-12
Ok, Thanks.
let me try that and get back to u.

---

### Post by bhatGanesh on 2009-01-12
Hi Guys,
Looks like the problem is with the compatibility with my hardware.

The above solution did not work for me.So,I reinstalled it, Still facing the same old problem. :confused:

Cant help. Let me try some other version of it.

Thanks allot for your suggestions/help.

---

### Post by bhatGanesh on 2009-01-12
Hi @sadaruwan12,
Thanks for ur gyans too.

Don't u think u talk like u are the center of universe?
Which position u reached today? CEO of google?
or senior- exec of great company?
Or Created your own Linux distribution?
Or you are a multi-billionaire? 

If none of them are true... then I don't think it wont worth stating about the position.

You don't even care about the problem, cant suggest the solution. what the heck.. you posted ur comments here.

The greatness is in being simple.. I really appreciate the other people, who tried to help me.

---

### Post by ugm6hr on 2009-01-12
> **bhatGanesh said:**
> I pressed Ctrl+Alt+F1 to get console.

Assuming you are still running Ubuntu 8.10.

From the console (Ctrl-Alt-F1), tell us what the following commands tell you.  Give us the lines that relate to your Video Card / driver:
```
lspci
lshw -class display
```

The problem of having a white screen with a mouse pointer is likely either:
Your graphics card is not supported out-of-the-box
Your installation is corrupt

Just to check - did you check the md5sum and run the "Check disc" option from ther LiveCD before installing.

---

