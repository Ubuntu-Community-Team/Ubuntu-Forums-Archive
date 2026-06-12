---
title: "Password management in Ubuntu"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Ryan20 on 2011-03-21
[FONT=Arial]Hi guys,

My questions are inspired after reading an article by Bruce Schneier about the security of our passwords from program-guessers.  [/FONT][http://www.schneier.com/essay-148.html](http://www.schneier.com/essay-148.html)

Was interested (and by interested I mean horrified) by this part:

> What's happening is that the Windows operating system's memory  management leaves data all over the place in the normal course of  operations. You'll type your password into a program, and it gets stored  in memory somewhere. Windows swaps the page out to disk, and it becomes  the tail end of some file. It gets moved to some far out portion of  your hard drive, and there it'll sit forever. Linux and Mac OS aren't  any better in this regard.I'm wondering if anyone can explain this in further detail for me.  What's he mean by our passwords becoming the tail-end of other files - and why would they do that?  Where is this "memory somewhere"?

I looked around on Google and found a few articles explaining that Linux saves passwords at /etc/passwd so I typed that into the terminal to see what would happen (yes I realise to those who know computer commands, I must sound like a real idiot ha ha).  Is it possible to look at this file?  

I also read another article about "Shadow Suite" ([http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.htm](http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.htm)) but I don't understand how this stops a cracker from just cracking into the "root" before accessing that also?  Where the heck is the website for Shadow Suite anyway?

I'm sorry for the mountainload of questions. I have more but I'll stop there.  I just need someone who can explain these things to me in easier terms or refer me to some place I can learn all about it.  All the articles assume prior knowledge...

Thank you, 

Ryan

---

### Post by andrewthomas on 2011-03-21
> **Ryan20 said:**
> 

I also read another article about "Shadow Suite" ([http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.htm](http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.htm)) but I don't understand how this stops a cracker from just cracking into the "root" before accessing that also?  Where the heck is the website for Shadow Suite anyway?


[http://tldp.org/HOWTO/Shadow-Password-HOWTO.html](http://tldp.org/HOWTO/Shadow-Password-HOWTO.html)

[Shadow-Password-HOWTO]("http://tldp.org/HOWTO/Shadow-Password-HOWTO.html"),  *Linux Shadow Password HOWTO*

[SIZE=2]***Updated: Apr 1996***[/SIZE]. How to obtain, install, and configure the Linux password Shadow Suite.

That page is fifteen years old.

---

### Post by Ryan20 on 2011-03-22
But was some of the information still relevant to today?  The other article by Bruce was only about 4 years old.

---

### Post by mcduck on 2011-03-22
Some, sure, but some is just plain nonsense. Like this, for example: "Windows swaps the page out to disk, and it becomes the tail end of some file. It gets moved to some far out portion of your hard drive, and there it'll sit forever".

swappwed data definitely doesn't sit in your hard drive forever, if it did you'd have to buy new hard drives every now and then as the old ones would fill up because of swapping. Instead hard drives are actually bale to *overwrite things* (:D), the same swap space gets used over and over again and thus anything writen there would get overwritten sooner or later. Usually pretty soon if your computer is actually using the swap.

Besides, most systems don't really use much swap these days, any modern system will have enough RAM to handle all normal usage so there's no much need for swapping. And even if there was, passwords aren't really the kind of thing that any program or OS would need to keep in memory, and thus they wouldn't ever end in swap either.

---

### Post by grahammechanical on 2011-03-22
The writer of that article is also wrong about this point:

> it becomes  the tail end of some fileAnd we would be wrong if we were to think that all our documents are on a part of the hard disc called Documents. When we use a file manager we are seeing a representation of the hard disc and not the actual state of the hard disc and where the data is actually on the disc.

When a blank hard disc is formatted for the first time the space is marked in clusters. I am not explaining this well. Here is a link that explains it better than I,

[http://searchexchange.techtarget.com/definition/cluster](http://searchexchange.techtarget.com/definition/cluster)

A password can be stored in the next cluster to some other file but it cannot become the tail end of that other file for it is also a file.

Hard discs are just that discs. Large hard discs are in fact several discs stacked on top of each other. The data in a document may actually be stored on different parts of different discs in the hard disc. This is how the system works. It is not something to panic over but some journalists like to cause a sensation with their articles. 

It does explain why the police take the hard disc out of a computer when they are investigating certain types of crime and why the best way to stop someone finding out what is on your hard disc is to smash it into pieces.

For most of us the key to protecting our passwords and data is first, ourselves, and second the operating system.

Regards.

---

### Post by Ryan20 on 2011-03-22
Thanks for the great responses and the link!    

So even if the author of that article did write a bit of nonsense it's still logical to believe that passwords would be stored somewhere for programs to access later no?  The reason I ask is because I was thinking of following some of his advice as far as making passwords more secure (using the entire keyboard and putting the root of the password after or in between) but I also want one place to store them all. I've been wanting to use Firefox's feature for remembering passwords for many years as well as the form-filler but I want to know how that gets stored too.

I realise how paranoid I sound, but when I was a kid my grandad told me about a program he found that could restore deleted folders and files.  The initial reaction was "wow that's useful" the second being "holy crap, that's scary!"  You're right, the best security is to keep it on you but as far as going about your second option, the OS, it would be nice to know how these things are stored so that I know where I'm dropping crumbs.

I also want to use some sort of password storage program even though admittedly I haven't done any research on that yet.  It's nerve wracking to think that I could have one master password loosely stored on my system that could be easily accessed.  Does /ect/pssword really exist?   And if someone had access to it, could they find the exact cluster the password is stored in?  It's still a very real threat if someone cracked into your system and attacked this folder with these password guessing programs, no?   

Again, thanks for the great responses.

---

### Post by JKyleOKC on 2011-03-22
> **Ryan20 said:**
> I also want one place to store them all. I've been wanting to use Firefox's feature for remembering passwords for many years as well as the form-filler but I want to know how that gets stored too.

(snipped)

I also want to use some sort of password storage program even though admittedly I haven't done any research on that yet.  It's nerve wracking to think that I could have one master password loosely stored on my system that could be easily accessed.  Does /ect/pssword really exist?   And if someone had access to it, could they find the exact cluster the password is stored in?While Bruce is one of the leading experts on computer security, some of his writings tend to be a bit over-sensational, not to mention over-simplified.

To begin to understand how passwords are treated these days, you have to be aware of the advanced cryptographic programs that are now commonplace. These are what's used to provide "secure" web pages for online banking and the like. A data stream encrypted by these techniques theoretically COULD be decrypted, but the best estimates that it would take longer than the Earth has existed to do so. For all practical purposes, they are secure.

When you create a password on your computer, such a program is used to encrypt it, and what's stored is the encrypted version rather than the password itself. The /etc/passwd file does, in fact exist, and it stores these encrypted versions. When a program asks for a password, it then encrypts it using the same keys (which are built into the system), and compares this encrypted version to what's stored on disk.

The Firefox password manager works the same way. I have no qualms about using it to keep my credit card and banking passwords, even without setting a master password to increase its security.

The important thing about passwords is to make them difficult to guess, and to avoid using the same one everywhere. My passwords are usually random strings of letters with mixed upper and lower case, plus a couple of numbers. This prevents a bad guy from simply going through a dictionary list, trying one word after another until he hits the one you chose. Longer passwords are better, simply because they cause brute-force attempts to crack them take much longer. If it will take three years of constant effort to learn your password, the bad guy will simply quit and try someone else. For instance, "MyDogHasFleas" would be a much better password than just "MyDog" because of this (although neither would really be very strong in this era of malware).

---

### Post by Ryan20 on 2011-03-24
Sorry it took so long for me to reply, been a little busy but I appreciate you taking the time to write such a big response.   It was very clear, informative and helped me out a lot!

---

### Post by JKyleOKC on 2011-03-24
You're quite welcome!

---

