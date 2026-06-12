---
title: "Parental Oversight"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Sava8420 on 2009-03-14
As I spread the word of Ubuntu and Linux in general,  I have a friend who's daughter loves Ubuntu now but this is a problem for me now because my friend was using Safe Eyes to monitor the child's web activity.  My friend though has no interest in leaving XP.  Anyone know of a way to setup this kind of oversight so they both will be happy?  Mainly in regards to using Pidgin for instant messaging.  Any thoughts would be appreciated.  Well except pushing Ubuntu on my friend as trust me it is a lost cause.

I personally wouldn't take these actions upon my children (if I had children) but am not trying to tell a single mother how to raise their teenage daughter.  At the same time though her daughter doesn't have a problem with it, or rather keeps them to herself so I would just like to see if there is a way for this to work.

---

### Post by northern lights on 2009-03-14
He might want to check out *[Squid]("http://www.squid-cache.org/")*.

The March issue of *Linux Magazine* just featured an article on how to use squid as a parental guidance app. Lemme check for it (April issue is out, dunno the whereabouts of the March issue, gotta look).

Squid is in the repos and installable via```
sudo apt-get install squid
```

---

### Post by rafac24 on 2009-03-14
And on top of 'Squid' you can also try the Educational and family version of ubuntu, known as: Edubuntu.

```
sudo apt-get install edubuntu-desktop
```

---

### Post by iKonaK on 2009-03-14
> **Sava8420 said:**
> monitor the child's web activity.
I don't think spying on your own kids is a healthy behavior, if parents have doubts of what their little punk dose they just have to talk to them and be open. I'm always freaked up when i hear parents willing to spy on their kids, it's like shouting "i don't trust you, you little punk..." :(

---

### Post by Old_Grey_Wolf on 2009-03-14
I will not make judgments concerning filtering or spying on children, since I do not know the circumstances. 

Check out [http://dansguardian.org/?page=whatisdg](http://dansguardian.org/?page=whatisdg).

Just to point out the futility of content filtering, even if you had the best most secure filter in the world it can easily be bypassed simply by popping in a live CD of any one of the Ubuntu or other Linux distros which would immediately give you free and unhindered access to the Internet.

---

### Post by Sava8420 on 2009-03-14
> **iKonaK said:**
> I don't think spying on your own kids is a healthy behavior, if parents have doubts of what their little punk dose they just have to talk to them and be open. I'm always freaked up when i hear parents willing to spy on their kids, it's like shouting "i don't trust you, you little punk..." :(

Oh I assure you that is not something I want to be in the middle of by any means.  No matter though my opinions, I am in no position to tell her how to raise her kid.

---

### Post by mister_pink on 2009-03-14
> **iKonaK said:**
> I don't think spying on your own kids is a healthy behavior, if parents have doubts of what their little punk dose they just have to talk to them and be open. I'm always freaked up when i hear parents willing to spy on their kids, it's like shouting "i don't trust you, you little punk..." :(
There's definitely a place for it, depending on the childs age. Not to prevent them from looking at things, but to prevent young kids genuinely accidentally seeing things they shouldn't.

That said, if they're that young, they should probably not be surfing the web unsupervised. 

As for content filters, squid will work well but I don't think its too easy to set up. There are a lot of quite good guides though.

---

### Post by iKonaK on 2009-03-14
> **Sava8420 said:**
> Oh I assure you that is not something I want to be in the middle of by any means.  No matter though my opinions, I am in no position to tell her how to raise her kid.
You are in no position to force her but you can suggest her, as a friendly advice, that by spying and enforcing restrictions to her daughter's behavior is not constructive and that is better to talk to a kid about sh*t so that the kid would understand what is proper to do or not ;) her daughter behavior dosen't stop after logout and she will eventually see or go on places that her mom dosen't want to go, so the only thing this behavior would do is to cool the relation between them.
A fried should be able to give advices specially when they're asked.

---

### Post by iKonaK on 2009-03-14
> **mister_pink said:**
> There's definitely a place for it, depending on the childs age.

That said, if they're that young, they should probably not be surfing the web unsupervised.
If they are that young they should not surf at all, they should play outside with other kids "[playing with sticks and making holes in the soil]("http://en.wikipedia.org/wiki/It%27s_Bad_for_Ya")", there is a time and a place for starting  internet use and is called teenage or high school ;)

---

### Post by brian_p on 2009-03-14
> **Sava8420 said:**
> 

Any thoughts would be appreciated.Well except pushing Ubuntu on my friend as trust me it is a lost cause.

Linux has nothing (that I know of) which offers the same as Safe Eyes. You could probably put together a set of utilities which do something similar but whether your friend considers this time well spent is questionable.

You mention instant messaging. The blurb for Safe Eyes says:

```
The Safe Eyes parental control software instant message monitor records and saves IM conversations so that parents can review them at a later time.

```

That shouldn't be hard to do but there is a degree of effort involved which require some knowledge of how the OS works.

Happiness for two is not easily achievable.

---

### Post by Dr Small on 2009-03-14
There is also transparent web filtering:
[http://ubuntuforums.org/showthread.php?t=1078033](http://ubuntuforums.org/showthread.php?t=1078033)

---

### Post by VraiChevalier on 2009-03-14
A good way to filter internet content is with "Open DNS". It can be set up to filter all sorts of content. As far as the instant messaging is concerned I don't know.

---

### Post by mikewhatever on 2009-03-14
I am amazed at how many repliers didn't read the original post. The OP explicitly asked for instant messaging monitoring solution, not web filtering. Is it asking to much to read before answering?


> **Sava8420 said:**
> **Anyone know of a way to setup this kind of oversight so they both will be happy?  Mainly in regards to using Pidgin for instant messaging.**

---

### Post by Sava8420 on 2009-03-15
> **brian_p said:**
> Linux has nothing (that I know of) which offers the same as Safe Eyes. You could probably put together a set of utilities which do something similar but whether your friend considers this time well spent is questionable.

You mention instant messaging. The blurb for Safe Eyes says:

```
The Safe Eyes parental control software instant message monitor records and saves IM conversations so that parents can review them at a later time.

```

That shouldn't be hard to do but there is a degree of effort involved which require some knowledge of how the OS works.

Happiness for two is not easily achievable.
Thanks for your input.  Is exactly what I was referring to.  So does Pidgen just utilize the online version of chat clients or how does it work?  I am pretty sure that if she can monitor her daughter's chat logs all would be good.

---

### Post by Sava8420 on 2009-03-15
> **mikewhatever said:**
> I am amazed at how many repliers didn't read the original post. The OP explicitly asked for instant messaging monitoring solution, not web filtering. Is it asking to much to read before answering?

You noticed this too huh?  lol is all good as I figured would get a variety of responses.

---

### Post by martrn on 2009-03-15
> **Sava8420 said:**
> What I wonder is if the chat logs are accessable in any way?

I reccomend a book : [book&cn=28]("http://resources.atcmhmr.com/poc/view_doc.php?id=1326&type=book&cn=28")

---

### Post by teamcoltra on 2009-03-15
I have a genuine reply that can have her "review conversation logs at a later time" 

First set up a plugin "Text Replacement" this will change OUTGOING words, so you could also change words like the F-Word to <cencored> now if they know computing basics they can disable this, but that comes to my second part.

Pidgin has logging capibilities so simply go into the /Home/$USER/.purple/logs (dumb name for a folder, something thats not the app name... oh well) and then just open up the folder of the chat client her son/daugther uses... and review the different logs... if she is looking for certain words just type "ctrl + F" and look up key swear words or something. 

Its not perfect, but if she needs to go any more extreme than this, then just tell her kids that htye can't use the internet. :P My mother got freaked out because I let my little brother come over and spend the night, and I took a picture of him and uploaded it to flickr, but that has nothing to do with this.

But honestly, she can look at the logs, if the kid trys to delete them, then take away his or her internet privlages.

---

### Post by Sava8420 on 2009-03-15
> **martrn said:**
> I reccomend a book : [book&cn=28]("http://resources.atcmhmr.com/poc/view_doc.php?id=1326&type=book&cn=28")

Ahhhh thanks man for your concern.  I'll make sure to pass on your link.  Maybe will be put to good use.

---

### Post by martrn on 2009-03-15
> **iKonaK said:**
> I don't think spying on your own kids is a healthy behavior, if parents have doubts of what their little punk dose they just have to talk to them and be open. I'm always freaked up when i hear parents willing to spy on their kids, it's like shouting "i don't trust you, you little punk..."

I agree.

---

### Post by ALIENDUDE5300 on 2009-03-15
> **iKonaK said:**
> I don't think spying on your own kids is a healthy behavior, if parents have doubts of what their little punk dose they just have to talk to them and be open. I'm always freaked up when i hear parents willing to spy on their kids, it's like shouting "i don't trust you, you little punk..." :(

I can completely agree with this... let kids be kids, just teach them what they can and can not do - spying on kids is an invasion of privacy. :/

---

### Post by teamcoltra on 2009-03-15
> **ALIENDUDE5300 said:**
> I can completely agree with this... let kids be kids, just teach them what they can and can not do - spying on kids is an invasion of privacy. :/

And its best to lets your kids get drunk in your own house so you can supervise it?

I am not a proponent of parents watching everything their kid does like a hawk, they should be good enough parents to have raised them right, and they wouldn't have to worry about it. However, saying its an invasion of privacy is not correct. Children do not get that right until they leave the house, as unfair as it may be (and courts have upheld this in the United States everywhere outside of the 7th district (even supreme court) and the 7th district is so pink-o its funny)

---

### Post by ramjet_1953 on 2009-03-15
FoxFilter is an add-on that is available readily by just using the add-on facility of Firefox.

It is just that - a content filter, not a heavy-handed "big brother" program.

It is password controlled and the sensitivity can be easily adjusted.

You can also add words and phrases to the filtering list.

Regards,
Roger :D

---

### Post by hyper_ch on 2009-03-15
> **teamcoltra said:**
> Children do not get that right until they leave the house, as unfair as it may be (and courts have upheld this in the United States everywhere outside of the 7th district (even supreme court) and the 7th district is so pink-o its funny)

Yet in other countries such basic civil rights are also granted to children.

---

### Post by brian_p on 2009-03-15
> **Sava8420 said:**
> Thanks for your input.  Is exactly what I was referring to.  So does Pidgen just utilize the online version of chat clients or how does it work?  I am pretty sure that if she can monitor her daughter's chat logs all would be good.

I am unfamiliar with pidgin and the wonderful world of instant messaging. However, I am familiar with parenting and would think the relationship between your friend and her daughter would be a factor in how a technical solution is implemented.

Monitoring the chat logs is easy enough. They could be mailed to her using cron, for example. But is logging to be enforced and is there a need to prevent deletion of the logs? You would be looking at file permissions and sticky bits on directories here. And is there a need to ensure alternative configuration files are not used? Do young people read man pages? It's an interesting problem to solve.

---

