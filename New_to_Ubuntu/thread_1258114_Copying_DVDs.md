---
title: "Copying DVDs"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by myolbug on 2009-09-04
I need help copying some DVDs.  These are for personal use, just to have back ups for my young boys.

I have had a friend with Windows put a movie on a normal 4.7GB DVD-R with no issues, plays in all of our DVD players.  When I try and use the Ubuntu 9.04 default, it will not put it on a normal DVD-R, so I tried DVD-R Dual Layer as it is 8.5GB and it copied, but it only plays on my computer.

I don't want to waste a bunch of DVD-R's trying to figure this out.


FWIW, I have an AMD 84bit Dual Core proc and a standard DVD burner and Ubuntu 9.04

Thanks!

**EDIT**  I am in the US, so Region 1 if that makes a difference.

---

### Post by oldos2er on 2009-09-04
You need to use k9copy (or something similar) to shrink your 8.x DVD to 4.x.

---

### Post by insane_alien on 2009-09-04
you probably burned it as a file. you need to burn it as a DVD video fromat.

look in the repos for DVD95 that'll do it automatically for you iirc

---

### Post by kelvin spratt on 2009-09-04
Use DVD95 that will shrink the to a standard DVD use the + version if possible as its the newer DVD version and gives better results.

---

### Post by hyperdude111 on 2009-09-04
I don't know about the legality of ripping dvds for personal use, but there are many tools that can help you.

Handbrake - Easy to install, use and it's cross platform. It also converts mltiple file types to many pre-sets. 

K3b - In the repos and the default in KDE. I always found this app a bit problematic but many people love it. 

There are loads of others, do some research. I think VLC can do it (to some level) as well.

---

### Post by MrWES on 2009-09-04
> **oldos2er said:**
> You need to use k9copy (or something similar) to shrink your 8.x DVD to 4.x.

+1 for K9copy -- use it to rip DVD9 to DVD5 iso file, and then use K3b to burn the iso file. Just make sure you set the iso size to 4400 mb.

Bill

It's not illegal to make a backup copy of your purchased DVD's.

---

### Post by halitech on 2009-09-04
> **myolbug said:**
> I need help copying some DVDs.  These are for personal use, just to have back ups for my young boys.

I have had a friend with Windows put a movie on a normal 4.7GB DVD-R with no issues, plays in all of our DVD players.  When I try and use the Ubuntu 9.04 default, it will not put it on a normal DVD-R, so I tried DVD-R Dual Layer as it is 8.5GB and it copied, but it only plays on my computer.

FWIW, I have an AMD 84bit Dual Core proc and a standard DVD burner and Ubuntu 9.04

First off, if they are encrypted, its going to be harder.

I'm not sure what you mean by the Ubuntu default? Do you mean you inserted the disk, waited for it to mount and clicked copy? In that case, you would probably need an 8.5gig disk but depending how it copied, it may not be readable (my standalone player doesn't like DL media)

K9copy should do most of what you need and personally I would install K3B to burn the ISO that K9copy will create.

PS. I think you mean an AMD 64bit CPU and not an 84bit ;)

---

### Post by k3lt01 on 2009-09-04
> **MrWES said:**
> It's not illegal to make a backup copy of your purchased DVD's.That needs to be clarified. Some countries allow copying dvds (cds etc) you personally purchased for personal use, others do not. A statement such as this made in such an all encompassing way isn't correct in more cases than it is correct.

---

### Post by Garrovick on 2009-09-04
Just some info...

In the U.S. we are allowed to make one back up copy of our media. Only the original can be used until it fails, then the back up can be used.  **The original media must be retained**. When the back up fails, the media must be repurchased. If we give away the original media, the back up must be destroyed and not given away.

And of course, uploading our media to the net is always against U.S. law.

Nor, in most cases, getting busted for having and using the back up on our computers.

---

### Post by dagoth_pie on 2009-09-04
Ironic isn't it, that a forum that almost qualifies as an attack on patented software, has more respect for intellectual property rights than the majority of the earth's population...

And people say we just use Linux because it's cheap...

---

### Post by Garrovick on 2009-09-04
> **dagoth_pie said:**
> Ironic isn't it, that a forum that almost qualifies as an attack on patented software, has more respect for intellectual property rights than the majority of the earth's population...

And people say we just use Linux because it's cheap...

Even if we do have to "sneak" in the back door to play mp3s and the like.

---

### Post by dagoth_pie on 2009-09-05
> **Garrovick said:**
> Even if we do have to "sneak" in the back door to play mp3s and the like.

Nonsence, I'd be more than happy to pay the royalty fee, all they have to do is come knock on my door and ask nicely...

---

### Post by MrWES on 2009-09-05
> **k3lt01 said:**
> That needs to be clarified. Some countries allow copying dvds (cds etc) you personally purchased for personal use, others do not. A statement such as this made in such an all encompassing way isn't correct in more cases than it is correct.

Blah...come on, that's like saying certain sexual positions are illegal -- which in some areas they are. :)

Bill

---

### Post by k3lt01 on 2009-09-05
> **MrWES said:**
> Blah...come on, that's like saying certain sexual positions are illegal -- which in some areas they are. :)

Bill
Sorry but your humour isn't funny and has nothing to do with the point of this thread.

All I did was state that your comment needed clarification. I think people have a right and a responsibility to know what is true for their situation with regards to the question at hand. If every person who read this forum believed that what is allowed in the USA is allowed in their country then they could quite well get in some serious trouble for their ignorance.

---

### Post by dagoth_pie on 2009-09-05
> Blah...come on, that's like saying certain sexual positions are illegal -- which in some areas they are.
Yes, in public where you can get caught...
> Sorry but your humour isn't funny and has nothing to do with the point of this thread.
I dissagree, it is funny, inappropriate and very off topic, but still I found it funny...
> All I did was state that your comment needed clarification. I think people have a right and a responsibility to know what is true for their situation with regards to the question at hand. If every person who read this forum believed that what is allowed in the USA is allowed in their country then they could quite well get in some serious trouble for their ignorance.
Your right there, to be honestly I have no clue what laws in my country say, you'd think I would, it's what the politicians are "debating" about these days, it's all because of that whole Pirate Bay being sued thing. In conclusion, check your laws before making backups of anything. Especially if your in France, I hear they have really strict laws when it comes to this sort of stuff...

Ps. Stuff is a technical word, my high school electronics teacher said so...

---

### Post by mangurt on 2009-09-05
To post a suggestion in regards to the orginal post/question:

You can run DVDFAB through wine,  it's a great program.

There is also a work around found here

[http://geek-out-blog.blogspot.com/2009/01/how-to-restart-dvdfab-trial-period.html]("http://geek-out-blog.blogspot.com/2009/01/how-to-restart-dvdfab-trial-period.html")

That you can use to restart the trial period.

---

### Post by 3rdalbum on 2009-09-05
> **Garrovick said:**
> Even if we do have to "sneak" in the back door to play mp3s and the like.

MP3s are perfectly legal to play in Ubuntu if you are using the gstreamer0.10-fluendo-mp3 codec, which is licensed.

---

### Post by k3lt01 on 2009-09-05
> **dagoth_pie said:**
> Ironic isn't it, that a forum that almost qualifies as an attack on patented software, has more respect for intellectual property rights than the majority of the earth's population... There is nothing wrong with software patents and there is certainly nothing wrong with intellectual property rights. The issue with these things is how they are enforced. Credit where credit is due is morally right but it doesn't mean that when giving credit we are also giving that person or their product/idea a higher place in society.

Off topic I know but I have only just seen this post.

---

### Post by myolbug on 2009-09-18
This may be just cheap DVD-R's but I was able how to copy one of my DVDs and it pauses, just briefly about every 30 seconds or so.  Any ideas?

I used DVD95 and K3B

---

### Post by myolbug on 2009-09-18
Bumpinski!!!

---

### Post by myolbug on 2009-09-18
Anyone?

---

### Post by Jazzy_Jeff on 2009-09-18
I have always had problems using DVD-R media. All I use now is the +R. Not sure if this would fix your problem.

---

### Post by scared0o0rabbit on 2009-09-18
Could be low quality dvd's, could be issues with the burn, could be the dvd player, could be a combination of them all.

---

### Post by mjp29 on 2009-09-28
interesting

---

### Post by mjp29 on 2009-09-28
thanks for the info

---

### Post by mjp29 on 2009-09-29
> **k3lt01 said:**
> That needs to be clarified. Some countries allow copying dvds (cds etc) you personally purchased for personal use, others do not. A statement such as this made in such an all encompassing way isn't correct in more cases than it is correct.

And you made the statement yourself that "A statement ... in such an all encompassing way isn't correct in more cases than it is correct."

So your statement has basically said that it is illegal in more places in the world to make a backup copy than it is legal to do so.  Think about that.

Can you prove that it "isn't correct in more cases than it is correct" ?

Can you prove that it is illegal in more countries (over 50%) than it is legal to make backup copies of what you've bought.  Can you prove that it is illegal in more places in the world to make a backup copy of something bought?

Look at your own all encompassing statement and prove to us you're right.

Proof is in the pudding.  Show us the pudding (link us to it) and we'll believe you if you can prove that your all encompassing statement is correct.

nough said (one would think but read on)


before many of us get mad at you or you get mad at me or i get mad at you (it goes on and on and on) let us all just pause and remember that Ubuntu is a word that means "humanity toward others"

in saying that I realize that the poster you responded to made a broad statement you didn't agree with as you didn't feel it applied everywhere and some responded to you in an ugly way and i then responded to you [in an ugly way here] where i felt you made an equally broad statement.

but in the end who cares or what really matters?

What really does matter is that the African word Ubuntu not only means humanity towards others but the word also means "I am what I am because of who we all are"

So perhaps, just perhaps, I am, you are, every single individual person that replied in this thread in either a positive way, a negative way, or neutral manner that has read and thought about this thread has become more like everyone here than what they were before they were here.  Even those that didn't even reply to this thread but simply read it have become more like us all (our negative comments, our positive comments, our neutral comments) because they have thought about what took place here even though they didn't partake.  Scarry in a way, I think.  But also enlightening in a way.


Think about it from a philosophical stand point.  Every person you interact with in life [have a conversation with let's say] either agrees with you, disagrees with you, or cares less about what you say [is neutral to you] but converses back (because they are being polite) have all become more like you and you have become more like them because you have all entered each others minds and touched the way they think (positive, neutral, negative). 

And by the way, in my opinion most people that listen to others talk about subjects like politics/religion etc. are polite when we disagree with them inside (because we don't verbally let it be known what we truly think) - yet what they said affect us both.

Which comes to an interesting thought that affects everyone in the modern day of electronics and the internet (and forums like this) and the such.  Most of us would not face off with someone we are standing in front of that is telling us about their politics and religion we disagree with yet in this modern age (internet forums) we are quick to reply and say what we really think.

So perhaps "humanity toward others" and "I am what I am because of who we all are" should apply here too - ?

Think about it.

p.s. I'll delete this post tomorrow as I and many of you probably find this post/reply ridiculous.  Nevertheless, Ubuntu to us all.

---

### Post by k3lt01 on 2009-09-30
> **mjp29 said:**
> And you made the statement yourself that "A statement ... in such an all encompassing way isn't correct in more cases than it is correct."

So your statement has basically said that it is illegal in more places in the world to make a backup copy than it is legal to do so.  Think about that.

Can you prove that it "isn't correct in more cases than it is correct" ?

Can you prove that it is illegal in more countries (over 50%) than it is legal to make backup copies of what you've bought.  Can you prove that it is illegal in more places in the world to make a backup copy of something bought?

Look at your own all encompassing statement and prove to us you're right.

Proof is in the pudding.  Show us the pudding (link us to it) and we'll believe you if you can prove that your all encompassing statement is correct.

nough said (one would think but read on)


before many of us get mad at you or you get mad at me or i get mad at you (it goes on and on and on) let us all just pause and remember that Ubuntu is a word that means "humanity toward others"

in saying that I realize that the poster you responded to made a broad statement you didn't agree with as you didn't feel it applied everywhere and some responded to you in an ugly way and i then responded to you [in an ugly way here] where i felt you made an equally broad statement.

but in the end who cares or what really matters?

What really does matter is that the African word Ubuntu not only means humanity towards others but the word also means "I am what I am because of who we all are"

So perhaps, just perhaps, I am, you are, every single individual person that replied in this thread in either a positive way, a negative way, or neutral manner that has read and thought about this thread has become more like everyone here than what they were before they were here.  Even those that didn't even reply to this thread but simply read it have become more like us all (our negative comments, our positive comments, our neutral comments) because they have thought about what took place here even though they didn't partake.  Scarry in a way, I think.  But also enlightening in a way.


Think about it from a philosophical stand point.  Every person you interact with in life [have a conversation with let's say] either agrees with you, disagrees with you, or cares less about what you say [is neutral to you] but converses back (because they are being polite) have all become more like you and you have become more like them because you have all entered each others minds and touched the way they think (positive, neutral, negative). 

And by the way, in my opinion most people that listen to others talk about subjects like politics/religion etc. are polite when we disagree with them inside (because we don't verbally let it be known what we truly think) - yet what they said affect us both.

Which comes to an interesting thought that affects everyone in the modern day of electronics and the internet (and forums like this) and the such.  Most of us would not face off with someone we are standing in front of that is telling us about their politics and religion we disagree with yet in this modern age (internet forums) we are quick to reply and say what we really think.

So perhaps "humanity toward others" and "I am what I am because of who we all are" should apply here too - ?

Think about it.

p.s. I'll delete this post tomorrow as I and many of you probably find this post/reply ridiculous.  Nevertheless, Ubuntu to us all.

Ubuntu to you to. Let me just say delete it if you will but that was a complete waste of your time cause you jarred yourself with your own argument against me. Mis-quoting, or deliberately leaving out parts of, a statement tp prove your own point is not very Ubuntuistic nor is it morally right or even nice. Now if you would care to revisit the original statement I said "A statement such as this made in such an all encompassing way isn't correct in more cases than it is correct." This statement is not all encompassing but is a general statement. That is indicated by the "such as this" part which you deliberately edited out.

I'm not really interested in the ecumenicality of copying dvds whether legally or illegally, what I am interested in is people knowing their rights and responsibilities in THEIR own legal situation. So the responsibility is not mine to prove my statement but each individuals to know their legal rights and responsibilities.

Last but not least you seem, in this thread at least, to be posting and then deleting (or editing) some of your posts. If your not going to be helpful at least leave me out of your trolling from this moment on.

---

### Post by mjp29 on 2009-09-30
> **k3lt01 said:**
> Ubuntu to you to. Let me just say delete it if you will but that was a complete waste of your time cause you jarred yourself with your own argument against me. Mis-quoting, or deliberately leaving out parts of, a statement tp prove your own point is not very Ubuntuistic nor is it morally right or even nice. Now if you would care to revisit the original statement I said "A statement such as this made in such an all encompassing way isn't correct in more cases than it is correct." This statement is not all encompassing but is a general statement. That is indicated by the "such as this" part which you deliberately edited out.

I'm not really interested in the ecumenicality of copying dvds whether legally or illegally, what I am interested in is people knowing their rights and responsibilities in THEIR own legal situation. So the responsibility is not mine to prove my statement but each individuals to know their legal rights and responsibilities.

Last but not least you seem, in this thread at least, to be posting and then deleting (or editing) some of your posts. If your not going to be helpful at least leave me out of your trolling from this moment on.

I was merely using ellipsis (three dots which are commonly used in written language).

With or without the ellipsis, the meaning of your statement does not change.  For the record you said "That needs to be clarified. Some countries allow copying dvds (cds etc) you personally purchased for personal use, others do not. A statement such as this made in such an all encompassing way isn't correct in more cases than it is correct." 

So I used ellipsis when I quoted you where I typed "A statement ... in such an all encompassing way isn't correct in more cases than it is correct."

Again, with or without the ellipsis, the meaning of your statement does not change.  I don't wish to argue with you.  

Ubuntu to you.

Good day.

---

### Post by k3lt01 on 2009-09-30
> **mjp29 said:**
> I was merely using ellipsis (three dots which are commonly used in written language).

With or without the ellipsis, the meaning of your statement does not change.  For the record you said "That needs to be clarified. Some countries allow copying dvds (cds etc) you personally purchased for personal use, others do not. A statement such as this made in such an all encompassing way isn't correct in more cases than it is correct." 

So I used ellipsis when I quoted you where I typed "A statement ... in such an all encompassing way isn't correct in more cases than it is correct."

Again, with or without the ellipsis, the meaning of your statement does not change.  I don't wish to argue with you.  

Ubuntu to you.

Good day.Wrong again, lol. Leaving words out changes meaning, you need to remember the Ubuntu Community is an international community and not everyone has your flair for written language. You should use the lowest common denominator so people from all walks of life can understand what you are saying.

Further communications will be in PMs.

---

### Post by bapoumba on 2009-09-30
> **mjp29 said:**
> 
p.s. I'll delete this post tomorrow as I and many of you probably find this post/reply ridiculous.  Nevertheless, Ubuntu to us all.
Ahem ..

---

