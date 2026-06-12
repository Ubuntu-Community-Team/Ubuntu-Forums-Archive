---
title: "Repository troubles?  Or  ..."
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Langstracht on 2009-04-06
I am having trouble with installing boxee, the following being the dialogue following $ sudo apt-get install boxee:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
python-mutagen apturl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
boxee
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/43.0MB of archives.
After this operation, 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
boxee
Install these packages without verification [y/N]?

And this is what installs. 0B!

Meaning exactly what I'm not sure.  I've had an ongoing interaction with boxee and they are adamant there is nothing wrong at their end - and they're probably right.  But does anyone have any idea what might be causing this (mis)behaviour?  A wrong setting somewhere perhaps ...

The (added) repository is "http://apt.boxee.tv hardy main".

Appreciate any assistance.

---

### Post by davec64 on 2009-04-06
Have you tried doing what it says and running: 

```
sudo apt-get autoremove
```

This will remove the packages that are no longer required.

You can then do:

```
sudo apt-get install boxee
```

---

### Post by Langstracht on 2009-04-06
Actually I had ... but I may have typed autoremove boxee rather than just autoremove.

In any event I did it again ... and while the report was still "0B" to download ... it now said it was going to use an extra 10 Meg of disk space.  Yes!  I thought, hope springing eternal.

But no, the same behaviour as before - there is a boxee icon, clicking on it blackens the screen momemtarily and there is a start up box on the active programs panel.  It persists for a number of seconds ... and then just goes away.

So now, suspecting a bad installation (rather than no installation) I went through the remove, purge, install routine again.  And with the same results.  Once more 0B.

(...sigh...)

---

### Post by gn2 on 2009-04-06
Do you have a 64-bit installation?

According to Wikipedia, Boxee is 32-bit only.

Apparently there is a way of making it run in 64-bit: [http://ubuntuforums.org/showthread.php?t=962134](http://ubuntuforums.org/showthread.php?t=962134)

---

### Post by Langstracht on 2009-04-06
No only 32.

---

### Post by davec64 on 2009-04-06
As that didn't seem to work, what about compiling from source?

---

### Post by Langstracht on 2009-04-06
Well ... I considered doing just that.  However I was completely put off by the troubles I read about in doing so.  Some claiming it cannot be compliled, others missing files and other troubles.  And, I was assuming, they are probably more adept at doing this kind of stuff than I am.  

However if someone "knows" it works and can provide the equivalent of a script (i.e. mind bogglingly pedantic) to do so I'd be prepared to give it a try.

All of that said though I can't help but thinking that there's something simple (albeit critical) missing or mis-set or something ...  Other software (comparable in the output sense if not the technological one) such as Miro, ChannelChooser and YouTube work just fine.

---

### Post by davec64 on 2009-04-06
I gotta agree with you there must be a simple fix, unfortunately I can't see it! :)

In the past autoremove has solved it for me and my installation troubles. Best of luck finding a solution.

---

### Post by Langstracht on 2009-04-06
I don't know that you said but, do you have boxee working on your machine?

I am using ubuntu 8.04 and intended to keep doing so until the next LTS shows up.

I notice(d finally) that you're using 8.10 ... and I am wondering if I might get over whatever ails me by abandoning my position and upgrading "now".

Any thoughts?

---

### Post by davec64 on 2009-04-06
I'll be honest boxee is something I've never heard of!
So I've added the repository you're using and installed via synaptic.
There were 17 packages in total for my install.

Installation was successful and the programme launched successfully. 

i'd guess from this that either the packages in that repository aren't compatible with 8.04, or perhaps the dependancy files you have in 8.04 aren't compatible with boxee.

So for me it works on 8.10.

It looks like an upgrade to 8.10 might solve the issue :)

Now I'd better go and see what this boxee thing is I've installed :)

---

### Post by davec64 on 2009-04-06
Just spotted! I used the Hardy repository in Intrepid!

Still worked!

---

### Post by Langstracht on 2009-04-07
And it looks like I have an upgrade to do!

It'll have to be (much) later today.

I'll be sure to report one way or the other.

Hope you find that boxee (and me!) was worth the trouble.

---

### Post by davec64 on 2009-04-07
Sorry I couldn't have been more help!

Still playing with boxee, looks good!

---

### Post by Langstracht on 2009-04-08
Change in plans.

I finally figured out how to find out what kind of card I have [ATI R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)] and I'm told THAT is my problem, rather than 8.04/8.10.

Don't know whether it's true or not.

I reckon on waiting a day or two to see if anyone responds on this thread.  And, if not, I'll start a new thread specifically on this subject.

Thanks again.

---

### Post by davec64 on 2009-04-08
Hope you gewt it sorted!

All the best

---

