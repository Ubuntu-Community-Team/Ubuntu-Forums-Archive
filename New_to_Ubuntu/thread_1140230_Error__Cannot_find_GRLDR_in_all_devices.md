---
title: "Error:  Cannot find GRLDR in all devices?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Servopal on 2009-04-27
Hi - My first post - please don't bite me?!

I've been really impressed by a friend's ubuntu machines, and wanted to give it a try.

He said I could do this 'risk free' by installing it inside windows, and even gave me a copy of the latest ubuntu.

It installed OK, and now I have the option to boot into either Windows or Ubuntu.  But when I pick Ubuntu, I get the error message

Cannot find GRLDR in all devices.

I asked my friend, who told me to do a 'defrag' and disk check.  I did, but still got the problem.  Then he admitted he was clueless about it, but he told me I would 'definitely' get a solution here.

I'm not sure about that, because you'll probably need all sorts of tech info, to help me?
And I'm a PC user, not a PC expert.

I would LOVE to be a Ubuntu user, and would be grateful if anyone can either advise me what's wrong or (gently) let me know that I'm not enough of an expert to ever fix this.

But I'm hoping someone can help, since this is 'Linux for Human Beings.'

Thanks!

---

### Post by Servopal on 2009-04-28
Hi, 

Sorry to post this as a 'reply' to my own question, but I'm totally 100% stuck.

I've found other forum threads on the exact same problem (some of them YEARS old!), and reading through them, it seems that the problem is either:

a) impossible to fix, so just try a different sort of Linux instead (PCLinuxOS was mentioned)

or

b)  Really, really, really, really, really, really hard to fix. (In which case, I have no chance whatsoever)

So I thought I'd have one more try.  My Ubuntu friend said I would definitely get an answer of some sort in this forum, but it seems not....

Maybe it's just God's way of saying, 'Stick with Windows, dummy - you're not smart enough for Ubuntu!'  Anyway, if anybody can help, I'd be really grateful.

---

### Post by d1gw33d on 2011-07-08
This is why Linux in general will always be obscure garbage. I mean really? I've dabbled in Ubuntu and other flavors over the years and am by no means knowledgeable but know quite a bit about computers in general. 

I got a new notebook I wanted to have an unbuntu install on. Come to the website and go with a Wubi install as its "simple and safe." 

But the ******* thing doesn't work. 

"Error: Cannot find GRLDR in all dvices. Press Ctrl+Alt+Delete"

Are you kidding me? Searches on this provide results from over 4 years ago WITH NO RESOLUTIONS. 

Way to fail.

---

### Post by bcbc on 2011-07-08
> **d1gw33d said:**
> This is why Linux in general will always be obscure garbage. I mean really? I've dabbled in Ubuntu and other flavors over the years and am by no means knowledgeable but know quite a bit about computers in general. 

I got a new notebook I wanted to have an unbuntu install on. Come to the website and go with a Wubi install as its "simple and safe." 

But the ******* thing doesn't work. 

"Error: Cannot find GRLDR in all dvices. Press Ctrl+Alt+Delete"

Are you kidding me? Searches on this provide results from over 4 years ago WITH NO RESOLUTIONS. 

Way to fail.

Please refer to [http://ubuntu-with-wubi.blogspot.com/2011/01/wubildr-wubildrmbr-and-grldr.html](http://ubuntu-with-wubi.blogspot.com/2011/01/wubildr-wubildrmbr-and-grldr.html) for a discussion of this issue and the potential causes.

Wubi is designed for easy trial for Windows users that are afraid of partitioning or don't want to unless they are sure they will keep Ubuntu. It does work for most without hassle, but of course not everyone (for obvious reasons).

I suggest - if you cannot resolve this problem - then you can try out Ubuntu in the following ways:
1. from a CD or USB stick
2. from a virtual machine
3. from a direct install (with partitioning)

While it's obviously frustrating that things didn't just work first time for you on your new machine... you probably want to avoid calling Linux garbage. It's inflammatory and most likely won't get you any help.

---

### Post by Rohit Sahu on 2013-02-19
> **Servopal said:**
> Hi - My first post - please don't bite me?!

I've been really impressed by a friend's ubuntu machines, and wanted to give it a try.

He said I could do this 'risk free' by installing it inside windows, and even gave me a copy of the latest ubuntu.

It installed OK, and now I have the option to boot into either Windows or Ubuntu.  But when I pick Ubuntu, I get the error message

Cannot find GRLDR in all devices.

I asked my friend, who told me to do a 'defrag' and disk check.  I did, but still got the problem.  Then he admitted he was clueless about it, but he told me I would 'definitely' get a solution here.

I'm not sure about that, because you'll probably need all sorts of tech info, to help me?
And I'm a PC user, not a PC expert.

I would LOVE to be a Ubuntu user, and would be grateful if anyone can either advise me what's wrong or (gently) let me know that I'm not enough of an expert to ever fix this.

But I'm hoping someone can help, since this is 'Linux for Human Beings.'

Thanks!


Solotion :- Log into Windows. You might have installed Ubuntu using Wubi on either C:/ drive or any other drive. Go to "ubuntu" folder in the location where ubuntu is installed. Copy wubildr and wubildr.mbr from this location and paste it in C:/ (not inside any folder).

Now reboot. . .and try booting into Ubuntu. . I'm sure. . it works. . .

---

### Post by Rohit Sahu on 2013-02-19
Solution :-  Log into Windows. You might have installed Ubuntu using Wubi on either C:/ drive or any other drive. Go to "ubuntu" folder in the location where ubuntu is installed. Copy wubildr and wubildr.mbr from this location and paste it in C:/ (not inside any folder).

Now reboot. . .and try booting into Ubuntu. . I'm sure. . it works. . .

---

### Post by oldos2er on 2013-02-19
Old thread closed, please don't bump old threads.

---

