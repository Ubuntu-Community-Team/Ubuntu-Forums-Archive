---
title: "Need Help FREEZING!!!!"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by jnmjr on 2010-02-17
Hey Guys:
 
I'm having a bad time with Karmic, it is constantly freezing, I've got no idea why, it works for about 10-15 mins. sometimes less and then freezes, doesn't matter what I'm doing, whether I'm on line or checking my e-mails or whatever, actually it had frozen a couple of times in the last week but I didn't think much of it, but as of today it's impossible. 
 
After it freezes it takes 3 to 4 reboots to get back in, I don't do any wierd stuff, like play around with software or the command line so it's not like I messed it up. 
 
As of now I'm working from Windows, I'm no expert on Linux, I would appreciate any help. The thing is I switched from WinXP to a hopefully more stable OS and I have spent a considerable amount of time and effort configuring and learning this Ubuntu, I really don't have the spare time to play around with computers, so it is very frustrating all the hickups with this OS, honestly atleast in my case so far, I don't see the advantages over WXP if it continues to prove to be mysteriously unstable.

---

### Post by spiderbatdad on 2010-02-17
what you are experiencing is of course very abnormal. If it were normal none of us would be using this OS. You should try to provide more information...at the very least, on what type of computer are you running Ubuntu?

---

### Post by jnmjr on 2010-02-17
> **spiderbatdad said:**
> what you are experiencing is of course very abnormal. If it were normal none of us would be using this OS. You should try to provide more information...at the very least, on what type of computer are you running Ubuntu?
 
 THX for your response......
 
MSI MS 6380
AMD XP2400+ 2.0 MHz 
NVidia GeForce 8400 GS
Audigy SE OEM
2 IDE drives WD 500 gig 1: XP Pro, 2: Ubuntu 9.10

 
What other info would you like?

---

### Post by k3lt01 on 2010-02-18
> **jnmjr said:**
> THX for your response......
 
MSI MS 6380
AMD XP2400+ 2.0 MHz 
NVidia GeForce 8400 GS
Audigy SE OEM
2 IDE drives WD 500 gig 1: XP Pro, 2: Ubuntu 9.10

 
What other info would you like?How much RAM? How much SWAP?

---

### Post by jnmjr on 2010-02-18
> **k3lt01 said:**
> How much RAM? How much SWAP?


Ram... 2gs
Swap...6gs

---

### Post by lidex on 2010-02-18
Is there a pattern? Any specific programs running consistently when it freezes? If you boot up and don't open anything will it freeze then as well?

Check the .x-session.errors file in your home directory as well as /var/log/syslog and /var/log/xorg.0.log

Run these commands in a terminal and reboot:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Just to make sure the kernel is updated and grub sees it.

---

### Post by lidex on 2010-02-18
Also what is the output of 
```
uname -a
```
 and 
```
sudo lshw
```

---

### Post by spiderbatdad on 2010-02-18
> **jnmjr said:**
> THX for your response......
 
MSI MS 6380
AMD XP2400+ 2.0 MHz 
NVidia GeForce 8400 GS
Audigy SE OEM
2 IDE drives WD 500 gig 1: XP Pro, 2: Ubuntu 9.10

 
What other info would you like?

I believe it is the graphics card...possibly in combination with desktop effects causing the problem. Start by making sure desktop effects are set to none in appearances menu. The are various issue with the 8400 card, and I'm not sure how to advise you. running in safe graphics or vesa is an option, or google nvidia 8400 ubuntu, and i'm sure you'll come up with plenty. I know you said you don't want to play around to get your computer working...sorry Ubuntu isn't working well on your hardware...there is also using xrandr [http://ubuntuforums.org/showpost.php?p=8560183&postcount=6](http://ubuntuforums.org/showpost.php?p=8560183&postcount=6) but it is also a good bitof work for the non geek. Best of luck.

---

### Post by jnmjr on 2010-02-18
> **spiderbatdad said:**
> I believe it is the graphics card...possibly in combination with desktop effects causing the problem. Start by making sure desktop effects are set to none in appearances menu. The are various issue with the 8400 card, and I'm not sure how to advise you. running in safe graphics or vesa is an option, or google nvidia 8400 ubuntu, and i'm sure you'll come up with plenty. I know you said you don't want to play around to get your computer working...sorry Ubuntu isn't working well on your hardware...there is also using xrandr [http://ubuntuforums.org/showpost.php?p=8560183&postcount=6](http://ubuntuforums.org/showpost.php?p=8560183&postcount=6) but it is also a good bitof work for the non geek. Best of luck.


THX Spider, I believe you may be right, it's the most logical conclusion, I did what you suggested on the desk top effects, when I get some time I'll research more thoroughly, How do you run in Vesa? in case I need to do it, so far by turning desktop to none OS is holding up....

THX to all, I appreciate your input, though I'm pursuing the Video Card angle, I will continue to welcome all your suggestions....BTW all freezes were completely random..

---

### Post by jnmjr on 2010-02-18
> **lidex said:**
> Is there a pattern? Any specific programs running consistently when it freezes? If you boot up and don't open anything will it freeze then as well?

Check the .x-session.errors file in your home directory as well as /var/log/syslog and /var/log/xorg.0.log

Run these commands in a terminal and reboot:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```Just to make sure the kernel is updated and grub sees it.

I'm attaching all info as per your post, I don't know what to look for??? You can review it and see if you notice a problem. THX

---

### Post by jnmjr on 2010-02-18
> **jnmjr said:**
> I'm attaching all info as per your post, I don't know what to look for??? You can review it and see if you notice a problem. THX


I guess I cant even do an Attachment. LOL

---

### Post by jnmjr on 2010-02-18
> **jnmjr said:**
> I guess I cant even do an Attachment. LOL

Can someone explain how to post a long file without taking a large amount of room? THX

---

### Post by k3lt01 on 2010-02-18
When you reply to a post before you hit the submit post button scroll down the page a bit and it will have a button in Additional Options saying manage attachments. Click that and follow the instructions.

---

### Post by jnmjr on 2010-02-18
> **lidex said:**
> Is there a pattern? Any specific programs running consistently when it freezes? If you boot up and don't open anything will it freeze then as well?

Check the .x-session.errors file in your home directory as well as /var/log/syslog and /var/log/xorg.0.log

Run these commands in a terminal and reboot:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```Just to make sure the kernel is updated and grub sees it.

Lets try again with the attachment.

---

### Post by jnmjr on 2010-02-18
> **k3lt01 said:**
> When you reply to a post before you hit the submit post button scroll down the page a bit and it will have a button in Additional Options saying manage attachments. Click that and follow the instructions.

THX for your reply, I figured out that the txt file was too large so I converted to pdf and it worked, thanks again, I just learned something new.

---

### Post by k3lt01 on 2010-02-18
Anytime ;)

---

### Post by vlad1975 on 2010-02-18
I hear yah.. it all started last night for me too that why i decided to re-install but now im having issue in GRUB

---

### Post by jnmjr on 2010-02-18
> **vlad1975 said:**
> I hear yah.. it all started last night for me too that why i decided to re-install but now im having issue in GRUB

Sorry to hear, NO WAY!!!!!!! would I re-install, I've spent toooooooo much time and effort getting this Os to where I want it as far as the stuff I need for my work. I'm no Linux wiz so it would take me days to get it back in shape, and I'm still learning. I honestly dont remember half the commands and stuff I did so I would need to research it again, forget it, I'd go back to WXP, if it would irreparably crash I could have it up and running in less than 3hrs. max. This is not to say that I not consider Linux a better Os, I do, but it's still a bit harsh on guys like me, I'm on the go and time is money, if you know what I mean, that's why I have WXP as a back-up.

Just to let all know, I've put desktop effects to none, and I'm not using my screensaver for now, the result has been no freezes so far, OS has been functioning for more than 14hrs. without a freeze. Tomorrow I will use screensaver and see what happens. Apparently Spider hit it right, it was the video card so I'm not closing this thread, I'm keeping my fingers crossed until tomorrow atleast. THX to all for your input

---

### Post by jnmjr on 2010-02-20
> **spiderbatdad said:**
> I believe it is the graphics card...possibly in combination with desktop effects causing the problem. Start by making sure desktop effects are set to none in appearances menu. The are various issue with the 8400 card, and I'm not sure how to advise you. running in safe graphics or vesa is an option, or google nvidia 8400 ubuntu, and i'm sure you'll come up with plenty. I know you said you don't want to play around to get your computer working...sorry Ubuntu isn't working well on your hardware...there is also using xrandr [http://ubuntuforums.org/showpost.php?p=8560183&postcount=6](http://ubuntuforums.org/showpost.php?p=8560183&postcount=6) but it is also a good bitof work for the non geek. Best of luck.


Well I'm going to close this thread, Spider you were right, GS8400 is full of issues, though it went 15hrs without freezing as soon as I turned on the Screensaver in 3D it froze again, i figured my only option was to swap cards, this has so far worked perfectly. I took an older AGP from my daughter's Pc a GS6200 and gave her mine (she only likes Windows)  so it works good for her and for me, the old card no hiccups so I'm happy!!!:P BTW I turned Desktop Effects back on. Thank you very much to all who participated on this issue.):P

---

