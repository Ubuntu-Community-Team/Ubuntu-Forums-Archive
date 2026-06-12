---
title: "Howto Hide Files inside JPGs -tweak hack?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-13
[http://www.youtube.com/watch?v=q6AQL55zMR4](http://www.youtube.com/watch?v=q6AQL55zMR4)

how do i do this in linux? can it be done?

---

### Post by travmanx on 2009-12-13
> **lance bermudez said:**
> [http://www.youtube.com/watch?v=q6AQL55zMR4](http://www.youtube.com/watch?v=q6AQL55zMR4)

how do i do this in linux? can it be done?

I believe it's done by this

cat f1 f2 > f3
f1 - jpeg
f2 - archive

A Image opener reads the file until the end of a JPEG source and a archiver searches through the file for the archive header file

like so

JPEG header
JPEG data
JPEG end
+
RAR header
RAR data
RAR end

So I would think that works.


EDIT: This works.

---

### Post by Shhnap on 2009-12-13
It's that easy because linux is awesome. This gets used quite alot but it's still [Steganography]("http://en.wikipedia.org/wiki/Steganography").

---

### Post by falconindy on 2009-12-13
"something bizzare like tar"

He actually sounded like he knew what he was talking about until that line. tar isn't even a compression format :(.

---

### Post by anewguy on 2009-12-14
Least of all not to mention that this has been a common way in the past to infect a Windows (gasp, I know, the "other" OS) PC, and I thought we tried to stay away from answering things like that in the forums?

Dave :)

---

### Post by CaptainMark on 2009-12-14
further to this im curious how you extract the files, on ubuntu nautilus think my jpeg is nothing more than a jpeg and gives no option to extract files when i right click, presumably theres a terminal program to do this

---

### Post by BenAshton24 on 2009-12-14
If you used a rar archive then extract it with this:
```
unrar e f3
```

---

### Post by CaptainMark on 2009-12-14
Okay i use zips and tar.gz, i got zip to work fine with $unzip secrets_zip.jpg but the tar.gz ive tested with is $tar -x secrets_tar.jpg and it just seems to stop, nothings happening, any ideas why?

---

### Post by ukripper on 2009-12-14
> **anewguy said:**
> least of all not to mention that this has been a common way in the past to infect a windows (gasp, i know, the "other" os) pc, and i thought we tried to stay away from answering things like that in the forums?

Dave :)

+1.

---

### Post by aimpau on 2009-12-14
...trying on my home folder now....:)

---

### Post by CaptainMark on 2009-12-14
> **ukripper said:**
> +1.
dont worry, im not interested in that, at work we use pcs that all access the same home folder, what id like is a way for the management team to be able to leave important financial information in there but not have to worry about everyone else seeing it, at the moment we all have usb drives, but sometimes they get lost, and if one manager is on a day off and his usb is at home we cant get it. having it all discuised on the network would save us a hell of a trouble

---

### Post by ukripper on 2009-12-14
> **CaptainMark said:**
> dont worry, im not interested in that, at work we use pcs that all access the same home folder, what id like is a way for the management team to be able to leave important financial information in there but not have to worry about everyone else seeing it, at the moment we all have usb drives, but sometimes they get lost, and if one manager is on a day off and his usb is at home we cant get it. having it all discuised on the network would save us a hell of a trouble

i thought that is why we have encryptions in place, and not dirty workarounds like that. have you considered truecrypt - [http://www.truecrypt.org/?](http://www.truecrypt.org/?)

---

### Post by falconindy on 2009-12-14
> **CaptainMark said:**
> Okay i use zips and tar.gz, i got zip to work fine with $unzip secrets_zip.jpg but the tar.gz ive tested with is $tar -x secrets_tar.jpg and it just seems to stop, nothings happening, any ideas why?
Probably because you need to tell tar its gzipped by using -xz instead of just -x.

---

### Post by lavinog on 2009-12-14
> **ukripper said:**
> i thought that is why we have encryptions in place, and not dirty workarounds like that. have you considered truecrypt - [http://www.truecrypt.org/?](http://www.truecrypt.org/?)

7z has built in encryption too.
I don't know why the video doesn't mention that...instead he says to use tar if you are paranoid???

---

### Post by anewguy on 2009-12-14
I suspect the reason for wanting to do this can't be what is mentioned, as there are so many other viable ways of protecting data.  I stand by my original post, and I plea to others to stop any more answers on this thread.

Dave :)

---

### Post by spiderbatdad on 2009-12-14
The concept is nothing new, and it is very simple to combine file types and separate the differences. This isn't black magic or rocket science. There is nothing wrong with having this information. Consider it educational. It is no different than speaking in code. You're either in the know or you're not.

---

### Post by Diametric on 2009-12-14
I respectfully, but highly object to anewguys approach.  Information is not dangerous, what you do with it can be.  This sort of information should be freely discussed in addition to the appropriate cautions/warnings.  Just because something *could *be used inappropriatly, does not mean we should begin censoring speech or ideas.

---

### Post by lavinog on 2009-12-14
> **anewguy said:**
> I suspect the reason for wanting to do this can't be what is mentioned, as there are so many other viable ways of protecting data.  I stand by my original post, and I plea to others to stop any more answers on this thread.

Dave :)

aww come on, I can see a use for this.
[i]'hey look this file is encrypted, it must be interesting, lets see if we can force him to give us the password.'
[/i]vs.[i]
'this guy doesn't seem to have anything on his computer except a bunch of cow pictures, and a bizzare tar file...I think we should leave this guy alone.'
[/i]
Truecrypt calls this plausible deniabilitiy.

---

### Post by earthpigg on 2009-12-14
> **Diametric said:**
> I respectfully, but highly object to anewguys approach.  Information is not dangerous, what you do with it can be.  This sort of information should be freely discussed in addition to the appropriate cautions/warnings.  Just because something *could *be used inappropriatly, does not mean we should begin censoring speech or ideas.

beat me to it.

---

### Post by anewguy on 2009-12-15
Let's see......if you know how to break into a server, create/send a virus, etc., you don't want to first ask WHY the information is needed?  Nobody up front asked why - they wanted to give HOW, as if trying to be the first to prove how much knowledge they have.

There's a valid objection here - too bad you can't see it.

---

### Post by Diametric on 2009-12-15
> **anewguy said:**
> Let's see......if you know how to break into a server, create/send a virus, etc., you don't want to first ask WHY the information is needed?  Nobody up front asked why - they wanted to give HOW, as if trying to be the first to prove how much knowledge they have.

There's a valid objection here - too bad you can't see it.

I see your objection, nothing in my reply suggests otherwise; I just do not agree with it.  

However, back to the more important topic at hand, whether or not "dangerous"  (and I use the term loosely) information should be censored.  The methods for making drugs or bombs or any other other "dangerous" activities should be freely available - and thankfully are despite the efforts of various legislators.  When you begin to curtail speech/ideas in the name of "safety" you have done just that  - curtailed the free flow of ideas, information and the right of people to exchange them.  This is a Linux forum, where an open source OS and all of its related files and programs are cussed and discussed ad nauseum.  To suggested to others that they should not contribute to this topic because of its **potential **is absurd.  That's what we're here for.  The thread originator may very well use this information for less than ideal purposes, but it is not up to you and I, in this forum to decide.  He/She has a right to learn it, and your efforts at thwarting that process amount to a form of censorship - stop it.  If you don't like it don't contribute, or report it to an administrator and let them do their job.

Please do not take my, somewhat, forceful reply personally.  I do not know you and we might be best friends one day - in fact, send me a friend invite.;)  I just cannot, under any circumstance, condone any efforts to limit the free flow of information and ideas.  We, Linux users, are better then that.

---

### Post by myolbug on 2009-12-15
Okay, so this then exposes an inherent weakness in Linux.  So instead of censoring info, how do you guard against this?

---

### Post by Diametric on 2009-12-15
> **myolbug said:**
> Okay, so this then exposes an inherent weakness in Linux.  So instead of censoring info, how do you guard against this?

If by "guarding against this" you mean guard against the potential abuse of a hack or such, then when replying make sure you include a warning or other such statement so that when you're giving someone information that has the potential to cause harm, you've given them the responsibility to make an informed choice. You can't make a choice for someone - you can only inform them as much as possible, but at some point the decision still rests with them.  However, I don't see how this "exposes and inherent weakness in Linux".

---

### Post by anewguy on 2009-12-15
Don't get me wrong - I'm all for freedom of speech, freedom of thought, etc..  There's a difference, however, between discussing those things in email or on another site - I just don't think a beginners forum for an OS is the appropriate place.  When things cross into murky waters, particularly when it is known that such things are showing how to do illegal activities (yes, at least in the U.S., it is illegal to create/populate a virus with known intent and that intent is purely to disrupt people), most forums similar to this one ban such activity.  There is still a thing called liability.  Want an example of something even less "sinister" in intent?  Go through the old camerahacking.com website (the domain name wasn't renewed, but I can point you to the web site if you want).  That site was dedicated mainly to the hardware hack and software hacks to make one-time use digital cameras from such places as CVS Pharmacy reusable.  The cameras require a "key" to unlock any communications with them.  Somewhere along the line, through whatever means, the code for generating the keys and unlocking the cameras was found and posted on the site.  This brought direct threat of legal action from the manufacturer, with the result being that the code had to be removed from the website and any links to that code had to be removed as well.  The owner of the domain name is the one who gets all the trouble.

Just saying - think about it first.  In answering a post would you be providing information purely because "everything has to be open and nobody can censor my data", or is it because it truely represents a legitimate concern (read "can't bring problems to the domain owner")?

That's all I'm getting at - keep it off this forum and find another means to communicate that type of information.

Understand I'm not taking offense to anything anyone is saying, and my remarks aren't meant in any way as a censoring of free thought and communication - just the medium in which the communication takes place.

Dave :)

---

### Post by earthpigg on 2009-12-15
those advocating that this informaiton be censored, please read this: [http://en.wikipedia.org/wiki/Streisand_effect](http://en.wikipedia.org/wiki/Streisand_effect)

the very act of objecting to this information being "out there" by posting in this thread demonstrates the effect in action -- way to send the information you dont want folks to see to the top of the thread list, thus ensuring that ***more*** people see it.

good game.


and, of course, if you choose to disagree with me and post a response in this thread to that effect... you perpetuate the effect even further.

can you bear to keep silent?! CAN YOU!?!!!

[IMG]http://imgs.xkcd.com/comics/duty_calls.png[/IMG]

<3 the internet.

(this is where you point out the irony of me posting the above comic, when my 1,866 beans are clearly visible :lolflag:...)

---

### Post by ukripper on 2009-12-15
> **earthpigg said:**
> 
can you bear to keep silent?! CAN YOU!?!!!

[IMG]http://imgs.xkcd.com/comics/duty_calls.png[/IMG]



Hmmm.. trying to relate this pic with the subject matter in this thread and failing miserably. Maybe it is time for me to retire from this thread.

---

### Post by northern lights on 2009-12-15
> **earthpigg said:**
> [http://en.wikipedia.org/wiki/Streisand_effect](http://en.wikipedia.org/wiki/Streisand_effect)

the very act of objecting to this information being "out there" by posting in this thread demonstrates the effect in action -- way to send the information you dont want folks to see to the top of the thread list, thus ensuring that ***more*** people see it.
I highly doubt that the issue at hand would ever be as interesting to the general public as Barbara Streisand's beachfront home.

We also choose not to give login-as-root-tutorials on this forum --> no Streisand effect there.

Noone is advocating censoring information, the notion is that certain information might just be inappropriate for these forums. That doesn't mean it's not allowed to exist elsewhere.

A not so direct answer might have been a good compromise. Instead of telling the OP (and everyone else reading this) directly how to do the above, a simple link to [man cat]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cat") would have sufficed. Either someone's able to read that file, or he or she should not know the above in the first place...

+1 for Dave.

---

### Post by Grenage on 2009-12-15
Considering how many bits of info could *potentially* be used to compromise a computer, these forums would be rather barren if they were all rescinded.

It's the same for computers as it is for every aspect of life.

Clay pigeon shooting? Noo, you might gun someone down.
Learning to drive, You might run someone over.
Handling cutlery? Think of the carnage!

---

### Post by wojox on 2009-12-15
[http://mozaiq.org/encrypt/](http://mozaiq.org/encrypt/)

---

### Post by ukripper on 2009-12-15
> **Grenage said:**
> 

Clay pigeon shooting? Noo, you might gun someone down.
Learning to drive, You might run someone over.
Handling cutlery? Think of the carnage!

Very valid in some context but not every.

How about giving a gun to a teenager who claim he will only shoot a clay pigeon, but he end up shooting the whole school.

---

### Post by northern lights on 2009-12-15
> **Grenage said:**
> Considering how many bits of info could *potentially* be used to compromise a computer, these forums would be rather barren if they were all rescinded.
Objectively false. Many a thread does not contain comparable information.

> **Grenage said:**
> Clay pigeon shooting? Noo, you might gun someone down.
Learning to drive, You might run someone over.
Handling cutlery? Think of the carnage!
Stretching a discussion into the realm of the ridiculous does not prove anyhting but a lack of more serious arguments.

How about information on how to build a timer for a C4 bomb? It is used in mining. But if you wanted to mine, you certainly wouldn't check that kind of thing on the internet. Same with this. For protecting sensitive data, there's much better ways.

---

### Post by Grenage on 2009-12-15
> Objectively false. Many a thread does not contain comparable information.

Let's remove all the DD guides, someone might wipe or inspect a drive they don't own. etc.

> Stretching a discussion into the realm of the ridiculous does not prove anyhting but a lack of more serious arguments.

Considering the subject matter in question, this argument requires no more than the ridiculous; it's completely laughable.

> For protecting sensitive data, there's much better ways.

In your opinion; horses for courses.

---

### Post by spiderbatdad on 2009-12-15
> **anewguy said:**
> Don't get me wrong - I'm all for freedom of speech, freedom of thought, etc..Just not here...and only if I approve the topic...and first I want valid reasons from those participating in the discussion, so I can make sure they don't have any ulterior motives, and I'd like to see any and all school records or possible police reports from all forum members, so we can weed out some of these bad eggs. :lolflag:

---

### Post by CaptainMark on 2009-12-15
> **falconindy said:**
> Probably because you need to tell tar its gzipped by using -xz instead of just -x.
This does the same thing???

EDIT: What the hell? I go away for a day and this post has completely lost track of the original question, I asked another question which I felt was within the topic of the original post title, it seems a beginner question to me so this forum seemed like a fine place.

For the record I am not a computer criminal, i wouldnt know how to spread a virus even if i knew how to make one, and would never want to. And two reasons for wanting to hide data this way, 1. As a previous post mentioned if people think theres nothing there to get at they wont try, 2. The work computers are administrated by head office IT dept so we cant install any software on them, seen as compression software is already installed by default, im trying to make the best use of what i have.

---

### Post by spiderbatdad on 2009-12-15
You have two options from synaptic package manager: steghide and outguess. They work similarly. By default steghide will encrypt your message and require a password. Outguess needs to be told to enctypt a plain text message. Steghide recognizes more file types. So: ```
sudo apt-get install steghide
``` Have a .jpg and a secret message text file handy.
```
$ steghide embed -cf vacation.jpg -ef secrets.txt -sf steg.jpeg
Enter passphrase: 
Re-Enter passphrase: 
embedding "secrets.txt" in "vacation.jpg"... done
writing stego file "steg.jpeg"... done

``` outguess uses slightly simpler format IMO. The -cf -ef -sf above stand for cover file, embeded file, steg file (output). So I hid secrets.txt inside vacation.jpg, and created a new file called steg.jpeg.
```
$ steghide extract -sf steg.jpeg
Enter passphrase: 
the file "secrets.txt" does already exist. overwrite ? (y/n) y
wrote extracted data to "secrets.txt".
$ cat secrets.txt
This is TOP SECRET.

```
ACK. sorry I misread...can't install any software.

---

### Post by CaptainMark on 2009-12-15
> **spiderbatdad said:**
> ACK. sorry I misread...can't install any software.Thanks for the effort though, the work ones are windows, so the zip format will do for most of what i need if for anyways

---

### Post by lance bermudez on 2009-12-15
I started this because i seen a video on youtube.com. I did not think it could be done on ubuntu. I also at the time of writing this did not know you could spread a vius this way. Nor do i want to spread a virus or any thing. I do not even know how to write a virus. True i should have thought out the possible trouble the post could have cuased but i just thought that if it was bad the ubuntu administrator would have issued me a warring and closed the post. I just thought that if i was not going to use the information for badness then no one else was going to use it for badness either. In fact sence i do not know encryption i just thought it would be a good way for me to store my files on my home computer for me only in an easy to understand simple way. one of you sounds a little parinod about the post. you for got to mention that if ubuntu was not going to give the info we could go ealse were to get it. that is if you know were and who to ask. as for me i do not i just know that if i want to know something i should come here bcuse the people here will keep me out of trobule (how the information should be used) and give me useful info

---

### Post by Grenage on 2009-12-15
I wouldn't worry.  Most of us assume that posters aren't terrorists.  If you start asking about uranium decay rates, we might get suspicious.

---

### Post by lance bermudez on 2009-12-15
I wouldn't worry.  Most of us assume that posters aren't terrorists.  If you start asking about plutonium decay rates, we might get suspicious.

isnt that what goodle is for? ha ha

thanks

---

### Post by Grenage on 2009-12-15
It certainly is ;)

---

### Post by earthpigg on 2009-12-15
> **Grenage said:**
> I wouldn't worry.  Most of us assume that posters aren't terrorists.  If you start asking about uranium decay rates, we might get suspicious.

that sounds like a good project for my rather pathetic but developing programing skills!

---

### Post by Grenage on 2009-12-15
Sounds like a plan, I shall start the refinery!

---

### Post by t0p on 2009-12-15
I dunno, some of you people are daft.  It might interest (horrify) you to learn that there is a steganography utility in the repositories:

```

sudo apt-get install steghide
```So is it against the CoC to tell members about a program in the repos?  Is it against the CoC to tell members of other methods to copy the functionality of a program in the repos?  Are approved applications not to be spoken of here?

Incidentally, there are good reasons why a member might want to use steganography.   The people you want to hide files from are not necessarily righteous.  Just because an app can be used for evil, must it be frowned upon?  I can think of countless evil purposes that Truecrypt could be put to.  Heck, a *web browser* can be used for evil.  What is it about steganography that makes it uniquely bad?

---

### Post by sdowney717 on 2009-12-15
i did this once in a windows program as a proof of concept idea to code for people who had paid for a program. i had a list and somehow i matched words within the list hidden in the jpeg file to code words they gave me. I would have to dig thru it again to remember what i did, but it worked pretty good. The unlock code generated was unique to them alone and could not be used on another system.

---

### Post by anewguy on 2009-12-15
Obviously some of you are confused - I am not paranoid about freedom of speech, freedom of thought, etc..  What I *am* against is the idea that any information, no matter what it could be used for, be populated on THIS forum.  I didn't say it can't be posted anywhere else your heart desires.  I don't know if they still do, but as an example at one time this forum referred people wanting to know how to copy protected DVD's to other places and not post the actual answer here.  Nit-picking - I think not - the actual information is not posted here.  I doubt you'd find the needed information for one of your aforementioned bombs in this forum - why is it so bad to just place the information for another type of bomb somewhere other than this forum?

For the people suggesting things from the repositories - 2 questions:  (1) why didn't you answer the post saying "try X from the repositories", (2) why didn't you answer earlier?  :):)

I am curious, since some of you seem to think I'm sort of anti-freedom person, how many of you grew up in the 60's?  I'm way past 50 and did.  What do you think we fought for all those years?

To the original poster - I apologize as nothing was meant to insult you, rather it was meant to direct these types of things elsewhere away from this forum.

I'm probably going to get banned or something from the forum now for using MY freedom of speech.  Any of you know what irony is?

Dave :)

EDIT:  And to save you the trouble, though you have the freedom to do so as well, I have already reported my own post.

---

### Post by CaptainMark on 2009-12-15
Uranium's half life is 4.47 billion years according to wikipedia if you needed to know, now thats a bomb with a decent shelf life!

Ps. 4 pages later and i still cant untar my jpg, any ideas? tar-zx /path_to_file doesnt wanna work

---

### Post by anewguy on 2009-12-15
That's almost the half-life of some of my uncle's underwear! :)

Sorry I can't help you further on your problem.

Dave ;)

---

### Post by Spiritof76 on 2009-12-16
I too am a child of the 60s and understand that we must have weapons to defend our freedom against the oppressors.  Steganography isn't a weapon to oppress it is not a good way to drop a virus, Viri aren't easily spread by passing them through a jpg, the only way you can pass them with data is to cause some sort of buffer overflow. that will react with the program opening the data.  That is way beyond this discussion.  

Computers, Ubuntu and the Ubuntu community in particular is about freedom, There are repressive governments that attempt to repress the basic human right of freedom of expression. Uganda, San Fransisco and China come to mind. It is important to provide these people with means to speak out to the rest of the world. Steganography is one of these tools that are about freedom, and privacy.

---

### Post by earthpigg on 2009-12-16
> There are repressive governments that attempt to repress the basic human right of freedom of expression. Uganda, ***San Fransisco*** and China come to mind.

:lolflag: thats my city!

---

### Post by anewguy on 2009-12-16
Again, point sadly missed.  The information being sought wasn't for a particular tool in the repos, it was for specifically encoding something inside of a jpeg, and yes this HAS been used to populate virus and trojans to (gasp again) Windows platforms.

I also fully understand people in the world not having a life anything like that which I have the freedom for. I also have fought to have things like (double-gasp) Windows 98 retained and maintained since I know there are many, many people in the world without access to the types of things I have access to.  I also applaud the open software community for its fantastic efforts. 

The point is that if something is a tool in the repos, point to it as a substitute for what the user was trying to do (and please don't say "we pointed out how to use a tool in the repos", because you know what I'm saying and that ISN'T it).  I hate doing this, as it makes it sound like I am against all kinds of things and accusing the original poster, which I am not.

Legitimate tools have a reason for being and should be recommended.  Spirally off saying every tool in the repos could be used for evil is COMPLETELY off the point.  The original responses were NOT pointing to any of the encryption tools in the repos, but rather right away telling someone how to imbed something else inside a jpeg.  That simple, and it's that information that should be pointed to off this site.  No breaks in freedom, no breaks in what you can do.  Everything has it's place, but providing THIS SPECIFIC METHOD of doing it WAS/IS a common way of corrupting a (gasp yet again) Windows machine.  If you really do value the freedoms you talk about, and the lack of repression, etc., then why in the world would you want to post here of all places the means to corrupt someone else's computer?

Use valid encryption, etc., tools to your hearts content.  Discuss them openly.  For THIS PARTICULAR METHOD (again, I really don't see why some of you refuse to understand something this simple) please link to information off this site.  I'm not saying don't discuss it, I'm not saying don't share, I'm not saying don't point to it off this site, I'm not saying ban all VALID encryption tools/means as are in the repos (no, no matter what you say, putting data in a jpeg just isn't the way to accomplish this).


Just so you know, I'll be reporting my own post again.  Please use your freedom to do so as well.

Dave

---

### Post by Spiritof76 on 2009-12-17
I blieve your refering to a very old issue in Internet explorer rendering where a jpeg could be expanded, with the right data to cause a buffer overflow condition. This was a trojan horse not really a virus, There is a good discussion about [the myth of jpg viri here]("http://www.security-forums.com/viewtopic.php?t=12541&postdays=0&postorder=asc&start=0").

---

### Post by lavinog on 2009-12-17
Dave,
I understand your intentions, and this trick can be used to embed malacious files, but there is no way to execute the code.
This trick does not serve much purpose for malacious intents.  It can be useful for plausible deniability where use of encryption is illegal.

---

### Post by llawwehttam on 2009-12-17
lol i recently made a post on another forum telling someone how to reset their root password because they had lost it. I think that is more dangerous than this.

And a virus can be disguised as a jpg forinstance nastyvirus.jpg.exe and some computers wouldn't show the .exe part but i believe that its also possible to place a virus inside a jpg.

---

### Post by northern lights on 2009-12-17
> **llawwehttam said:**
> 
And a virus can be disguised as a jpg forinstance nastyvirus.jpg.exeThat's not *inside* a jpeg, that's *disguised as*.

---

### Post by anewguy on 2009-12-17
> **llawwehttam said:**
> lol i recently made a post on another forum telling someone how to reset their root password because they had lost it. I think that is more dangerous than this.


First, not an attack in ANY way shape or form to you llawwehttam, but rather to expand upon what you posted:

And, if you hadn't noticed, there has always been a refrain on this forum from showing people how to activate root (so as not to be a danger to THEMSELVES).  Besides the bad activity possibility, there's also the idea here of protecting the user from themselves - don't know if you'll understand that either.  That's all I'm saying about this particular instance.  I really thought the point of just moving this off of THIS forum would be easy to understand - apparently not.

Yes, this was one way to take advantage of some of the buffer overrun problems in IE and thereby exploit a system.  Yes, there have been patches to supposedly fix that problem, but not everyone will have those patches.  Yes, it's on "that other OS".  Doesn't responsibility come with freedom and openness?  Don't we owe to our other computer bretheren, no matter what OS or skill level, to not directly contribute to a known potential problem from this forum?  I thought we did. 

People seem to blowing this way out of proportion, and making some rather outlandish comparisons.  Again, for the particular question asked, why is it so hard to say "look here" for an answer to your question?  If this is a way for people in parts of the world where things are repressive to be able to protect their data, fine, I have no problem with it, but given the potential for THIS PARTICULAR THING ONLY, why not move the answer off this forum?  Again, the forum has always refrained from telling people how to activate root login (even though it is extremely simple) because they (1) want to protect them from rendering their own system inoperable (2) don't want to have people inadvertedly open their system up to attack.  Doesn't say don't ever post it any where, just not in this forum.  Why is this so hard to understand in this instance?

Dave :)

---

### Post by llawwehttam on 2009-12-17
Thanks anewguy, I should have made my post more clear. Just to clarify, in my last post I was not telling people how to activate their root account. I was merely giving an example of some help I had given some-one else with resetting a FORGOTTEN root password as it was a red hat based machine in question so root was already activated as it is quite necessary for red hat machines. 

And northern lights if you had read the post which you even quoted, I said DISGUISED not inside. But maybe I wasn't clear enough. 

Anyway I see no constructive point in this thread in the first place. If you want to use this method to secure your computer try encrypting your drive and setting BIOS and GRUB/LILO passwords and having a decent root/ administrator password instead. The only time I have ever used this sort of thing was for experiments to see what I could do and that was not with good intentions so please do not use any information on this forum for malicious uses as that just ruins everyones day.

Personally I always use the root account in terminal for modifying 'system' files but I have been using various linux distros for years and that was the way it was done in earlier versions of fedora. 
With Ubuntu unless you are very skilled with the command line there is no need whatsoever for the root account to be used as sudo is fine and I would never recommend some-one new to linux to use it. 

After all the root account is like having the power of God inside your computer, not a good idea unless you know how to use that power carefully.

---

### Post by anewguy on 2009-12-17
Thanks for the reply!  Your point about the root account, and trying something like this, is exactly the simple point I was trying to make.  Like you, I see no need to continue this, as I thought it was a simple idea and simple request - no censoring, etc., just a request to move it away from this forum.  Considering I have reported my own posts twice now in this thread, I was hoping one of the moderators might somehow bring a little enlightenment on this in a kind and constructive way, and then close the thread.  

I guess they're just waiting for me to hang myself!  :):)

dave :)

BTW - llawwehttam, I apologize for the wording of my previous post - the "you" I used in there was supposed to be a generic "you" to people reading the thread, and going back over it I can see where you might think I was referring directly to you.  I apologize if it came across that way as it wasn't meant to!

---

### Post by northern lights on 2009-12-17
> **llawwehttam said:**
> And northern lights if you had read the post which you even quoted, I said DISGUISED not inside. But maybe I wasn't clear enough.Nopes, that was quite clearly stated actually. Probably my daftest post on these forums ever. F***in A, I need more sleep.

:)

---

### Post by cariboo on 2009-12-18
It seems that this thread has run it's course. Next time something like this comes up it should be posted in the [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") sub-forum, as this type of discussion is welcome there. This thread is closed.

---

