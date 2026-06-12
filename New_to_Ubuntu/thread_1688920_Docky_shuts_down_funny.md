---
title: "Docky shuts down funny"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by jermza on 2011-02-16
Docky is great.  It's quick and very responsive.

But when I shut down Ubuntu, there is often a lengthy pause because Docky pops up a notification saying that it can't run properly because certain things need to be running (which have obviously stopped running since I told the machine to shut down).

Not only is this annoying, it seems to be sloppy programming on Docky's part.

Any idea how to stop it from doing this?

---

### Post by ikt on 2011-02-16
> **jermza said:**
> Not only is this annoying, it seems to be sloppy programming on Docky's part.

Any idea how to stop it from doing this?

I don't understand, if you can see the code why not fix it?

---

### Post by jermza on 2011-02-16
> **ikt said:**
> I don't understand, if you can see the code why not fix it?
I don't know the first thing about coding.

What I DO know is that Docky shouldn't give an error message on shutting now, as it seems sloppy and unpolished.

Just wondering if anyone else has had this problem and whether or not they fixed it.

---

### Post by ikt on 2011-02-16
> **jermza said:**
> I don't know the first thing about coding.

What I DO know is that Docky shouldn't give an error message on shutting now, as it seems sloppy and unpolished.

Oh, I thought you had looked at the code and saw that it was sloppy and then were complaining about that code.

> **jermza said:**
> 
Just wondering if anyone else has had this problem and whether or not they fixed it.

[https://bugs.launchpad.net/ubuntu/+source/docky/+bug/688804](https://bugs.launchpad.net/ubuntu/+source/docky/+bug/688804)

> Basically, this is a bug with gnome-session. It needs to know to shut down Docky before Compiz/Metacity.

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/612108](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/612108)

Just so you know an error occurring does not equal sloppy code, some people/programmers might find that a little trollish/insulting.

---

### Post by jermza on 2011-02-17
> **ikt said:**
> Oh, I thought you had looked at the code and saw that it was sloppy and then were complaining about that code.



[https://bugs.launchpad.net/ubuntu/+source/docky/+bug/688804](https://bugs.launchpad.net/ubuntu/+source/docky/+bug/688804)



[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/612108](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/612108)

Just so you know an error occurring does not equal sloppy code, some people/programmers might find that a little trollish/insulting.
Thanks for the links.  Will have a look.

By the way, I didn't say it IS sloppy; I said it SEEMS sloppy (and it DOES seem sloppy).  Nothing insulting about that, and my post history will tell you I'm not a troll.

---

### Post by bornagainpenguin on 2011-02-19
> **ikt said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/docky/+bug/688804](https://bugs.launchpad.net/ubuntu/+source/docky/+bug/688804)

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/612108](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/612108)



[Sigh]

Both of those reports have the same guy saying not my problem, talk to the other guys.  The second one has him saying this isn't even an issue at all!

When users encounter attitudes like that it really makes them want to shrug and walk away since clearly the developers could care less about the user's problems.

I'd like to add my two cents in at this point and agree that not fixing this issue makes the program look sloppy.  Trying to pass the buck or pretend it isn't an issue makes it look even worse.  If this makes me a troll...well I don't know what to tell you.

--bornagainpenguin

---

### Post by ikt on 2011-03-05
> **bornagainpenguin said:**
> I'd like to add my two cents in at this point and agree that not fixing this issue makes the program look sloppy.

Oh I agree, it does look sloppy, but that wasn't what was originally said.

> **jermza said:**
> Not only is this annoying, it seems to be sloppy programming on Docky's part.

He specifically stated that the program seems to be poorly coded, the first statement 'program looks sloppy' is an attack on how the program feels, the second is an attack on the programmers.

Slight difference but makes all the difference.

> **bornagainpenguin said:**
> Both of those reports have the same guy saying not my problem, talk to the other guys.  The second one has him saying this isn't even an issue at all!


That's because it isn't for him, there's nothing he can do about it.

> **bornagainpenguin said:**
> When users encounter attitudes like that it really makes them want to shrug and walk away since clearly the developers could care less about the user's problems.

Not at all, if you even slightly read the reports you would see it's an issue with gnome-session, the bug is there, and it needs to be fixed by the people who maintain gnome-session.

The bug report for gnome-session is here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/159160](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/159160)

Note the date it was opened, think I might open this upstream, see if it progress's any faster.

---

### Post by jermza on 2011-03-05
> Oh I agree, it does look sloppy, but that wasn't what was originally said.I said that it makes Docky's programming look sloppy, and I maintain what I said, whether or not you think it's insulting / trolling  whatever.  I - along with many new Ubuntu users - don't have the technical savvy to distinguish where, exactly, the sloppiness comes from.  All I know is that, when Ubuntu shuts down, Docky displays an error message, leading me - the average user - to believe that the fault lies with Docky.  

> He specifically stated that the program seems to be poorly coded, the  first statement 'program looks sloppy' is an attack on how the program  feels, the second is an attack on the programmers.Don't be silly (and overly sensitive).  There's no attack on anyone.  I simply said that "*it seems*".  I didn't make a statement of fact, thus meaning it is my opinion (which I'm entitled to).

Nevertheless, I will wait patiently for the bug fix (or Unity's new interface).

---

### Post by ikt on 2011-03-05
> **jermza said:**
> I said that it makes Docky's programming look sloppy.

Nope, you said "Not only is this annoying, it seems to be sloppy programming on Docky's part."

As in, 

"docky is poorly coded, causing this issue,"

not:

"this issue, is causing docky to appear poorly coded"

I'm just saying one is an attack on the programmer, the other is an attack on the program. for example:

"docky is poorly coded, causing this issue"

The programmer can respond by saying, "the program is not coded poorly, you can look at the code yourself".

however if you said the second statement, he could agree with you, "the issue does make the program look bad."

Small difference, completely different outcomes :)

> **jermza said:**
> 
Nevertheless, I will wait patiently for the bug fix (or Unity's new interface).

If you've got some time to muck around I suggest grabbing VirtualBox and the natty Alpha 3 and mucking around, unity is brilliant imo. 10/10 stuff. :KS

---

### Post by jermza on 2011-03-05
> Nope, you said "Not only is this annoying, it seems to be sloppy programming on Docky's part."

As in, 

"docky is poorly coded, causing this issue,"

You removed part of my sentence.  My full sentence has "it seems" in it.  Don't selectively read things.

I maintain what I said.  ***It seems*** to be sloppy programming on Docky's part because, well, that is what I see when Docky gives me an error message.  I don't see Gnome - or anything else - giving me the message (and I'm not going to enter into an inconsequential technical debate about from where inside Ubuntu the message, itself, is actually generated)

It is an opinion.  Not a factual statement.  I am entitled to express it.

You're being too touchy (and pedantic).  And I'm pretty sure that Docky's programmers won't feel attacked or threatened in any way.  Plus, it should be clear that my OPINION is not malicious and therefore not an attack on anything or anyone.  And if you feel that I am a troll, then please report me.

---

### Post by ikt on 2011-03-05
Relax :)

We're arguing about semantics, I don't think you're a troll or anything, I'm just curious about the wording of a particular sentence :p

> **jermza said:**
> You removed part of my sentence.  My full sentence has "it seems" in it.  Don't selectively read things.

Whether it has "it seems" in it or not is irrelevant, all "it seems" does is imply that you're not 100% sure, that doesn't change that you're making a statement about the quality of something.

"Docky seems to be poorly coded, causing this issue" is still an attack on the programmers.
"This issue makes docky seem to be poorly coded" is still an attack on the program.

"This car seems bad" attack on the car.
"This car seems to be built poorly" attack on the people who built the car.


> **jermza said:**
> 
I maintain what I said.  ***It seems*** to be sloppy programming on Docky's part because, well, that is what I see when Docky gives me an error message.

Ah so it seems I can focus on the source of the issue, an error message does not imply poor programming, in fact an error message may actually be a sign of good programming, as opposed to no error message, and the screen just locking up. :)

One of the big issues I have at the moment is with Ubuntu One, it has poor communication with users, I can't see when it's updated, how fast it's updated, the progress, any errors or issues at all... which makes it seem poorly coded. ;)

> **jermza said:**
> 
It is an opinion.  Not a factual statement.  I am entitled to express it.


You are entitled to express your opinion to a degree, if I say "I think x person is an idiot", it might be my opinion, but it's also an attack on a person.

> **jermza said:**
> 
You're being too touchy (and pedantic).

I know, I'm just arguing semantics because of the way the initial post came across to me... and I'm bored :D

---

### Post by jermza on 2011-03-06
Despite your bloated and selective response, I will maintain everything I said.  

- Ubuntu shuts down.
- A message appears, saying Docky is having some troubles.
- Me, the average user, thinks Docky is to blame and, thus, poorly coded.

Because it's what ***it seems***.  This isn't difficult to understand.

Whether or not you (strangely) believe my observation to be an "attack" (ha ha) on whatever / whoever is your concern and your sensitivities with which to deal.

My concern, however, is that Docky doesn't shut down properly.  But as I've said, it probably doesn't matter since Natty has its own dock which I'm excited to see. :D

---

