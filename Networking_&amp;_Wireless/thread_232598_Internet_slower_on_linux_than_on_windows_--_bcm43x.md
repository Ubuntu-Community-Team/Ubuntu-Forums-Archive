---
title: "Internet slower on linux than on windows -- bcm43xx issue?"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by sqlplus on 2006-08-08
Hi all,

I've recently started trying ubuntu/kubuntu on my hp laptop in a dual boot xp system.  It seems that my internet speed is significantly slower when using linux than it is with windows and I was hoping for some pointers and assistance to help verify if this is the case and diagnose the reasons.  

I almost solely use wireless and my initial thought is that the slowness is due to my broadcom 4318 card running at 11M/s under ubuntu rather than at 36M/s or 54M/s which I think it runs at in windows.

In windows under wireless connections it currently shows that my speed is 48Mbps (sometimes it's 54, sometimes it's 36...).

Under ubunutu I'm using the bcm43xx driver which I believe has a limitation of 11Mbps.

So...

(a) How can I verify that this is in fact the problem? Is there a tool I can use in linux to objective measure my connection speed? In windows?

(b) If I switch to from using the bcm43xx driver to ndiswrapper would I be able to get higher than 11Mbps?

(c) Anything else I should be using to help diagnose these issues and optimize internet speed?

Thanks so much in advance...

---

### Post by LadyDoor on 2006-08-08
My experience has been that NDISWrapper is a) fast and b) working, which has been different than my experience with the BCMxx kernel drivers in two ways (see a and b). That's just my experience on this computer, though--I honestly have no idea what will happen on your computer, especially since I have heard of good experiences using the bcm43xx. Also, if need be you might consider using programs such as swiftfox and surfraw to speed things up.

Good luck,
Door

---

### Post by sqlplus on 2006-08-09
Thanks for the input.  I am thinking about switching to ndiswrapper but bcm43xx seems to be working fine for me except for the 11M limitation, if that is in fact what is slowing me down.

What utility would I use check my my actual speed transfer rate so that I can get objective data?  Would that be iwconfig? It seems though like that shows what the connection is set up for, not the actual transfer rate.

Thanks...

---

### Post by Richo on 2006-08-20
I'm using the bcm43xx kernel driver and it is slow, but I don't think it is related to the 11MB limit. There appears to be a pause before each request and then once the pause is over the actual comms for each request is quick. It is very frustrating, but I have only installed this the last couple of days, and have only just started researching a solution.

---

### Post by Richo on 2006-08-20
I'm using the bcm43xx kernel driver and it is slow, but I don't think it is related to the 11MB limit. There appears to be a pause before each request and then once the pause is over the actual comms for each request is quick. It is very frustrating, but I have only installed this the last couple of days, and have only just started researching a solution.

---

### Post by sqlplus on 2006-08-23
Have you found a solution yet? I agree that the issue is not the 11M limitaion but possibily it is the bcm43xx driver. I think that I'm going to try ndiswrapper to see if that makes a difference.

---

### Post by tribaal on 2006-08-23
Is you connection slower when surfing the web in particular (with firefox)? If that's the case, you might want to try the "[ipv6 firefox trick]("http://en.opensuse.org/Disable_IPv6_for_Firefox")" (this is from Suse's website but the trick is the same, really), and see if that helps.

A good way to check if the problem is with firefox is to mesure the time it takes for you to "time sudo aptitude update"... Mine (on a fast connection) never takes more than 15-20 seconds.

- trib'

---

